---
title: "Ubuntu 10.04 -- No Sound -- Errors in Processing Files"
date: 2011-04-12
forum: Multimedia Software
---

### Post by freddyb590 on 2011-04-12
Hi, all. . .

Ubuntu 10.04 with an HP d530 SFF

From lspci:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

When trying to do sudo apt-get install -f, I get this:

Errors were encountered while processing:
 libdirac-encoder0
 libfaac0
 libfaad2
 libopenjpeg2
 libqt4-dbus
 librtmp0
 libva1
 libxvidcore4
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no sound.  When trying to change sound preferences, I get:  "Waiting for sound system to respond."

Any tips or tricks?

--  Fred

---

### Post by epyonx1 on 2011-05-17
> **freddyb590 said:**
> 
I have no sound.  When trying to change sound preferences, I get:  "Waiting for sound system to respond."
Any tips or tricks?
--  Fred

I had the same issue. I am using Ubuntu 10.10.

1) First, I used System -> Administration -> "System Testing"
- Ubuntu suggested testing headphones. They worked fine but I could not hear the desktop's internal speakers.

2) Then I opened up the Terminal & used the "alsamixer" command
- Press F6 for the option "F6: Select sound card"
---- Of the sound cards, I selected Intel ICH5 (Yours might be different. Use the command "lspci" and see what it says under the "Multimedia audio controller")
---- Pushed all volumes to max
(You MAY have to reboot if the following steps don't work & try again)

3) Then I used System -> Administration -> "Synaptic Package Manager"
- I made sure the following were installed (I'm not sure which ones exactly did the trick):
---- alsa-base
---- alsa-firmware-loaders
---- alsa-oss
---- alsa-tools
---- alsa-tools-gui
---- alsa-utils
---- alsamixergui
---- gnome-alsamixer

4) Lastly, I went to "Sound & Video" -> alsamixergui
- Make sure all the speaker icons ABOVE the bars are green
- Make sure all lock icons BELOW the bars are locked
- Push all the volume bars to max. Adjust as necessary. The main one is "Master Mono"

(These are ALL of the steps I went through to get it to work by a MIRACLE 0_0 ... if anyone can find out EXACTLY which ones to focus on, by all means, let it be known to all. Thanks.)

:)

---

