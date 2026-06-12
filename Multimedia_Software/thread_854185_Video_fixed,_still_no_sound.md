---
title: "Video fixed, still no sound"
date: 2008-07-09
forum: Multimedia Software
---

### Post by snurfle on 2008-07-09
I guess I shouldve posted this here originally rather than in the 'general help' section, but there were just so many issues that I figured that was a good starting point.  However, as I have received absolutely no replies whatsoever there, and since I essentially only have sound issues at this point, I guess this is where it belongs...
[http://ubuntuforums.org/showthread.php?t=853663](http://ubuntuforums.org/showthread.php?t=853663)

---

### Post by snurfle on 2008-07-09
OK... maybe what I want to do can't be answered so easily.
So let me try this, instead.
Let's say I am going to take out my sound card and put in a whole different new one.
How do I get rid of all the settings and drivers and such for the old one and put in all the drivers and settings and such for the new one?
How do I configure it (the new one, that is) to run 5.1 just like Windows?

---

### Post by xc3RnbFO8P on 2008-07-09
Just put the new card in and start the computer.
If it doesnt work, in Terminal:
> aplay -l
show the output here.

---

### Post by snurfle on 2008-07-09
"If it doesnt work..."
It does not.

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by xc3RnbFO8P on 2008-07-09
Output of:
> lspci -vv
and:
> gedit /etc/modprobe.d/alsa-base

---

### Post by snurfle on 2008-07-09
sorry for the long delay in replying... I'm on zero sleep and my third pot of coffee trying to get anything to work on this thing.

$lspvi -vv
bash: lspvi: command not found

---

### Post by xc3RnbFO8P on 2008-07-09
Its a typo.

---

### Post by snurfle on 2008-07-09
First one is typed
second one is copied from your post

greg@greg-desktop:~$ lspvi -vv
bash: lspvi: command not found
greg@greg-desktop:~$ lspvi -vv
bash: lspvi: command not found
greg@greg-desktop:~$ sudo lspvi -vv
[sudo] password for greg: 
sudo: lspvi: command not found


So it appears I'm missing a command on top of everything else?

---

### Post by xc3RnbFO8P on 2008-07-09
Look at post #5.

---

### Post by snurfle on 2008-07-09
Sorry.  I misread it.  Nine hours of blurry 800x600 killed my eyes!


00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
	Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 0
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [80] AGP version 3.5
		Status: RQ=32 Iso- ArqSz=0 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8,x16
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ce000000-cfefffff
	Prefetchable memory behind bridge: cff00000-dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0e.0 Communication controller: Intel Corporation 536EP Data Fax Modem
	Subsystem: Intel Corporation Unknown device 1000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at cd800000 (32-bit, non-prefetchable) [size=4M]
	Capabilities: [e0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=375mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at d800 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 16
	Region 4: I/O ports at d400 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 16
	Region 4: I/O ports at d000 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev 1.01
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 16
	Region 0: Memory at cd000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev. 1.01
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at b800 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 18
	Region 0: I/O ports at e000 [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
	Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (750ns min, 2000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at b400 [size=256]
	Region 1: Memory at cc800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Expansion ROM at cffe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [44] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>



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

---

### Post by xc3RnbFO8P on 2008-07-09
Switch sound card again
and do **lspci | grep -i audio**

---

### Post by snurfle on 2008-07-09
My apologies... I think I didnt do a good job of explaining... the sound issues I am having are just part of the mess that I have right now.  After 10 hours of no replies to my initial post (there's a link in the first message of this thread) I posted just the sound issue here...  I only have the one (integrated) sound card, and I was really wanting to just completely blow away all things sound related and start over.
But trying to do that reminded me of a blue million other issues I am having with Ubuntu recently, and I finally got disgusted with the whole giant ball of poo and posted it in the 'general help' section.
I eventually gave up caring about anything else, it's apparently as good as it's gonna get without new hardware all the way around, but I was really wanting to at least get my sound working again, preferably in 5.1... in hind sight, it really doesn't matter either, since I can't actually imagine myself watching a DVD on this system with the video the way it is now, but it would be nice if I at least could listen to an MP3 every once in a while.
Sorry for the confusion.

---

### Post by xc3RnbFO8P on 2008-07-09
What about reinstalling?
First getting sound and video to work.

---

### Post by snurfle on 2008-07-09
"What about reinstalling?
First getting sound and video to work."

I dont guess I understand your statements.
Reinstalling... Ubuntu?  If that's what it takes, because right now I am stuck at 800x600 again, I have downloaded and reinstalled the latest video drivers several times and I am just utterly stunned that it is this difficult to do something as simple as "make the video work".

"First getting sound and video to work."
If I could get the sound to work, or even the video at this point, then I wouldnt need to reinstall.
To be completely honest, I am of the opinion that as many problems as I have had to live with since getting into Ubuntu, and as impossible as it seems to be to get it working properly for longer than it takes for one or two updates to futz it all up...
I installed one piece of software, and the week that I spent getting it to work resulted in my sound getting munched.
I couldn't uninstall that piece of software, because I get video errors.
I get the video working, but every update seems to break it again.
Now I can't even get the video to give me more than a blurry 800x600 display on a 22" monitor, and the only sound I can get anymore is the beep from the computer speaker when I have to reboot.
When the display was right, updating to 8.04 brought back a screen shift that can only be fixed by the 'auto-config' button on the monitor moving the picture to match the video input (and losing the brightness etc settings) every time I boot to Ubuntu.
The numlock light is on regardless of the keyboard used), yet the keypad doesnt work unless I poke the numlock button 3 times in a row.

I have spent years trying to make Linux work, and today and yesterday I have spent 24 hours straight in front of it trying to get *one* thing to work properly, when it was working mostly fine 3 days ago.
Forgive me for being a little hateful sounding, but the coffee and snacks I've been living on, plus the day I took off of work (after being up all night with this) has put me in a lousy mood.
Trust me... I want this to work.  I really really do.
But right now, if I have to reinstall Ubuntu to make it work right, I am tempted to just yank it completely and use the space for XP.  I know that's a sh*tty thing to say, but I am fed up with it right now.

I appreciate your assistance, but I really cannot understand why it has to be this difficult to make it work.  I know I do not write code, so maybe I am expecting the system to be a lot easier than is possible to use... And believe me -- I have tried to be a fanboy of Linux... but Linux is making it very hard for me to base my opinion on anything substantial.

---

### Post by xc3RnbFO8P on 2008-07-09
To your screen problem try **Screens and Graphics**
Application> other (if not)
System> Preferences> Main Menu> Other, check Screens and Graphics
Choose Generic

---

### Post by snurfle on 2008-07-09
Wow.

"Choose Generic"
 -> All users must log off for changes to take effect.
rebooted
Here's how that went:
Ubuntu splash screen = 1024x768 (but that hasn't really changed ever)
Login screen = 1280x1024, but the picture is WAAAAYYY larger than the monitor... the login txtbox is almost against the right edge of the screen, and it's about 3/4 of the way down the screen.  'Autoconfig' from the monitor changes absolutely nothing.
After logging in, the screen goes all garbled; looks like the vertical hold is off!  Again, the autoconfig from the monitor does nothing.
Did that a few times till I got bored with it.
Reboot, select "recovery mode"
try the "xfix" option.
Now the login screen is 1680x1050, and looks gorgeous, but is shifted about 2 inches to the right, with a big black bar dwon the left side.  This is what has been Ubuntu's version of "normal" for at least six months.
But after logging in, it jumps right back to blurry 800x600 mode, AND it's now shifted about 4" to the LEFT, with a giant black bar down the right side of the screen!!!  Yippee!!!

After more than 24 hours of losing ground tryint to make the speakers work, and essentially screwing up the video worse than I have ever seen it before, I take this as a sign that it is simply not going to work right at all.
I give up, Ubuntu has beaten me.
I am going to sleep, and tomorrow I am wiping grub, and repartitioning the whole d*mn thing to reclaim the 70 Gb of hard drive space.
Maybe some day I will try again, but for now, Linux has officially kicked my ***.
Good night.

---

### Post by snurfle on 2008-07-09
OK.
I calmed down.
Walked away, took a walk, drank some coke, came back.
Still the same.  Crisp clear beautiful 1680x1050 at the login screen, just what I need to breathe a sigh of relief.  And then back to blurry 800 x 600 after login.
And now, just cause I wanted to see how 'squished' a video would look playing it at this rez, I discovered that any videos I play are not only silent, they are also now ***black and white***
Totem gxine, VLC, Kaffeine... all black and white.  Well, more like black and really light greeninsh-blue.
It's NEVER been like this before. Ever.
And yes, I checked to make sure all the 'settings' were correct.

If I had to guess, I'd say someone was in here purposely changing settings every five minutes just to see how pissed off I would get.
But I've been right here in front of it the whole time.

So it's back to plan A.

I took offence when the Illinois State Legislature compared Linux to a high school science project last year, but the past day has made me realize the truth behind that observation.
This is just a home computer.  What it was a computer in a business? Or at a hospital?  Or a fire department?  What if it *had* to work?  This kind of nonsense wouldn't be tolerated for one second if it was running a cash register at Starbucks... let alone if it was somwhere critical.

I hope Linux matures into a viable alternative that is as stable and solid as I have been telling anyone who will listen.
But until then, I am going back to the herd and sticking with big fat greedy (and reliable) XP.

Thanks for the assistance, but I think I either dont have enough hardware to run it, or enough smarts to figure it out.

---

### Post by scochran on 2008-07-10
Ummmm...  If your login screen has the correct resolution, then the problem is fixed; all you have to do after your logged in is 
system -> preferences -> screen resolution 
and select the right resolution.

---

### Post by scochran on 2008-07-10
snurfle?  did that fix it?

---

### Post by snurfle on 2008-07-10
I don't know.
Live CD works just fine, booting to HDD just jumps around from one resolution to another from Splash screen to Login screen to Desktop, not counting the flickering from terminal to solid orange and back to terminal a bunch of times before deciding to go to the login screen... I don't know what resolutions it's bouncing through there, but I guess that Ubuntu changes screen resolutions no fewer than six times before making it to the desktop.
And then, no sound, b/w video, offcenter display, numlock, no compiz...  
All this in a couple of days.
I figured giving myself a day to get away and start over fresh would do it, but it's just too ridiculous to me that it is this bad for any reason... I can't even begin to imagine how to make something like this happen on purpose on any system at all, let alone that is happens out of the blue while trying to *solve* problems.

---

### Post by markbuntu on 2008-07-10
When you get to that beautiful login screen, click on the little icon on the bottom left corner and change the session to gnome safe mode. Then log in.

---

