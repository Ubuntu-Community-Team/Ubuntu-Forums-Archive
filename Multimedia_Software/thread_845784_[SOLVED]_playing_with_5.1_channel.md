---
title: "[SOLVED] playing with 5.1 channel"
date: 2008-06-30
forum: Multimedia Software
---

### Post by prabath_fun on 2008-06-30
Hi,
  I want to enable 5.1 surround while playing DVD's or even  MP3 in Ubuntu 8.04.
My Desktop Mother board Details are
D102GGC2.
Xpress200 chipset.

for "aplay -l" command, I am getting
**** List of PLAYBACK Hardware Device *****
card 0: SB{HDA ATI SB], Device 0: ALC883 Analog [ALC883 Analog]
Subdevice: 1/1
Subdevice #0: Subdevice #0

I tried by changing volume levels for surround, LFE, PCM,Channels from 2ch to 6ch etc., in "alsamixer". Also, I installed "AlsaMixerGUI" and there also checked. Nothing muted. 

I am getting same sound in my rear speakers as in front speakers(only while changing 2 to 6 channel in alsamixer), not dolby surround.

 I have tried speaker test. Only for front right and front left channels, sound is available. Nothing else.

Please help me to enable 5.1 in my motherboard.





**[B]Note:**[/B] I already refered following threads and sites

[http://ubuntuforums.org/showthread.php?t=805532](http://ubuntuforums.org/showthread.php?t=805532) ([ubuntu] Alsa Surround Sound - Realtek ALC883)
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) (HDA ATI SB / INTEL Sound card problem [SOLUTION!])
+ + + + + + +

---

### Post by kpkeerthi on 2008-07-01
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by prabath_fun on 2008-07-02
No Improvement. Any other hints / way.

---

### Post by prabath_fun on 2008-07-07
My Motherboard details

**_Intel make- D102GGC2. _**
Some hints about my motherboard:
High Definition Audio Subsystem
The board includes a flexible 6-channel audio subsystem based on a High Definition Audio interface. The audio subsystem features:
• ATI IXP 450 Southbridge
• Realtek ALC883 audio codec
• Impedance sensing capability for jack re-tasking
• S/N (signal-to-noise) ratio of 90 dB
• Microphone input supporting:
&#9135; Stereo microphone
&#9135; Microphone boost
   My motherboard contains 3 jacks at backside and 2 jacks at front side. By default, only backside 3 jacks were enabled. One- audio out, two – Line in and three – Mic in. In windows by using motherboard driver, I will be selecting 6 channel output in driver software. During that time, the back panel connectors will be used for 6-channel output and front panel connector for MIC-in and headphone out. If this is common in other motherboards also, ignore it. 

Please help me.

---

### Post by mcduck on 2008-07-08
You can't get Dolby Surround (or any other true 5.1 sound) from normal 2 channel recordings. When the recording only has 2 channels it only has 2 channels, and that's it.

The only thing that can be done to even use the rear channels is to copy front channels to rear. Or use some amplifier that has ProLogic or ProLogic2 (whicha re technologies that try to calculate some kind of rear channel(s) from stereo recording, sometimes with quite OK results. (This far I've never even heard of any other device than amplifiers doing this.)

---

### Post by prabath_fun on 2008-07-08
Thanks. 

But, I am tring to get Dolby / DTS surround for the 5.1 channel encoded audio streams (DVD with 5.1  Dolby / DTS option, .vob files)
Regards,
Prabath

---

### Post by prabath_fun on 2008-12-16
[COLOR="RoyalBlue"]Hi,
       Finally, I got 5.1 speaker supports with Ubuntu 8.10 and works very good. I got integrated sound card in my motherboard and its model number is[/COLOR] [COLOR="Purple"]D102GGC2[/COLOR].
[COLOR="royalblue"]I followed the following steps and got succeeded.
1.	Take backup of /etc/pulse/daemon.conf.
2.	Edit /etc/pulse/daemon.conf with text editor.
I used gedit tool triggered from terminal as follows
Sudo gedit /edit/pulse/daemon.conf
3.	Scroll down to 
;default-sample-channels=2
 option.
a.	Uncomment it. That is, remove “;” symbol at starting.
b.	Change 2 to 6 for 5.1 channels / speaker.
4.	Restart system to take changes get effect.
5.	In terminal, do speaker test with following command in terminal
Speaker-test –Dplug:surround51 –c6 -11 –twav
If it is not working, please update thread, I got a 6 channel testing mp3 voice based file. I will upload it in this thread, if possible. I used this file instead of above command.
6.	If some problem in hearing sound in rear speakers, double click on speaker icon at top of the desktop, which opens preference. Check surround, center and LFE are not muted and in full/required volume levels.
7.	Further check the player, also set for 5.1 surround support in there preferences.

Now, I got 98% of functionality with Ubuntu 8.10. one extra application looking for is phone manager for my Sony Ericsson W810I model with SMS backup, call backup,[/COLOR] [COLOR="Red"]data transfer without switching to “file transfer” mode[/COLOR], [COLOR="royalblue"]etc., that is at least looking for 80% functionality from “My phone manager” tool.[/COLOR]

---

### Post by Norman IV on 2009-03-15
Is anyone still reading this post? If so I am wondering why I only get stereo (front speakers only) in the movie player because the speaker test correctly identifies all 6 channels (left and right surround work in speaker test but not in movie player, even with 5.1 channel DVDs). And the movie players (totem xine)audio preferences are set to 5.1.

update:
NM, I fixed it using advice from directly above post. changing default channels in /etc/pulse/daemon.conf to 6 corrected the problem, sorry if I wasted anyones time but I didn't expect this to work because speaker test and music player already worked with all 5.1 channels ( I guess they don't need pulse config to work right)

---

### Post by prabath_fun on 2009-10-20
Hi, No need to worry about 5.1 channel sttings in Ubuntu9.04. It is very simple, just by speaker Icon and click on "open Volume Control". Then, select device. For my mother Board it is "HDA ATI SB". Then, click on preference. check "channel mode", "front", "surround", "Center" and "LFE". Then close it. Then, go to "option" tab and change channel mode to "6". Thats all. 
  I am using VLC player for all type of playbacks including mp3. It gives output in dolby surround format and it is very good.

Prabath

---

### Post by prabath_fun on 2009-12-01
Hi,
 I got 5.1 speaker supports with Ubuntu 9.10 as well.

I followed the following steps and got succeeded.
1. Take backup of /etc/pulse/daemon.conf.
2. Edit /etc/pulse/daemon.conf with text editor.
I used gedit tool triggered from terminal as follows
Sudo gedit /edit/pulse/daemon.conf
3. Scroll down to 
;default-sample-channels=2 
option.
a. Uncomment it. That is, remove “;” symbol at starting.
b. Change 2 to 6 for 5.1 channels / speaker.
4. Open "alsamixer" by typing same in terminal.
5. Verify surround, LFE are not muted and channels for 6.
6. Restart system to take changes get effect.

That’s it. I got it worked. I saw the change in sound card selection in preference from right click on speaker icon as “ALC883 5.1……….”.

7. Further checked the VLC player output also, by setting 5.1 surround supports in there preferences.

I am too happy with Ubuntu9.10 as it works faster than Ubuntu9.04, got all the necessary softwares like office, KDE, Audacity, VLC player, Virtual box, etc., Thanks to canonical / Ubuntu team.

---

