---
title: "Cant get sound through my hdmi on my tv"
date: 2011-08-05
forum: Multimedia Software
---

### Post by razz8606 on 2011-08-05
[SIZE=2]i have just recently switched back to Ubuntu and im trying to run my sound through my tv which is connected through my computer using a hdmi cable thats plugged into my EVGA  Nvidia GeForce  210  video card ... i have my computer monitor set up as my main screen but i have my tv set up as separate X screen so i can drag over a movie and watch it on the big tv screen and still do things on my monitor ... when i was running windows i was able to get the sound to play through my tv just as i am tryin to do  now... does anyone know how i can do this on Ubuntu 10.04 ?? [/SIZE]


[SIZE=2]Ty for any help in advance \\:D/[/SIZE]

---

### Post by BicyclerBoy on 2011-08-05
You may need to update the alsa drivers to 1.0.24.
I guess you are using nvidia driver 260 or later ?

The alsa driver update is as easy as adding the iquik audio ppa.

**[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu) lucid main**

But post your
aplay -l

then we can try to output noise thru' the possible physical codecs...

Note the GT520 is a better choice than GT210 but both are not really ideal for HTPC.
The GT 530*, 430, 220 240 are recommended.

---

### Post by razz8606 on 2011-08-06
> **BicyclerBoy said:**
> You may need to update the alsa drivers to 1.0.24.
I guess you are using nvidia driver 260 or later ?

The alsa driver update is as easy as adding the ubuntu audio devs ppa.

But post your
aplay -l

then we can try to output noise thru' the possible physical codecs...

Note the GT520 is a better choice than GT210 but both are not really ideal for HTPC.
The GT 530*, 430, 220 240 are recommended.

im honestly not sure what driver i have or how to check or update :( .... if u could walk me through it that would be great

---

### Post by 4Orbs on 2011-08-06
I'm using ATI graphics, not NVIDIA... but in order to get sound thru HDMI, I found it necessary to disable sound from the other sound card on my system by using the Sound Preferences settings.

[ATTACH]199359[/ATTACH]

---

### Post by razz8606 on 2011-08-06
> **4Orbs said:**
> I'm using ATI graphics, not NVIDIA... but in order to get sound thru HDMI, I found it necessary to disable sound from the other sound card on my system by using the Sound Preferences settings.

[ATTACH]199359[/ATTACH]

this is what i have on my sound preferences ... what do i need to disable or enable cuz i dont c a hdmi that is in ur SS 

[IMG]http://i307.photobucket.com/albums/nn311/cowboyup8608/Screenshot.png[/IMG]

---

### Post by BicyclerBoy on 2011-08-06
Both alsa & pulseaudio have problems with the HDMI "sound-cards"

alsa can only enumerate (2) subdevices but most HDMI codecs expose (>=4)
pulseaudio allows only (1) extra sink module so max=2.

By disabling one soundcard &/or using module probe_mask values you can work-around the above limitations.

@OP
alsactl --version
speaker-test -h
There can be a difference in versions of the kernel module & the userspace driver modules.

I'm sure you need the iquik audio ppa with 10.04

**[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu) lucid main**

[]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa?field.series_filter=lucid")Then add the packages
alsa-base
linux-sound-base

this package version should match the current kernel version you have installed.
The version matches the 10.04 kernel right now..

You did not post your aplay -l...

---

### Post by razz8606 on 2011-08-06
> **BicyclerBoy said:**
> Both alsa & pulseaudio have problems with the HDMI "sound-cards"

alsa can only enumerate (2) subdevices but most HDMI codecs expose (>=4)
pulseaudio allows only (1) extra sink module so max=2.

By disabling one soundcard &/or using module probe_mask values you can work-around the above limitations.

@OP
alsactl --version
speaker-test -h
There can be a difference in versions of the kernel module & the userspace driver modules.

I'm sure you need the audio dev ppa with 10.04
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa?field.series_filter=lucid")

Then add the package 
linux-alsa-driver-modules

this package version should match the current kernel version you have installed.
The version matches the 10.04 kernel right now..

You did not post your aplay -l...

did not post my aplay-l ?? and im sorry im so confused lol  im still getitng used to all this :( any way i could get a simple step by step instruction ??

---

### Post by BicyclerBoy on 2011-08-06
Sorry but if you do not understand how to run
aplay -l
I don't know how to proceed (my fault not yours)...

Using the gnome sound prefs (what you posted as a screenshot)
On the hardware tab:
Do you see the drop down selector labeled "Settings for the selected device" "profile" ?

Click this & see if you can select HDMI device..
Then you can configure the HDMI device.

If you are really lucky your HDMI subdevice will be one of the first (2) enumerated so this could work.
 
A better tool that does a similar thing is
pavucontrol
You will have to install it from repository/software centre.

---

### Post by razz8606 on 2011-08-06
> **BicyclerBoy said:**
> Sorry but if you do not understand how to run
aplay -l
I don't know how to proceed (my fault not yours)...

Using the gnome sound prefs (what you posted as a screenshot)
On the hardware tab:
Do you see the drop down selector labeled "Settings for the selected device" "profile" ?

Click this & see if you can select HDMI device..
Then you can configure the HDMI device.

If you are really lucky your HDMI subdevice will be one of the first (2) enumerated so this could work.
 
A better tool that does a similar thing is
pavucontrol
You will have to install it from repository/software centre.


in the settings for the selected device tab i have 4 options 

Off
Analog  stereo  input 
Analog  stereo  output
Analog  stereo  duplex 

nothing about hdmi :(

---

### Post by BicyclerBoy on 2011-08-06
This means that pulseaudio does not know about your HDMI sound device.

First need to fix/check alsa.

We need to determine the devices alsa can see so run from terminal..
aplay -l
aplay -L

---

### Post by razz8606 on 2011-08-06
> **BicyclerBoy said:**
> This means that pulseaudio does not know about your HDMI sound device.

First need to fix/check alsa.

We need to determine the devices alsa can see so run from terminal..
aplay -l
aplay -L


heres what i got when i typed them 2 commands into terminal


[IMG]http://i307.photobucket.com/albums/nn311/cowboyup8608/Screenshot-1.png[/IMG]

---

### Post by BicyclerBoy on 2011-08-06
When posting terminal output please select the text & then use the terminal menu "copy" then paste into reply or into a text file (use gedit).

And please stop quoting my entire post each time you reply..

It looks to me that your alsa is only finding your onboard soundcard (nVidia chipset).

What is this output
alsactl --version
lspci

I think you will need to look at the audio dev ppa posted earlier..there is a step-by-step guide on each launchpad ppa & **very good** documentation on the Ubuntu website.

Are you using the nVidia video graphics driver ? Gnome menu/administration/additional hardware drivers (jockey)

---

### Post by isee on 2011-08-06
Hey, I don't mean to hijack this thread but I am having difficulty with getting HDMI audio to my TV.  If I've breached any protocol just let me know and I'll start my own thread.

I installed a Nvidia GT220, as far as I can tell have all the drivers installed, the latest alsa driver for my kernel and the proprietary Nvidia drivers.

Here are some terminal results
**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**brief lspci**
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT216 [GeForce GT 220] [10de:0a20] (rev a2)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1132]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at ee000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fcf00000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidia-173, nvidiafb, nouveau

02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be2] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1132]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

**uname -a**
Linux Medion 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 i686 GNU/Linux

**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

**alsactl --version**
alsactl version 1.0.22


If you need more pls let me know.  I have in my Sound Preferences HDMI selections, but they don't seem to work.  I've tried disabling the internal sound but that didn't work.

Thank you!

---

### Post by BicyclerBoy on 2011-08-06
@isee
You don't mean to hijack this thread but you have..

Your solution is not to dissimilar to the OP.
You need to update your alsa driver modules to 1.0.24 before anything will work.

Don't use the  ppa posted earlier ..

**[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu) lucid main**


speaker-test reports the alsa driver modules version..

Then try
speaker-test -c2 -r 48000 -D hw1:3
speaker-test -c2 -r 48000 -D hw1:7
speaker-test -c2 -r 48000 -D hw1:8
speaker-test -c2 -r 48000 -D hw1:9

and report which one produced pink noise..

---

### Post by isee on 2011-08-06
Well, thank you for helping me here.

I have ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu lucid main in my repositories.  I found that looking for answers this evening.  And with that I was able to install the alsa driver in Synaptic for my kernel.  I haven't found any other info yet, or I should say I haven't been able to read or follow some things I have found.

Perhaps I should just start a new thread.  I've been looking and clicking on many links in my search, and this thread seemed to get closest to what I'm looking for.

I don't know what you mean by "not dissimilar to the OP".  I don't know what OP means.

I'm going to search for a means for me to upgrade to the .24 alsa that I need.  I'm not that technical so there are things I have trouble following.

Thanks!  I'd appreciate it if you would help with difficulties I may have.  This has become a particularly important aspect of using Linux for me, as I'd like to send video with audio to my livingroom TV.  I understand I may not be technical enough, but I am going to try.

---

### Post by isee on 2011-08-06
Should I add this to my repositories?
[B]ppa:ubuntu-audio-dev/ppa

[/B]I went ahead and added it, I'm trying to find out what's next.

---

### Post by BicyclerBoy on 2011-08-06
After checking my 10.04 system..

You need to add this ppa to get the alsa upgrade...the audio-dev ppa is not that useful..
We just need the userspace driver update ...the current alsa kernel module is usable.

**[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu) lucid main**

alsa-base
linux-sound-base
libasound2
alsa-utils
lib32asound2

@OP   just means "at the original poster"

---

### Post by isee on 2011-08-06
I guess my question here is what package am I looking for to upgrade to 1.0.24.

Oh wait, I just reopened Synaptic to look at the repositories and its not there, I don't know why.  I got the warning about changed repositories and everything.

I'll have to try again.

---

### Post by isee on 2011-08-06
OK  This is very confusing.
> Use the audio dev ppa posted earlier
> the audio-dev ppa is not that useful

---

### Post by BicyclerBoy on 2011-08-06
You always need to reload synaptic after repository changes..

Sorry that was my mistake...
I have both the iquik ppa & audio-dev ppa in synaptic (for so long I forgot which was which)
But only the iquik ppa is needed to solve your problem..
The audio-dev ppa has not done any harm.

---

### Post by isee on 2011-08-06
Your link took me here:[SIZE=1]** Index of /team-iquik/alsa/ubuntu **at[B]  [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/)

[/B]There are two folders there, dists and pool.
[/SIZE]

---

### Post by BicyclerBoy on 2011-08-07
The ppa URL was not the http homepage browser link but the link information for synaptic package manager repository directly..

Here you go
[https://launchpad.net/~team-iquik/+archive/alsa]("https://launchpad.net/%7Eteam-iquik/+archive/alsa")

---

### Post by isee on 2011-08-07
I tried adding that to my repositories again and reloaded, still is not there, but you say its not important, so thats fine with me.

I need to get the iquik ppa added then.  I'd like to read more about this.

---

### Post by isee on 2011-08-07
> The ppa URL was not the http homepage browser link but the link information for synaptic package manager repository directly..

I understand this now.

---

### Post by BicyclerBoy on 2011-08-07
I should have directed you to the launchpad ppa homepage so you could decide..

The iQuik ppa has worked well for me & many XBMC live users.

XBMC live is based on Ubuntu 10.04 so the default alsa/HDMI audio is mostly broken.

---

### Post by isee on 2011-08-07
Thank you, BicyclerBoy, for your help.  I can do no more tonight, and I am working remotely out of town for a week, so am offline then.  When I get back, I will be looking to get my audio working, and would appreciate help.

Thanks again!:KS

---

### Post by BicyclerBoy on 2011-08-07
This thread had better be solved before then..
But I tend to look any of the HDMI audio posts..

---

