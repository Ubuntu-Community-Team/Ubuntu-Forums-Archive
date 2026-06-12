---
title: "No Audio 8.10 Intel hda"
date: 2008-10-29
forum: Multimedia Software
---

### Post by warb on 2008-10-29
I've got no audio on the digital out  of my system.

Your ALSA information is located at [http://www.alsa-project.org/db/?f=b54b81692ff014f29e8fbfdc8cb8a798c3cbba26](http://www.alsa-project.org/db/?f=b54b81692ff014f29e8fbfdc8cb8a798c3cbba26)

ran the alsa script. 

I don't see any problems, just   no audio....

---

### Post by wolfen69 on 2008-10-29
[This]("https://help.ubuntu.com/community/HdaIntelSoundHowto") may help.

---

### Post by warb on 2008-10-29
Thanks, I really don't  want to get into compiling and installing modules
for the kernel. 

I did find from that site.... right mouse on the kmix shows the
sound muted, but I  cannot get it  to un-mute.

---

### Post by Kirenhob on 2008-11-04
Hi !

I got a solution on my laptop Fujitsu with Ubuntu 8.10 :

sudo lspci -vv

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: Fujitsu Siemens Computers Device 10ac
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 22
Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

Solution :
$sudo gedit /etc/modprobe.d/alsa-base
add that line :
options snd-hda-intel enable=1 index=0 model=fujitsu

save alsa-base, and do a :
$sudo /etc/init.d/alsa-utils restart

restart your computer

open the Volume Control, and check Speaker in the Preferences, and put the Speaker volume at its maximum

That's working here !

---

### Post by Kirenhob on 2008-11-09
Another good solution is to follow that link :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It works on my Fujitsu pc laptop, with alsa-driver, lib, and utils-1.0.18

For yet, all speaker and headphone are working. 

On the recording side, I can blow in my microphone to hear that blowing, but I can't hear other sounds ! Funny thing...

---

### Post by stir-crazy on 2008-11-10
I'm having a similar issue since upgrading, updated to latest version of alsa, tried the modprobe thing...bupkiss.

But my situation is a little different in that after the upgrade, I WAS able to enjoy sound for several hours, and after a couple of reboots.  I was listening to a youtube video (had already listened to several others), when the sound suddenly stopped, and I get the permanently checked mute button in KMix.

I stongly suspect that this is KDE related, as I do have the Ubuntu drums at the login GUI just fine, sometimes a logon sound for KDE4 gets most of the way through playing before it's cut off, and my gnome desktop on the same machine doesn't have these issues at all.

:cry::cry::cry:

EDIT Nov. 11th, 2008
Okay, been in Ubuntu, not Kubuntu this past week.  Had no problems there for a while, but then my headphone port didn't seem to work...hope it isn't a hardware issue.  But had several updates come in tonight, and now sound seems to work, though still buggy.  The mute button is still checked.  Oh well, it's a big start in the right direction.

EDIT Nov 21st, 2008
Not a hardware issue; live CD of 8.04 makes use of the headphones just fine.







EDIT FEB 18th, 2009
I can't recall when things resolved themselves (for the most part), but at some point some ALSA updates fixed "most" of my sound issues.  The only issues I have now are that system sounds (mail in, log in, log out, etc) always play at full volume, regardless of where I have the system volume set; mute still mutes, thankfully.

---

### Post by Gerard R. on 2008-11-21
I use Kubuntu 8.10 32 bits on a 64 bits Celeron 2core.
What you guys write is wellknown here.
Routing of sound looks like a buggy thing in KDE 4. So do I have a problem with recording sound with different recorders/sound editors.

I see 50% indication on soundlevelmeters when there is no
sound. When I try a microphone I see indication, but no
'throughput' of sound on for instance Audacity.
When I listen to a produced file there is almost nothing
to hear. I'm searching now for two days and I don't find it. 

For the rest all sound and video of other software is not too bed (with win32).

---

### Post by seraphim_72 on 2009-02-19
I ran into this as well, 8.10 on a Lenovo x200 Thinkpad. 

After spending a bit at the command line and getting to the point of thinking about trying to boot into other kernals. So I reboot I got an odd thought and booted into my Windows partition. It was muted so I unmuted it had it make some noise (random youtube vid) and booted back to my normal kernal - all my sound worked again. System/Flash/Amarok the whole thing. 

Now I figure that my laptop has a hardware mute switch. I *had* hit the switch to try to get sound back testing it at each time. This wouldn't be the only switch on my laptop that doesn't work correctly under linux. but odd that the software mute in Windows sets the hardware switch. 

Not much of a fix unless you dual boot, but maybe something to put in the back of your head for the future.:):)

---

### Post by Reeman on 2009-02-19
> **warb said:**
> I've got no audio on the digital out  of my system.

Your ALSA information is located at [http://www.alsa-project.org/db/?f=b54b81692ff014f29e8fbfdc8cb8a798c3cbba26](http://www.alsa-project.org/db/?f=b54b81692ff014f29e8fbfdc8cb8a798c3cbba26)

ran the alsa script. 

I don't see any problems, just   no audio....
Try the command in a terminal **alsamixer -c 0** if your desktop is blocking access by alsamixer and making the desktop sound server the default then you can access the iec958 on the onboard chip directly by calling alsamixer directly to /dev/dsp0. This is because the real device can be directly accessed unless the esd (enlightened sound deamon) or in the case of KDE the artsd is throwing a locks on some of dev's sound devices. Shutdown the esd or the artsd and let programs directly access alsa! The rediculous Gnome and KDE sound schemes have been doing this crap for years. In alsamixer you should be able to activate your mike and or digital i/o directly. I use alsamixer exclusively for this reason and use only programs like VLC, and Audacity set up to use alsa resources directly. I ditch Totem, Gstreamer, and the Desktop sound server and have no sound trouble anymore period. The only thing is that the totem interface to browsers gets borked so you cannot watch wma content..which you will find is no where near as much of a headache as you think. You can install Realplayer with all the wma codecs and it works better than most hard nosed GNU people will admit...completely free software or not!

---

### Post by rijnsma on 2009-02-19
Thanks a lot for the support.
But I had after time more issues in Kubuntu. I even lost one time the whole OS when I thouched some wrong button at login.
To make a long story short: I experimented al lot with other
OS's and my regular one PCLOS, which I still have on another
partition. (PCLOS is trying to come to the 2009 version, but 
they are experimenting a lot. And for the time being it is not
my main OS any more.) 
I ended at Ubuntu, which has the least trouble for now. I'm 
using it for some weeks. 
All Gnome is doing fine, and the possibillity of Debian install ánd even much KDE-stuff is great. (I even have Opera back (great browser with some tiny special things like 'session-save with remembering refresh-intervals of groups of sites')) and I could installe for instance Frostwire, which is not illegal in my country if you only download with it. Medibuntu is fine for codecs and libdvdcss.; Realplayer .Deb-file is doing fine.) 
I did try Ubuntu in the past and kept searching, but Ubuntu is fine now for me and I keep it.
Recording in Ubuntu is no problem. Audacity and for instance mhWaveEdit are doing great!

---

### Post by warb on 2009-05-18
Well I finally have sound, 

using alsamixer I tabbed over to IEC958 P and set it to PCM, now sound
come out the spdif ... Anyone know what this does?

---

