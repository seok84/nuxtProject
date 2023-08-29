<template>
    <div>
        <h1>Layout</h1>

        <h2>Container</h2>
        <v-container>
            <v-row justify="center">
                <v-col
                    v-for="(_, n) in 12"
                    :key="n"
                    cols="auto"
                    >
                    <v-card
                        height="100"
                        width="100"
                        :class="['d-flex justify-center align-center bg-secondary', `elevation-${n}`]"
                    >
                        <div>{{ n }}</div>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>

        <h2>Flexbox</h2>
        <section>
            <div class="d-flex justify-start mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-start
                </v-sheet>
            </div>

            <div class="d-flex justify-end mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-end
                </v-sheet>
            </div>

            <div class="d-flex justify-center mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-center
                </v-sheet>
            </div>

            <div class="d-flex justify-space-between mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-space-between
                </v-sheet>
            </div>

            <div class="d-flex justify-space-around mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-space-around
                </v-sheet>
            </div>

            <div class="d-flex justify-space-evenly mb-6 bg-surface-variant">
                <v-sheet
                    v-for="n in 3"
                    :key="n"
                    class="ma-2 pa-2"
                    >
                    justify-space-evenly
                </v-sheet>
            </div>

        </section>

        <h2>Spacing</h2>
        <v-container class="spacing-playground pa-6" fluid>
            <v-row>
            <v-col
                class="d-flex align-center"
                cols="12"
                sm="6"
            >
                <v-select
                v-model="paddingDirection"
                :items="directions"
                class="pe-2"
                label="Padding"
                >
                <template v-slot:prepend>
                    <strong class="text-primary py-1">p</strong>
                </template>

                <template v-slot:append-outer>
                    <div class="py-1">
                    -
                    </div>
                </template>
                </v-select>

                <v-select
                v-model="paddingSize"
                :items="paddingSizes.slice(1)"
                label="Size"
                ></v-select>
            </v-col>

            <v-col
                class="d-flex"
                cols="12"
                sm="6"
            >
                <v-select
                v-model="marginDirection"
                :items="directions"
                class="pe-2"
                label="Margin"
                >
                <template v-slot:prepend>
                    <strong class="text-primary py-1">m</strong>
                </template>

                <template v-slot:append-outer>
                    <div class="py-1">
                    -
                    </div>
                </template>
                </v-select>

                <v-select
                v-model="marginSize"
                :items="marginSizes"
                label="Size"
                ></v-select>
            </v-col>

            <v-col
                class="bg-orange-lighten-3 pa-0"
                cols="12"
            >
                <v-sheet
                    :class="[computedMargin]"
                    elevation="4"
                    rounded
                >
                <div
                    :class="[computedPadding]"
                    class="bg-light-green-lighten-3"
                >
                    <div
                    class="bg-white text-center py-6"
                    v-text="playgroundText"
                    ></div>
                </div>
                </v-sheet>
            </v-col>
            </v-row>
        </v-container>

    </div>
</template>

<script>
export default {
    name: 'uitestPage',
    data () {
      const spacers = Array.from({ length: 17 }, (val, i) => `${i}`)
      const nspacers = Array.from({ length: 16 }, (val, i) => `n${i + 1}`)
      const defaults = ['auto', ...spacers]

      return {
        directions: ['t', 'b', 'l', 'r', 's', 'e', 'x', 'y', 'a'],
        marginDirection: 'a',
        marginSize: '2',
        marginSizes: [...defaults, ...nspacers],
        paddingDirection: 'a',
        paddingSize: '6',
        paddingSizes: defaults,
        playgroundText: 'Use the controls above to try out the different spacing helpers.',
      }
    },

    computed: {
      computedPadding () {
        return `p${this.paddingDirection}-${this.paddingSize}`
      },
      computedMargin () {
        return `m${this.marginDirection}-${this.marginSize}`
      },
    },
}
</script>
