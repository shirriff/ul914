# Uncovering the Silicon: Fairchild's μL914 NOR gate from 1964

For the Maker Faire, I built a replica of the μL914 NOR gate using discrete transistors on a PCB. This circuit functions just like the real chip.

![PCB implementation of the μL914 NOR gate.](box.jpg?raw=true "μL914 NOR gate.")

You can compare this to a die photo of the chip ([decapping video](https://youtu.be/GfbNiD0pmgs)):

![Die photo of μL914 NOR gate, courtesy of John McMaster](decap.jpg?raw=true "Die photo of μL914 NOR gate, courtesy of John McMaster")

I build this as part of the "Uncovering the Silicon" project at Maker Faire, along with Lenore Edman, Windell Oskay, Eric Schlaepfer and John McMaster.
The purpose of this project was to help people understand how ICs actually function internally.
See the Evil Mad Scientist [blog post](https://www.evilmadscientist.com/2019/uncovering-the-silicon-%CE%BCl914/) for more details on our Maker Faire project.

This repository contains the Kicad files for this board.

## The printed circuit board

If you decide to build this, a few important notes:

1. This PCB is pretty unusual. Let OSH Park know that the board is supposed to look unusual. Also tell them not to clip the silk. (Normally they clip silk screen that's directly on metal.)



3. The drill holes on the pads are small; they fit a few strands from a stranded wire. You might want to enlarge them.

4. My board is available on OSH Park [here](https://oshpark.com/shared_projects/wVhkKsxW
).

## Building the project

Wiring up the PCB is pretty straightforward.

Transistors on the die are arranged base-emitter-collector, while most discrete transistors are emitter-base-collector. I bent the leads on 2N3904 transistors into the right arrangement. Alternatively, you could use VHF transistors (such as MPSH10), which have the base-emitter-collector order. (I haven't tested the MPSH10; the transistors arrived too late for Maker Faire.)

For the resistors, I used two 100Ω pull-ups, and four 2.2KΩ resistors on the inputs, somewhat arbitrarily. The chip uses values of 640Ω for the pull-ups and 450Ω for the inputs, based on the [datasheet](http://shadowtron.info/Datasheets/Fairchild%20Micrologic%201/RTL%20uL900-914/1.jpg).

The connections to the PCB are straightforward. I used a USB charger to provide +5 and ground. The four pushbuttons are wired to +5 and the inputs. The two LEDs are wired to the outputs and ground. (The pull-ups on the PCB limit the LED current, so external resistors aren't needed.)

## How I designed the board

To design the board, I made a simple schematic in Kicad. Next, I took the die photo from [John McMaster](https://siliconpr0n.org/) and used GIMP to clean up the die photo and create the silkscreen and solder mask images. I ensured that there was solder mask under the silk screen. I imported these images into Kicad using the Bitmap2Component tool.

I started off the PCB layout by putting down traces, but that wasn't the best approach. The width and position of traces didn't quite match, and they were rounded at the ends. I switched to drawing polygonal fill regions, and that worked much better. It was still difficult to get the silk screen and the traces to line up, and I did a lot of adjustment.