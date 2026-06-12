---
title: "Problems with making DVD"
date: 2023-12-31
forum: Multimedia Software
---

### Post by msknight on 2023-12-31
I'm trying to make a PAL, widescreen DVD. - Lobster cinnamon 5.6.7 kernel 6.2.0-39-generic

I've used Brasero 3.12.3, but it insists on either converting the file and making a very bad job of it (most of the plugins are greyed out so I can't configure them) or else failing immediately with "Impossible to link plugin pads."

This is despite using KDEnlive to create an MPEG2 file and also trying to feed the file through ffmpeg with the -target pal-dvd option.

dvdstyler appears to no longer have an installation candidate.

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack Output set (AUDIO) image = /home/michelle/tmp/brasero_tmp_QCC4G2.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_action
BraseroVob deactivating
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_session_output_size
BraseroVob Output set (AUDIO) image = /home/michelle/tmp/brasero_tmp_KPB4G2.cdr
BraseroVob called brasero_job_get_session_output_size
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_output_type
BraseroVob Got output type (is DVD 1, is SVCD 0)
BraseroVob Creating new pipeline
BraseroVob called brasero_job_get_current_track
BraseroVob called brasero_job_get_audio_output
BraseroVob called brasero_job_tag_lookup
BraseroVob called brasero_job_tag_lookup
BraseroVob Setting ratio 16:9
BraseroVob Error while linking pads
BraseroVob can't create object : Impossible to link plugin pads 

BraseroVob stopping
Session error : Impossible to link plugin pads (brasero_burn_record brasero-burn.c:2854)
```

---

### Post by #&amp;thj^% on 2023-12-31
Have you yet tried Handbreak? It's my go to for DVDs
```
apt search handbrake
Sorting... Done
Full Text Search... Done
handbrake/noble 1.7.2+ds1-1 arm64
  versatile DVD ripper and video transcoder (GTK+ GUI)

handbrake-cli/noble 1.7.2+ds1-1 arm64
  versatile DVD ripper and video transcoder (command line)


```

---

### Post by msknight on 2023-12-31
I'm not ripping them... I'm trying to create them. :-)

---

### Post by #&amp;thj^% on 2023-12-31
An example would be nice then.

BTW Handbrake will make home DVDs as well

---

### Post by Holger_Gehrke on 2023-12-31
'devede' is in the repositories. The package should actually be called DeVeDeNG since it's a rewrite of the original DeVeDe to use Python 3 and GTK 3. Found on [https://alternative.to](https://alternative.to) when searching for alternatives to dvdstyler.

---

### Post by #&amp;thj^% on 2023-12-31
Also since you mention Ffmeg:
```
apt show qwinff
Package: qwinff
Version: 0.2.1+git20201215-2
Priority: optional
Section: video
Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Installed-Size: 1,125 kB
Depends: libc6 (>= 2.34), libgcc-s1 (>= 3.0), libgl1, libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.14.1), libqt5gui5 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5network5 (>= 5.0.2), libqt5opengl5 (>= 5.0.2), libqt5widgets5 (>= 5.0.2), libstdc++6 (>= 5.2), ffmpeg, mpv, sox
Homepage: http://qwinff.github.io/
Tag: implemented-in::c++, interface::graphical, interface::x11,
 role::program, uitoolkit::qt, x11::application
Download-Size: 459 kB
APT-Manual-Installed: yes
APT-Sources: https://deb.parrot.sh/parrot lory/main amd64 Packages
Description: GUI for FFmpeg
 This is a free and open source media converter frontend to FFmpeg. FFmpeg
 is a powerful command-line utility to convert audio and video file into
 numerous formats. QWinFF features a rich set of presets to help users use
 FFmpeg easily without having to manually input command-line flags. Average
 users can convert multiple media files in just a few clicks, while advanced
 users can still adjust conversion parameters in detail.

```

---

### Post by msknight on 2023-12-31
> **Holger_Gehrke said:**
> 'devede' is in the repositories. The package should actually be called DeVeDeNG since it's a rewrite of the original DeVeDe to use Python 3 and GTK 3. Found on [https://alternative.to](https://alternative.to) when searching for alternatives to dvdstyler.

Thanks. That did the job. It also converted the MPEG2 file I created, but it did a great job of it and created a good quality output. Many thanks.

---

### Post by littlepeon on 2024-01-22
If you want to save a little time, you can transcode the original codec faster with just ffmpeg. You would use:```
ffmpeg -i input.avi -target pal-dvd output.vob
```
This transcodes the original file to a mpeg2 compliant vob that DVDStylerNG can quickly turn into a DVD. (you can also change -target pal-dvd to -target ntsc-dvd for your USA friends)

---

