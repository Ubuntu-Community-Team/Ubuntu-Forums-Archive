---
title: "Command Line Help for Sound Troubleshooting"
date: 2009-01-27
forum: Multimedia Software
---

### Post by markbuntu on 2009-01-27
Command Line Help for Sound Troubleshooting

This is an addendum to

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

so if you are looking for troubleshooting help you should really start there.

When troubleshooting a sound problem it is important to gather as much information as possible. Here are a bunch of commands you can execute from a terminal that will gather that information. These commands are very simple and will not do anything but display information.

The terminal is where you execute commands. The line you write these commands to is called the command line. You can open a terminal by going to Applications/Accessories/Terminal.

These are the commands we will be using. You can copy them from here with ctrl-c and paste them in terminal with ctrl-shift-v and then hit enter to execute them. Do this one at a time.

```


lspci

lsusb

cat /proc/asound/cards

cat /proc/asound/modules

aplay -l

arecord -l


```

Since you will  want to save this information you can copy it from terminal by highlighting the information you want to save with the cursor and using ctrl-shift-c to copy it. You can then use ctrl-v to paste it to a tomboy note or some other notepad. 

These listings following are the actual results of using these commands on my machine. I have 5 hardware sound devices. A sound chip on my motherboard, a pci sound card, a HDMI sound chip on my graphics cards, a usb webcam, and a usb headset. This is how we find them and gather information about them.

lspci will list all the pci devices the system can detect. Of importance for sound troubleshooting are devices listed as Audio device or Multimedia audio controller and the usb controllers for my usb devices. As you can see, 3 of the devices are detected and 6 usb controllers so thing are looking good so far. There is the Audio device: ATI....SBx00 Azalia which is my on-board sound chip. There is the Audio Device: ATI...RV635 Audio Device which is my HDMI chip on my HD3650 graphics card. There is the Multimedia Controller: C_Media 8738 (rev 10) which is my C-Media 8768 PCI sound card.
```

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3600 Series
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

To find the usb devices we need to use lsusb. It will list everything connected by usb. It sees my multicard reader, my C-Media usb headset (which is a Plantronics) and my Logitec webcam.

```

lsusb
Bus 007 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08d7 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

Now we will use cat /proc/asound/cards. cat is short for concatenate or add to the end. It will take a file and add it to the end of the standard output which is the terminal screen. /proc is a sort of virtual directory where processes hang out. So to find out what the process asound, which is the sound process, has found for sound cards/hardware devices we use cat /proc/asound/cards
```

cat /proc/asound/cards
 0 [CMI8768        ]: CMI8738-MC8 - C-Media CMI8768
                      C-Media CMI8768 at 0xe800, irq 21
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe9f4000 irq 18
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeaec000 irq 17
 3 [U0x46d0x8d7    ]: USB-Audio - USB Device 0x46d:0x8d7
                      USB Device 0x46d:0x8d7 at usb-0000:00:12.0-3, full speed
 4 [default        ]: USB-Audio - C-Media USB Headphone Set  
                      C-Media USB Headphone Set   at usb-0000:00:13.1-1, full speed

```
As you can see, asound has all the cards. It has even numbered them for us and told us what irq interrupts or usb controllers they are using . 

Now we should see which alsa modules these cards are using. For that we use cat /proc/asound/modules.
```

 cat /proc/asound/modules
 0 snd_cmipci
 1 snd_hda_intel
 2 snd_hda_intel
 3 snd_usb_audio
 4 snd_usb_audio

```
As you can see, the C_Media card is using the cmipci module, the two HDA devices are using the snd_hda_intel module and the usb devices are using the snd_usb_audio device module.

Now we will use aplay-l to get some other specific information. aplay-l will list for us all the outputdevices hiding in our hardware and tell us their addresses. My C-Media card is card 0 and has a PCI DAC/ADC (DAC, digital to analog converter, ADC analog to digital converter) as device 0. It also has a 2nd DAC as device 1 and a IEC958 (digital) as device 2. My on-board sound chip is card 1 and has ALC883 Analog as device 0 and ALC883 Digital as device 1. My HDMI chip is card 2 and device 3 on the graphics card and the usb headphones are device 0.
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
This is critical information for configuring direct hardware addressing. The standard is hw(card),(device). Thus my C-Media primary output is hw0,0 and the digital is hw0,2. The HDMI output of my graphics card is hw2,3. The webcam, card 3, is not listed here as it has no output, no speaker, only a microphone for capture.

Now we will see what our hardware can give us for capture devices. arecord -l will list for us all available hardware that can capture sound for us to record with. As you can see, there are some changes from aplay -l.  For one thing, there is no device 1 on the C-Media card. This is because device 1 is for rear speaker surround sound playback only. card 3 is now listed. That means the mic on the webcam is available, yay.

 arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: U0x46d0x8d7 [USB Device 0x46d:0x8d7], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Now we have a ton of information about my hardware.
We know that my C-Media8768 card is actually a C-Media8738-MC8 (rev10) PCI card on irq 21. It has a primary DAC/ADC input and output at hw0,0 and a second DAC for output only at hw0,1 and digital input and output at hw0,2and it is using the cmipci alsa module. We also know that my SB x00 Azalia HDA Intel chip on the motherboard is a ALC883 with analog and digital input and output and is using the snd_hda_intel module and is hw1. We know the HDMI output on my gpu is hw2,3 and that both of my usb devices are detected at hw3,0 and hw4,0 and we have their IDs. All this without trying to find the owners manual or opening the case up or spending hours searching the forums and google.

If you are having trouble with sound starting and stopping and pulseaudio crashes you can run pulseaudio from a terminal in verbose mode and gather a lot of information.

In a terminal type
```

killall pulseaudio

pulseaudio -vvv

```

This can pinpoint problems with alsa drivers, pulseaudio and applications.

You should save this information somewhere that is easy to get to and cut and paste from. I use tomboy notes myself. 

If you are posting for help in the forums it is very important that you can share this information or it can be very difficult to help you. It is also important to give information on the make and model of your machine especially as there are many solutions that are very specific for certain machines.

Now you can return to the 10,000 page guide fully armed and if that does not help you now have enough information to obtain help from others.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Athena1 on 2009-02-11
Hi All..

I have some problem with my laptop. when i tested for sound cards i got following information.

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)


Bus 005 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x92500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0x92410000 irq 19

 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

I am looking for STAC9250 which has the model as m6...however when i modified the alsa-base code to the above mentioned m6 nothing works...Can you please help me fix this???

---

### Post by redroad55 on 2009-02-11
I just wanted to give you a shout out and thank you for your efforts to help make it easier for folks but more importantly it helps those of us who are trying to help others trouble shoot their systems .. Thanks, Great effort

---

### Post by markbuntu on 2009-02-11
So, you have a gateway NX something???
That option does not seem to work for all of the NX series.
If it is a pa6 you can try the pa6 option.

Which ubuntu are you using?
If it is Intrepid you might want to consider upgrading to ALSA 1.1.19 if none of the available options work for you. It may or may not improve your situation though and will make kernel updates a pain. Be sure to read through the post before doing anything.

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by Athena1 on 2009-02-12
Oooops I'm sorry to have posted at the wrong place...

However my problem is solved..after running the command

a)cat /proc/asound/cards
b)Instead of looking at the HDA ATI SB, I verified the alsa mixer gnome for the chip which listed as IDT 92HD71B7X
c)This looks like dell-series under 92hd71b* series in the list
d)Modifying the alsa base model=dell-m4-1 and restarting my laptop.....geeeeee the sound works :)


Thanks and sorry guys :)

---

### Post by markbuntu on 2009-02-12
Well, I am glad you figured that out....

---

### Post by corrupteddata on 2009-02-24
Thanks for the tut. I was with you until I got this:

russell@MCP:~$ aplay -l
aplay: device_list:207: no soundcards found...
russell@MCP:~$ arecord -l
arecord: device_list:207: no soundcards found...
russell@MCP:~$ /proc/asound/cards
bash: /proc/asound/cards: No such file or directory

Of course, the rest of your instruction wasn't much help after this. 

BACKGROUND:
I had sound playing through both the external speakers and the headphones (no headphone jack override). A few posts suggested updating the ALSA drivers, which I did by running alsa_setup.sh. Now I have no sound at all and the volume control says it can't recognize any devices. On top of that, when I try to adjust volume in Firefox (Pandora radio, for example) the screen goes grey and I have to force quit.

What's confusing is that "lspci" DOES find the card:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)

I'm just seriously confused and I keep making it worse. Help.

Thanks.

---

### Post by markbuntu on 2009-02-24
Well, lspci just asks the bios for the hardware so that means the system still knows its there. There are some options for the AC'97. There is some info about that here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You can always go back to the old ALSA. Directions fir that should be where you got the directions for using the script.

---

### Post by Eric06 on 2009-02-24
Helloneed help 
I have 8.10 in a packarg bell laptop easynote RS65-M023FR pn=PC28E01502
windows = sound ok; ubuntu no sound + 

here is my config

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdcf8000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfddec000 irq 17

 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

 aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC663 Analog [ALC663 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  1: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

I have upgraded to ALSA 1.0.19 without problem, and tryed to check every single sound control (also tryed headset)
Result is zero sound
I have not made changes to my alsa base file

I am desperate to get the sound working, any help or step by step (yes tryed the forums...) checking wellcome
This is making me mad

:confused:

---

### Post by markbuntu on 2009-02-24
You can look here, there is a listing for the Easynote

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

You can also go here for more help


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Eric06 on 2009-02-25
Thanks for your pointers; I have sound :-({|=

I could get sound by adding a line in alsa-base
I found that there were many possible values (the txt file in the packages to install alsa 1.0.19 list them all
so I tryed all of them and tested speakers/headset/volume/touchpad
I chosed 
options snd-hda-intel model=m51va
(added at the end of my etc/modbase.d/alsa-base file

here is a summary of what i saw working or not:
(i did all the test without rebooting, just by reloading alsa with : 'sudo alsa force-reload'; playing with the controls loading 'alsamixer' : with 2 terminals, the cd player and the sound recorder, and a bit of patience)

I could not get the mic to give me more than very faint sound, this will be another test, and I did not test the HDMI output


#ALC662/663:HP/mic/headset/ touchpad
#3stack-dig: ok/no/no
#3stack-6ch: ok/ bof/no
#3stack-6ch-dig: ok/no/ no
#6stack-dig: ok / no / no
#lenovo-101e: ok / lo / no/ no
#eeepc-p701: bad sound
#eeepc-ep20: ok / no / no / no
#m51va: ok / lo / ok / part
#g71v: ok / no / ok / part
#h13 : ok / low/ ok / part
#g50v: ok / no / no / part
# auto auto-config reading BIOS (default) zero son 

Thanks to the helping people in the universe !
Hopefully the future distributions will be better at 'auto setup'
):P

---

### Post by thriven on 2009-03-06
I recently installed ubuntu studio and I have no sound.  I have heard only faint sound, one time from a file bring played by limewire.  Otherwise I have no sound at all.

Here is the relevant information re my system.  I really appreciate any and all help.

lspci

Returns:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
______________________________________________

lsusb

Returns:
Bus 005 Device 003: ID 06e6:c200 Tiger Jet Network, Inc. Internet Phone
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
______________________________________________

cat /proc/asound/cards

Returns:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 16
 1 [TigerJet       ]: USB-Audio - USB Internet Phone by TigerJet
                      TigerJet Network, Inc. USB Internet Phone by TigerJet at usb-0000:00:1d.7-6, hi
______________________________________________

cat /proc/asound/modules

Returns:
0 snd_hda_intel
 1 snd_usb_audio
______________________________________________

aplay -l

Returns:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: TigerJet [USB Internet Phone by TigerJet], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
______________________________________________

arecord -l

Returns:
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: TigerJet [USB Internet Phone by TigerJet], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by enz1m3 on 2009-05-13
Hi, I've got an SB Live 5.1 soundcard and when I upgraded from 8.10 to 9.04 I lost sound.

I already did the pulseaudio thing (set it as default, make myself as user for groups pulse, pulse-access and pulse-rt), etc. but nothing seems to work so far...

Here're my outputs:

lspci
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900] (rev a1)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:02.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

```

cat /proc/asound/cards
```

 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with CMI9739 at irq 17
 1 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                      SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0x9c00, irq 17

```

cat /proc/asound/modules
```

 0 snd_intel8x0
 1 snd_emu10k1

```

aplay -l
```

**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdispositivos: 32/32
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
  Subdispositivo #31: subdevice #31
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdispositivos: 8/8
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 3: emu10k1 [Multichannel Playback]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

arecord -l
```

**** Lista de Dispositivos de Hardware CAPTURE ****
placa 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: ICH5 [Intel ICH5], dispositivo 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: ICH5 [Intel ICH5], dispositivo 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: ICH5 [Intel ICH5], dispositivo 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 1: emu10k1 mic [Mic Capture]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 1: Live [SBLive 5.1 [SB0060]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Please help :)

---

### Post by deankovell on 2009-06-30
hp says my soundcard is alc 888s. 
jaunty tells me this though. 

mark@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mark@ubuntu:~

do i need to change this? and how? 
thanks.

---

### Post by anjojo on 2009-09-06
New to Ubuntu.Understand that it will take some effort to get to ropes with Ubuntu,but as somebody else have rightly mentioned,".Somehow the "Linux officials" haven't realized that the audio capabilities of a Linux system belong to the very basic functions of a PC and OS, which have to work from day one."
I have been battling now for 2 weeks to get sound on system.No sound at all.Clean install on new system.On dual  boot with windows.Sound in windows works just wonderfull,no problems at all.
Ubuntu,TOTAL different story.Tried everything I could find in forums.Also Alsa**ALSA Upgrade Script** [B]& Multiple Sound Solution (ALSA w Pulseaudio)section 
[/B]But to no avail.Any advice will be appreciated.Volume controle shows,volume is not on mute. In sound preferences everything is on Aoto detect.And I have tried all different configurations.
Pulse audio volume controle shows playback:Audio on  Mute[Red Dot] and Output Devices:HDA Intel-ALC883 Analog"Audio also on Mute-Red Dot"
                                   
  	 	 	 	 	 	  System  info:Ubuntu 9.04.
DMI Information:Gigabyte Technology                 EP45-UD3P
 Kernel release:    2.6.28-15-generic 

Architecture:      x86_64
 ALSA Version:Driver version:     1.0.18rc3
              Library version:    1.0.18              Utilities version:  1.0.18
 Loaded ALSA modules:snd_hda_intel
 Sound Servers on this system:Pulseaudio:                              Installed - Yes (/usr/bin/pulseaudio)                              Running - Yes
                 ESound Daemon:Installed - Yes (/usr/bin/esd)                              Running - No       PCI Soundcards installed in the system
:00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 


When I type folowing in Terminal to try and manual start Audio driver  I get this:anjojo@anjojo:~$ sudo modprobe snd-ALC883.
                     [sudo] password for anjojo:
  Also when I try typing this in Terminal I get this:sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di                      [sudo] pasword for anjojo:
 But when I try typing my pasword for anjojo,nothing is typed.No matter what keys I type. 


   	 	 	 	 	 	  lspci 
 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03) 
 00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) 
 00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 
 00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 
 00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 
 00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 
 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 
 00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 
 00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4 
 00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 
 00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 
 00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 
 00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 
 00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 
 00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) 
 00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller 
 00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller 
 00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
 00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller 
 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1) 
 03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
 03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
 06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
 

 

  lspci 
 bash: anjojo@anjojo:~$: command not found 
 anjojo@anjojo:~$ 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ 06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
 bash: syntax error near unexpected token `(' 
 anjojo@anjojo:~$ anjojo@anjojo:~$  
 bash: anjojo@anjojo:~$: command not found 
 anjojo@anjojo:~$ anjojo@anjojo:~$  
 bash: anjojo@anjojo:~$: command not found 
 anjojo@anjojo:~$  
 

 

 

  cat /proc/asound/cards 
  0 [Intel          ]: HDA-Intel - HDA Intel 
                       HDA Intel at 0xc9400000 irq 22 
 

  cat /proc/asound/modules 
  0 snd_hda_intel 
 

 

 aplay -l 
 **** List of PLAYBACK Hardware Devices **** 
 card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 

  
   arecord -l 
 **** List of CAPTURE Hardware Devices **** 
 card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 

 Feels like I am running into brick walls.

---

### Post by Nwwmac on 2010-04-28
I am trying to solve a sound issue I'm having with a fresh install of 10.04 on an Intel iMac. I installed 9.10 and upgraded to the 10.04 beta last night. I figured with two days to go for it's release, it's probably good to go. Ubuntu runs fine - although this is my first install and there is no swap file. 

I don't think that's relevant, however. I think the drivers for the soundcard are incorrect, but that is only my guess. Following the instructions at the top of this thread, here is an interesting error message from terminal after killing pulseaudio and running pulseaudio -vvv. 

Can anyone tell me what this means? Is it useful? 

xxxx@Ubuntu:~$ killall pulseaudio
xxxx@Ubuntu:~$ pulseaudio -vvv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in Valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is a20f928d35efba1038a038484bd77370.
I: main.c: Session ID is a20f928d35efba1038a038484bd77370-1272488222.177409-1038958343.
I: main.c: Using runtime directory /home/curt/.pulse/a20f928d35efba1038a038484bd77370-runtime.
I: main.c: Using state directory /home/curt/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: **Daemon already running.**
E: main.c: **pa_pid_file_create() failed.**


My soundcard info:

**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

