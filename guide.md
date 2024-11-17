# Lumberjack Pro - Kit assembly guide

This assembly guide will guide you through putting together your Lumberjack Pro keyboard PCB kit. The process is quite simple with only basic soldering experience required.

⚠️ Please note this guide was adapted for the Lumberjack Pro from the original build guide and some pictures have not been update yet.

## Before starting

* Check you have all the required items not included in the kit.
    * Soldering iron
    * Solder
    * Flush cutters
    * 60-61 MX key switches
* Check that you have all the components. See [BOM](BOM.md)
* If you are not used to soldering, learn how to solder components.
    * https://learn.adafruit.com/adafruit-guide-excellent-soldering/tools

## Soldering

### Controller considerations

The PCB supports either the Frood controller (wired only), or the nice!nano wireless controller.

#### Frood

When using the Frood, install the on-board USB-C socket that is positioned to fit many cases, or a USB-C daughterboard.

#### nice!nano

* You can make your Lumberjack Pro wireless using teh nice!nano controller
* A 1S (3.7 V) Li-Po battery can be connected to the JST socket pads marked "B+/B-"
  * There is currently no power switch on the PCB, so the controller will be permanently powered. However, this is not really an issue because the controller is very power efficient and enters a sleep mode after a short while, and you can use a sizeable battery with the Lumberjack Pro
  * The battery can only be charged via the USB-C socket on the nice!nano, which might be a bit difficult due to the position of the controller
* ⚠️ **DO NOT** fit the USB-C socket or a daughterboard when using the nice!nano with a battery! ⚠️
  * nice!nano doesn't have the USB data lines broken out, so the wired communication will not work (although the controller itself can be powered from the USB-C socket or the daughterboard)
  * ⚠️ The battery connected to the JST socket pads would be connected directly to the USB 5 V supply and could be overcharged easily and quickly, potentially leading to a fire! ⚠️

### USB socket (J1)

First you will solder the USB connector to the **underside** of the PCB. All other components (except the JST sockets) go on the top.

Due to the small size of the pins on the connector you might want to use a different soldering technique called drag soldering. You will need a separate supply of flux to do this, either liquid flux or a flux pen. However, with a suitable soldering iron tip the pins can be soldered traditionally as well.

* Insert the USB connector into the board.
* Flip the board over and solder one of the legs into place.
* Reheat the pad and press the USB port firmly into place to ensure it sits flat before then soldering the other 3 legs.
* Apply no-clean flux across all of the small pins.
* Apply a small amount of solder to your iron and drag it across the pins, repeat until all holes are filled with solder.
* The flux will cause the solder to flow to the pins and avoid creating solder bridges between the pins.
* Add more flux as needed as you go along.
* Use your iron between the pads to remove any solder bridges.
* Check the solder joints carefully, under a magnifying glass if needed, to ensure there are no bridges between pads.

Remember to also install the two extra resistors (R5 & R6).

![USB-C](images/guide/usb-c.jpg)

If you have a multimeter you can use it to check for bridges, put it into continuity mode and check that the following pins connect to each other and all others do not:

* Top 1 & 8, bottom 1 & 8 are ground pins and should all connect to each other and the square ground pad of the USB-mini footprint.
* Top 2 & 7, bottom 2 & 7 are V+ pins and should all connect to each other and the round bottom left pad of the USB-mini.
* Top 4 & bottom 5 are D- pins and should connect to top left pad of the USB-mini.
* Top 5 & bottom 4 are D+ pins and should connect to bottom center pad of the USB-mini.
* Bottom 3 is the CC1 pin and should connect to the top pad of the R5 resistor.
* Top 6 is the CC2 pin and should connect to the top pad of the R6 resistor.

#### JST connector (J3,4)

If you want to use a daughterboard instead of a USB connector, there are footprints for both a SMD or a THT connector. The connectors are positioned between the top and second row of switches so as to fall within the cable gutter of cases such as the Bakeneko, be aware that this might not be a suitable position for all cases.

Note: A JST connector is not included in the Lumberjack kit, the SMD variant is part JST-SR-4 and for THT it is S4B-ZR.

### Resistors for USB-C (R5,6)

If you are using a UCB-C connector you will need to solder these extra two resistors. They are marked in the kit with a black dot on the paper to help distingish them from the other resistors.

* R5,6: 5.1kΩ Green, brown, black, brown, red

### Hotswap sockets

* To solder the hotswap sockets, first put a healthy amount of solder on one of the pads of each socket footprint
* Then put the sockets into place over the solder
* Reheat the solder under the socket contact and gently push the socket down into the molten solder using a pair of tweezers
* To avoid creating a cold joint, keep heating for a second maintaining contact with the socket contact, then keep holding the socket in place while the solder solidifies. Avoid blowing on the solder to speed up the cooling
* Add solder to the other contact of each hotswap socket. Make sure to use enough heat so that the solder flows into the joint instead of just inside the contact

### Diodes 1N4148 (D1-61)

Solder the diodes.

Diodes are a polarized component and therefore take care of direction, the black line on the diode is the cathode and goes in the square pad on PCB.

### Tactile switch (SW1)

Push the switches into the PCB and solder the legs.

### Firmware

Follow the [QMK firmware instructions](https://docs.qmk.fm/#/flashing) to build and flash the firmware.

`qmk compile -kb 42keebs/lumberjack_pro -km vial`

### Check list

Now the board should be fully functional, so check that everything works before adding the switches.

Plug in the PCB and use a pair of tweezers or a piece of wire to check each keyswitch pad triggers a keypress.

## Switches

### Stabilizers

If you are using 2u keys and want to use key stabilizers, fix them to the board before inserting the switches.

If you are using screw in stabilizers, be aware that the screws can cause a short to the unused switch pads for the 1u keys. To avoid this, use plastic washers or electrical tape under the screws to isolate them from the PCB.

### Trim switch legs

When fitting key switches, the switches at the 'Q' and 'P' positions on the 2nd row will fowl on the standoffs in your keyboard case, so you need to trim down one of the stabilizing pins and part of the center pin to ensure the PCB fits flush within the case.

![Switch legs](images/guide/switch-mod1.jpg)

If you are using a 2u key on the right hand side, you will also need to trim down the center pin so that it does not fowl on the standoff. The position the case standoffs will be is marked on the soldermask of the underside of the PCB.

![Switch center pin](images/guide/switch-mod2.jpg)

### Insert switches

Insert the switches into the hotswap sockets in the PCB.

If you are using a plate, insert the switches through the plate.

Note also that the switch at the 'Q' position is upside down so that the switch pins do not interfere with the case standoff. So are switches in the Esc/Grave and 1 positions to avoid interference with the USB-C socket.

## Component cover

Affix the 4 standoffs to the PCB with screws from underneath the PCB. Use the remaining 4 screws to attach the acrylic to the top of the standoffs.

Do not overtighten the screws as this could crack the acrylic.

## Case fitting

When fixing the PCB to your case you will only use the center, the left and the right screw holes. Depending on your case design, the PCB will be supported by the other standoffs.

## The End

Congratulations, your build is complete.
