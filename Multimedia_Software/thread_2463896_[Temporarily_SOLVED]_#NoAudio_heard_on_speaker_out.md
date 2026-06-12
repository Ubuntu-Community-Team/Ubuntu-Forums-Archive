---
title: "[Temporarily SOLVED] #NoAudio heard on speaker output from players"
date: 2021-06-20
forum: Multimedia Software
---

### Post by ccor58 on 2021-06-20
Update:  REMOVED PULSEAUDIO until pulseaudio guru can answer questions laid out here to get to permanent solution.


I am running ubuntustudio 20.04LTS and am unable to hear sounds from player software or browser listen live links. 

The docx file from link:

 [https://drive.google.com/file/d/1q8GN-4qrOjAZ5OIZQiINtE3cyNd1NSYO/view?usp=sharing](https://drive.google.com/file/d/1q8GN-4qrOjAZ5OIZQiINtE3cyNd1NSYO/view?usp=sharing)

 describes problem and troubleshooting steps in more detail. If I select "sound settings" from the audio volume icon in notification area nothing launches. If I select pulse server manager or configure pulserver I am unable to as both of these are greyed out. If I view the PAVU (PulseAudio Volume Control) screen the level indicators show the players and/or browser sources are playing and outputting audio as expected; it just has everything going to a "DUMMY" device. It does not indicate it has recognized the integrated sound card from the mainboard as a configured device and hence the reason for Dummy device use and no speaker output.

I am able to play an .mp3 selection using the play and mpg123 CLI commands and can hear the audio through the sound card and speakers OK , so I know they work. I can see the GUI driven player programs and browser sound feeds on the level control indicators so I am assuming they are all serviceable. I can see pulseaudio server is running as a daemon OK using ps -A|grep pulseaudio command but there seems to be a disconnect at this point. Since everything seems to work to a dummy the logs are not indicating major obvious errors. I have added my userID to both audio, dialout and root and adm groups in case it is a permissions issue but that did not appear to be the needed cure. All the usual details and system hardware troubleshooting steps are included in aforementioned docx file. The gfx's show no mutes are on in alsamixer.

I would appreciate any help at all ; I have been at this for about 7 hrs now and am running out of ideas.

Thanks  for any tips at all

---

### Post by ccor58 on 2021-06-22
Does anyone have a link to serious discussion or instruction on how Pulseaudio loads needed modules to connect with installed hardware or even the code areas how it detects available hardware and then selects correct module to add???

---

### Post by ajgreeny on 2021-06-22
What is showing in the right hand tab in pulseaudio-volume-control, the configuration tab?

Does that help you as it maybe that HDMI is the active one and your internal sound system is Off.

---

### Post by ccor58 on 2021-06-22
Nothing is showing as any device in the Right hand tab of PAVU (see att.) I have removed the webcam mic and also the USB simple sound dongle so the internal integrated sound card should be showing. Setup program shows it turned on; aplay -l lists it and as the pics show in the initial post's link docx file alsamixer shows the card as being detected, and available and all settings can be adjusted and MUTEs removed.

---

