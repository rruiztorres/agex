<template>
    <div>
        <!-- 27 CESIÓN DEL CONTRATO -->
        <h3>27.- CESIÓN DEL CONTRATO</h3>
        <br/>
        <v-row class="rowGroup">
            <v-col cols="12">
                <h5>Conforme al artículo 214 de la LCSP, este contrato podrá ser cedido:</h5>
                <v-radio-group v-model="datos.cesion">
                    <v-radio label="Si; siempre que se cumplan los requisitos del artículo 214 de la LCSP" :value="true"></v-radio>
                    <v-radio label="No" :value="false"></v-radio>
                </v-radio-group>
            </v-col>
        </v-row>
        <br/>

        <!-- 28 SUBCONTRATACIÓN -->
        <h3>28.- SUBCONTRATACIÓN</h3>
        <br/>
        <v-row class="rowGroup">
            <v-col cols="12">
                <h5>Parte de los trabajos, en atención a su especial naturaleza, deben ser ejecutados
                    directamente por el propio licitador o por una de las empresas de la UTE 
                    [artículo 75.4 LCSP]
                </h5>
                <v-row>
                    <v-col cols="12" md="1">
                        <v-radio-group v-model="datos.subcontrata">
                            <v-radio label="Si" :value="true"></v-radio>
                            <v-radio label="No" :value="false"></v-radio>
                        </v-radio-group>
                    </v-col>

                    <!-- EN CASO AFIRMATIVO -->
                    <v-col cols="12" md="6" v-if="datos.subcontrata === true">
                        <h5>En caso afirmativo, justificar:</h5>
                        <v-text-field filled label="Justificación" v-model="datos.subcontrataJustif"></v-text-field>
                    </v-col>

                    <!-- TRABAJOS A REALIZAR -->
                    <v-col cols="12" md="5" v-if="datos.subcontrata === true">
                        <h5>Trabajos a realizar directamente por adjudicatario:</h5>
                        <v-text-field filled label="Trabajos" v-model="datos.subcontrataTrabajos"></v-text-field>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
        <br/>

        <!-- 29 FACULTADES DE INSPECCION -->
        <h3>29.- FACULTADES DE INSPECCIÓN DE INSTALACIONES Y OFICINAS DEL CONTRATISTA</h3>
        <br/>
        <v-row class="rowGroup">
            <h5 class="subtitle marginL">
            El órgano de contratación ostenta la facultad de inspección de las actividades
            desarrolladas por el contratista durante la ejecución del contrato
            en los términos establecidos en el artículo 190 de la LCSP            
            </h5>
                <v-col cols="12">
                    <v-radio-group v-model="datos.facultInspecc">
                        <v-radio label="En este contrato el ejercicio de esta facultad sí se extiende a la inspección de las instalaciones, oficinas y demás emplazamientos en los que el contratista desarrolle sus actividades." :value="true"></v-radio>
                        <v-radio label="En este contrato el ejercicio de esta facultad no se extiende a la inspección de las instalaciones, oficinas y demás emplazamientos en los que el contratista desarrolle sus actividades" :value="false"></v-radio>   
                    </v-radio-group>
                </v-col>

                <v-col cols="12" v-if="datos.facultInspecc === true">
                    <h5>En caso afirmativo, justificar: </h5>
                    <v-textarea auto-grow filled v-model="datos.justifFacultInspecc"></v-textarea>
                </v-col>
        </v-row>
        <br/>

        <!-- 30 PLAZO DE RECEPCIÓN -->
        <h3>30.- PLAZO DE RECEPCIÓN</h3>
        <br/>
        <v-row class="rowGroup">
            <v-col cols="12" md="2">
                <h5>Plazo:</h5>
                <v-radio-group v-model="datos.plazoRecep">
                    <v-radio label="Un (1) mes." :value="true"></v-radio>
                    <v-radio label="Otro" :value="false"></v-radio>
                </v-radio-group>
            </v-col>

                <!-- EN CASO DE SER OTRO ... -->
                <v-col cols="12" md="3" v-if="datos.plazoRecep === false">
                    <h5>En caso de ser otro plazo, especificar:</h5>
                    <br/>
                    <v-text-field filled label="Plazo" v-model="datos.otroPlazo"></v-text-field>
                </v-col>

                <!-- JUSTIFICAR ... -->
                <v-col cols="12" md="7" v-if="datos.plazoRecep === false">
                    <h5>Justificación:</h5>
                    <br/>
                    <v-text-field filled label="Justificación" v-model="datos.otroPlazoJusti"></v-text-field>
                </v-col>
        </v-row> 
        <br/>

        <!-- 31 GARANTIA -->
        <h3>31.- PLAZO DE GARANTÍA</h3>
        <br/>
        <v-row class="rowGroup">
            <v-col cols="12" md="4">
                <h5>Plazo:</h5>
                <v-radio-group v-model="datos.plazoGarant">
                    <v-radio label="Un (1) año a partir de la recepción." :value="true"></v-radio>
                    <v-radio label="Otro" :value="false"></v-radio>
                </v-radio-group>
            </v-col>

                <!-- EN CASO DE SER OTRO ... -->
                <v-col cols="12" md="3" v-if="datos.plazoGarant === false">
                    <h5>En caso de ser otro plazo, especificar:</h5>
                    <br/>
                    <v-text-field filled label="Plazo" v-model="datos.otroPlazoGarant"></v-text-field>
                </v-col>

                <!-- JUSTIFICAR ... -->
                <v-col cols="12" md="5" v-if="datos.plazoGarant === false">
                    <h5>Justificación:</h5>
                    <br/>
                    <v-text-field filled label="Justificación" v-model="datos.otroPlazoGarantJustif"></v-text-field>
                </v-col>
        </v-row> 


    </div>
</template>

<script>
    export default {
        name: 'CesionSubcontrataOtros',
        data(){
            return {
                datos: {
                    componente: 'CesionSubcontrataOtros',
                    cesion: false,
                    subcontrata: false,
                    subcontrataJustif: false,
                    subcontrataTrabajos: false,
                    facultInspecc: false,
                    justifFacultInspecc: '',
                    plazoRecep: false,
                    otroPlazo: false,
                    otroPlazoJusti: false,
                    plazoGarant: false,
                    otroPlazoGarant: false,
                    otroPlazoGarantJustif: false,
                }
            }
        },

        created(){
            this.initialize();
        },

        beforeDestroy(){
            this.$emit('datos', this.datos)
        },

        methods:{
            initialize(){
                if(this.datosGuardados !== undefined){
                    this.datos = this.datosGuardados
                }
            }
        }
    }
</script>

<style scoped>
    .marginL {
        margin-left: 1rem;
    }
</style>