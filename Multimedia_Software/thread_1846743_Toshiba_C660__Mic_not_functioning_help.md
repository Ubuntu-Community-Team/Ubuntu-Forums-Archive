---
title: "Toshiba C660 : Mic not functioning help"
date: 2011-09-19
forum: Multimedia Software
---

### Post by lordbux on 2011-09-19
hai friends

I am using a TOSHIBA SATELLITE C660 Laptop: 

It has 
** [COLOR="Red"]INBUILT MIC[/COLOR], INBUILT WEBCAM, 2 INBUILT SPEAKERS, AUDIO PORT,[COLOR="Red"]MIC PORT[/COLOR]**

Other than for the INBUILT MIC, and MIC PORT all others are working fine.

so basically i can't use mic with my Laptop.:confused:

# lspci- OUTPUT
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

*** ****SOUND RECORDER**
  In my sound recorder the only** "Record From Input"** is **Master**
and it successfully records any sound played in the system.

*** Sound Preferences**
           #Hardware choices:
               1 Analog Stereo input
               2 Analog Surround 4.0 Output
    NOW USED**   3 analog stereo 4.0 Output + Analog stereo input**
               4 Analog stereo output
               5 Analog Stereo Duplex
I have tried changing them into all possible once still got no mic.:frown:

 
***Alsa Mixer**
as per alsa mixer the data says
```

card: HDA INTEL
chip: Realtek ALC269

```

I have  :**FRONT MIC BOOST, MIC BOOST, CAPTURE DIGITAL [COLOR="Red"](in the capture section)[/COLOR]**

**MASTER,HEADPHONE,SPEAKER,PCM,FRONT MIC, MIC BOOST, [COLOR="Red"](in playback)[/COLOR]**

[CENTER][ALL PARAMETERS ARE SET TO THE HIGHEST][/CENTER]:-k

*GSTREAMER-PROPERTIES

Default Input
     1)  Plugin : ALSA Device: Default Pipeline: alsarc **[Selected]**
     2)  Plugin : OSS (unsupported)
     3)  Plugin : Pulse Audio  Device: Unknown 
**[COLOR="Red"]TRIED ALL BUT YET NO MIC[/COLOR]** :confused:


So dear friend this is the trouble i am going through, I cant get neither my internal nor external mic to work on my laptop. and i have an important project coming up so would be great if someone could give a solution fast:popcorn: 

Thanks in advance

---

### Post by lordbux on 2011-09-19
bump

---

### Post by dodle on 2011-09-20
This is what worked for me, but your issue may be different. I installed gnome-alsamixer. Under the section called "Capture" I checked "Rec." and raised the meter all the way up and my mic started working. Hope this helps.

**----- NOTE -----**
If you don't wait 24 hours before "bumping" your threads you will probably get an infraction from a moderator. That happened to me.

---

### Post by lordbux on 2011-09-20
> **dodle said:**
> This is what worked for me, but your issue may be different. I installed gnome-alsamixer. Under the section called "Capture" I checked "Rec." and raised the meter all the way up and my mic started working. Hope this helps.

**----- NOTE -----**
If you don't wait 24 hours before "bumping" your threads you will probably get an infraction from a moderator. That happened to me.



Checked in, **Rec is checked** still no sound being recorded, when i plug in mic the distortion is recorded. ..Thanks for the help though bro
Bump .. please help guys ](*,)

---

### Post by lidex on 2011-09-21
> **lordbux said:**
> Checked in, **Rec is checked** still no sound being recorded, when i plug in mic the distortion is recorded. ..Thanks for the help though bro
Bump .. please help guys ](*,)

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by lordbux on 2011-09-21
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

hi bro
here is the uploaded report:  [http://www.alsa-project.org/db/?f=ff152ede533bf6cf202787ea8ce7a4cc562d40df](http://www.alsa-project.org/db/?f=ff152ede533bf6cf202787ea8ce7a4cc562d40df)

---

### Post by lordbux on 2011-09-22
Bump

---

### Post by perspectoff on 2011-09-22
You have PulseAudio installed, which takes over all the controls (until the day you uninstall it completely, lol). THIS HAPPENS EVEN IF YOU DON"T HAVE IT SET AS THE DEFAULT IN MULTIMEDIA SETTINGS.

Once you get used to PulseAudio (and all its quirks), though, you'll swear by it. It can mux lots of inputs and can clone outputs virtually. Very nice. PulseAudio is most mature in Natty (and I have the best success with it in Natty). There are a few niggles with PulseAudio in Lucid, still. 

I used to love Lucid, but for multimedia I tend to like Natty better (in no small part because of the improvements in PulseAudio).

You must install PulseAudio Volume Control.

 sudo apt-get install pavucontrol


* Start PulseAudio Volume Control: 

    Menu -> Multimedia -> PulseAudio Volume Control 

* Select as an input "Monitor of Internal Audio Analog Stereo": 

        PulseAudio Volume Control -> Input Devices -> Show: All Input Devices 
        -> Make sure Monitor of Internal Audio Analog Stereo is not muted (click on speaker icon) 

* Make sure your microphone is plugged in if using an external one. 

* Select as an input "Internal Audio Analog Stereo: Analog Microphone": 

        PulseAudio Volume Control -> Input Devices -> Show: All Input Devices 
        -> Make sure "Monitor of Internal Audio Analog Stereo: Port: Analog Microphone " is not muted (click on speaker icon) 

(Of course, you could use the "internal microphone" on your laptop instead. I personally use an external microphone so I don't pick up the ambient room noise so much.)

* Start recording with your recording program (in this example I am using FFMPEG, but you could use Audacity or RecordMyDesktop or something else).

* Make sure the "Internal Audio Analog Stereo" device is selected for the ALSA plug-in [ffmpeg] application: 

        PulseAudio Volume Control -> Recording -> ALSA plug-in [ffmpeg]: ALSA capture from: Internal Audio Analog Stereo 

Note that this last step has to be done once for every recording app that you use (while it is recording). If you use FFMPEG and Audacity (like I do), you have to do it once for each.

In this example I am using FFMPEG as my recording program (since I use it for screencapture /screencasts), but of course, you may be using some other recording program. ***This will only show up if the recording is already started. When you set it once, it will stay set, so you can stop recording and then re-start a real session later.

From:

[http://www.kubuntuguide.info/index.php/Natty#Recording_with_PulseAudio](http://www.kubuntuguide.info/index.php/Natty#Recording_with_PulseAudio)

or

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Recording_with_PulseAudio](http://ubuntuguide.org/wiki/Ubuntu:Natty#Recording_with_PulseAudio)

---

### Post by lordbux on 2011-09-22
> **perspectoff said:**
> You have PulseAudio installed, which takes over all the controls (until the day you uninstall it completely, lol). THIS HAPPENS EVEN IF YOU DON"T HAVE IT SET AS THE DEFAULT IN MULTIMEDIA SETTINGS.

Once you get used to PulseAudio (and all its quirks), though, you'll swear by it. It can mux lots of inputs and can clone outputs virtually. Very nice. PulseAudio is most mature in Natty (and I have the best success with it in Natty). There are a few niggles with PulseAudio in Lucid, still. 

I used to love Lucid, but for multimedia I tend to like Natty better (in no small part because of the improvements in PulseAudio).

You must install PulseAudio Volume Control.

 sudo apt-get install pavucontrol


* Start PulseAudio Volume Control: 

    Menu -> Multimedia -> PulseAudio Volume Control 

* Select as an input "Monitor of Internal Audio Analog Stereo": 

        PulseAudio Volume Control -> Input Devices -> Show: All Input Devices 
        -> Make sure Monitor of Internal Audio Analog Stereo is not muted (click on speaker icon) 

* Make sure your microphone is plugged in if using an external one. 

* Select as an input "Internal Audio Analog Stereo: Analog Microphone": 

        PulseAudio Volume Control -> Input Devices -> Show: All Input Devices 
        -> Make sure "Monitor of Internal Audio Analog Stereo: Port: Analog Microphone " is not muted (click on speaker icon) 

(Of course, you could use the "internal microphone" on your laptop instead. I personally use an external microphone so I don't pick up the ambient room noise so much.)

* Start recording with your recording program (in this example I am using FFMPEG, but you could use Audacity or RecordMyDesktop or something else).

* Make sure the "Internal Audio Analog Stereo" device is selected for the ALSA plug-in [ffmpeg] application: 

        PulseAudio Volume Control -> Recording -> ALSA plug-in [ffmpeg]: ALSA capture from: Internal Audio Analog Stereo 

Note that this last step has to be done once for every recording app that you use (while it is recording). If you use FFMPEG and Audacity (like I do), you have to do it once for each.

In this example I am using FFMPEG as my recording program (since I use it for screencapture /screencasts), but of course, you may be using some other recording program. ***This will only show up if the recording is already started. When you set it once, it will stay set, so you can stop recording and then re-start a real session later.

From:

[http://www.kubuntuguide.info/index.php/Natty#Recording_with_PulseAudio](http://www.kubuntuguide.info/index.php/Natty#Recording_with_PulseAudio)

or

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Recording_with_PulseAudio](http://ubuntuguide.org/wiki/Ubuntu:Natty#Recording_with_PulseAudio)


did it, and the result is

Internal audio analog stereo is live but the movement of volume level is very low, and does not change as per mic input
Monitor of internal audio only become live when i play some music inside laptop.

and the only option in sound recorder for input is MASTER

and the only sound i can record is of things i play in the computer

[ALSA REPORT] [http://www.alsa-project.org/db/?f=ff152ede533bf6cf202787ea8ce7a4cc562d40df](http://www.alsa-project.org/db/?f=ff152ede533bf6cf202787ea8ce7a4cc562d40df)

---

### Post by lidex on 2011-09-22
The thinkpad model is not for you. Try basic or auto.

---

### Post by snake_eyes on 2011-09-23
I have the same problem on my toshiba c660 satellite ubuntu 10,04 LTS 64-bit the mic is not working how do I fix it? although I installed the gnome-alsamixer and all the mixers are on

---

### Post by lordbux on 2011-09-23
> **lidex said:**
> The thinkpad model is not for you. Try basic or auto.

I changed thinkpad to "auto" (basic does not work, headphone not working)
auto is working well

BUT STILL CANT get the mic to work.

I ahve made a new alsa info report: [http://www.alsa-project.org/db/?f=94a3cfcee02222f082379f0fc81a0104beac8574](http://www.alsa-project.org/db/?f=94a3cfcee02222f082379f0fc81a0104beac8574)

I dont understand what is wrong, please help.:confused:

---

### Post by snake_eyes on 2011-09-23
Hello,

This is mine also
[http://www.alsa-project.org/db/?f=f8c3cd796c191a423d7438c773f64674df279a20](http://www.alsa-project.org/db/?f=f8c3cd796c191a423d7438c773f64674df279a20)

but if you understand something..... I do :D

---

### Post by lidex on 2011-09-23
I think the next course of action is upgrading alsa. Follow the link in my sig.

---

### Post by lordbux on 2011-09-24
> **lidex said:**
> I think the next course of action is upgrading alsa. Follow the link in my sig.


The script is exiting with error on line 75, then 102 and 104 etc


UPDATE#
CLEARED ..now no problem

---

### Post by lidex on 2011-09-24
@snake_eyes
Thinkpad/ideapad are not valid models for your codec. You have chosen thinkpad so get rid of that and try these instead:
```
ALC269
======
  basic         Basic preset
  quanta        Quanta FL1
  laptop-amic   Laptops with analog-mic input
  laptop-dmic   Laptops with digital-mic input
  fujitsu       FSC Amilo
  lifebook      Fujitsu Lifebook S6420
  auto          auto-config reading BIOS (default)

```

---

### Post by lordbux on 2011-09-25
> **lidex said:**
> I think the next course of action is upgrading alsa. Follow the link in my sig.

UPGRADED ALSA DRIVER and it worked awesome,
All problems solved. . .just follow the same script.

Thank you all who helped great work and great support
Long live open source.
**current module = auto**

 long live opensource:popcorn:

UPGRADE SCRIPT = [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

