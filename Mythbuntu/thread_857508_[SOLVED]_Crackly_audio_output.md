---
title: "[SOLVED] Crackly audio output"
date: 2008-07-12
forum: Mythbuntu
---

### Post by rts on 2008-07-12
My hardware:

- Asus M3N78-EMH HDMI motherboard, using the onboard graphics and audio, with an AMD X2 5000

My software:
- Kernel 2.6.25.9, compiled myself (to get the motherboard working properly)
- Asound drivers 1.0.17rc3 (in an attempt to get audio working)
- Completely up-to-date Hardy install with weekly MythTV repos enabled.

I get crackly audio in MythTV.  It is especially bad in the music player, but also happens intermittently in the video player, and never when watching live TV.

Some things I have tried to fix this that didn't work:

- Everything mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
- Removed pulse audio completely
- Upgraded from Alsa 1.0.16 to 1.0.17rc3
- Removed powernowd

Audio is coming out the pale pink jack (not using HDMI).

It doesn't seem to be a CPU power issue as crackling is observed *most* when playing MP3s, which do not tax the CPU at all.  It also seems fairly random when it happens during video playback.  It seems to get worse the longer a video is, but then (usually) clears up after starting a new video.

Other than that myth works great on this set up.

Any have any other suggestions to try to clear up this crackly audio?


EDIT: Downgrading to the 0404 version of the BIOS seems to solve the problem.

[http://drivers.softpedia.com/get/BIOS/Asus/ASUS-M3N78-EMH-HDMI-BIOS-0404.shtml](http://drivers.softpedia.com/get/BIOS/Asus/ASUS-M3N78-EMH-HDMI-BIOS-0404.shtml)

---

### Post by pluckypigeon on 2008-07-12
I bet you are running Intrepid alpha

---

### Post by rts on 2008-07-12
> **pluckypigeon said:**
> I bet you are running Intrepid alpha

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

Nope.

---

### Post by jbman on 2008-07-13
Running the same board, standard kernel on ubuntu 8.04.1 with all the normal updates nothing extra with optical out via the optional board I have no audio issues.

I am guessing the audio is analogue coming from that output so that is where is issue must lie.

---

### Post by stevew1954 on 2008-07-24
I noticed crackly sound with m3n78-emh 8.04.1 when I used anything above bios update 404.  409, 506 and 507 all result in crackling - sort of reverberation and distortion.  Tried latest 1.17 alsa and played round with audio settings but only thing that changed the distortion was returning to 404 bios.

---

### Post by rts on 2008-07-25
> **stevew1954 said:**
> I noticed crackly sound with m3n78-emh 8.04.1 when I used anything above bios update 404.  409, 506 and 507 all result in crackling - sort of reverberation and distortion.  Tried latest 1.17 alsa and played round with audio settings but only thing that changed the distortion was returning to 404 bios.

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3N78-EMH](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3N78-EMH) HDMI

That page only goes back as far as 409... where can I get 404 from?


Edit:

Found it here:

[http://drivers.softpedia.com/get/BIOS/Asus/ASUS-M3N78-EMH-HDMI-BIOS-0404.shtml](http://drivers.softpedia.com/get/BIOS/Asus/ASUS-M3N78-EMH-HDMI-BIOS-0404.shtml)


and yes! That seems to have solved the crackly audio.  Thank you.

---

### Post by ghjf345 on 2008-10-25
I found that the latest BIOS version (0601, available on the Asus website) did the trick, as well.

---

