---
title: "Alsa Surround Sound - Realtek ALC883"
date: 2008-05-24
forum: Multimedia Software
---

### Post by nuclearpidgeon on 2008-05-24
Hi, here's yet *ANOTHER* sound problem. If you are reading this, thank you for taking the time to pick out this particular post - it is much appreciated.

I'm using Ubuntu 8.04 with an Intel HD Audio card. my lspci | grep Audio returns:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```aplay -l returns:
```

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I want to use surround sound, mainly because of my sub woofer 8-), but when I run:
```
speaker-test -Dplug:surround51 -c6 -twav
```I get a "Front Right", and "Front Right" and nothing else. It's all muted. My surround sound works fine in windows.

I've checked my alsamixer and un-muted all the things - this is my alsamixer output:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                                                          &#9474;
&#9474; Chip: Realtek ALC883                                                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                                                            &#9474;
&#9474; Item: Master [dB gain=-9.00]                                                                                                                             &#9474;
&#9474;                                                                                                                                                          &#9474;
&#9474;                                                                                                                                                          &#9474;
&#9474;                                                                                                                                                          &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;      &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;      &#9474;MM&#9474;              &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;      &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     81              100<>100  81<>81     0<>0     0<>0   100<>100     100      100      0<>0     0<>0    81<>81     0<>0     0<>0               0<>0     &#9474;
&#9474; < Master >Headphon    PCM     Front    Front Mi Front Mi Surround   Center    LFE       Side     Line      CD       Mic    Mic Boos   IEC958  PC Speak   &#9474;
&#9474;                                                                                                                                                          &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```Not shown is the Channel Option - I can choose 6 or 8 channels.

My Sound card is integrated into my motherboard and I have my surround sound speakers plugged in as:
 * Green Sound out - Front
 * Blue Sound In - Rear
 * Red Microphone - Center/Sub woofer
This works fine in Windows.
I have looked around the interweb and found no real guide to do with this - any ideas?

Thanks in advance

---

### Post by zeny on 2008-05-24
I'm having the same issue, actually I hear nothing during the test. I'll basically answer your question. 


5.1 does not work in Linux. Linux has horrible hardware support. Everything just works in windows, where as Linux it doesn't. I've gone through 3 sound cards and never gotten 5.1 surround sound. Some people will with certain cards, but you have to get those certain cards. With the card you have it WON'T work. I've been searching for awhile and nothing has worked.

---

### Post by nuclearpidgeon on 2008-05-24
> **zeny said:**
> ... I hear nothing during the test...
Just to clarify: my sound DOES work - I get playback and everything, but ONLY ON THE **FRONT** SPEAKERS.
* Green Sound out - Front **WORKS**
* Blue Sound In - Rear **DOESN"T WORK**
* Red Microphone - Center/Sub woofer [B]DOESN'T WORK
[/B]
And also, I've been led to believe that 5.1 *does* work on linux. I've seen a few tutorials for it, and after reading them it seems that surround51 is a raw PCM definition for 6 channel sound. I mean, Totem Movie player supports 5.1 surround sound in it's options...

Should I perhaps post my question on an ALSA forum?

---

### Post by prabath_fun on 2008-06-30
Hi,
  I am also facing same problem with Intels D102GGC2 Motherboard.
for "aplay -l" command, I am getting
**** List of PLAYBACK Hardware Device *****
card 0: SB{HDA ATI SB], Device 0: ALC883 Analog [ALC883 Analog]
Subdevice: 1/1
Subdevice #0: Subdevice #0

I am getting same sound in all speakers by changing 2ch to 6 ch in alsamixer. But, not dolby surround even while playing dolby encoded DVD's.

If anyboby helps will be thankful.

---

### Post by daitheflu08 on 2008-07-02
I'm using the digital out and before I formatted the HD SOMEHOW I got surround sound out of my speakers.  Now I'm at a loss as to how the hell I did that.

It's tricky but doable, I think.

:confused:

---

### Post by Afkpuz on 2008-07-12
Give this a try.  It's easy to undo also.

[http://ubuntuforums.org/showthread.php?t=755479](http://ubuntuforums.org/showthread.php?t=755479)

---

### Post by prabath_fun on 2008-12-16
Hi,
       Finally, I got 5.1 speaker supports with Ubuntu 8.10 and works very good. I got integrated sound card in my motherboard and its model number is D102GGC2.
I followed the following steps and got succeeded.
1.	Take backup of /etc/pulse/daemon.conf.
2.	Edit /etc/pulse/daemon.conf with text editor.
I used gedit tool triggered from terminal as follows
Sudo gedit /edit/pulse/daemon.conf
3.	Scroll down to 
;default-sample-channels=2
 option.
a.	Uncomment it. That is, remove &#8220;;&#8221; symbol at starting.
b.	Change 2 to 6 for 5.1 channels / speaker.
4.	Restart system to take changes get effect.
5.	In terminal, do speaker test with following command in terminal
Speaker-test &#8211;Dplug:surround51 &#8211;c6 -11 &#8211;twav
6.	If some problem in hearing sound in rear speakers, double click on speaker icon at top of the desktop, which opens preference. Check surround, center and LFE are not muted and in full/required volume levels.
7.	Further check the player, also set for 5.1 surround support in there preferences.

Now, I got 98% of functionality with Ubuntu 8.10. one extra application looking for is phone manager for my Sony Ericsson W810I model with SMS backup, call backup, data transfer without switching to &#8220;file transfer&#8221; mode, etc., that is at least looking for 80% functionality from &#8220;My phone manager&#8221; tool.

---

### Post by nuclearpidgeon on 2009-01-07
> **prabath_fun said:**
> Hi,

Finally, I got 5.1 speaker supports with Ubuntu 8.10 and works very good. I got integrated sound card in my motherboard and its model number is D102GGC2.

I followed the following steps and got succeeded.

1.    Take backup of /etc/pulse/daemon.conf.

2.    Edit /etc/pulse/daemon.conf with text editor.

I used gedit tool triggered from terminal as follows

Sudo gedit /edit/pulse/daemon.conf

3.    Scroll down to

;default-sample-channels=2

option.

a.    Uncomment it. That is, remove &#147;;&#148; symbol at starting.

b.    Change 2 to 6 for 5.1 channels / speaker.

4.    Restart system to take changes get effect.

5.    In terminal, do speaker test with following command in terminal

Speaker-test &#150;Dplug:surround51 &#150;c6 -11 &#150;twav

6.    If some problem in hearing sound in rear speakers, double click on speaker icon at top of the desktop, which opens preference. Check surround, center and LFE are not muted and in full/required volume levels.

7.    Further check the player, also set for 5.1 surround support in there preferences.





I've tried this and it doesn't work. Using Ubuntu 8.10, the speaker-test results in only the front two speakers working.



note to anyone wanting to try this - some spaces are missing from the command and there should be no capitalization. It should read:

```
speaker-test -D plug:surround51 -c 6 -l 1 -t wav
```

---

### Post by maumaufck on 2009-04-24
i have installed the drivers from the realtek site and works 5.1 sound...in sound preferences the Center, rear, subwoofer are visible..

---

