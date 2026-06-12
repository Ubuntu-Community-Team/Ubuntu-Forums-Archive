---
title: "New Mythbuntu 2010 Hardware"
date: 2010-09-18
forum: Mythbuntu
---

### Post by aperifanos on 2010-09-18
[FONT=Calibri]Hi,[/FONT]
 
[FONT=Calibri]I was wondering if you are able to assist me. I'm new to Linux (I've never used it before), and I’m new to HTPC as well.[/FONT]
 
[FONT=Calibri]My aim to set up a HTPC, where I can view, and record live hd TV (through 24" Dell monitor initially), as well as view and stream my ripped dvd's, music and other multimedia data.[/FONT]
 
[FONT=Calibri]I've spoken to a few guys at work, and they've recommended Mythbuntu and XMBC to me. The main advantage that I see with Mythbuntu/Linux is that once the system is set up, stable, and working properly, it won’t require any maintenance, I can just set it and forget it.[/FONT]
 
[FONT=Calibri]The main disadvantage, is that I've never used Linux before, and I’m having trouble identifying compatible hardware that is guaranteed to work as is. This is where I'd like your assistance if possible.[/FONT]
 
[FONT=Calibri]I've have the following hardware from a failed Windows Media Centre HTPC build from last year, I would like to try and utilise this components, as long as they are compatible with Mythbuntu.[/FONT]
 
[FONT=Calibri][FONT=Symbol]· [/FONT]DIVCO Fusion HDTV Dual Digital 4 - I've read some posts that say that this tv tuner card is not compatible with Mythbuntu, and I've read some others that indicate that it is compatible. I'm hoping I can use this tuner card, could anyone confirm that it's compatible?
[FONT=Symbol]· [/FONT]HIS PCI RADEON HD 4350 Video Card - This card might not be required, as I'm looking to purchase a motherboard with integrated video and sound, however i'd like to utilise this card if it's compatible with Mythbuntu.
 
I've done my research, my understanding is that I need to purchase a motherboard that is compatible out of the box with Linux, which has integrated video and sound, with VDPAU acceleration and on-board DXVA. I've read some review and posts that indicate that any of the motherboards that I've listed below are suitable. Today I went to 5 computer stores in Melbourne, and they all said that these cards are not available anymore. I asked them if they have the current equivalent motherboards that are compatible with Linux, however they weren’t able to assist me. It seems as though they are reluctant to offer any advice on Linux systems, has anyone else found this?
 
[FONT=Symbol]· [/FONT]Zotac GF9300-G-E ITX 
[FONT=Symbol]· [/FONT]Asus P5N7A-VM 
[FONT=Symbol]· [/FONT]Gigabyte GA-E7AUM-DS2H 
[FONT=Symbol]· [/FONT]Asus M3N78-EM (AMD) 
[FONT=Symbol]· [/FONT]Gigabyte GA-M85M-US2H (AMD) 
 
Could you please recommend a current available motherboard and CPU that is guaranteed to work out of the box with Linux/Mythbuntu? I'm not fussed between INTEL and AMD, my main concern is building a stable cost effective HTPC.
 
I intend to use this box as frontend/backend initially, and then further down the track store it away as a backend system attached to a NAS and have simple frontend box's attached to the various TV’s in the house.
 
For the rest of the system, I’ve identified the following components
 
[FONT=Calibri]1. [/FONT]Motherboard: ?
[FONT=Calibri]2. [/FONT]CPU: Intel Core Duo 2.9 GHz or AMD equivalent
[FONT=Calibri]3. [/FONT]Case: Antec NSK 6582
[FONT=Calibri]4. [/FONT]RAM: Kingston 2GB
[FONT=Calibri]5. [/FONT]HDD: Seagate 500GB 7200 SATA
[FONT=Calibri]6. [/FONT]DVDR: LG DVDR SATA
 
I've got a few questions. Am I crazy for venturing into Linux/Mythbuntu seeing though I don’t have any experience with it? Are my hardware components suitable? Can you recommend a suitable motherboard and cpu hardware ?
 
Thanks for your help
[/FONT]

---

### Post by jaakan on 2010-09-18
Here is my current setup

Core 2 Duo E7500
Intel DG43GT Motherboard
# HDMI Video/Audio works out of the box!
#  on-board X4500 video (G43)
2Gb+1Gb DDR2 ram
Hauppauge HVR-1250 ( supports OTA HD and ClearQAM/unencrypted digital cable in the USA )

it plays back 1920 x 1080i HD with no issues while recording another show or movie in HD.

Gaming is not bad on it at all.

My last system was Q6600 Quad core, 6GB ram, NV GT220, which was kind of over kill.

---

### Post by LowSky on 2010-09-18
You not crazy going to Linux for your media center needs.
Nearly all components will work fine, sans tv tuner cards, they can be annoying if you dont know what to look for. But that why we are here.

1. all those motherboards should be availible. All are current models. Try Ebay if you cant find them in a store, or a online retailer. Buying in store is usually more expensive anyway. But just an FYI any motherboard will do just fine. If you want hardware video acceleration get one with a Nvidia chipset that has 9300 series or higher chip built in. ASUS P5N7A-VM is the perfect choice for Intel, AMD doesn't really have an option unfortunatly when it comes to Nvidia chipsets, the two companies are not exactly friends at the moment, which is sad and hurts business I think.

2. Why 2.9 Ghz?  A $70USD processor will be more than fine like a Intel Pentium Dual-Core E5400. You can go cheaper... Intel Celeron E3300 for around $50USD

3.looks good

4. I would go to 4GB if you plan to use on board video

5. you will need more space if you plan to record HD video. 1 hour = 6GB at 1080i. 500 GB will go quick if you want to keep recordings.

6. brand of optical drive wont matter.


as for tuner cards. Im partial to the Happauge 2200 series. But the Divco you named should run fine as seen here
[http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation)

just follow the instructions, they are pretty easy.

---

### Post by aperifanos on 2010-09-18
Hi Guys,

Thanks for your quick reply's.

I've had a quick look at the Motherboards that you guys recommended, the Intel DG43GT is around AUS$120, whereas the ASUS P5N7A-VM is not so readily available and around $230.

I'm happy to pay the extra money, as long as it's worth the extra cost? Is the ASUS a top range motherboard? Forgive my ignorance, but this is all very new to me. If you guys were in my position, which motherboard would you go for? I&#8217;m still not sure what the best and easiest option is for me?

I did see all those motherboards online, put I thought I&#8217;d be better off purchasing motherboard and cpu from a retail store, to make sure that they are compatible with each other, as well as Linux. But with a bit of assistance from you guys, I might be alright going down the online route.

I thought I&#8217;d go for the lowest spec Duo Core CPU, they retail for about AUS$90 over here.

I'll take your advice and go for the 4GB ram, I decided to go for the 2GB, because I read that was more than enough?

I have 3TB of external hardrives where I store my media, I&#8217;m planning on buying a QNAP Nas once I successfully set up the HTPC and stream from there. I assume this is possible with Mythbuntu?

Thanks for DIVICO link!

Have I chosen the right case? Can you guys recommend something more suitable / cost effective?

---

### Post by LowSky on 2010-09-18
asus is a tier 1 manufacturer. they are one of the best out there. other companies with similar records are: gigabyte, msi, biostar, foxconn, and intel

as for buying online... all mothboards will list what socket they are compatable with, and so will processors. if your not sure just ask core 2 duo ibelieve are socket 775. 99.99999% of all motherboards and processors will work with Linux

by the way the case is fine... everyone has there own style and price they can pay. remember its your pc in the end, make it look and perform how you want it to.

---

### Post by aperifanos on 2010-09-19
Thanks for all your help.

Ok, I have my box up and running! I've encountered some issues though, my main stumbling block is that I can't get any audio out. I've got the tv working, but no sound.

When I go to Multimedia - Mixer. I get the following error message

" GStreamer was unable to detect any sound devices. Some sound systems specific GStreamer packages may be missing. It may also be a permissions problem"

My motherboard is GA-G41MT-D3, with onboard sound. Do I need to manually install the drivers? I'm not sure how to install drivers on linux?

Can someone point me in the right direction please?

---

### Post by larsolav on 2010-09-19
How are you connecting sound? Are you using digital or analog sound? Are you using HDMI or SPDIF for sound/TV?
If using digital audio, maybe see here for some help: [http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)
did you unmute in alsamixer?
what is the result of:
 aplay -L
 aplay -l
Good luck!

---

### Post by aperifanos on 2010-09-19
I think i'm using analogue sound, I have connected a rjjack (the same connection that is used for headphones) onto a pair of bose speakers.

I havent unmuted the alsamixer, I'm not sure how to do this?

Do I need to install drivers? If so is there a step by step wiki on how to do this. This is the first time i'm venturing away from WIndows...

Thanks, sorry to be annoying

[COLOR=Blue]antonios@Mythbuntu:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC887 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output

antonios@Mythbuntu:~$ alsamixer help
cannot load mixer controls: Invalid argument
antonios@Mythbuntu:~$ aplay -I
aplay: playbackv:2585: You need to specify 1 files
antonios@Mythbuntu:~$ alsamixer
cannot load mixer controls: Invalid argument

[/COLOR]

---

### Post by LowSky on 2010-09-19
go into mythtv frontend

go to setup general and on the one of thos pages is options for sound, and choose ALSA

hope that works

---

### Post by forkd on 2010-09-19
I just posted my hardware in the hardware sticky post and it works well.

I must say that I recently upgraded to the Zotac GF9300 motherboard and I am extremely happy with it.  I have a big shuriken HSF on it and it is almost inaudible and plays HD video perfectly.

---

### Post by aperifanos on 2010-09-21
Hi guys,

I'm still having issues with sound. At this stage, i'm trying to get sound out of Mythbuntu, instead of Myth TV. So i've put a cd in, and kicked off VLC. The tracks are playing except no audio coming out of my speakers..

Trying to launch Gnome volume control - gnome-volume-control
I get "The program 'gnome-volume-control" is currently not installed

so then I tried to install it

sudo apt-get install gnome-media
"Reading oackage lists...Done
E: Couldnt find package gnome-media

So then I tried "sudo aplay -l"
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Analog [ALC887 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

I'm not sure what to try next? Is there anyone who could step me through the process please?

When I select Applications - Multimedia - Mixer. I get the following error message "GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem"

---

### Post by LowSky on 2010-09-21
how are you tring to listen to sound? PC speakers, analog output (green connector) or HDMI or something else?

open the sound mixer and make sure sound isn't muted. also make sure you are using the correct profile, ALC887 Analog.

---

### Post by aperifanos on 2010-09-21
I'm trying to listen to sound via PC speakers via analog out.

My motherboard has gygabyte motherboard has onboard sound, I have a seperate gygabyte nvidia video card, and that has a hdmi connection. Could the system try and push sound out of this instead of the analog connector?

When you say open the sound mixer, are do you mean alsamixer? I can't launch alsamixer.I type in alsamixer, and I get "invalid argument"

When I select Applications - Multimedia - Mixer. I get the following error message "GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem"

---

