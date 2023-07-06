# Bent Wavefield
An analog synthesizer composed of a modified Baby8 Sequencer and Atari Punk Console, which can be used to create a variety of eight-note musical sequences.

![schematic](https://github.com/wenbakefield/bent-wavefield/assets/8831999/308b0091-3f66-43bd-a638-f8f21a3a5d72)

## Introduction

The goal of this project was to achieve the effect of the EMS Synthi AKS, as used by Pink Floyd in “On The Run”. This was accomplished by pairing two well-known audio circuits together: the Baby8 Sequencer and the Atari Punk Console. The resulting combined circuit can be used to create eight note musical sequences, with adjustable BPM, pitch, and timbre.

## Baby8 Sequencer

The heart of the system is the Baby8 Sequencer circuit, which has an adjustable clock and eight adjustable pitch outputs. The circuit utilizes a 555 timer for the clock, which can be altered using a potentiometer. It also utilizes a 4017 counter with eight individual outputs for different voltages, each of which can be adjusted using eight corresponding potentiometers. The outputs of the counter can also be turned off individually via slide switches, allowing for rhythmic customization. Each output also has its own indicator LED to show which one is currently active. Additionally, the sequencer circuit features a global reset button, which restarts the sequence from the beginning. The reset button can also be held down to sustain the only the first note in the sequence if desired.

## Atari Punk Console

The system employs the Atari Punk Console circuit for sound synthesis. This circuit utilizes two 555 timers, one being an astable oscillator that acts as a trigger for the other monostable oscillator. The astable oscillator receives an input voltage which determines the frequency of the oscillation. Additionally, a potentiometer is placed in series with the input voltage, which has the effect of a global pitch shifter. The monostable oscillator has a potentiometer that adjusts the pulse width of the signal. Thus, the circuit outputs a square wave signal with an adjustable pulse width, which permits an interesting variety of sounds. Different voltage-controlled oscillators can also be substituted for the Atari Punk Console in this stage of the system, but the retro sounds it produces pair very well with the Baby8 sequencer. Lastly, the output is AC-coupled with an operational amplifier, with a trimmer serving as a gain control.

## Schematics

The schematics for the circuits were designed in KiCAD. Download links for the project files are provided below.

### Baby8 Sequencer
![baby8](https://github.com/wenbakefield/bent-wavefield/assets/8831999/3599c672-7e88-426e-a219-2739e757d8e0)


### Atari Punk Console
![apc](https://github.com/wenbakefield/bent-wavefield/assets/8831999/2b6d7f18-8bea-4ef4-a20f-36c8b991be76)


## Bill of Materials

* 3 x LM555N
* 1 x CD4017BE
* 1 x LM324N
* 8 x 1N4148
* 8 x 5mm LED
* 10 x 1 kΩ resistor
* 1 x 50 kΩ resistor
* 1 x 100 kΩ resistor
* 10 x 500 kΩ variable resistor
* 1 x 100 kΩ variable resistor
* 2 x 0.1 μF capacitor
* 1 x 10 μF capacitor
* 1 x 1 mF capacitor
* 8 x SPDT switch
* 1 x push-button switch
* 1 x TRS audio jack

## Simulation Prototype

![falstad](https://github.com/wenbakefield/bent-wavefield/assets/8831999/2a2a8c7e-d22e-47cb-8a97-e9eea9766657)

The Falstad simulation tool was used to prototype the design virtually and perform circuit analysis. Visualizing the flow of current, tracking notable voltage levels at each stage of the synthesizer, and previewing the audio output were helpful takeaways from this preliminary analysis.

[View Simulation](https://tinyurl.com/y227klll)

## Breadboard Prototype

![topdown](https://github.com/wenbakefield/bent-wavefield/assets/8831999/1fcb967b-b85b-48d5-94c2-fa0ac3117789)

The Atari Punk Console subcircuit is on the right, and the Baby8 Sequencer subcircuit is on the left.

## Demo

https://github.com/wenbakefield/bent-wavefield/assets/8831999/ea71ef28-c8e0-4d38-b798-221f7f643fc3

[View on YouTube](https://youtu.be/5s4sRJsfbWM)

## Future Improvements

Ideally, the design should be modularized so that each individual circuit is self-contained, with audio jacks and patch cables between them for each relevant signal (gate, trigger, CV). Additionally, operational amplifiers should be placed at the output of each stage, rather than just the last stage, to ensure that the proper range of voltages is maintained. Currently, the sequencer stage can output voltages that are outside of the standard Eurorack control voltage range (-2.5V to +2.5V). It is still functional, but the potentiometers that adjust each note’s pitch are overly sensitive. Constraining the output to a set standard will allow it to be used with other synthesizer circuits that accept a Eurorack CV input.

Another potential improvement to the design would be to add an ADSR envelope generator after the synthesizer stage. This was attempted during development but proved to be overly complicated, and produced unwanted interactions with the Atari Punk Console. Although the Atari Punk Console produces interesting and complex sounds, it is chaotic by design. Changing either of the parameters will sometimes result in unexpected global pitch shifting and altering the pulse width does not apply it uniformly to each note. Replacing it with a simple square wave generator with an accompanying ADSR envelope generator (or triangle wave integrator), would yield more musically robust results.

Lastly, additional switches can be added to the sequencer to allow for any one of the outputs to act as an automatic reset trigger. This would permit sequences between lengths of 1-8, rather than only 8. This was considered during development but would have required double the amount of switches, and there was simply not enough space on the breadboard to accommodate them.

## References

* Baby10 Sequencer Guide: [https://hackaday.com/2016/01/14/oh-baby-baby10-build-a-classic-analog-music-sequencer/](https://hackaday.com/2016/01/14/oh-baby-baby10-build-a-classic-analog-music-sequencer/)
* Atari Punk Console Guide: [https://sdiy.info/wiki/Atari_Punk_Console](https://sdiy.info/wiki/Atari_Punk_Console)
* Eurorack Standard Overview: [https://en.wikipedia.org/wiki/Eurorack](https://en.wikipedia.org/wiki/Eurorack)
* KiCAD (for schematic design): [https://www.kicad.org/](https://www.kicad.org/)
* Falstad (for circuit analysis): [https://www.falstad.com/circuit/](https://www.falstad.com/circuit/)
* Mouser (for components): [https://www.mouser.com/](https://www.mouser.com/)
