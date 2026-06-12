---
title: "No sound in ubuntu 11.10"
date: 2011-11-23
forum: Multimedia Software
---

### Post by Dieter_C on 2011-11-23
[SIZE=2]I can't get the sound working om my pc. I've read lots of threads on this forum about sound but no answer to my problem.

I can see my soundcard:[/SIZE] [SIZE=2]
[/SIZE] [FONT=Courier New][SIZE=2]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/SIZE][/FONT][SIZE=2]
Starting alsamixer gives me:

[/SIZE]```
|Card: HDA ATI HDMI                                   F1:  Help               &#9474;
&#9474; Chip: ATI R6xx HDMI                                  F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;

&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                  < S/PDIF >                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                          
```[SIZE=2]aplay gives me this:
[/SIZE] [FONT=Courier New][SIZE=2]ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:660: audio open error: No such file or directory

[/SIZE][FONT=Verdana][SIZE=2]If i go to gnome control centre the is no hardware device and is ouputs:[/SIZE][/FONT][SIZE=2]
(gnome-control-center:2013): sound-cc-panel-WARNING **: Failed to connect context: Connection refused[/SIZE]

[FONT=Verdana][SIZE=2]What other checks can I do? Who can help me?[/SIZE][/FONT]
[/FONT]

---

### Post by gordintoronto on 2011-11-23
The sound card you are looking at is for output over HDMI, such as on an HDTV. Select your other sound device with F6, to get sound from your built-in speakers.

It never hurts to tell people what version of Ubuntu you are using, and the brand and model of computer.

---

### Post by Dieter_C on 2011-11-24
The pc is a HP Compaq dc7900 running ubuntu 11.10 
When I press F6 in alsamixer I can't select another soundcard
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472; Sound Card &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;-  (default)           &#9474;
&#9474;0  HDA ATI HDMI        &#9474;
&#9474;   enter device name...&#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
```Now I've found out that it works when I remove the ATI video card.

I can see the card with lspci and aplay -l
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)

 **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When putting in the ATI video card, the Intel card disappears. 
How can I use them both?

---

### Post by donbudafuko on 2011-12-12
i have the same problem. i have a hdmi video card an it will only recognize that, but en i take it out it then will use the onboard sound. has anyone found out how to fix this yet?  thanks

---

### Post by Cheiff on 2011-12-17
Hi,

this worked for me:

edit /etc/asound.conf (if it does not exist, create the file):
```
sudo nano /etc/asound.conf
```
Paste this as content:
```
pcm.!default {
  type plug
  slave {
    pcm "hw:1,0" #delete the first hash for sound over analog
#    pcm "hw:1,1" #delete the first hash for sound over optical
#    pcm "hw:0,3" #delete the first hash for sound over hdmi
    rate 48000
  }
}

```
Save the file.
Try to play some audio.

Got it from openelec.tv
Hope this helps.

Cheers

---

### Post by youvebeengoosed on 2011-12-28
everything works till i change to hmdi for sound and the video speeds fast and i don`t hear anything at all
i`m a new come mer to linux any help would be hot

---

### Post by ydeardorff on 2012-02-28
I have a lenovo ideapad S10e.
It has windows 7 on it, and ubuntu 11.10 installed.

Windows doesnt let the audio to function. Everthing else works perfectly. I get error code(10) constantly, and I think I have tried just about every realtek driver on the web by now.

I installed ubuntu 11.10 in hopes I could get past any previous owner issues with win 7, and get everything working including the WIFI.

I too have an HDMI output. Perhaps someone could lend me a hand here to get this stupid audio problem fixed?

When i run the command above I get nothing in my asound.conf file.

---

### Post by stoynev on 2012-07-24
Solved my problem too, Very helpful suggestion **Cheiff**


```
root@......:/etc# cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 44
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb40000 irq 16

```

```
root@cashterminal-ru:/etc# speaker-test

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
^C

```

```
root@.....:/etc# arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 2: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by CitizenJimserac on 2012-10-06
> **Cheiff said:**
> Hi,

this worked for me:

edit /etc/asound.conf (if it does not exist, create the file):
```
sudo nano /etc/asound.conf
```
Paste this as content:
```
pcm.!default {
  type plug
  slave {
    pcm "hw:1,0" #delete the first hash for sound over analog
#    pcm "hw:1,1" #delete the first hash for sound over optical
#    pcm "hw:0,3" #delete the first hash for sound over hdmi
    rate 48000
  }
}

```
Save the file.
Try to play some audio.

Got it from openelec.tv
Hope this helps.

Cheers

Many thanks to Chieff.  There was no asound.conf in /etc so I created it via sudo gedit asound.conf and inserted the text and it got back both my sound and the missing panel volume icon after I rebooted.  Saving me the trouble of trickier and harder solutions.  Well done!  Against thanks (Ubuntu Precise on EMachines Model 1431 old desktop)

---

### Post by boudiccas on 2013-01-09
This thread came up in google when I was trying to find a solution to the lack of sound in my mpd, and as it was so useful I'll also post what I did here to help others. 

This is a brand new computer, only 4 days old, running Debian testing. 

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 43
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb40000 irq 16

lspci | egrep -i audio 
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek
HDMI Audio [Radeon HD 6500D and 6400G-6600G series] 00:14.2 Audio
device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)

/etc/asound.conf
pcm.!default {
  type plug
  slave {
    pcm "hw:1,0" #delete the first hash for sound over analog
#    pcm "hw:1,1" #delete the first hash for sound over optical
#    pcm "hw:0,3" #delete the first hash for sound over hdmi
    rate 48000
  }
}

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

.asoundrc
pcm.mpd {
  type hw
  card 1 
}

the ALSA output in the mpd.conf
audio_output {
        type            "alsa"
  	name		"My ALSA Device"
	device		"hw:1,0"	
#        mixer_type      "software"
#        mixer_device    "default"
#        mixer_control   "PCM"
}

And now its all working, apart from the lack of volume control in the client, but I can live with that.

Thank you for providing information to help us solve our problems.

Sharon.

---

