---
title: "Getting a Lifeview TV Tuner to work on a laptop"
date: 2008-08-15
forum: Multimedia Software
---

### Post by markmorgan on 2008-08-15
Hi

I've a savrow blade 75 and installed ubuntu. Installed via DVD and upgraded to 8.04.

But Windows (which I used to have on the pc) automatically picked up the Lifeview DVB-TV Tuner which is built into the laptop.Once I installed the software the TV card worked fine. The graphics card is a Geoforce model.

If I run lspci, I get this..

06:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
	Subsystem: Animation Technologies Inc. Unknown device 3307
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 181 (21000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at b4006000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-


Now Ive tried using MythTV and TVTime with ubuntu but I just get a blank screen. When using other programs in linux - graphics and sound work fine.

If someone has managed to get this combination working can they let me know. Any help would be welcome here as I've tried using both KDE and Gnome but with no luck. Is there any program I can use to get this card working ?

thanks
mark

---

### Post by steefjeqv on 2008-08-16
Hi,

One of the easiest programs to use is Kaffeine.
When your DVB card is fully recognized Kaffeine will show a digital TV icon.

Before starting up Kaffeine, do the following (terminal) :
The first three commands will temporarily remove the drivers. Try them one at a time. Then load the driver with the fourth command.

sudo rmmod saa7134
sudo rmmod saa7134_alsa
sudo rmmod saa7134-dvb
sudo modprobe saa7134-dvb

If this doesn't work you can try :

sudo rmmod saa7134-dvb
sudo modprobe saa7134-dvb card=2

If the card still isn't recognized you can retry the above commands with the following card numbers : 3 - 39 - 54 - 55 - 60 - 74 - 86 - 94 - 95 or 97.

These numbers all represent different PCI Lifeview TV cards who use the saa713x chipset. Hopefully your laptop version is similar to one of these.

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134")

Let me know how you get on.

Greetings,
Steven

---

### Post by markmorgan on 2008-08-16
Steven

Thanks very much for the detailed help :)
I will try this later on this morning and let you know.

Mark

---

### Post by markmorgan on 2008-08-16
Hi Steven,

Well so far I get this..

~# sudo modprobe saa7134-dvb card=2
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.24-19-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

will try the other choices 

thanks
Mark

---

### Post by markmorgan on 2008-08-16
Steven

No such luck Im afraid (unless Im doing something totally wrong here...)a

I did try all the card numbers....
once again - if you have any ideas i'd appreciate hearing them
thanks

Mark


FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.24-19-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@garrincha:~# sudo modprobe saa7134-dvb card=95
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.24-19-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@garrincha:~# sudo modprobe saa7134-dvb card=97
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.24-19-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by markmorgan on 2008-08-16
have I got the syntax of the command correct ???

[ 3343.567775] saa7134_dvb: Unknown parameter `card'
[ 3346.214679] saa7134_dvb: Unknown parameter `card'
[ 3346.513331] saa7134_dvb: Unknown parameter `card'
[ 3346.797602] saa7134_dvb: Unknown parameter `card'
[ 3346.990008] saa7134_dvb: Unknown parameter `card'
[ 3347.172389] saa7134_dvb: Unknown parameter `card'
[ 3347.347033] saa7134_dvb: Unknown parameter `card'
[ 3347.849177] saa7134_dvb: Unknown parameter `card'
[ 3348.064331] saa7134_dvb: Unknown parameter `card'
[ 3348.250906] saa7134_dvb: Unknown parameter `card'
[ 3348.713731] saa7134_dvb: Unknown parameter `card'
[ 3348.894792] saa7134_dvb: Unknown parameter `card'
[ 3349.033207] saa7134_dvb: Unknown parameter `card'
[ 3356.413042] saa7134_dvb: Unknown parameter `card'
[ 3357.886267] saa7134 ALSA driver for DMA sound unloaded
[ 3358.106453] saa7134_dvb: Unknown parameter `card'
[ 3380.551901] saa7134_dvb: Unknown parameter `card'
[ 3381.921720] saa7134_dvb: Unknown parameter `card'
[ 3382.052738] saa7134_dvb: Unknown parameter `card'
[ 3385.449027] saa7134_dvb: Unknown parameter `card'

---

### Post by markmorgan on 2008-08-16
Magic

Managed to get it working with Kaffeine.

Thanks once again !

M

---

### Post by steefjeqv on 2008-08-17
Sorry,

When you use the "card" option, you have to use saa7134 in stead of saa7134-dvb.

Greetings,
Steven

---

### Post by markmorgan on 2008-08-17
no worries - and thanks for your help.
steven - on a similar issue - do you know the 'tvtime' application.

it picks up terrestrial broadcasts (which kaffeine cannot seem to do) but tvtime has no sound - even though the picture is good.

thanks
mark

---

### Post by steefjeqv on 2008-08-18
Hi Mark,

Last week, a friend of mine had a similar issue with a saa7134 based card combined with TVTime.

We managed to solve it by installing alsamixergui.
Using this alsa frontend we opened up (and unmuted) all the sound channels available (normally the aux channel should do the trick).

Then we tried out the different PAL audio settings of TVTime, and  finally sound worked.

saa7134 cards sometimes are a bit of a hassle when it comes to analog TV sound (don't know why exactly). You'll find lots of people having trouble with this issue.

Greetings,
Steven

---

### Post by markmorgan on 2008-08-19
Steven

Thanks once again - I installed the GUI for ALSAMixer and I unlocked all the channels - however I find that I cannot raise the volume above zero for capture (capture 1 and 2) as well as input source ( and input source 1 and 2)
This is odd - as sound works fine in everything except tv tune 

any ideas ?

cheers
Mark

---

### Post by steefjeqv on 2008-08-22
Hi,

Maybe these channels you've mentioned simply aren't available on your sound card.



You can trying loading the sound driver with modprobe :

sudo modprobe saa7134_alsa

Hope this helps.

Greetings,
Steven

---

### Post by markmorgan on 2008-08-23
cheers Steven.

Will give it a try.

Mark.

---

### Post by markmorgan on 2008-08-23
hmm, it looks like maybe something isnt installed ?

but bear in mind the card works fine in kaffeine - its just that kaffeine cannot do terrestrial broadcasts, only dvb.



FATAL: Error inserting saa7134_alsa (/lib/modules/2.6.24-19-386/ubuntu/media/saa7134/saa7134-alsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

