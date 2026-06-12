---
title: "raw1394 kernal module error when opening Kino"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by mmmpancakes on 2006-09-20
I've attached my JVC digital camcorder to my PC via Firewire. I open Kino, which starts fine, but when I click the capture tab, I get an error message at the bottom that says "WARNING: raw1394 kernal module not loaded or failure to read / write /dev/raw1394!" . 

I can't seem to capture video from this point. I searched the forums/Google without luck.

---

### Post by mmmpancakes on 2006-09-20
bump

---

### Post by mmmpancakes on 2006-09-21
bump

---

### Post by spottraining on 2006-10-01
sudo modprobe raw1394
sudo chmod a+rw /dev/*1394

Its work on Ubuntu 6.06, but not in 6.10 right now.

---

### Post by josh76 on 2006-12-06
is 6.10 edgy ready to run this script yet?

---

### Post by g0pbe on 2006-12-06
I have tried the:-

sudo modprobe raw1394
sudo chmod a+rw /dev/*1394

and that at least got KINO to recognise the camera. I even got control of the playback system on the camera. The only problem now is that I cannot get the video to show in the KINO window either in playback or Capture mode 

I hope someone out there can help. I would dearly love to finally be able to kick Windows into touch but I really need to get KINO (or something elsa) working first

Thanks

Dave

---

