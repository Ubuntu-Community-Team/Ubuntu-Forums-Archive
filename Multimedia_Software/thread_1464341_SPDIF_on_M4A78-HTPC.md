---
title: "SPDIF on M4A78-HTPC"
date: 2010-04-28
forum: Multimedia Software
---

### Post by Solsiden on 2010-04-28
[FONT=Arial][SIZE=3]I am trying to switch from Windows XP to Ubuntu 9.04 (10.04) for my HTPC, but cannot get sound out of the SPDIF/IEC958.[/SIZE][/FONT]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[FONT=Arial][SIZE=3]The motherboard is Asus M4A78-HTPC it works under Windows, but I can only get ”digital” sound out through the HDMI. Windows uses a HDA ATI 791A driver and a VIA VT 1718S codec. As soon as Ubuntu is booting the Optical signal is disabled. Ubuntu does show the sound card as ATI RS690/780 HDMI. GNOME-ALSA Mixer has a button titled IEC959, but nothing happens when it is activated.[/SIZE][/FONT]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[FONT=Arial][SIZE=3]I am a beginner concerning Linux. What can I do?  I would like to give Linux a chance before switching to Win 7.[/SIZE][/FONT]

---

### Post by lidex on 2010-04-29
Have a look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")

---

### Post by Solsiden on 2010-05-05
[FONT=Arial][SIZE=3]Thank you, but I am still missing the sound through IEC958. I have tried to follow the instructions in [/SIZE][/FONT][[FONT=Arial][SIZE=3]http://alsa.opensrc.org/index.php/DigitalOut#Find_your_device[/SIZE][/FONT]]("http://alsa.opensrc.org/index.php/DigitalOut#Find_your_device")[FONT=Arial][SIZE=3]. May be I have misunderstood something, but I cannot figure out what. I get the following using aplay and iecset:[/SIZE][/FONT]
[FONT=Arial][SIZE=3]per@music:~$ aplay -l[/SIZE][/FONT]
[FONT=Arial][SIZE=3]**** List of PLAYBACK Hardware Devices ****[/SIZE][/FONT]
[FONT=Arial][SIZE=3]card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic][/SIZE][/FONT]
[SIZE=3][FONT=Arial]Subdevices: 1/1[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Subdevice #0: subdevice #0[/FONT][/SIZE]
[FONT=Arial][SIZE=3]card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI][/SIZE][/FONT]
[SIZE=3][FONT=Arial]Subdevices: 1/1[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Subdevice #0: subdevice #0[/FONT][/SIZE]
[FONT=Arial][SIZE=3]per@music:~$ iecset[/SIZE][/FONT]
[FONT=Arial][SIZE=3]control "IEC958 Playback Default" (index -1) not found[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Any suggestions?[/SIZE][/FONT]

---

### Post by lidex on 2010-05-05
Make sure you spdif's are not muted in alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Solsiden on 2010-05-07
[FONT=Arial][SIZE=3]I have tried running alsamixer and chosen all soundcards, but no change. The sound played with aplay or other players, all come through the HDMI, not the SPDIF![/SIZE][/FONT]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[FONT=Arial][SIZE=3]The SPDIF output is inactive – no light! How can it be enabled?[/SIZE][/FONT]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[FONT=Arial][SIZE=3]I have looked in the file /proc/asound/cards:[/SIZE][/FONT]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Arial] 0 [SB             ]: HDA-Intel - HDA ATI SB[/FONT][/SIZE]
[SIZE=3][FONT=Arial]                      HDA ATI SB at 0xfbbf4000 irq 16[/FONT][/SIZE]
[SIZE=3][FONT=Arial] 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI[/FONT][/SIZE]
[SIZE=3][FONT=Arial]                      HDA ATI HDMI at 0xfbde8000 irq 19[/FONT][/SIZE]
[SIZE=3][FONT=Arial] 2 [SAA7134        ]: SAA7134 - SAA7134[/FONT][/SIZE]
[SIZE=3][FONT=Arial]                      saa7133[0] at 0xfbfff800 irq 20[/FONT][/SIZE]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[FONT=Arial][SIZE=3]It does not show any IEC958/SPDIF options.[/SIZE][/FONT]

---

### Post by schildpad on 2010-05-07
I have the same problem, my board is m4a785g :)
Tried the suggested solutions, but still no luck with sound over spdif.

This is very frustrating because i want all sound routed over SDDIF to my Sony receiver (which doesnt have HDMI).

Any help is welcome.

---

### Post by lidex on 2010-05-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Solsiden on 2010-05-09
```

[FONT=Arial][SIZE=3]per@music:~$ uname -a[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Linux music 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux[/SIZE][/FONT]
[FONT=Arial][SIZE=3]per@music:~$ aplay -l[/SIZE][/FONT]
[FONT=Arial][SIZE=3]**** List of PLAYBACK Hardware Devices ****[/SIZE][/FONT]
[FONT=Arial][SIZE=3]card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic][/SIZE][/FONT]
[SIZE=3][FONT=Arial] Subdevices: 1/1[/FONT][/SIZE]
[SIZE=3][FONT=Arial] Subdevice #0: subdevice #0[/FONT][/SIZE]
[FONT=Arial][SIZE=3]card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI][/SIZE][/FONT]
[SIZE=3][FONT=Arial] Subdevices: 1/1[/FONT][/SIZE]
[SIZE=3][FONT=Arial] Subdevice #0: subdevice #0[/FONT][/SIZE]
[FONT=Arial][SIZE=3]per@music:~$ cat /proc/asound/version[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Advanced Linux Sound Architecture Driver Version 1.0.21.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]per@music:~$ head -n 1 /proc/asound/card*/codec#*[/SIZE][/FONT]
[FONT=Arial][SIZE=3]==> /proc/asound/card0/codec#0 <==[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Codec: VIA ID 4428[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]==> /proc/asound/card1/codec#0 <==[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Codec: ATI RS690/780 HDMI[/SIZE][/FONT]
[FONT=Arial][SIZE=3]per@music:~$[/SIZE][/FONT]
 
 

```
[FONT=Arial][SIZE=3]-------------------[/SIZE][/FONT]
[FONT=Arial][SIZE=3]The Pc is home build based on the Asus M4A78-HTPC motherboard. Bios version 0302 build 04/02/09. As mentioned earlier – under Windows XP the SPDIF works fine.[/SIZE][/FONT]

[FONT=Arial][SIZE=3]BR[/SIZE][/FONT]

---

### Post by lidex on 2010-05-11
Try an alsa upgrade. Use the link in my sig.

---

### Post by schildpad on 2010-05-12
Thanks man! 

I upgraded Alsa according to your post (follow the link "Alsa Upgrade Script" in the signature from Lidex:)
Then i runned "alsamixer" and unmuted the SPDID and IEC958 and voila, sound all the way.

Did I say Thank You already?

No?

THANKS!!!

Greetings Sven

---

### Post by stunted on 2010-05-12
If you're reluctant to upgrade alsa post the output of these 4 commands.

```
cat /proc/asound/cards
cat /proc/asound/pcm
aplay -l
aplay -L
```

you probably need a line like 
```
options snd-hda-intel model=6stack-dig position_fix=1
```
near the bottom of your /etc/modprobe.d/alsa-base file, and lines like ```
load-module module-alsa-sink device="iec958:CARD=SB,DEV=0" sink_name=digital_out
load-module module-alsa-sink device="front:CARD=SB,DEV=0" sink_name=analog_out
load-module module-combine sink_name=combined master=digital_out slaves=analog_out
```
in /etc/pulse/default.pa

Please note I don't have the HDMI output enabled in BIOS so not using that wasn't an issue for me.

Also I hate software mixing and in fact have gone back to my old and trusty SBLive! Value with hardware mixing, the only reason I use pulse on one machine is a power spike zapped the on-board NIC and my graphics cooler covers all bar one of the pci and pci/e slots which I need for a network card, but that PC's running Debian Lenny, so maybe pulse has improved a lot in the last 2 years.

---

### Post by Sepepe on 2010-05-13
I have ASUS M4A77 motherboard and also have problem with S/PDIF output. Motherboards soundchip is VIA VT1818S. I read this thread and did the alsa upgrade. 

Speaker test worked with this line
```
speaker-test -Dplughw:0,1 -c2

```Other than that the computer stays silent. I also tried every profile option from the sound preferences tool next to the clock but no success. In alsamixer S/PDIF is unmuted and it recognizes the card as HDA ATI SB and the chip as VIA VT1818S.

Should I add some lines to alsa-base.conf and default.pa? Since the speaker test works I think the solution is quite easy but as a total Ubuntu noob I'm still baffled.

Here's also commands and outputs asked earlier from others

uname -l:
```
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```cat /proc/asound/version:
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 13 2010 for kernel 2.6.32-21-generic (SMP).

```

---

### Post by Sepepe on 2010-05-13
OK, solved this simply by just booting my DAC :P

---

### Post by Solsiden on 2010-05-16
I did run the "Alsa Upgrade Script" and are now running Alsa version 1.0.23. This works!!! :P All the build-in soundcard options are now available in "Sound properties" in Ubuntu.
 
Thank you!!
 
I just wonder why Alsa Version 1.0.23 is not includ ed in the newest release of Ubuntu:confused:
 
BR

---

### Post by lidex on 2010-05-16
> **Solsiden said:**
> I did run the "Alsa Upgrade Script" and are now running Alsa version 1.0.23. This works!!! :P All the build-in soundcard options are now available in "Sound properties" in Ubuntu.
 
Thank you!!
 
I just wonder why Alsa Version 1.0.23 is not included in the newest release of Ubuntu:confused: 
BR
Then it would be like a party. You know geeks don't get invited to parties. :rolleyes:

---

### Post by schildpad on 2010-05-16
Did I say thank you already?
No?

THANK YOU :)

---

### Post by lidex on 2010-05-16
Solsiden,
Can you mark this thread as solved so I can quit looking at it? ;)

---

### Post by Paullus_N on 2010-08-22
Hi all,

I've been working on this problem for a couples of days now.
I have an Asus M4A77D motherboard and a Asus EN9500GT VGA.
The SPDIF cable is connected to the VGA as instructed.

I have updated Alsa to the latest version:
> server@HomeServer:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 22 2010 for kernel 2.6.32-21-generic (SMP).
The SPDIF en SPDIF Default PCM devices are unmuted in alsamixer. I have selected Analog Stereo Duplex in the sound configuration tool, and done the gstreamer-properties setting as instructed, tot Alsa with the digital output. 

And this results in no sound at all over the HDMI connection to my tv.
I've rebooted, pc and tv 

Speaker-test is silent. 
It worked with analog connection to my amplifier, but since my tv does some extra stuff the sound is playing ahead of the image. So, I *need* to get sound over the HDMI so both audio and video are in sync. 

Any help is welcome.

note: I'm not a total noob in linux, but I do love to know all the commands if I need to do stuff :D

Thanks!

[edit]
for those who want to know:

> server@HomeServer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> server@HomeServer:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, VT1818S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Digital
    IEC958 (S/PDIF) Digital Audio Output


---

### Post by lidex on 2010-08-23
You're using the hdmi port on the 9500gt? What nvidia driver are you using?

Have you looked here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Exxplicit on 2010-09-28
Using a M4A77D mobo did the Alsa update and BAM I have sound!  It took me an eternity to find this solution but much thanks is appreciated!

---

