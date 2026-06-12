---
title: "Tip: Adding a video card to a system with onboard video"
date: 2007-12-09
forum: Mythbuntu
---

### Post by ahood on 2007-12-09
While installing Mythbuntu based on Gutsy Gibbon, version 7,10, I had some trouble switching from onboard video to a PCIe videocard. Below is a detailed description of the problem and the steps taken to fix it. I hope this helps others.

**BACKGROUND**
I am building a Mythbuntu system using a motherboard (Foxconn [[COLOR="DarkOrange"]**6150K8MA-8EKRS**[/COLOR]]("http://www.foxconnchannel.com/product/Motherboards/detail_overview.aspx?ID=en-us0000034")) with onboard video. The onboard video has an analog D connector which works with just about any monitor on the market. Mythbuntu recognized the onboard video and worked well.  Because the onboard video is an nvidia 6150 GPU chip, the driver that worked initially was the opensource nv obtained from the Synaptic Package Manager. 

Using the onboard analog video is okay for watching video on a computer monitor, but I want to output video to a TV. Because my amplifier/TV has DVI, HDMI, and component inputs, all I need is a video card with DVI, HDMI and/or component out. Because the motherboard has a PCIe slot, I purchased a PCIe (16x) Nvidia GeForce 8400 GS video card that has analog, DVI and component out.

CHECK THE BIOS
Before installing this video card, I had to check the BIOS setting and made sure that the onboard video was set to **initialize the PCIe first** on boot up. 

*Note: Some motherboard might require the onboard be **disabled**. Because each BIOS is different, it is not possible to give detailed instructions on how to do this for others. It is recommended to look for either _Plug-n-Play_ or  _Integrated Peripherals_ in the BIOS.*


**PROBLEM #1**
I installed the PCIe video card and connected my monitor to the analog output to the PCIe video card. I rebooted the machine and there was just a black screen all the way through the entire boot up. Nothing appeared what-so-ever at any time.

**PROBABLE CAUSE FOR PROBLEM #1**
Because nothing appeared on the screen at all during boot up, suggested that the video was not directed to the **analog** out on the PCIe video card. 

**FIX FOR PROBLEM #1**
I connected my monitor to the DVI out on the PCIe video card and I rebooted. I saw the normal BIOS POST screen, grub screen, and Mythbuntu splash screen (with blue bar) on boot up.


**PROBLEM #2**
When booting up, I was able to see the normal BIOS POST and grub screens, as well as the Mythbuntu splash screen with the blue bar moving across. 

Unfortunately, the XFCE desktop screen never showed. I was back to a black screen.

**PROBABLE CAUSE FOR PROBLEM #2**
Because I could see the BIOS POST, grub and Mythbuntu splash screens suggested that the hardware could see the PCIe card and the problem was in the Mythbuntu software. 

Time to check which video device Mythbuntu was using for video.

[LIST=1]
[*]Rebooted
[*]When Grub prompt appears (count down to 0), pressed the **Esc**  key.
[*]Selected option #2 (recovery mode).
[*]At the command prompt, enter the following command
> nano /etc/X11/Xorg.conf
[*] Scrolled down to the **Section "Device"** and looked at the video card setting and found the following:
> Section "Device"
     Identifier         "Generic Video Card"
     Boardname     "nVidia Corporation C51PV [GeForce 6150] (rev a2)"
     BusID             "PCI:0:5:0"
     Driver             "nv"
[/LIST]

Wholla! The fact that the boardname had **[GeForce 6150]** told me that Mythbuntu was trying to use the onboard video to display the desktop user interface.

**FIX FOR PROBLEM #2**
The fix was to update the xorg.conf file with the correct video card device. Mythbuntu comes with a utility called 'dpkg-reconfigure' that will ask questions and modify the the xorg.conf file; however, before I could use this utility I needed to first determine the BusID of the PCIe video card.

**[COLOR="Blue"]DETERMINE BUSID OF PCIe VIDEO CARD[/COLOR]**
[LIST=1]
[*]Launch a terminal (Applications --> Accessories --> Terminal)
[*]Enter the following command
> lspci -x | grep -i "vga\|display"
*Note: The above command will display video pci devices.*

[*]Review PCI device output
> PCI:00:05.0 nVidia Corporation C51PV [GeForce 6150] (rev a2)
PCI:03:00.0 nVidia Corporation GeForce 8400 GS (rev a1)
[/LIST]

The output provided the BUSID of the PCIe GeForce 8400 GS video card, which was PCI:03:00.0.  

**[COLOR="Blue"]UPDATED XORG.CONF[/COLOR]**
To update the xorg.conf file with the BUSID of the PCIe video card, execute the following command in a terminal.

> dpkg-reconfigure xserver-xorg

This utility will ask questions and configure video, keyboard and monitor settings. 

For video, the following three questions will be asked.

[LIST=1]
[*]Driver
[*]Device Name
[*]BusID
[/LIST]

For my system, I entered the following for each...

[LIST=1]
[*]Driver - nv
[*]Device Name - nVidia Corporation GeForce 8400 GS (rev a1)
[*]BusID - PCI:3:0:0
[/LIST]

Notice that the BusID entered was slightly different from the way it was displayed with the lspci command. This is because I entered the BusID in hex mode and the lspci was not. To change to hex, I simply replaced the periods (.) with semicolons ( : ) and removed the extra zeros (0).

For the keyboard and monitor settings, I accepted the defaults.

The dpkg-reconfigure utility ended by asking to save and over write the current xorg.conf file (it automatically created a backup), which I did.


**ALL FIXED!!**
After updating the xorg.conf file, I rebooted and Mythbuntu booted up completely to the XFCE desktop.

***HURRAY!!!!*** 

I hope this helps others.

---

### Post by Ratham on 2008-01-02
Hi- I have an Intel graphics chipset onboard but I want to use a PCI video card.  When I install the card and change the "Init Display First" to 'PCI Slot' my system starts booting and gives the post screen and the splash screen and progress bar start, but the system hangs with the progress bar less than 20% full.

I tried selecting Recovery Mode from GRUB, and the system looks like it starts loading but then a number of messages start scrolling by faster than I can read them.  I let that run for over 40 minutes and nothing else ever happened, other than the number on the left of the string kept incrementing.

I also tried using the LiveCD and it wouldn't boot using the PCI Slot either.

If I leave the "Init Display First" option set to onboard, the system boots up properly and I can set it to use the PCI card with Xorg.conf.  That also works fine and once I log in I get my video on the monitor I have attached to the card.  The problem is, my system POST, the Ubuntu spalsh screens, and worse any text terminal sessions all still come out of the Onboard video card.  I want EVERYTHING to come out of the PCI card so I can eventually use Nvidea TwinView and set up dual monitors (I originally hoped to use an older PCI card and the onboard graphics for dual monitors with Xinerama, but that hasn't worked for me either!!!)

The motherboard is an abit LG-95Z and I am trying to use Gutsy (7.10) with Gnome 2.20.0.  I've tried two different PCI video cards (one at a time!):
a GeForce FX 5200 with 128 MB RAM
and a GeForce 6200 with 256 MB RAM

[NOTE:  This motherboard does NOT have a PCI Express x16 slot or an AGP one, just onboard video, two 'regular' PCI slots and a PCI Express x1 slot]

Thanks for any help!

---

### Post by ahood on 2008-01-05
> **Ratham said:**
> Hi- I have an Intel graphics chipset onboard but I want to use a PCI video card.  When I install the card and change the "Init Display First" to 'PCI Slot' my system starts booting and gives the post screen and the splash screen and progress bar start, but the system hangs with the progress bar less than 20% full.

I tried selecting Recovery Mode from GRUB, and the system looks like it starts loading but then a number of messages start scrolling by faster than I can read them.  I let that run for over 40 minutes and nothing else ever happened, other than the number on the left of the string kept incrementing.

I also tried using the LiveCD and it wouldn't boot using the PCI Slot either.

If I leave the "Init Display First" option set to onboard, the system boots up properly and I can set it to use the PCI card with Xorg.conf.  That also works fine and once I log in I get my video on the monitor I have attached to the card.  The problem is, my system POST, the Ubuntu spalsh screens, and worse any text terminal sessions all still come out of the Onboard video card.  I want EVERYTHING to come out of the PCI card so I can eventually use Nvidea TwinView and set up dual monitors (I originally hoped to use an older PCI card and the onboard graphics for dual monitors with Xinerama, but that hasn't worked for me either!!!)

The motherboard is an abit LG-95Z and I am trying to use Gutsy (7.10) with Gnome 2.20.0.  I've tried two different PCI video cards (one at a time!):
a GeForce FX 5200 with 128 MB RAM
and a GeForce 6200 with 256 MB RAM

[NOTE:  This motherboard does NOT have a PCI Express x16 slot or an AGP one, just onboard video, two 'regular' PCI slots and a PCI Express x1 slot]

Thanks for any help!

I don't think I can be of much help. I have not come across a problem as complex as this one. It does appear that motherboards that do not disable onboard video can be problematic. 

I have only a few suggestions to consider....

Because the card is a PCI device, I wonder if the problem might be related to an IRQ issue? To find out, enter the BIOS and make sure that the settings for PnP OS is set to OFF or DISABLE and under the "Plug and Play" section manually set the IRQ if they are automatically assigned. The third BIOS setting to consider changing is ACPI, and you might try disabling this as well. Of course, I would recommend doing this one at a time and see if there is any difference.

Alternatively to changing the BIOS settings, moving the PCI video card to the other PCI slot could also have an effect if it is an IRQ issue and might be worth doing if not done already.

Lastly, check to see if there is a BIOS update from the manufacturer website, and if so, evaluate whether the new version might resolve the issue.

Hope this helps...

---

### Post by Ratham on 2008-01-08
Hi-  Thanks for your post but I gave up and just bought a new mobo with a PCI Express x16 slot and a new Nvidia card.  Dual monitors are working beautifully with TwinView for me now!

---

