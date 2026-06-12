---
title: "How-to Install the Matrox P750 Proprietary Driver on 7.04"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by dmBriarwood on 2007-08-15
I thought someone might find this useful:  

*** What I was trying to do:***

Install the proprietary driver for a Matrox P750 video card on a fresh Feisty install which would enable me to set the screen size and refresh rate to the manufacturers recommended settings (1440x900 @ 60 mhz) 

*** My System:***

AMD Athlon XP 3200 Barton 400 FSB with 1 Gb of memory, a Matrox P750 DDR 64 Mb Dual video card, a Creative Labs Soundblaster Live! DE 5.1 sound card all on a  ASUS A7V600 motherboard.

*** Useful Resources:***

Matrox Drivers/Utilities website: [http://www.matrox.com/graphics/en/corpo/support/drivers/home.php](http://www.matrox.com/graphics/en/corpo/support/drivers/home.php)

*** Procedure:***

Due to the compatability problems in 6.10 with Matrox video cards, I opted to wait for 7.04 before upgrading my Ubuntu distribution.  Once installed and updated, I installed the Matrox proprietary driver using the following method:[LIST]
[*]  I downloaded the most recent version of the Parahelia driver from the Matrox website: [http://www.matrox.com/graphics/en/corpo/support/drivers/home.php](http://www.matrox.com/graphics/en/corpo/support/drivers/home.php)
[*]  Using Synaptic, I installed the latest version of the build essentials package
[*]I changed the permissions of the driver file $ chmod 777 <name of driver file>
[*]I ran the driver installer from the command line: $ sudo sh <name of driver file> – instructing it when prompted to extract and install the archive in /usr/lib/
[*]With the driver installed, I then modified the X-org configuration file.  Using the command line I entered:  $ sudo gedit – navigated to /etc/X11/ and opened the xorg.conf file.  (The xorg.conf file can only be changed with a text editor in super-user mode.  As this is such an important file to the proper functioning of your computer, I strongly recommend you create a back-up of this file before making any changes to it!)[/LIST]a) Change 1: Insert “mtx” in the Device Section:

Section "Device"[INDENT]     Identifier    "Generic Video Card"
    Driver        "**mtx**"
    BusID        "PCI:1:0:0"
[/INDENT]EndSection

b) Change 2: Insert the Horizontal and Vertical refresh parameters as indicated in the monitor's technical specifications (found in the user manual)

Section "Monitor"[INDENT]     Identifier        "Generic Monitor"
    Option           "DPMS"
    HorizSync        **31-80**
    VertRefresh     **56-75**
[/INDENT]EndSection

c) Change 3: The 1440x900 resolution my monitor required was not listed in the Display Subsection. So, in the Modes line for each Depth level (1, 4, 8, 15, 16, 24) I entered “1440x900” - as an example, here is  Section “Screen” Subsection “Display” Depth 8 (remember to do this for all the depth levels):

Section "Screen"[INDENT]     Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
[/INDENT]SubSection "Display"[INDENT]     Depth        8[INDENT]     Modes        "**1440x900**" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
[/INDENT][/INDENT]EndSubSection[LIST]
[*]Save and close xorg.conf
[*]Restart system (upon restart, you should see the blue Matrox Parhalia splash screen)
[*]From the Ubuntu 7.04 desktop select <System> <Preferences> <Screen Resolution>.  If it is not already so, using the drop down menu set <Resolution> to 1440x900 and <Refresh Rate> to 60 Hz[/LIST]

---

