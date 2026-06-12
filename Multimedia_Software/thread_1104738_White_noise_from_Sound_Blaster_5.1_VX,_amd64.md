---
title: "White noise from Sound Blaster 5.1 VX, amd64"
date: 2009-03-23
forum: Multimedia Software
---

### Post by panrosen on 2009-03-23
Hi,

I have been trying to get my Sound Blaster 5.1 VX to work, but I only got white noise from it when I play something out. I finally decided to install windows and try it there, just to verify that there was no hardware problem with the sound card. It worked fine in windows, and when I rebooted to linux, it worked there too. It turns out that if I first boot windows and then reboot, it will work fine under linux, but if I boot linux immediately after power up, I only get noise.

I guess the windows drivers perform some initialization of the card that is needed.

Does anyone know how to get around this problem? I have been surfing quite a lot, but not seen anything about this particular problem.

Some info about my system:

osen@hathor:~$ aplay -L
front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
rear:CARD=CA0106,DEV=0
    CA0106, CA0106
    Rear speakers
center_lfe:CARD=CA0106,DEV=0
    CA0106, CA0106
    Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
    CA0106, CA0106
    Side speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
    CA0106, CA0106
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


rosen@hathor:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)


rosen@hathor:~$ uname -a
Linux hathor 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

I'm running ubuntu intrepid.

Best regards,
Anders

---

### Post by rlsn on 2009-04-25
Hi,

I'm using the exact same Sound card on Intel 32 bit, I had the exact same problem on inteprid. So I did a fresh install of Jaunty and still have the same problem. It works fine if I boot into windows first and then reboot into ubuntu.

Has anyone filed a bug report for this?

Some hardware devices need firmware initialization before they work, this seems like one of those.

---

### Post by SpencerHolst on 2009-06-09
The same here. Intel 32 bit and Sound Blaster 5.1 Vx. A fresh start of ubuntu, I get white noise; booting windows first then restarting with ubuntu, it works (only front speakers though, not 5.1)

One more thing, maybe this will also apply to all. When I return to Windows, after a working Sound Blaster within ubuntu (I mean windows-restart-ubuntu-restart-windows), I get some annoying clicking, clipping, pzzt like short (like 1/5 secs or so) noises from random speakers when playing sound files and also in games.

there is still no answer, so I wanted to stir the topic and add the above syptom.

Can

---

### Post by karbolet on 2009-11-15
same here.
onboard card works fine in both systems (XP + ubuntu 9.04), but pci card (sb 5.1 vx) works only after a windows boot.

---

### Post by Steve R. on 2009-11-23
Interesting.  I was having the same problem.  See: [Rockfish Sound Card - Static (White Noise)]("http://ubuntuforums.org/showthread.php?t=1333652").  I ran out of time this weekend, so I returned the sound card.  When I have some time available again, I can give it a try.  The computer is dual boot already so it should be (famous last words) "simple"!!!

---

### Post by Steve R. on 2010-01-16
Today I received the Creative Blaster Audigy SE card.  I first booted into WindowsXP and got it working. I then rebooted into Ubuntu and the card worked!

Since I got it configured to work in WindowsXP first, I can't answer the question of whether it would work should you install it and boot directly into Ubuntu. 

Anyway Success, :D!:D:D

---

### Post by nevingeorge on 2010-02-08
I have the exact same problem.Has this ever been solved?I boot into windows then ubuntu no problem.If i boot up straight to ubuntu harsh noise.now how do i fix this?

---

### Post by jeff3 on 2010-02-11
I have the same problem running CentOS 5.4 (kernel 2.6.18-164 and alsa-utils 1.0.17-1) on an Acer M460.  White noise on the green output when running the sound test in System/Administration/Soundcard Detection.  One post ([http://bugs.gentoo.org/36415](http://bugs.gentoo.org/36415)) indicates that the problem has been known since 2005.  There's a code fragment for ca0106_main.c at [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011333.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011333.html) which purportedly makes the card work, however I haven't time to start building drivers, so I can't confirm that.

---

### Post by na0aki shimokawa on 2010-03-15
hi
i had same problem on amd64 but i solved this problem.
if you have white noise, you already can solve this problem. because, it was alsa problem in my case.

go to Applications tab in sound window
[System] -> [Preferences] -> [Sound]

then you will see ALSA plug-in slide bar. that volume turn down to most small sound that you can hear sound.
but now you cant get enough sound, so you have to turn up the Output volume.

finally, i could get sound on Sound Blaster 5.1 VX.

if you could not get white noise, you should try bellow driver.

[http://www.4front-tech.com/download.cgi]("http://www.4front-tech.com/download.cgi")

and i tried some case to solve this problem.
i could get sound temporary, i install the driver and restart (Note: its not cold start) and remove it. and restart. so you can get sound. but if you shutdown once, you lost the sound.

my english is not good, sorry.

---

### Post by rickq on 2010-03-16
Hi all,

I've got the same problem. White noise after sound card installation. After rebooting to Windows and back to Ubuntu sound works.

I've tried to download ALSA sources and add the code fragment described at [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011333.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011333.html) into ca0106_main.c. Compilation and installation were successful. I can see the modified driver in multimedia system setting window (I am using Kubuntu). 

Unfortunately, it did not solve the problem completely but I experienced a small progress. 
1) Booting to Windows does not affect sound in Ubuntu
2) After computer power on and booting Ubuntu, sound works in one case: MPlayer is playing an mp3 (still no sound) and when I select the sound driver in multimedia system setting window and click Test button, I can hear the mp3 played by MPlayer, as long as the sound test is running.

Can anybody explain this behavior ? I believe there is an easy way how to modify the sound driver to work properly.

Kind regards,

Rick

---

### Post by badbod on 2010-04-08
Has anyone found a fix for this yet, There seems to be a pre-amp on the card that needs its level setting/initializing, as turning output volumes down does eventually provide sound. The white noise is simply a maxed out pre-amp distorting like mad.

the problem with turning the output volume down to get audio is that there is a lot of hiss and noise coming from the maxed out amp, so the audio quality is still quite poor.

Is there a way to hack the alsa drivers to initialize the card correctly, like the windows drivers do?

This is my second card that does not work correctly in Ubuntu so I dont wanna buy yet another. I have onboard AC97 realtek which only works in 2 speaker mode in ubuntu, and this SB 5.1 VX which does work in 5.1 mode but has bad audio due to not being initialized correctly.

Any help would be really appeciated, and I dont mind compiling stuff etc if it will fix it, but I can't find anyone who has got this working yet.

---

### Post by glenn_uplb on 2010-04-17
I got mine working on Debian by uninstalling ALSA altogether and installing OSS instead.
You can get OSS here:
    [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

---

### Post by badbod on 2010-05-09
What did you get working? the SB 5.1VX or the on-board ac97?  Do your volume controls work normally? Does pulse work with OSS?

 I might consider changing to OSS if it does fix the 5.1VX (or the on-board for 5.1 output). For now I have installed windows in dual boot, I boot into windows then reboot into ubuntu so 5.1VX works properly. Hardly ideal.


[edit] I did install OSS according to [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) and all works perfect straight from computer power up, no  booting into windows first (except no systems sounds when login etc,  World of Warcraft also works without cracks or pops too (I had to make a gdm session or unload pulse before for this) so excellent suggestion Many Thanks!!. I am using Ubuntu 10.04LTS (Lucid) AMD_X64 so followed the instructions for >= 9.1 / 9.04 .  I will now set about trying to get systems sounds but not important really, movies mp3's and games are fine. [/edit]

[edit] oops,  after installing the repositories as per previous instructions for system sounds, you need to do
```

sudo apt-get update
sudo apt-get upgrade
sudo reboot

```

system sounds now work.
[/edit]

---

### Post by badbod on 2010-05-09
> **glenn_uplb said:**
> I got mine working on Debian by uninstalling ALSA altogether and installing OSS instead.
You can get OSS here:
    [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)



  download this OSS ,  NOT the one in the link I provide, Just follow the instructions from the link I provide except for the download/compile part.

Thanks for the fix and download link [B]glenn_uplb .
[/B]

---

### Post by badbod on 2010-05-09
Next test is to see if my on-board AC97 5.1 worx in 5.1 mode?  But thats for another day.  And another thread I guess.

---

### Post by capraMambrica on 2010-05-24
For anyones information, this seemed to work really well for me. Following the OSS installation. I haven't tested it throughly, but as I don't have a windows installation to boot into, this is certainly the best option for me. Thanks guys!

---

### Post by hansum_rahul on 2010-06-20
OSS worked for me but would really want to go back to ALSA!

---

### Post by mejoto on 2010-08-21
Strange things happened to Ubuntu 10.4 with SB 5.1 vx sound driver!!!

Explain this:
I've Ubuntu 10.04 installed a dual-booting with Windows 7  the Primary Boot (1st partition). IF first booting is the Ubuntu, I had crackling noise and subsequently no sound can be heard. BUT if the first booting is Windows 7, the audio works well in both Windows 7 and after shutting down the Windows 7 followed by  booting Ubuntu it "creates" the sound, the audio works O.K. Can anyone explain this?

TRY to install Windows 7 first and then Ubuntu 10.04 in a dual-boot system. SB 5.1 vx driver is installed in the Windows 7 and do the run test.

Good luck.

---

### Post by vaikz on 2010-11-08
> **badbod said:**
> download this OSS ,  NOT the one in the link I provide, Just follow the instructions from the link I provide except for the download/compile part.

Thanks for the fix and download link [B]glenn_uplb .
[/B]

Hi, I just want to ask if your mic is working? I just switch to oss4 and it seems that i can't record.

---

### Post by CCrake on 2011-01-03
Hey, 

Using a Realtek ALC660-VD i eliminated persistent white noise through GNOME ALSA Mixer (software center) by muting a channel marked "Mic".  It should be mentioned to that i havent been able to get my integrated mic to work in Ubuntu before or after this issue and i have not tested my microphone jack after applying this fix.

---

### Post by Darkman87SA on 2011-03-31
Sorry, I do not know English.

Here is the solution for ALSA:

```
cd /lib/modules/$(uname -r)/kernel/sound/
ln soundcore.ko snd.ko --symbolic
echo "snd-ca0106" >> /etc/modules
echo "soundcore" >> /etc/modules
```

---

### Post by hugo_koopmans on 2011-07-24
Hi Darkman,

Your solution did not work for me...

hugo

---

