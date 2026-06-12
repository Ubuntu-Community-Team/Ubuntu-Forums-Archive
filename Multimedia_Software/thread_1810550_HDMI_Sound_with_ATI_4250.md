---
title: "HDMI Sound with ATI 4250"
date: 2011-07-23
forum: Multimedia Software
---

### Post by KevinJaeger on 2011-07-23
I've built a MythTV system based on a Gigabyte [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]GA-880GM-D2H motherboard and MythBuntu 11.04 with the latest updates applied.  

This motherboard has ATI 4250 integrated graphics which I'm using the Catalyst drivers to drive my Samsung HD TV through the HDMI port. Everything is working great but I can only get analog sound out of the PC speakers - nothing I've tried has worked to get the sound to play through the HDMI port - either through Mythtv or just using aplay or speaker-test.

The details:
[FONT=System]
[/FONT][/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]kevin@mythtv:~$ aplay -l[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]Playing sound on the analog device works fine:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D plughw:0,0 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]

[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333] This yields no errors, but also no sound:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D plughw:1,3 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]Without the plug prefix I get an error:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D hw:1,3 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay: set_params:1065: Channels count non available[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT]I've unmuted the device with alsamixer -c1.  It shows the SPDIF device as 00.

As far as I can tell the hardware is supported and should work.  Any suggestions?

The full output of alsa-info.sh is here: [URL="http://www.alsa-project.org/db/?f=3913976290579f93d85fbd0d439975b579812016"]http://www.alsa-project.org/db/?f=3913976290579f93d85fbd0d439975b579812016
[/URL]

---

### Post by teejay17 on 2011-10-24
> **KevinJaeger said:**
> I've built a MythTV system based on a Gigabyte [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]GA-880GM-D2H motherboard and MythBuntu 11.04 with the latest updates applied.  

This motherboard has ATI 4250 integrated graphics which I'm using the Catalyst drivers to drive my Samsung HD TV through the HDMI port. Everything is working great but I can only get analog sound out of the PC speakers - nothing I've tried has worked to get the sound to play through the HDMI port - either through Mythtv or just using aplay or speaker-test.

The details:
[FONT=System]
[/FONT][/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]kevin@mythtv:~$ aplay -l[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevices: 1/1[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]  Subdevice #0: subdevice #0[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]Playing sound on the analog device works fine:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D plughw:0,0 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]

[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333] This yields no errors, but also no sound:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D plughw:1,3 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]Without the plug prefix I get an error:
[/COLOR][/SIZE][/FONT][INDENT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay -D hw:1,3 Front_Center.wav [/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]Playing WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][FONT=System]aplay: set_params:1065: Channels count non available[/FONT][/COLOR][/SIZE][/FONT]
[/INDENT]I've unmuted the device with alsamixer -c1.  It shows the SPDIF device as 00.

As far as I can tell the hardware is supported and should work.  Any suggestions?

The full output of alsa-info.sh is here: [URL="http://www.alsa-project.org/db/?f=3913976290579f93d85fbd0d439975b579812016"]http://www.alsa-project.org/db/?f=3913976290579f93d85fbd0d439975b579812016
[/URL]
Have you tried these steps? 
[SIZE=2][FONT=verdana,sans-serif][COLOR=#333333][FONT=Verdana]1. enter ubuntu software center
2. install GNOME ALSA Mixer
3. enter GNOME ALSA Mixer
4. mark the empty IEC958 checkbox as well
5. reboot
6. enter System / Prefernces / Sound
7. choose Hardware tab
8. choose profile: Digital Stereo (HDMI) Output

p.s. Overall, how do you find the ATI 4250 under Ubuntu? Good for watching hi-def videos on a large TV?
[/FONT][/COLOR][/FONT][/SIZE]

---

