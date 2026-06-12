---
title: "Geforce 210 hdmi audio"
date: 2009-11-06
forum: Multimedia Software
---

### Post by frank_acies on 2009-11-06
I recently bought the geforce 210, it does hdmi though pci-e instead of a passthough, but I can't get the audio to work with hdmi.

it shows up in aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and I've tried the various tips found on the web, changing default.pa to add

load-module module-alsa-sink device=hw:0,3

as well as changing the asound.conf file, neither have worked

although sound does come out the internal spifd connector on the motherboard.

has anyone had any luck with the geforce 210 getting audio out of hdmi? or is it just not supported yet?

Thanks

---

### Post by jocefus on 2009-11-06
I have the same issue. This card is supposed to have an integrated sound processor that alsa doesn't seem to be recognizing.
 
My motherboard has onboard nvidia hdmi with audio. My aplay list looks exactly like yours and I get no audio over the pci-e hdmi card. The audio device should be on card 1 not card 0. When I completely disable the onboard graphics/audio through bios my aplay list is blank, however when i do 'lspci' I see the audio device listed. It would seem alsa doesn't know how to talk to it.

---

### Post by jocefus on 2009-11-06
More specifically do 'lscpi -vv'
 
I want to output to this device:
 
```
02:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
        Subsystem: eVga.com. Corp. Device 1210
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steppin-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MA-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```
 
as opposed to this device which is all aplay list is seeing
 
```
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definiti)
        Subsystem: ASUSTeK Computer Inc. Device 82fe
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steppin-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MA-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```
 
How can I get alsa to recognize this device. My guess is that it is not supported in the current version of alsa included in karmic release.

---

### Post by jocefus on 2009-11-06
err... ls**pci** -vv' .. sorry

---

### Post by jocefus on 2009-11-06
I see also there are no kernel modules or drivers loaded for it... hrm... im new to the linux world, learning as I go. Not getting much help from alsa or nvidia forums. I guess loading the kernel driver and module would be the first step in getting alsa to see the device. The manufacturer evga offers no *nix drivers... but its nvidia's chipset and they claim it will work.
 
I am also using the latest prop. drivers 190.46 from nvidia which states support for this card.
 
How can I make my box load this device?

---

### Post by frank_acies on 2009-11-07
> **jocefus said:**
> I see also there are no kernel modules or drivers loaded for it... hrm... im new to the linux world, learning as I go. Not getting much help from alsa or nvidia forums. I guess loading the kernel driver and module would be the first step in getting alsa to see the device. The manufacturer evga offers no *nix drivers... but its nvidia's chipset and they claim it will work.
 
I am also using the latest prop. drivers 190.46 from nvidia which states support for this card.
 
How can I make my box load this device?

as far as I've seen it's not supported by alsa as of yet, though there is some progress.
this is the best I've found so far. 

[http://www.nvnews.net/vbulletin/showthread.php?t=140264](http://www.nvnews.net/vbulletin/showthread.php?t=140264)

---

### Post by jocefus on 2009-11-07
Not supported in latest alsa stable release either... just finished compiling. There are a few open postings in alsa bug-tracker, none helpful. Looks like its back to over-workin my processor with onboard a/v at least for now.

---

### Post by aradaj on 2009-12-19
i read in the avs forums that the HDMI audio should now be supported in ALSA 1.0.22

[http://www.avsforum.com/avs-vb/showthread.php?p=17705737](http://www.avsforum.com/avs-vb/showthread.php?p=17705737)
[http://www.avsforum.com/avs-vb/showthread.php?t=1207264](http://www.avsforum.com/avs-vb/showthread.php?t=1207264)

ALSA change log:
[http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22](http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22)

"ALSA: hda - Add PCI IDs for Nvidia G2xx-series"

---

### Post by jocefus on 2009-12-24
compiled today... no such luck. the onboard hdmi passthru on this m3n72d mobo sill functions, however that is it. It no longer loads the analog or 5.1 HD capababilities for regular pc speakers. no listings in alsamixer or aplay. Of course the hdmi audio on the discrete geforce 210 is a no go as well. funny thing is alsaconf sees both cards and claims to configure them successfully. Downgrade to 1.0.21a restores everything except g210 audiio.
I dont know alsa's workings well. getting this error tho:

[   14.540047] hda_codec: cannot build controlsfor #0 (error -22)

Have attempted this several times in various orders of installs... killing alsa/not killing gdm/not reboot after reboot. Everything compiles and installs fine but does not function on my particular system (x86_64). Further reading in alsa bugtracker reveals many problems with hda_intel 1.0.22 module.

---

### Post by skdevnath on 2010-01-18
This is very disappointing, even ATI's HD3200 audio works on Linux.
I brought nvidia card so that I have better support of Linux driver, didn't know that they will screw up the audio driver. Video is working very good, absolutely no load to my CPU.  :(

---

### Post by jocefus on 2010-01-23
well compiled 1.0.22.1 and... fixed issues with not recognizing onboard HD audio and such, but still no sound through this gforce 210 HDMI pass-thru. it seems to be trying to pass to the onboard hdmi although onboard video is disabled in bios. also alsaconf seems to be missing? can't figure out how to tell alsa to use the device on 2nd card. definately not the experience i was hoping for when i got this card.

edit:

aplay -l 

card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

However... cat /proc/asound/cards reveals

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 21
 1 [NVidia_1       ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 29

I have also tried disabling onboard HD audio, but that leaves no hardware devices listed in ubuntu's sound config gui, which I am assuming is the recommended replacement for alsaconf? I am going to force onboard graphics on as a last test. The gui config should show two seperate HDMI output devices, but it doesn't. When I try to initialize the card manually via alsactl I get some errors. May be a bug in alsa treating the card as if it had a built in "sound card," but from what I've read, its simply passing pcm via a pci brige from your existing hd audio device. I believe it because this card is tiny and doesn't even require separate 12v source.

Also.. I recompiled alsa-utils and alsaconf is back now but it mysteriously finds no cards at all. More reading in my future, however I'm done with it for today.

---

### Post by skdevnath on 2010-02-05
> **jocefus said:**
> well compiled 1.0.22.1 and... fixed issues with not recognizing onboard HD audio and such, but still no sound through this gforce 210 HDMI pass-thru. it seems to be trying to pass to the onboard hdmi although onboard video is disabled in bios. also alsaconf seems to be missing? can't figure out how to tell alsa to use the device on 2nd card. definately not the experience i was hoping for when i got this card.

edit:

aplay -l 

card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

However... cat /proc/asound/cards reveals

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 21
 1 [NVidia_1       ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 29

I have also tried disabling onboard HD audio, but that leaves no hardware devices listed in ubuntu's sound config gui, which I am assuming is the recommended replacement for alsaconf? I am going to force onboard graphics on as a last test. The gui config should show two seperate HDMI output devices, but it doesn't. When I try to initialize the card manually via alsactl I get some errors. May be a bug in alsa treating the card as if it had a built in "sound card," but from what I've read, its simply passing pcm via a pci brige from your existing hd audio device. I believe it because this card is tiny and doesn't even require separate 12v source.

Also.. I recompiled alsa-utils and alsaconf is back now but it mysteriously finds no cards at all. More reading in my future, however I'm done with it for today.

Did you look into this alsa development thread on this chipset ?
[thread ]("http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024233.html")

Sounds like, they were able to make it work partially. So looks like there is some hope to use the HDMI Audio feature of this card.

---

### Post by chalewa on 2010-02-15
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

I should be hopefully getting this card tomorrow, and have been doing some digging on this problem... 

anyone with this card care to give this a shot? looks promising.

---

### Post by maxchock on 2010-03-03
i'm using Mint on geforce210 HDMI audio, when i ran "aplay -l" it only show:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

can't see any "NVIDIA HDMI [NVIDIA HDMI]" device on the list like you guys. What may went wrong?

i'm using LinuxMint 8 (Helena)
kernel 2.6.31-14-generic.
Gnome 2.28.1

Thanks & regards,
Max Chock.

---

### Post by jocefus on 2010-05-02
> **maxchock said:**
> i'm using Mint on geforce210 HDMI audio, when i ran "aplay -l" it only show:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

can't see any "NVIDIA HDMI [NVIDIA HDMI]" device on the list like you guys. What may went wrong?

i'm using LinuxMint 8 (Helena)
kernel 2.6.31-14-generic.
Gnome 2.28.1

Thanks & regards,
Max Chock.

what version of alsa do you have installed? The default in ubuntu karmic and lucid is alsa 1.0.21. I have been compiling/upgrading to latest alsa-stable releases, however, I have not yet tested alsa1.0.23... been upgrading laptop to lucid and settling in.

 you can check your alsa version with 'cat /proc/asound/version' on ubuntu. no experience with mint... may be the same.

will post results of hdmi audio with alsa1.0.23 when I get time to spend on my htpc. the link in chalewa's post above looks promising as well.[U]
[/U]

---

### Post by ngupta on 2010-05-07
Got it all working today.. spent almost half a night in troubleshooting and reading various forums. The problem was quite simple as usual :p

Lets see if my activity can help others in getting this GeForce 210 card working with Ubuntu 9.10.

1. My distro is Element 1.1 which is Karmic Koala 9.10 based
uname -a
Linux htpc 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

2. Mobo is Asus M4A785TD-M EVO which has onboard ATI Radeon 4200 HD
Unfortunately, I am not happy with ATI performance.. Lot of vsync and tearing issues. Ati's fglrx software is not as capable as nvidia's in my opinion, so I decided to buy this cheap geforce 210 from frys. $19.99 after rebate !!!

Its EVGA branded, with 512MB DDR2 memory. 589 Core clock.

The card may not be high end for gaming and some reviews on internet suggest its a very basic card. But its multimedia performance on Linux is not as bad.. in fact very superior to ATI 4200.

I also disabled onboard HDMI audio from BIOS to use this nvidia.

3. Installed Alsa 1.0.23 from source directly. The instructions are very simple on alsa's install webpage.
1.0.22-1 didnt work very well.

4. aplay -l shows card 0 and 1. 1 refers to Nvidia. So my /etc/modprobe.d/sound.conf looks like this:

           options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

4. /etc/asound.conf looks like this so that default works with card 1, device 3.

pcm.!default {
type hw
card 1
device 3
}

5. Now the tricky part was to unmute nvidia :)

sudo alsamixer

Hit <F6> to select device and select Nvidia
If you see it muted, then press "m" and exit 

Thats it folks.. my HDMI sound was working like a charm.

In Mythtv frontend, you can specify plughw:1,3 based on my examples.

In Boxee and XBMC also, the sound works perfect now.

I am so glad that HDMI video is far better than onboard ATI Radeon 4200. 1080i playback is very nice. ):P

---

### Post by jocefus on 2010-05-18
I can confirm the hdmi audio is finally working with geforce 210 on my lucid lynx machine using alsa 1.0.23 from source, however not without .conf tweaks posted by ngupta. much thanks.

---

### Post by Kalibur on 2010-05-18
This is all great news guys.  I am shopping for a new graphics card because my current a nvidia GeForce 8400 GS.  Am using the DVI with a hdmi adapter so I dont expect any audio from it.  For audio I use digital out from the mobo audio card however this is only providing stereo sound and not 7.1 as it does using the stereo pins and possibly in hdmi with I dont use because i use a pci-e graphics card (one mentioned above).

The problem I have with my Geforce 9400 GS is that on video play back where the action gets fast I see blocks of bittering like its not pumping out enough frames per second.  So does the GT210 show any such jitter and is the audio from the hdmi surround sound at least 5.1.

---

### Post by ngupta on 2010-05-18
I just got a new Asus GT220 today. Replaced the previous eVGA 210. Unmuted in alsamixer again and thats it. Perfect HDMI video+audio working with Geforce 220 also. I bought 220 just because I heard better reviews on it and thought to give it a shot. Both are low profile and fits perfect in my Antec Microfusion 350 based HTPC.

---

### Post by trevs.bronco on 2010-05-30
I have the geforce 210 as well with freshly compiled alsa 1.0.23 on Mythbuntu 10.04.
alplay -l gets me this
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```my asound.conf is
```
pcm.!default {
type hw
card 0
device 3
}
```I selected all 4 IEC958 switches but can't get a peep out of anything I am probably missing something obvious but I can't figure out what. can anyone point it out to me?
Thanks,

Trev

---

### Post by trevs.bronco on 2010-05-30
I knew it was simple, all I had to do was change the device from 0,3  0,7

Trev

---

### Post by jocefus on 2010-05-31
Remember... the vdpau is a whole different beast. Since I started using the card heavily totem doesn't know what to do and crashed my system. (repeatedly) However, nvidia's modified smplayer works well when configured properly... and processor usage is dramatically reduced when playing H264 coded videos. I definitely recommend using smplayer from nvidia's ppa for your video playback. Google it.

---

### Post by jocefus on 2010-05-31
> **trevs.bronco said:**
> I have the geforce 210 as well with freshly compiled alsa 1.0.23 on Mythbuntu 10.04.
alplay -l gets me this
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```my asound.conf is
```
pcm.!default {
type hw
card 0
device 3
}
```I selected all 4 IEC958 switches but can't get a peep out of anything I am probably missing something obvious but I can't figure out what. can anyone point it out to me?

Trev

I had same issue until I followed these instructions I read over... once I did that and rebooted there was only 1 spdif switch to unmute in alsamixer and everything worked.

-

in /etc/modprobe.d/sound.conf place the following line
 
            options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

---

### Post by jmail524 on 2010-07-02
Hi everyone,

I'm having (what looks like) the same problem that has been discussed here except that I still have had no luck getting sound to work.

I have a PNY GeForce 210 video card hooked up to my TV via HDMI.  It's installed in a MSI motherboard with on-board nVidia 6150 that has been disabled in the BIOS (no longer shows up when using "lspci -v".) Here is a little history of what has happened so far:

"lspci -v" shows the new video card and audio components but "aplay -l" doesn't show anything. Downloaded and compiled ALSA 1.0.23.  "aplay -l" now shows 4 HDMI audio devices (#3,7,8,9) and Ubuntu sound preference's show "High Definition Audio Controller" output device but I still don't have any sound.  Then I created the "/etc/modprobe.d/sound.conf" and populated it with "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2" as per *ngupta's* instructions.  Still no sound.  So I created the file "/etc/asound.conf" with "pcm.!default {type hw card 1 device 3}" also as per *ngupta's* instructions.  Still no sound.  I have also tried different device numbers (3,7,8,9) without luck.  Also, I have umuted all 4 of the digital outputs in "alsamixer" and have checked back after every change to make sure nothing became muted.

I'm sure I'm missing something obvious, but I'm not sure where to go from here.  Any help will be greatly appreciated.

Thanks,
Brian

---

### Post by horkthegreen on 2010-07-10
I followed the instructions in this thread and was able to get sound to my TV through the hdmi audio. 

I'm not sure I understand the reasoning behind choosing device 7 from the list of four devices in the config file. Would they all work? Can someone explain why I would choose a particular one?

I was really happy to get this working since the picture via HDMI is so much better than what I was getting from VGA + audio cable from sound card. However, with the HDMI audio it plays fine for awhile (20 mins +) and then the sounds starts degrading... It gets fuzzy and then crackly. Has anyone else had this issue?

I'm wondering if maybe it's a heat issue due to the new card? I'm going to take the top of my case off and see if it makes a difference. If the sound degrades over time still, I'm not sure what to troubleshoot next.

---

### Post by imbmiller on 2010-07-12
> **jmail524 said:**
> Hi everyone,

I'm having (what looks like) the same problem that has been discussed here except that I still have had no luck getting sound to work.

I have a PNY GeForce 210 video card hooked up to my TV via HDMI.  It's installed in a MSI motherboard with on-board nVidia 6150 that has been disabled in the BIOS (no longer shows up when using "lspci -v".) Here is a little history of what has happened so far:

"lspci -v" shows the new video card and audio components but "aplay -l" doesn't show anything. Downloaded and compiled ALSA 1.0.23.  "aplay -l" now shows 4 HDMI audio devices (#3,7,8,9) and Ubuntu sound preference's show "High Definition Audio Controller" output device but I still don't have any sound.  Then I created the "/etc/modprobe.d/sound.conf" and populated it with "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2" as per *ngupta's* instructions.  Still no sound.  So I created the file "/etc/asound.conf" with "pcm.!default {type hw card 1 device 3}" also as per *ngupta's* instructions.  Still no sound.  I have also tried different device numbers (3,7,8,9) without luck.  Also, I have umuted all 4 of the digital outputs in "alsamixer" and have checked back after every change to make sure nothing became muted.

I'm sure I'm missing something obvious, but I'm not sure where to go from here.  Any help will be greatly appreciated.

Thanks,
Brian


I've got a virtually identical setup to you Brian and am having near identical issues as well.  I have probably invested upwards of twenty hours to this one issue in the last three days.  I've followed every guide on "also from source" "upgrading alsa" "using alsa" etc etc with no luck.  I have yet to see any listing in my aplay -l of my Nvidia card.  Of course it does show up in lspci -vv perfectly.  

It seems fairly backassed to approach this whole problem using alsa when there should be a driver out there from Nvidia.  I've only found one mention of it anywhere and it was a brief snippet from the Nvidia support forum.  I'm going to try to compile it on a fresh Lucid build that I made today and see if I have any look.  Ideally I would like to be able to compile a driver sans alsa since 1)I've obviously never gotten it to work the way I need it to and 2)running a native driver makes sooo much more sense to me.  

It makes me so angry that win xp does this perfectly ootb.  someone tell me why?

---

### Post by ubermunkey on 2010-07-12
Hi,
Just thought I would chime in here.

SYS SPEC: GeForce 210 512 MB BOARD RAM / 2 GIG SYS RAM / Ubuntu 10.04 32-Bit

In my case getting Audio over HDMI took 5 steps.

   1. I added the PPA for alsa, canaberra, and pulseaudio by running the following : ```
sudo add-apt-repository ppa:ricotz/unstable && sudo apt-get update
```
   2. After pulling updates for apt I wanted to start from scratch with my sound settings ( new card pushed me to think this ). So, rather than use apt, I used synaptic to Completely remove both alsa and pulseaudio from my system and then reinstalled it. ```
 sudo apt-get purge pulseaudio alsa-base && sudo apt-get install alsa-base pulseaudio
```. Now, check and make sure you have the ppa version ( thats newest stuff ) installed : ```
:~$ dpkg-query --show alsa-base pulseaudio
      alsa-base    1.0.23+dfsg-1ubuntu2
      pulseaudio    1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu16
```If your output matches mine your cookin' with pertrol!!
   3. As per a post on the arch forums [http://bbs.archlinux.org/viewtopic.php?id=90350](http://bbs.archlinux.org/viewtopic.php?id=90350) I had one more step to complete. Apparently, alsa was trying to load the incorrect driver for the card. The following code ( READ THE ARCH POST ) got sound working before and after a reboot. So, as per results from aplay -l```
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
        Subdevices: 0/1
        Subdevice #0: subdevice #0
``` I pointed alsa to the device with ```
sudo echo /etc/modprobe.d/alsa-base.conf >> options snd-hda-intel probe_mask=0xffff,0xfff2
```. Now to make sure the edit took with ```
 sudo cat /etc/modprobe.d/alsa-base.conf
``` NOTE: it appears that ubuntu uses alsa-base.conf rather than sound.conf!!!
   4. At this point sound worked! I went ahead and rebooted anyways.

The only issue I am having at this point is tearing in the video ( its not the machine so much as the driver ). Anyone else getting this with this card and the repo driver?

---

### Post by jmail524 on 2010-07-14
Hi everyone,

I have resolved my audio over HDMI issue.  It was very frustrating and I was so close to the solution a few times but never knew it.

Here is what I did to resolve the problem:

1) Installed a PPA for ALSA Version 1.0.23, rather than trying to compile it myself.  (I found this at *[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")* under comment #17.)
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-23-generic
```2) Reboot the computer to start the new/updated ALSA software.

3) Unmute all of the audio channels using the alsamixer command.
```
alsamixer
```4) Use the *aplay* command to detect what sound devices are available.
```
aplay -l
```    In my case 4 audio devices were found.
```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` If, like me, more than one audio device was shown you have to determine which device is the correct one.  If only one is listed you could probably skip to step 6, but testing it wouldn't be a bad idea.

5) To determine which audio device was the correct one to use, use the *aplay* command again to play a test sound file.  Use the *-D* option to force it to play to a particular device and listen for the results.  The *plughw:X,Y* determines which device it tries to use.  X is the card number and Y is the device number which were listed by issuing the *aplay -l *command in step 4. *test.wav* is the path and name of a sound file. (I used a WAV file because I'm unsure it *aplay* can play MP3s.)  For me I didn't hear anything until I hit device 7 on card 0.
```
aplay -D plughw:0,7 test.wav
```6) Create the file */etc/asound.conf* and populate it with what we have learned. After the card and device entries, enter the values that worked for you.  In my case card 0, device 7 is what worked for me so that is what I put in the config file.
```
sudo gedit /etc/asound.conf
```Here is what I put into the *asound.conf *file.```
pcm.!default {
     type plug
     slave.pcm {
         type hw
         card 0
         device 7
     }
}
```7) Reboot the computer for all of the changes to take effect. (There may be a better way than rebooting.  It's just what was easiest for me.)

8) Test the new sound configuration using the *aplay* command again. This time don't tell it what device to use, the default ALSA device should work at this point.
```
aplay *test.wav*
```9) Finally tell MythTV to use your default ALSA device.  Go into the setup menu under *General / Audio System* (page 3 I believe) and set "Audio output device" to "ALSA:default".

That should be it.  After that I had sound coming through my TV speakers.  It was clean sounding and quite a bit louder that when I using an analog audio cable connect to my TV.  I have had no problem to date, although I have only had it working for about 2-3 days.

I hope this helps,
Brian

---

### Post by jocefus on 2010-07-18
My system:
Lucid Lynx AMD64
Asus M3NHT-deluxe mobo (onboard audio enabled)
Evga Geforce GT 240 - pci-e

Regardless of your nvidia-driver version (though it obviously needs to support the card)...

1. You must have alsa 1.0.23 installed. Google 'Ubuntu lucid Alsa upgrade' for easy solutions as there are a lot out there like: automated scripts, ppa repositories, and a great blog with posts outlining the manual compilation method. I prefer manual compilation and installation from upstream source. Use what ever you are most comfortable.

2. To correct the 4 switches listed in alsamixer, you must edit the file  /etc/modprobe.d/alsa-base.conf in Ubuntu 10.04. The needed settings depends on the number of audio cards you have  installed and their position reported by alsa. You can type 'aplay -l' to see a list of available devices/cards on your machine.

Look for a line that says:
```
options snd-hda-intel blah blah
```If there isn't a line already with options create it, if there is append  to it. In my case, there was no line and the audio device on the video  card is listed as the second card (card 1). I added:
   ```
options snd-hda-intel probe_mask=0xffff,0xfff2
```If you have only the audio devices on the video card (would be card 0) available you should add only:
   ```
options snd-hda-intel probe_mask=0xfff2
```If you had three cards and the one in question was last then:
```
options snd-hda-intel probe_mask=0xffff,0xffff,0xfff2
```Modify your file accordingly. Do you get the idea?

3. Flash Audio - They say if you have Lucid Lynx you don't need this  because npviewer.bin (flash) should default to using pulse, but on my  machine flash always defaulted to alsa and I had no way to tell it to  use a specific alsa output. Changing the default alsa output in  ~/.asoundrc works, but I switch audio outputs quite frequently (hdmi to  display or toslink to amplifier) and this method was a bit cumbersome.  This method must also be used for each user on your machine. So the  solution I've found works best is to create the file /etc/asound.conf  which works for every user login and insert the following:
                ```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```This ensures that all sounds and controls are routed to pulseaudio by default. On a side note, you should also remove or comment out any ~/.asoundrc settings you or your machines other users may have as they could cause a conflict. 

4. After making these changes, reboot the system.
Run alsamixer in terminal. check all cards installed and unmute all relevant switches as they are usually muted by default
Switching to the GT2** HDMI card in alsa should now only show one s/pdif switch

All other settings are achieved through sound preferences gui in gnome...
In 'hardware' tab you should now see a device 'High Definition Audio  Controller' with only 1 output 'Digital Stereo (HDMI)' and 1 profile 
In output tab you should be able to select 'High Definition Audio Controller Digital Stereo (HDMI) Stereo'

All built-in apps (including flash/firefox npviewer.bin) should list in  'applications' tab and should now be coming through your hdmi port. I  don't know about system sounds, as those are disabled promptly on my  machines. Another thing to remember is that pulse automatically scales  all audio to 2ch stereo, so for 5.1+ surround high-def content you will  want to by-pass pulse and stream lpcm straight to alsa, but that is  another topic all together. Most other good Linux media applications including mplayer have settings in preferences for this, but flash obviously doesn't. 

--

I am able to use the sound preferences gui to seamlessly switch  between available sound cards, outputs, and profiles. Some displays (my Sony Bravia HDTV for instance) are funny about midstream audio switching, specially during hotplugging display devices. May be something to do with their *cough* HDCP protocol. In any case stopping/restarting audio playback usually fixes the issue. I have experienced no degradation of  sound quality over time, and my card (210) runs cool even at 1920x1080 (some  very active videos are a little choppy). 

I recently switched to a GT240  card. Temps are a bit warmer because of DDR5 memory, however video is much more smooth and stable.

The way I do it (nvidia-installer from their site/alsa 1.0.23 from  source) means I have to manually reinstall nvidia driver and recompile alsa every time a kernel or  even kernel header update comes through, but I have done it many times  and it doesn't take long on my machine.

---

### Post by chmelarp on 2010-11-02
I'm affraid this doesn't work in Ubuntu 10.10.

According to *aplay -l* I can play a sample sound using *aplay -D plughw:1,7 test.wav* and It works fine with no other activities necessary.

However, If I put into the *asound.conf *file.     
```
     pcm.!default {
     type plug
     slave.pcm {
         type hw
         card 1
         device 7
     }
} 
```then It works only for FLV player in Firefox, but it has no effect for other sounds in the system (because using pulseaudio I guess). Moreover, there can be only one sound playing at a time. *aplay -D plughw:1,7 test.wav* returns device bussy when playing flash video or other aplay together.

Also, if I set in */etc/modprobe.d/alsa-base.conf*
```

options snd-hda-intel probe_mask=0xffff,0xfff2
```the gnome-volume-control 2.31.6 (and pulse audio) doesn't work at all.

So I set the */etc/pulse/default.pa*
```
load-module module-alsa-sink device=hw:1,7 sink_name=Yamaha
set-default-sink Yamaha
```However, this has no effect at all, except in the gnome-volume-control there is another output selected and *pacmd list-sinks* has an other sink:
```
  * index: 1
    name: <Yamaha>
    driver: <module-alsa-sink.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 2
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
    module: 18
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "NVIDIA HDMI"
        alsa.id = "NVIDIA HDMI"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfe9fc000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "nVidia Corporation"
        device.product.id = "0be3"
        device.product.name = "High Definition Audio Controller"
        device.string = "hw:1,7"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.description = "High Definition Audio Controller"
        device.icon_name = "audio-card-pci"
```so it seems it should work, but no - there is no sound at all. 

Is there a problem with the driver? Probably it should be instead <module-alsa-card.c> of <module-alsa-sink.c> - does anybody know how to change it? Also, other pulse sinks have device.string = "hdmi:1", but there is no other hdmi in fact - do you know how to change the device, which is automatically detected? Or do you think it is a problem of alsa? How can I fix it and attach pulse to it?

---

### Post by efflandt on 2010-11-02
**ngypta**'s reply sure helped me to get HDMI sound working on a GT220 in 64-bit Maverick with i5 650 cpu.  Other web searches and posts were somewhat confusing because they had to do other things before HDMI audio support was in an included alsa version, and were not clear what files to put which settings in.

In the end all I needed was create **/etc/modprobe.d/sound.conf** containing the following:

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```Instead that could be added to /etc/modprobe.d/alsa-base.conf, but then it might disappear after an alsa update or system upgrade.

To use pulse audio (like gnome Sound Preferences) to control it create **/etc/asound.conf** containing:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```Then it simply worked.  I can play Rhythmbox and use **Sound Preferences** to switch Output between **Internal Analog Stereo** and **High Definition Audio Controller Digital Stereo (HDMI)** on the fly.  Although, I will have to research how other apps work because real 64-bit flash now seems to default to HDMI audio, or maybe it depends what was set when Firefox is started.

Suggestions to add a line in /etc/pulse/default.pa about module-alsa-sink just broke sound, so I deleted that added line.

**aplay -l** (I think there were at least 2 if not 4 NVidia devices listed before I set sound.conf and asound.conf above):

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```**horkthegreen**, make sure that your video card fan is running.  I have seen posts of people with gpu fan not running on their GT220 or 210 (overheating).  If I run my GT220 gpu at 100% until temperature stops rising, it is only about 55 C with variable speed fan auto running 30%.  Although, I heard that the 210 has a fixed speed fan (if it is running).

PS: I have some time lag during boot (at console screen before gui login screen) when HDMI audio is configured, regardless of whether I have analog or HDMI audio set for Output in gnome:

**dmesg | grep -i hda**
```
[   12.483849] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.483852] hda_intel: codec_mask forced to 0xff
[   12.483900] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.577738] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   16.585109] hda-intel: Codec #1 probe error; disabling it...
[   17.672215] hda-intel: Codec #2 probe error; disabling it...
[   17.778334] hda_codec: ALC887: BIOS auto-probing.
[   17.791427] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.791431] hda_intel: codec_mask forced to 0xf2
[   17.791469] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.932552] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   21.939922] hda-intel: Codec #4 probe error; disabling it...
[   23.038338] hda-intel: Codec #5 probe error; disabling it...
[   24.135425] hda-intel: Codec #6 probe error; disabling it...
[   25.232556] hda-intel: Codec #7 probe error; disabling it...
[   32.666771] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```**dmesg | grep -i hdmi**
```
[   27.082570] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   27.108021] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   29.121131] HDMI: detected monitor LG TV
[   29.121134]        at connection type HDMI
[   29.121143] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
[   31.105973] HDMI: detected monitor LG TV
[   31.105976]        at connection type HDMI
[   31.105984] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
```Although, once X is up and running things work fine.

PS: Changed /etc/asound.conf so real 64-bit flash would use gnome (pulse) Sound Preferences instead of default alsa audio.

PPS: I have been experimenting with settings, and following for **/etc/modprobe.d/sound.conf** (or added to alsa-base.conf) works cleaner by eliminating boot lag/errors probing unnecessary codecs:

```
options snd-hda-intel enable_msi=0 probe_mask=1,2
```dmesg | grep -i hda```
[   21.691215] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.691277] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.798873] hda_codec: ALC887: BIOS auto-probing.
[   21.805925] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.805965] HDA Intel 0000:01:00.1: setting latency timer to 64
[   30.107862] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```Still have not figured out how to set bdl_pos_adj for nvidia, but IRQ then works for analog sound and HDMI sound works fine.

---

### Post by SlugmanSlimer on 2010-11-04
Hi all, 
Hopefully I can find some help here.  I've read through this forum, and tried all but to no avail.  I still get no audio through my HDMI cable.  I have the GeForce 210 Video/Sound card and a Asus P5Q Pro motherboard with onboard sound.  If I switch sound cards in alsamixer and make sure volume is on for both, I don't get any volume from either sound card - I'd like to get at least one working, but would prefer sound to come from HDMI through TV.

Here is a print out of what I have

--------------------------------
**dmesg | grep -i hdmi**


[   26.767134] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   26.790026] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   28.751274] HDMI: detected monitor SAMSUNG DLP
[   28.751277]  at connection type HDMI
[   28.751282] HDMI: available speakers: FL/FR
[   28.751289] HDMI: supports coding type LPCM: channels = 2, rates = 44100 4800                       0 88200, bits = 16 20
[   30.720156] HDMI: detected monitor SAMSUNG DLP
[   30.720158]  at connection type HDMI
[   30.720161] HDMI: available speakers: FL/FR
[   30.720165] HDMI: supports coding type LPCM: channels = 2, rates = 44100 4800                       0 88200, bits = 16 20

---------------------------------
**dmesg | grep -i hda**

[    9.795539] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.795728] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    9.795758] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.056950] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.056955] hda_intel: Disable MSI for Nvidia chipset
[   10.056991] HDA Intel 0000:01:00.1: setting latency timer to 64
[   38.447171] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

--------------------------------------
**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks!

---

### Post by efflandt on 2010-11-04
SlugmanSlimer, what do you have in /etc/modprobe.d/sound.conf (or alsa-base.conf there) related to snd-hda-intel?

---

### Post by SlugmanSlimer on 2010-11-04
Here is my alsa-base.conf, there is no sound.conf file (which I believe is correct

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by arriflex on 2010-11-06
This seems to be becoming a definitive Geforce 210 audio guide! I was able to get mine running following the XBMC wiki. However, there is a problem with one of the ATSC channels that is encoding audio this way:
```
scan: audio 0x1: AC-3, rate=48000Hz, bitrate=256000 English (AC3) (2.0 ch)
```

However, watching mythfrontend -v audio in the terminal shows the following (amongst other things):

```
AO: Original audio codec was AC3
AudioOutputALSA::GetSupportedRates opening plughw:1,7
AO: Sample rate 22050 is supported
AO: Sample rate 44100 is supported
AO: Sample rate 48000 is supported
AO: Sample rate 88200 is supported
AO: Sample rate 96000 is supported
AO: Sample rate 176400 is supported
AO: Sample rate 192000 is supported
Opening audio device 'plughw:1,7'. ch 2(2) sr 48000 (reenc 0)
Setting IEC958 status: audio
Opening ALSA audio device 'plughw:1,7'.

```

My concern is that the drivers don't support the higher sample rate. This seems to manifest itself in poor playback of recordings from CBS which is broadcasting their atsc stream with 256k audio around my parts. The recordings are jittery, refuse audio sync, and the video seems to play at around 2x while filling up my mythfrontend.log with various buffering errors.

I guess one thing would be to go back to analog audio and forget about using the HDMI cable for audio. Are there other options? I probably should mention that my nVidia driver is 260.19.06

Hope this helps someone else, meanwhile I'm open to options.

arri

---

### Post by SlugmanSlimer on 2010-11-06
Sorry, I'm not much help here, as I don't understand the audio playback in linux very well at all.  However, I do have another issue that is potentially related.  The video playback on most video files on my system seems is playing back at a faster rate than it should.  Don't know why this is happening, but if audio is effected through the same device, I'm wondering if there is some sort of playback rate that is been effected.

Hope I'm relaying my 'simple' problem correctly...

---

### Post by chmelarp on 2010-11-12
efflandt: Thank you VERY much... [this works]("http://ubuntuforums.org/showthread.php?p=10108349#post10108349") including the boot lag, flash and everything :P

---

### Post by todd_vohs on 2010-12-05
OK, I thought I would dump my Vista box in lieu of Ubuntu 10.10.  I have a Dell Precision 470, Xeon 3.2Ghz, 4GB RAM, 160GB HDD.  I removed the SoundBlaster card that came with it and disabled the onboard audio.  I then installed an eVGA GeForce 210.  Worked great on Vista since everything is hooked to a Pioneer VSX-1020k Receiver via HDMI.  The Pioneer is hooked to my Panasonic 50G10 Plasma and upconverts everything to 1080p and will decode just about anything audio.  From what I understand about the whole thing is that I should be able to pass undecoded audio to the Pioneer and let it, and not the PC, decode it.

I have been following this post since everything went flawlessly installing except for audio across the HDMI.  I started out with 4 devices on my aplay -l but am now down to a single device after all the installations, .conf editing, etc. and being fairly new to the Linux world, I am starting to get confused and it seems my 10.10 is going backwards.

**aplay -l** looks like:
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

There used to be 3 additional devices numbered 7, 8 and 9.  Now there is one left.  I have added the following line to alsa-base.conf since an earlier post stated the sound.conf was not supported in 10.10 but I created the sound.conf file too:

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

My asound.conf looks like:
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

I have installed the latest PULSE according to earlier posts but now my **dmesg | grep -i hda **shows:**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
root@unbuntu:/home/todd# dmesg | grep -i hda
[   21.840216] HDA Intel 0000:05:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.840257] HDA Intel 0000:05:00.1: setting latency timer to 64
[   21.840263] ALSA hda_intel.c:2559: chipset global capabilities = 0x2403
[   21.864373] ALSA hda_intel.c:914: codec_mask = 0xf
[   21.884046] ALSA hda_intel.c:1354: codec #0 probed OK
[   21.998193] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_get_connections
[   21.998200] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_get_connections (err -22)
[   21.998313] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_codec_read
[   21.998317] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_codec_read (err -22)
[   21.998429] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_delete_codec_preset
[   21.998432] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_delete_codec_preset (err -22)
[   21.998568] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_eld_proc_free (err 0)
[   21.998678] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_open
[   21.998681] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_open (err -22)
[   21.998806] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_get_sub_nodes
[   21.998809] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_get_sub_nodes (err -22)
[   21.998921] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_close
[   21.998924] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_close (err -22)
[   21.999036] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_sequence_write
[   21.999039] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_sequence_write (err -22)
[   21.999159] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_codec_write
[   21.999162] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_codec_write (err -22)
[   21.999275] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_add_codec_preset
[   21.999278] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_add_codec_preset (err -22)
[   21.999405] snd_hda_codec_nvhdmi: Unknown symbol snd_print_channel_allocation (err 0)
[   21.999531] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_pin_sense
[   21.999534] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_pin_sense (err -22)
[   21.999657] snd_hda_codec_nvhdmi: Unknown symbol snd_hdmi_show_eld (err 0)
[   21.999774] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_create_spdif_out_ctls
[   21.999778] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_create_spdif_out_ctls (err -22)
[   21.999899] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_prepare
[   21.999902] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_prepare (err -22)
[   22.000063] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_eld_proc_new (err 0)
[   22.002037] snd_hda_codec_nvhdmi: Unknown symbol snd_hdmi_get_eld (err 0)
[   26.498648] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.512411] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   26.536129] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.552044] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   26.553835] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   26.553877] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   26.558127] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.572042] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   26.572108] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.588060] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   26.934125] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   32.827610] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   32.827667] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[  760.233836] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[  983.352060] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  983.368054] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[  983.368119] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  983.384054] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
And **dmesg | grep -i hdmi** is showing:
[   21.998193] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_get_connections
[   21.998200] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_get_connections (err -22)
[   21.998313] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_codec_read
[   21.998317] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_codec_read (err -22)
[   21.998429] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_delete_codec_preset
[   21.998432] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_delete_codec_preset (err -22)
[   21.998568] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_eld_proc_free (err 0)
[   21.998678] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_open
[   21.998681] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_open (err -22)
[   21.998806] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_get_sub_nodes
[   21.998809] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_get_sub_nodes (err -22)
[   21.998921] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_close
[   21.998924] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_close (err -22)
[   21.999036] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_sequence_write
[   21.999039] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_sequence_write (err -22)
[   21.999159] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_codec_write
[   21.999162] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_codec_write (err -22)
[   21.999275] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_add_codec_preset
[   21.999278] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_add_codec_preset (err -22)
[   21.999405] snd_hda_codec_nvhdmi: Unknown symbol snd_print_channel_allocation (err 0)
[   21.999531] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_pin_sense
[   21.999534] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_pin_sense (err -22)
[   21.999657] snd_hda_codec_nvhdmi: Unknown symbol snd_hdmi_show_eld (err 0)
[   21.999774] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_create_spdif_out_ctls
[   21.999778] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_create_spdif_out_ctls (err -22)
[   21.999899] snd_hda_codec_nvhdmi: disagrees about version of symbol snd_hda_multi_out_dig_prepare
[   21.999902] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_multi_out_dig_prepare (err -22)
[   22.000063] snd_hda_codec_nvhdmi: Unknown symbol snd_hda_eld_proc_new (err 0)
[   22.002037] snd_hda_codec_nvhdmi: Unknown symbol snd_hdmi_get_eld (err 0)
[   26.512404] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   26.552036] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   26.572035] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   26.588052] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
[  983.368047] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
[  983.384047] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40

So, I was wondering if anyone knows any idea of how to get this to work since it is beyond me now.  It only takes a few minutes for me to totally reload 10.10 since there is nothing else on the machine and it is coming off a USB thumb drive.  I can see there are errors, I just don't know how to fix them or if it worth the time to try to fix them and just reload and try again.

At one point, my alsamixer was showing 4 devices, then a single Pulse device and now it is refusing my connection:

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused

And just for reference, 

**lspci -vv**
05:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. Device 1210
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at dfbfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #4, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <1us, L1 <1us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Any simple solutions or just reload and try again?

One othe thing, since I am pumping through a receiver that upconverts the video, the PC overscans and leaves all upper and lower menu bars off the edge of the TV.  I can adjust the overscan in the nVidia settings but cannot get it to stay so every time I login or reboot, I have to adjust it again.  I have tried saving the xserver file but it will only maintain the resolution, refresh, etc.  At first I thought the PC just locked up but finally moved the mouse over the time and a drop down came on the screen so I knew there was something up there, just couldn't read it so I poked around a while before I got it figured out.

Thanks,

Todd.

---

### Post by V1eras on 2010-12-23
God bless jmail524 and message #28  :popcorn:

Now I've sound over hdmi  :D

---

### Post by efflandt on 2010-12-23
I have totally changed my thinking about this since I switched from a GT 220 to GT 430.  For the GT 220 my HDMI audio in Maverick was card 1, device 3.  So my earlier post eliminated card 1, devices 7, 8, 9, making 1,3 the default, and set pulse to use it.

The current Maverick kernel supports my card without the alsa ppa.  But the method I used for the GT 220 did not work because the only HDMI audio that works for the GT 430 is card 1, device 9, and the earlier method makes that disappear.

So in the end, all I had to do was:

[LIST=1]
[*]Make sure the HDA NVidia devices show up in **aplay -l**
[*]Use **alsamixer** to _unmute_ all the S/PDIF devices for HDA NVidia
[*]**aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav** or 1,7 1,8 or 1,9 until I figured out which one worked (1,9 for me)
[/LIST]
Then the _only system configuration_ was to insert the following line after the commented out alsa-sink line in /etc/pulse/default.pa

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Reboot.  Then you can use **Sound Preferences** to set the **Output** device.  Although, you will end up with an extra device and the one that works for HDMI is the NVidia one that does NOT say HDMI.  The speaker test in Sound Preferences will not work, but you can easily run Rythmbox and test different Outputs on the fly.

---

### Post by gillis892 on 2011-03-13
hey all, these threads have been a tremendous help to me setting up my HTPC. i now have Ubuntu 10.10 with a geforce 210 with audio through hdmi.
i have found that the video isnt what it should so i started playing with depth, turned it to 16 and the play back is much better, am i wrong or should this video card beable to keep up with 60hz refresh rate and 24 color depth?  or is it a problem with the drivers
i am currently running nvidia 160.19.06
just thought id throw it out here in case any one has had this problem.
thanks.

---

### Post by gillis892 on 2011-03-13
just incase,my xorg.conf reads

```

```# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics LG TV"
    HorizSync       31.0 - 82.0
    VertRefresh     57.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection

Section "Screen"

# Removed Option "metamodes" "1360x768 +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1360x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

```

---

### Post by gillis892 on 2011-03-14
hey all i have fixed this problem, and i will post what i did for anyone else that this may happen to.
 
if you have a geforce 210 with ubunutu and have 'lines' during fast video playback. this is called video tearing and can be fixed.
go to your nvidia x server conf and find 'sync to blank' or 'sync to vblank' enable this where ever you can find it, you will also find it under setting in XBMC as 'vertical blank sync'.

If this method did nothing for you try these:
[http://ubuntuforums.org/showthread.php?t=1628754](http://ubuntuforums.org/showthread.php?t=1628754)

---

### Post by bcschmerker on 2011-04-22
Thanks, everybody, for a heads up on the GeForce® 200 series issues.  I am starting the rebuild of my down (as of April 2011) eMachines®/Acer® EL1210-09 and now have a Shuttle® PC6300002 power supply in for the stock LiteOn® PS-5221-06 (which, I found out to my chagrin, was mis-built with no +3.3VDC to the SATA).  I may be retrofitting an [Asus® ENGT220/DI/1GD3(LP)](http://usa.asus.com/) ([nVIDIA® GeForce® GT 220 GPU](http://www.nvidia.com/), PCI-Express x16 half-height) to supersede the planar GeForce® 8200 GPU subsystem; Ubuntu® supports nVIDIA® hardware well enough for testing purposes (I already know the entire GeForce® Series to be fully supported in Microsoft® Windows® Se7en 7.0.8001 and Server 2008R2 6.1.7601, but that OS is *quite* expensive to license and install).

---

### Post by sniper69 on 2011-06-30
With the geforce 210 hdmi - it works with no problems in ubuntu 11.04.  I just had to go into sound preferences, then click on the hardware tab, make sure internal wasn't checked, then under the output tab make sure output was set to hdmi and not internal.  Under the hardware tab, I chose nr 2 for the hdmi profile.  Everything is working fine with the audio.  
My geforce 210 is an EVGA brand and it is installed in a shuttle SG33G5.  
This was done on a fresh install on a dual boot set up.

---

### Post by pablox1 on 2011-09-20
I tried everything, but still doesn't work. ¿any sugestion?



_My #ALSA Information Script v 0.4.60#_

[http://www.alsa-project.org/db/?f=3d90aa64d246841f2cda5d43bb0b52a0b4ecfda0](http://www.alsa-project.org/db/?f=3d90aa64d246841f2cda5d43bb0b52a0b4ecfda0)

---

### Post by sniper69 on 2011-09-20
> **pablox1 said:**
> I tried everything, but still doesn't work. ¿any sugestion?



_My #ALSA Information Script v 0.4.60#_

[http://www.alsa-project.org/db/?f=3d90aa64d246841f2cda5d43bb0b52a0b4ecfda0](http://www.alsa-project.org/db/?f=3d90aa64d246841f2cda5d43bb0b52a0b4ecfda0)

Which version of ubuntu are you using?  :)

---

### Post by pablox1 on 2011-09-20
> **sniper69 said:**
> which version of ubuntu are you using?  :)

11.04

---

### Post by BicyclerBoy on 2011-09-20
The module probe_mask values are all wrong.
It looks like you used the XBMC GT210/220 wiki page which is almost all wrong/incorrect.

You have probe_mask setup for (2) soundcards & the values are both incorrect/invalid.
The values should be [-1, 0 - 15].
[-1] means ignore
[ 0 - 15] form the 4 bit mask on exposing codecs.

Your alsa default is pointing to hw:0,3.
This could work if probe_mask=0x8

1. Remove the probe_mask (s) 
2. [sudo] update-initramfs -u
3. aplay -l
4. dmesg | grep HDMI
5. speaker-test -c 2 -r 48000 -D hw:0,9
6. cat /proc/asound/card0/eld#3.0

Step 2. may not be necessary..

The probe_mask of 0xffff is being applied to the first snd card (HDA nVidia), this value is currently == 0xf or 15. This exposes all codecs.

---

### Post by pablox1 on 2011-09-20
> **BicyclerBoy said:**
> The module probe_mask values are all wrong.
It looks like you used the XBMC GT210/220 wiki page which is almost all wrong/incorrect.

You have probe_mask setup for (2) soundcards & the values are both incorrect/invalid.
The values should be [-1, 0 - 15].
[-1] means ignore
[ 0 - 15] form the 4 bit mask on exposing codecs.

Your alsa default is pointing to hw:0,3.
This could work if probe_mask=0x8

1. Remove the probe_mask (s) 
2. [sudo] update-initramfs -u
3. aplay -l
4. dmesg | grep HDMI
5. speaker-test -c 2 -r 48000 -D hw:0,9
6. cat /proc/asound/card0/eld#0.3

Step 2. may not be necessary..

The probe_mask of 0xffff is being applied to the first snd card (HDA nVidia), this value is currently == 0xf or 15. This exposes all codecs.


1. done

2. done

3. aplay -l
```
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```4. dmesg | grep HDMI
```
[   20.736293] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   20.736354] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   20.736401] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   20.736452] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input9
[   24.088089] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.120044] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.192046] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.224045] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.296037] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.328036] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.400042] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   24.432040] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.436043] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.468080] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.540040] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.572090] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.652070] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.684042] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.756038] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   32.788026] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  121.176066] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  121.216065] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  122.684095] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  122.724067] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  124.384079] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  124.424083] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  125.424059] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[  125.464070] ALSA patch_hdmi.c:450: HDMI: select CA 0xb for 6-channel allocation:  FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
```5. No sound

6. don't exist


Still no sound..](*,)

---

### Post by pablox1 on 2011-09-20
/etc/modprobe.d/alsa-base.conf

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto
```

---

### Post by BicyclerBoy on 2011-09-21
Made a mistake with step 6.

cat /proc/asound/card0/eld#3.0

Is your HDMI audio receiver directly connected ?
You **must** be running the proprietary nVidia X server driver.
The X server must be active..

The dmesg output shows you have no detected HDMI device..

I think you should **not** have any snd-hda-intel module options..
snd-hda-intel model=auto
snd-hda-intel enable_msi=0

Maybe you should post your
/var/log/Xorg.0.log

---

### Post by pablox1 on 2011-09-21
/var/log/Xorg.0.log 	

```
[    21.606] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.606] X Protocol Version 11, Revision 0
[    21.606] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.606] Current Operating System: Linux H1 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    21.606] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e6af46ce-2b71-4e09-86a2-d52b897ef0d5 ro quiet splash vt.handoff=7
[    21.606] Build Date: 11 August 2011  03:47:56PM
[    21.606] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    21.606] Current version of pixman: 0.20.2
[    21.606]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.606] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.606] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 21 09:24:40 2011
[    21.606] (==) Using config file: "/etc/X11/xorg.conf"
[    21.606] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.607] (==) ServerLayout "Layout0"
[    21.607] (**) |-->Screen "Screen0" (0)
[    21.607] (**) |   |-->Monitor "Monitor0"
[    21.607] (**) |   |-->Device "Device0"
[    21.607] (**) |-->Input Device "Keyboard0"
[    21.607] (**) |-->Input Device "Mouse0"
[    21.607] (**) Option "Xinerama" "0"
[    21.607] (==) Automatically adding devices
[    21.607] (==) Automatically enabling devices
[    21.607] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.607]     Entry deleted from font path.
[    21.607] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.607] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.607] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.607] (WW) Disabling Keyboard0
[    21.607] (WW) Disabling Mouse0
[    21.607] (II) Loader magic: 0x81ffde0
[    21.607] (II) Module ABI versions:
[    21.607]     X.Org ANSI C Emulation: 0.4
[    21.607]     X.Org Video Driver: 10.0
[    21.607]     X.Org XInput driver : 12.3
[    21.607]     X.Org Server Extension : 5.0
[    21.608] (--) PCI:*(0:1:0:0) 10de:0a65:3842:1212 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    21.608] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.608] (II) LoadModule: "extmod"
[    21.639] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.639] (II) Module extmod: vendor="X.Org Foundation"
[    21.639]     compiled for 1.10.1, module version = 1.0.0
[    21.639]     Module class: X.Org Server Extension
[    21.639]     ABI class: X.Org Server Extension, version 5.0
[    21.639] (II) Loading extension MIT-SCREEN-SAVER
[    21.639] (II) Loading extension XFree86-VidModeExtension
[    21.639] (II) Loading extension XFree86-DGA
[    21.639] (II) Loading extension DPMS
[    21.639] (II) Loading extension XVideo
[    21.639] (II) Loading extension XVideo-MotionCompensation
[    21.639] (II) Loading extension X-Resource
[    21.639] (II) LoadModule: "dbe"
[    21.640] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.640] (II) Module dbe: vendor="X.Org Foundation"
[    21.640]     compiled for 1.10.1, module version = 1.0.0
[    21.640]     Module class: X.Org Server Extension
[    21.640]     ABI class: X.Org Server Extension, version 5.0
[    21.640] (II) Loading extension DOUBLE-BUFFER
[    21.640] (II) LoadModule: "glx"
[    21.640] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.658] (II) Module glx: vendor="NVIDIA Corporation"
[    21.658]     compiled for 4.0.2, module version = 1.0.0
[    21.658]     Module class: X.Org Server Extension
[    21.658] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    21.658] (II) Loading extension GLX
[    21.658] (II) LoadModule: "record"
[    21.658] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.658] (II) Module record: vendor="X.Org Foundation"
[    21.658]     compiled for 1.10.1, module version = 1.13.0
[    21.658]     Module class: X.Org Server Extension
[    21.658]     ABI class: X.Org Server Extension, version 5.0
[    21.658] (II) Loading extension RECORD
[    21.658] (II) LoadModule: "dri"
[    21.659] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.659] (II) Module dri: vendor="X.Org Foundation"
[    21.659]     compiled for 1.10.1, module version = 1.0.0
[    21.659]     ABI class: X.Org Server Extension, version 5.0
[    21.659] (II) Loading extension XFree86-DRI
[    21.659] (II) LoadModule: "dri2"
[    21.659] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.659] (II) Module dri2: vendor="X.Org Foundation"
[    21.659]     compiled for 1.10.1, module version = 1.2.0
[    21.659]     ABI class: X.Org Server Extension, version 5.0
[    21.659] (II) Loading extension DRI2
[    21.659] (II) LoadModule: "nvidia"
[    21.659] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.659] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.659]     compiled for 4.0.2, module version = 1.0.0
[    21.659]     Module class: X.Org Video Driver
[    21.659] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    21.659] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.659] (++) using VT number 7

[    21.660] (II) Loading sub module "fb"
[    21.660] (II) LoadModule: "fb"
[    21.660] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.660] (II) Module fb: vendor="X.Org Foundation"
[    21.660]     compiled for 1.10.1, module version = 1.0.0
[    21.660]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.660] (II) Loading sub module "wfb"
[    21.660] (II) LoadModule: "wfb"
[    21.660] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.660] (II) Module wfb: vendor="X.Org Foundation"
[    21.660]     compiled for 1.10.1, module version = 1.0.0
[    21.660]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.660] (II) Loading sub module "ramdac"
[    21.660] (II) LoadModule: "ramdac"
[    21.660] (II) Module "ramdac" already built-in
[    21.660] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.660] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.660] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.660] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.660] (==) NVIDIA(0): RGB weight 888
[    21.660] (==) NVIDIA(0): Default visual is TrueColor
[    21.660] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.660] (**) NVIDIA(0): Option "TwinView" "1"
[    21.660] (**) NVIDIA(0): Option "MetaModes" "CRT-0: 1440x900 +1440+0, CRT-1: 1440x900 +0+0"
[    21.660] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
[    22.232] (II) NVIDIA(GPU-0): Display (Samsung SM2333T (CRT-0)) does not support NVIDIA 3D
[    22.232] (II) NVIDIA(GPU-0):     Vision stereo.
[    22.249] (II) NVIDIA(GPU-0): Display (Samsung SM2333TN (CRT-1)) does not support NVIDIA 3D
[    22.249] (II) NVIDIA(GPU-0):     Vision stereo.
[    22.250] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)
[    22.250] (--) NVIDIA(0): Memory: 1048576 kBytes
[    22.250] (--) NVIDIA(0): VideoBIOS: 70.18.36.00.14
[    22.250] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    22.250] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.250] (--) NVIDIA(0): Connected display device(s) on GeForce 210 at PCI:1:0:0
[    22.250] (--) NVIDIA(0):     Samsung SM2333T (CRT-0)
[    22.250] (--) NVIDIA(0):     Samsung SM2333TN (CRT-1)
[    22.250] (--) NVIDIA(0): Samsung SM2333T (CRT-0): 400.0 MHz maximum pixel clock
[    22.250] (--) NVIDIA(0): Samsung SM2333TN (CRT-1): 400.0 MHz maximum pixel clock
[    22.251] (**) NVIDIA(0): TwinView enabled
[    22.251] (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
[    22.262] (II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
[    22.262] (II) NVIDIA(0): Validated modes:
[    22.262] (II) NVIDIA(0):     "CRT-0:1440x900+1440+0,CRT-1:1440x900+0+0"
[    22.262] (II) NVIDIA(0): Virtual screen size determined to be 2880 x 900
[    22.282] (--) NVIDIA(0): DPI set to (71, 78); computed from "UseEdidDpi" X config
[    22.282] (--) NVIDIA(0):     option
[    22.282] (--) Depth 24 pixmap format is 32 bpp
[    22.283] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.285] (II) NVIDIA(0): Setting mode "CRT-0:1440x900+1440+0,CRT-1:1440x900+0+0"
[    22.392] (II) Loading extension NV-GLX
[    22.552] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.552] (==) NVIDIA(0): Backing store disabled
[    22.552] (==) NVIDIA(0): Silken mouse enabled
[    22.552] (**) NVIDIA(0): DPMS enabled
[    22.552] (II) Loading extension NV-CONTROL
[    22.553] (II) Loading extension XINERAMA
[    22.553] (II) Loading sub module "dri2"
[    22.553] (II) LoadModule: "dri2"
[    22.553] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.553] (II) Module dri2: vendor="X.Org Foundation"
[    22.553]     compiled for 1.10.1, module version = 1.2.0
[    22.553]     ABI class: X.Org Server Extension, version 5.0
[    22.553] (II) NVIDIA(0): [DRI2] Setup complete
[    22.553] (==) RandR enabled
[    22.553] (II) Initializing built-in extension Generic Event Extension
[    22.553] (II) Initializing built-in extension SHAPE
[    22.553] (II) Initializing built-in extension MIT-SHM
[    22.553] (II) Initializing built-in extension XInputExtension
[    22.553] (II) Initializing built-in extension XTEST
[    22.553] (II) Initializing built-in extension BIG-REQUESTS
[    22.553] (II) Initializing built-in extension SYNC
[    22.553] (II) Initializing built-in extension XKEYBOARD
[    22.553] (II) Initializing built-in extension XC-MISC
[    22.553] (II) Initializing built-in extension SECURITY
[    22.553] (II) Initializing built-in extension XINERAMA
[    22.553] (II) Initializing built-in extension XFIXES
[    22.553] (II) Initializing built-in extension RENDER
[    22.553] (II) Initializing built-in extension RANDR
[    22.553] (II) Initializing built-in extension COMPOSITE
[    22.553] (II) Initializing built-in extension DAMAGE
[    22.553] (II) Initializing built-in extension GESTURE
[    22.555] (II) Initializing extension GLX
[    22.580] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.587] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.587] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.587] (II) LoadModule: "evdev"
[    22.588] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.588] (II) Module evdev: vendor="X.Org Foundation"
[    22.588]     compiled for 1.10.0.902, module version = 2.6.0
[    22.588]     Module class: X.Org XInput Driver
[    22.588]     ABI class: X.Org XInput driver, version 12.3
[    22.588] (II) Using input driver 'evdev' for 'Power Button'
[    22.588] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.588] (**) Power Button: always reports core events
[    22.588] (**) Power Button: Device: "/dev/input/event1"
[    22.604] (--) Power Button: Found keys
[    22.604] (II) Power Button: Configuring as keyboard
[    22.604] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.604] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.604] (**) Option "xkb_rules" "evdev"
[    22.604] (**) Option "xkb_model" "pc105"
[    22.604] (**) Option "xkb_layout" "latam"
[    22.606] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[    22.608] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.608] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.608] (II) Using input driver 'evdev' for 'Power Button'
[    22.608] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.608] (**) Power Button: always reports core events
[    22.608] (**) Power Button: Device: "/dev/input/event0"
[    22.621] (--) Power Button: Found keys
[    22.621] (II) Power Button: Configuring as keyboard
[    22.621] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.621] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.621] (**) Option "xkb_rules" "evdev"
[    22.621] (**) Option "xkb_model" "pc105"
[    22.621] (**) Option "xkb_layout" "latam"
[    22.622] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/input/event6)
[    22.622] (II) No input driver/identifier specified (ignoring)
[    22.623] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/input/event7)
[    22.623] (II) No input driver/identifier specified (ignoring)
[    22.623] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/input/event8)
[    22.623] (II) No input driver/identifier specified (ignoring)
[    22.623] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/input/event9)
[    22.623] (II) No input driver/identifier specified (ignoring)
[    22.626] (II) config/udev: Adding input device CHICONY USB Keyboard (/dev/input/event2)
[    22.626] (**) CHICONY USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.626] (II) Using input driver 'evdev' for 'CHICONY USB Keyboard'
[    22.626] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.626] (**) CHICONY USB Keyboard: always reports core events
[    22.626] (**) CHICONY USB Keyboard: Device: "/dev/input/event2"
[    22.626] (--) CHICONY USB Keyboard: Found keys
[    22.626] (II) CHICONY USB Keyboard: Configuring as keyboard
[    22.626] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input2/event2"
[    22.626] (II) XINPUT: Adding extended input device "CHICONY USB Keyboard" (type: KEYBOARD)
[    22.626] (**) Option "xkb_rules" "evdev"
[    22.626] (**) Option "xkb_model" "pc105"
[    22.626] (**) Option "xkb_layout" "latam"
[    22.626] (II) config/udev: Adding input device CHICONY USB Keyboard (/dev/input/event3)
[    22.626] (**) CHICONY USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.626] (II) Using input driver 'evdev' for 'CHICONY USB Keyboard'
[    22.626] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.626] (**) CHICONY USB Keyboard: always reports core events
[    22.627] (**) CHICONY USB Keyboard: Device: "/dev/input/event3"
[    22.627] (--) CHICONY USB Keyboard: Found keys
[    22.627] (II) CHICONY USB Keyboard: Configuring as keyboard
[    22.627] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.1/input/input3/event3"
[    22.627] (II) XINPUT: Adding extended input device "CHICONY USB Keyboard" (type: KEYBOARD)
[    22.627] (**) Option "xkb_rules" "evdev"
[    22.627] (**) Option "xkb_model" "pc105"
[    22.627] (**) Option "xkb_layout" "latam"
[    22.628] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    22.628] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    22.628] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    22.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.628] (**) Logitech USB Receiver: always reports core events
[    22.628] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    22.628] (--) Logitech USB Receiver: Found 20 mouse buttons
[    22.628] (--) Logitech USB Receiver: Found scroll wheel(s)
[    22.628] (--) Logitech USB Receiver: Found relative axes
[    22.628] (--) Logitech USB Receiver: Found x and y relative axes
[    22.628] (II) Logitech USB Receiver: Configuring as mouse
[    22.628] (II) Logitech USB Receiver: Adding scrollwheel support
[    22.628] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    22.628] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.628] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input4/event4"
[    22.628] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    22.628] (II) Logitech USB Receiver: initialized for relative axes.
[    22.628] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    22.628] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    22.628] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    22.628] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    22.628] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    22.628] (II) No input driver/identifier specified (ignoring)
[    22.629] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    22.629] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    22.629] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    22.629] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.629] (**) Logitech USB Receiver: always reports core events
[    22.629] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    22.629] (--) Logitech USB Receiver: Found 1 mouse buttons
[    22.629] (--) Logitech USB Receiver: Found scroll wheel(s)
[    22.629] (--) Logitech USB Receiver: Found relative axes
[    22.629] (--) Logitech USB Receiver: Found absolute axes
[    22.629] (II) evdev-grail: failed to open grail, no gesture support
[    22.629] (--) Logitech USB Receiver: Found keys
[    22.629] (II) Logitech USB Receiver: Configuring as mouse
[    22.629] (II) Logitech USB Receiver: Configuring as keyboard
[    22.629] (II) Logitech USB Receiver: Adding scrollwheel support
[    22.629] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    22.629] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input5/event5"
[    22.629] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    22.629] (**) Option "xkb_rules" "evdev"
[    22.629] (**) Option "xkb_model" "pc105"
[    22.629] (**) Option "xkb_layout" "latam"
[    22.629] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    22.629] (II) Logitech USB Receiver: initialized for absolute axes.
[    22.629] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    22.629] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    22.629] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    22.629] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[   556.369] (II) XKB: reuse xkmfile /var/lib/xkb/server-BB2AA0BD457DC1C0881C2493AAF6EE210822E28F.xkm
```

---

### Post by pablox1 on 2011-09-21
cat /proc/asound/card0/eld#3.0
```
monitor_present        0
eld_valid        0
monitor_name        
connection_type        HDMI
eld_version        [0x0] reserved
edid_version        [0x0] no CEA EDID Timing Extension block present
manufacture_id        0x0
product_id        0x0
port_id            0x0
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
sad_count        0

```

Operating System: Linux-x86
Nvidia driver version 270.41.06

---

### Post by BicyclerBoy on 2011-09-21
Both your monitors are connected by VGA cables...
There are no detected HDMI devices because there are none..

You must connect some HDMI receiver by DVI-D or DVI-D-HDMI(single link) or HDMI cable.
You must have a X screen active on that connection, it can be a dummy forced output (no real video device)

---

### Post by pablox1 on 2011-09-23
> **BicyclerBoy said:**
> Both your monitors are connected by VGA cables...
There are no detected HDMI devices because there are none..

You must connect some HDMI receiver by DVI-D or DVI-D-HDMI(single link) or HDMI cable.
You must have a X screen active on that connection, it can be a dummy forced output (no real video device)

- I bought dvi-hdmi cables but the sound doesnt work...

- I reinstalled the latest drivers for nvidia (280.13) but the sound still doesnt work...


I think that the problem is with the nvidia driver, but the gt210 nvidia driver (256.53) was "unable to build the NVIDIA kernel module" and I can't kill gdm with sudo...

I need a very specific and detailed guide, since i'm not programmer

---

### Post by sniper69 on 2011-09-23
> **pablox1 said:**
> - I bought dvi-hdmi cables but the sound doesnt work...

- I reinstalled the latest drivers for nvidia (280.13) but the sound still doesnt work...


I think that the problem is with the nvidia driver, but the gt210 nvidia driver (256.53) was "unable to build the NVIDIA kernel module" and I can't kill gdm with sudo...

I need a very specific and detailed guide, since i'm not programmer

The dvi to hdmi cables are only good for a video only connection.  In other words you would also need a separate cable for an audio connection.  The HDMI cable needs to be HDMI to HDMI for video and audio to go through the single cable.

---

### Post by BicyclerBoy on 2011-09-23
That is wrong. HDMI digital audio can be output over DVI.
There is no technical reason why HDMI audio can not be passed end-to-end over DVI or DP.
19 pin HDMI is a single link DVI in a consumer grade plug at hifi price.

The DVI standard has not been extended to include audio.
The problem is there are few/none receivers with DVI supporting HDMI audio.

DVI-HDMI adaptor cables do work with audio.
The DVI end **must** be at the video card end..
The video card needs to have the HDA codec-pin complex wired thru' to the DVI jack..
I'm sure the GT210 has audio over both digital outputs.


What does not work now ??
Does your monitor actually support audio ?
Only the HDMI input will be HDCP compliant or have audio support..

speaker-test -c 2 -r 48000 -D hw:0,9
speaker-test -c 2 -r 48000 -D hw:0,8
speaker-test -c 2 -r 48000 -D hw:0,7
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 2 -r 44100 -D hw:0,9
speaker-test -c 2 -r 44100 -D hw:0,8
speaker-test -c 2 -r 44100 -D hw:0,7
speaker-test -c 2 -r 44100 -D hw:0,3
Note: close & re-open the terminal each time..

cat /proc/asound/card0/eld#....????

Video driver
Don't bother with building driver by the nVidia installer method. It will break with next kernel update.
Just use the repository driver, the GT210 is not new.

But the driver readme describes the process completely..

get dependencies (build essentials, kernel headers ++++)
console login
service gdm stop
run-installer
service gdm start

---

### Post by sniper69 on 2011-09-24
> **BicyclerBoy said:**
> That is wrong. HDMI digital audio can be output over DVI.
There is no technical reason why HDMI audio can not be passed end-to-end over DVI or DP.
19 pin HDMI is a single link DVI in a consumer grade plug at hifi price.

The DVI standard has not been extended to include audio.
The problem is there are few/none receivers with DVI supporting HDMI audio.

DVI-HDMI adaptor cables do work with audio.
The DVI end **must** be at the video card end..
The video card needs to have the HDA codec-pin complex wired thru' to the DVI jack..
I'm sure the GT210 has audio over both digital outputs.

Thanks for the correction.  I didn't realize that DVI to HDMI could also support audio.  :)

---

### Post by BicyclerBoy on 2011-09-24
But only if the DVI jack is wired up to the HDA codec in the video card.
Try finding that out before you buy...

---

### Post by pablox1 on 2011-09-24
```
cat /proc/asound/card0/codec#0


Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x1043841b
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Converter: stream=5, channel=2
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=4
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3f 0x3f]
  Converter: stream=5, channel=6
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0xa8 0xa8]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x9a 0x9a] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x25 0x0b


```

---

### Post by BicyclerBoy on 2011-09-24
That's not very helpful.

codec#0 is the HDA codec attached to first (on card) pin widget complex.
It just reveals lots of capabilities of the h/w but not the attached HDMI receiver.
The possibly useful info is:
Misc = NO_PRESENCE

Please read post #58

---

### Post by pablox1 on 2011-09-24
> **BicyclerBoy said:**
> 
Does your monitor actually support audio ?

yes. Samsung 2333tn


> **BicyclerBoy said:**
> 
speaker-test -c 2 -r 48000 -D hw:0,9
speaker-test -c 2 -r 48000 -D hw:0,8
speaker-test -c 2 -r 48000 -D hw:0,7
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 2 -r 44100 -D hw:0,9
speaker-test -c 2 -r 44100 -D hw:0,8
speaker-test -c 2 -r 44100 -D hw:0,7
speaker-test -c 2 -r 44100 -D hw:0,3

no sound.

> **BicyclerBoy said:**
> 
cat /proc/asound/card0/eld#....????
cat /proc/asound/card0/eld#3.0


doesnt exist.



Im really tired of this s*.


backing to onboard sound...

---

### Post by BicyclerBoy on 2011-09-24
You may be tired of this s**t but you don't need to vent it here.
How does that make anyone want to help ?

The specs I find for that monitor suggest:
VGA & DVI (EDID=DDC-2B)
no HDMI & not HDCP compliant & no speakers..

---

### Post by PeterStevensMC on 2011-09-28
Okay so I've rocked out the advice in this thread and my tv will make noise using aplay and speaker-test but the sound preferences doesn't work. And nothing else plays sound. nVidia gt210 and the audio plays out on 0,7

Is this the file that I need to make changes to? or is system.pa the one being read/used?
/etc/pulse/default.pa:
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-udev-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-source device=hw:0,7
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
load-module module-jackdbus-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish
.ifexists module-zeroconf-discover.so
.nofail
load-module module-zeroconf-discover
.fail
.endif
.ifexists module-raop-discover.so
.nofail
load-module module-raop-discover
.fail
.endif

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by BicyclerBoy on 2011-09-28
Are you sure the nVidia HDA is card0 ?
No mobo soundcard ?

aplay -l


You have the right file but the wrong text..
load-module module-alsa-source device=hw:0,7
load-module module-alsa-sink device=hw:x,7
where I suspect x=1.

You should place your corrected entry at the eof.

---

### Post by PeterStevensMC on 2011-09-30
Thanks BicyclerBoy.
I'm at work now but I can answer now that it's 0,7 the computer is a N36L (HP MicroServer) so no onboard sound.

I've only got:

load-module module-alsa-**source** device=hw:0,7

set. should I also have sink set? (as below:- )

load-module module-alsa-**source** device=hw:0,7
load-module module-alsa-**sink** device=hw:0,7

---

### Post by BicyclerBoy on 2011-09-30
Maybe should post
aplay -l

I thought you had edit/added the module-alsa-source line..
I think it can be left untouched..
Just add the module-alsa-sink line as post previous.

The aplay -l output should help to explain if it is necessary..

---

### Post by PeterStevensMC on 2011-10-04
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm trying to restart alsa (trying to restart audio without rebooting) in 11.04 I have no /etc/init.d/alsa-utils to restart...

---

### Post by BicyclerBoy on 2011-10-04
if 
speaker-test -c 2 -r 44100 -D hw:0,7
produces pink noise in 2 ch, in sequence, then

post
cat /proc/asound/card0/eld#1.0

And add into /etc/pulse/default.pa
load-module module-alsa-sink device=hw:0,7

If you kill pulse audio it re-spawns..no need to reboot.
Nothing to do with alsa..

Run
pavucontrol
look for & select the 2nd hdmi audio device listed.

---

### Post by thewump on 2011-10-17
Note, I was expecting to battle through this issue with a new card, but for first boot I connected (as I had with previous card) using a DVI to HDMI cable.. and sound miraculously works!

After a bit of research I found this is a feature of many cards that have HDMI and DVI connectors.

If it ain't broke, don't fix it.. so I'm done.

K

---

