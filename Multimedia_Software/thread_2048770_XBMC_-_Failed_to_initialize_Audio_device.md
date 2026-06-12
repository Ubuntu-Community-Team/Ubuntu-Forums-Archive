---
title: "XBMC - Failed to initialize Audio device"
date: 2012-08-27
forum: Multimedia Software
---

### Post by slippyjim on 2012-08-27
[FONT=Arial][SIZE=2][FONT=&quot]Hiya,

I have been using XBMCLive /win7 dual boot for over 3 years then one day it all messed up so Ive decided to take the plunge and go for all Linux on my media PC.....[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]Acer Revo R3610, 2GB RAM, 320GB
installed ubuntu 12.04 64bit
latest version of xbmc v11.0
latest nvidia drivers v304.37
hdmi into sony 40" lcd[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2]
spdif optical into sony dts amp

When playing some 720p mkv files

[SIZE=3]**smplayer**[/SIZE] 
video juddery but audio OK
[/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=&quot] settings - alsa (0.0 hda nvidia)
ac3/dts pass thorugh spdif ticked
channels by default 6 (5.1 surround) [/FONT][/SIZE][/FONT]
  

[SIZE=3]**[FONT=Arial][FONT=&quot]XBMC [/FONT][/FONT]**[/SIZE]
[FONT=Arial][SIZE=2][FONT=&quot]Video fine but no audio at all I get what after searching google seems to be the dreaded "Failed to initialize Audio device. check your audiosettings" 
[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]I get the same error if i try to play an mp3 file as well.[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]In XBMC system audio setup there is a long list of audio output devices and I'm sure I've tried them all with no luck.[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]Audio device - Optical/coax[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]audio output - Ive tried all combos of iec958[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]audio passthru output - Ive tried all combos of iec958[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&quot]In System Settings -> Sound I have
HDMI /DisplayPort - I do a test and no sound comes out my TV 
Digital Output SPDIF - I do the Test and it is OK 
 
 [/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]Had a look in XBMC and CPU1 was at 70%, CPU2,3,4 were at about 30% and all that was running XBMC and Deluge Seems noiser than before when I had XBMCLive/Win 7 dual boot [/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]I need XBMC to work as I can’t get the screen to fit right on the normal Linux desktop, need to resize the picture like I can in XBMC[/FONT][/SIZE][/FONT]


[FONT=Arial][SIZE=2]Any ideas?
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Thanks,
[/SIZE][/FONT] 
[FONT=Arial][SIZE=2][FONT=&quot] Steve[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]

---

### Post by harger on 2012-11-05
I am having the exact same problem. Audio works in dual boot with win7 but fails to initialize  if xbmc is the only OS. I am using the onboard sound via the usual 3,5 mm plugs (only got stereo speakers)

MoBo: [MSI K8N Neo4-F (PCB 1.0)]("http://www.msi.com/product/mb/K8N-Neo4-F--PCB-1-0-.html")
Cpu: 3800+ XP single core
Ram: 1 Gb

Sorry for the thread resurrection but this was the best description of my problem i found.

---

### Post by Dale61 on 2012-11-05
I tried XBMC for about a month, and could never get the sound to initialise when I had it set to HDMI.  Once I changed it to any of the other two settings, sound was fine, but NOT in 5.1.

I had it set to HDMI as I was running my laptop through a digital a/v control centre (via HDMI), then from the a/v to my 106cm HDTV (via HDMI).

I was prepared to live with that when XBMC started to get laggy, seemed to take forever to find and add movie info, then started to display the wrong names for some of my movies.

Needless to say, I reverted back to what I knew worked.  Not as fancy, but just as effective.

---

### Post by harger on 2012-11-06
Okay my problem can be fixed with installing XBMC on a xubuntu distribution. Only had the problem with XBMCbuntu but not on Xubuntu 12.10. The new disribution uses pulseaudio maybe thats a help to someone.

---

