---
title: "Another post about not having sound in 8.10"
date: 2009-03-04
forum: Multimedia Software
---

### Post by Dr.Suave on 2009-03-04
Hi everyone

Sorry to add to the abundance of these posts...:)

Yesterday I installed Intrepid on a new laptop, and have got most of it running smoothly, however, I've been without sound since the live disk. I've tried two Ubuntu 8.10 live disks and a Linux Mint 6 live disk, and none have any audio.

I've been following various tutorials and trouble shooting guides, but I can't seem to enable whatever it is that needs enabling.

I'd really appreciate any advice at all at this stage!

Here's the output of a few commands that you might find useful:

```

wilf@drsuave:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

```
wilf@drsuave:~$ lsusb
Bus 007 Device 007: ID 07b3:0900 Plustek, Inc. 
Bus 007 Device 006: ID 04a9:10c9 Canon, Inc. 
Bus 007 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 007 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 147e:2016  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```

wilf@drsuave:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfb300000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfb010000 irq 17
```

```
wilf@drsuave:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
```

```
wilf@drsuave:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
wilf@drsuave:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm more then willing to provide any extra information needed.

Something of a side note: 
The ATI sound chip only seems capable of turning IEC958 on and off (in ALSA mixer at least), and the only chip (is that the right word?) that can control PCM is HDA INTEL Alsa Mixer.

And another bit of information I just thought of!

Neither my user or root were members of the groups pulse, pulse-access, or pulse-rt - I've since fixed this, but I don't know enough about these things to know if that was an indicator of what might be causing the problem - perhaps there are other groups I need to 'join'?

I've also updated alsa using [this script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

Edit: I've since found that with these things the brand of your computer is important - it's a [Hi-Grade Notino D7000SRA]("http://www.higrade.com/nqcontent.cfm?a_id=3674") - its the best computer I've ever had - it would bring tears to my eyes if I couldn't get Ubuntu working properly on it!


I hope I provided enough info - thanks for reading!
Wilf

---

### Post by Dr.Suave on 2009-03-04
Something terrifying just happened - I had exactly the same bug with the Fedora 10 Live Disk - sound works in Vista - I hope this bug isn't linux-wide...

---

### Post by Dr.Suave on 2009-03-04
Also, here's the result of the alsa-info.sh script, if anyone's interested: [http://www.alsa-project.org/db/?f=849dc970f609153856aae12d370f893952af98f0](http://www.alsa-project.org/db/?f=849dc970f609153856aae12d370f893952af98f0)

The problem is also in OpenSuse 11 - I also found that none of the users (my user or root) had the ability to use audio devices in System > Administration > Users and Groups > Properties.

My hunch is that this might be a permissions issue, what this coupled with my user and root not belonging to the pulse related groups. I don't know enough about Ubuntu to know where else to look in order to find similiar permissions etc.

Can anyone point me in the right direction?

Thanks for reading,
Wilf

---

### Post by Dr.Suave on 2009-03-05
I've also noticed something strange about the PCM control in alsamixer - it doesn't have the mute/unmute icon - I've attached a screenshot.

Anyone know anything at all that could help me?

---

### Post by avrilrox on 2009-03-05
I think i know whats going on. You sound driver is not being loaded for the correct audio device.

See:

```
sudo cat /etc/modprobe.d/alsa-base
```

In order to get **my** audio chip to work i had to edit snd_usb_audio, like this:

options snd-usb-audio index=0

You probably need to do it with your intel driver, maybe?

---

### Post by markbuntu on 2009-03-05
Well, the specs are a little confusing and vague

                 - Sound Blaster Pro compatible
                 - High Definition Audio Codec
                 - Compliant with Azalia
                 - 7.1 channel SPDIF support
                 - 2X Speakers (1.5Watt each)
Audio System     - Built-in dual array microphone

At a guess I would say it is possibly a ALC883 or ALC888 which should have been autodetected as such and not generic which is sort of weird. If it is a new new new machine with a new new new HDA chip it is possible the alsa driver writers have not seen it yet and so have not figured out the driver options it needs.

You should contact the manufacturer and ask them exactly which chip they are using then come back here and we will see what we can do.

---

### Post by Therion on 2009-03-05
Just too eliminate something stupid...

Right-click on the Volume icon and then click on Properties.

Do you see a "Switches" tab?  If not, you can stop reading now.

If you do, do you see a check-box labeled **Audigy Digital Input/Output Jack** under that tab?  

If so, and it's checked, clear the box and check for joy.  Conversely, if it's clear, check it "on" and repeat check for joy.

Joy?

---

### Post by Dr.Suave on 2009-03-05
avrilrox: thanks for the hint, but I think I already have the right card set to 0 - out of interest which USB soundcard are you using? It would be good to know what to purchase if I can't enable my onboard device.

markbuntu: swish! I've just filled out a customer service form asking for more details on the sound card - is there a command I can use to set my settings to one of the cards you suspected of being in my laptop? Thanks a lot for the response! :)

Therion: Alas! No joy, and no switches tab, but I'm always willing to eliminate stupid things, so thanks for the pointer.

Thanks for the help, everyone, will post new info as it comes.

Wilf

---

### Post by avrilrox on 2009-03-05
> **Dr.Suave said:**
> avrilrox: thanks for the hint, but I think I already have the right card set to 0 - out of interest which USB soundcard are you using? It would be good to know what to purchase if I can't enable my onboard device.

markbuntu: swish! I've just filled out a customer service form asking for more details on the sound card - is there a command I can use to set my settings to one of the cards you suspected of being in my laptop? Thanks a lot for the response! :)

Therion: Alas! No joy, and no switches tab, but I'm always willing to eliminate stupid things, so thanks for the pointer.

Thanks for the help, everyone, will post new info as it comes.

Wilf

My sound chip is an **onboard** CM6501 device.

---

### Post by markbuntu on 2009-03-05
There is a zillion options for the snd_hda_intel driver. A few of them are here and in the links

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Dr.Suave on 2009-03-05
> **avrilrox said:**
> My sound chip is an **onboard** CM6501 device.
Ah - then I will spend tomorrow doing some fiddling with 0s

:)

---

### Post by Dr.Suave on 2009-03-05
> **markbuntu said:**
> There is a zillion options for the snd_hda_intel driver. A few of them are here and in the links

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Oh yeah, have seen that list, maybe a bit too many for a trial and error method!

---

### Post by Dr.Suave on 2009-03-08
> **avrilrox said:**
> I think i know whats going on. You sound driver is not being loaded for the correct audio device.

See:

```
sudo cat /etc/modprobe.d/alsa-base
```

In order to get **my** audio chip to work i had to edit snd_usb_audio, like this:

options snd-usb-audio index=0

You probably need to do it with your intel driver, maybe?

This is what my alsa-base file looked like when I opened it up:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

options snd-hda-intel probe_mask=1
```

Here's how I've fiddled with it (all my fiddling has been pretty much a stab in the dark - I'm just guessing based on the small amount of knowledge I do have):

```
# 
**options snd-atiixp-modem index=-1**
**options snd-intel8x0m index=-0**
**options snd-usb-audio index=-0**

**options snd-pcsp index=-3**
**options snd-hda-intel model=w810** (<-- That was just a guess, I'm doing a bit of trial and error, will be trying a few more model numbers this afternoon)

```

Any suggestions with numbering (or anything else!)?

Thanks
Wilf

---

### Post by fayezderya on 2009-03-08
I am using ubuntu 8.04 on IBM lenovo and I have the same sound card intel 82801H ICH8 family. 

and I have been looking around. I did almost every thing you have done. with nothing. 

I also learned that this is a problem created since the developers decided to go with a complete FOSS driver rather than the intel.at least that what I read. 

I love linux but it is sad that my sound works in windows just fine and I have to look around for almost a week to get the sound work in ubuntu. my question is why don't the developers of ubuntu present a solution for this problem.

at least somebody gives me a satisfying answer why I can't find a solution for the problem. 

I really want this to work.

---

### Post by fayezderya on 2009-03-08
I found the solution in one of the ubuntu forums. 

the solution is you have to make changes to /etc/modprobe.d/alsa-base
and add the following line. 

options snd-hda-intel model=lenovo and if you don't know your model do this 
model=auto

just the same as you did but you have to reboot to hear the changes.

many thanks for every one 
at last my linux ubuntu works just fine I can kiss windows good bye.

---

### Post by fayezderya on 2009-03-08
in case any body asks this is how you do it. 

open the terminal

write this code

sudo nano /etc/modprobe.d/alsa-base 

and at the end add this line 

options snd_hda_intel model=lenovo

and reboot and your sound card should work just fine.unless you have a bigger problem.

---

### Post by Dr.Suave on 2009-03-08
> **fayezderya said:**
> I found the solution in one of the ubuntu forums. 

the solution is you have to make changes to /etc/modprobe.d/alsa-base
and add the following line. 

options snd-hda-intel model=lenovo and if you don't know your model do this 
model=auto

just the same as you did but you have to reboot to hear the changes.

many thanks for every one 
at last my linux ubuntu works just fine I can kiss windows good bye.

I'm glad you got it working!

Gives me hope, but I'm afraid my laptop isn't listed anywhere on any of those lists, and auto didn't work for me. I'm now testing each configuration that has SPDIF, as I know my card supports it.

---

### Post by Dr.Suave on 2009-03-16
OK, the company ignored my emails asking to know which chip was in my laptop, but alsamixer -Dhw tells me it's a SigmaTel ID 7698.

There's a patch designed for Mandriva which fixes problem - but I don't know how to install patches, or even know if there's a way to install a Mandriva patch on Ubuntu - I'm hoping the problem is fundamental enough for the patch to work on all Linux distros.

The bug report (with the patch attached to comment #1) is found here: [https://qa.mandriva.com/show_bug.cgi?id=41385](https://qa.mandriva.com/show_bug.cgi?id=41385)

I'd really appreciate someone telling me how to apply the patch.

Thanks a lot,
Wilf

---

### Post by Dr.Suave on 2009-03-16
Bump!

---

### Post by Mindzai on 2009-05-23
Did you get anywhere with this? I just installed Jaunty on the same laptop, ran all updates, still no audio.

---

### Post by Dr.Suave on 2009-05-23
Well, I made some progress on this thread here: [http://ubuntuforums.org/showthread.php?t=1099743](http://ubuntuforums.org/showthread.php?t=1099743)

But sound was only partially enabled (on board speakers only), and the patch has since been removed from Crimsun's kernel - bringing me back to square one.

If enough people ask for this card to be supported in Ubuntu it'll come eventually, I'm sure - as you can see on the thread I linked to there's a partially working patch out there, it just can't seem to ever make it to the kernel. 

The card seems to barely work on any OS - there are a lot of things I can't get it to do in Vista as well (which is the system I've now had to convert to - it brings tears to my eyes, but I didn't have much of a choice.)

Be sure to let me know if you have any luck with this - I've had to throw in the towel for now.

---

