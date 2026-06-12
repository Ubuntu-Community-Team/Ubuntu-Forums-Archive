---
title: "Intrepid Ibex: no fast forward/rewind in Totem and Rhythmbox with mp3 files"
date: 2008-12-02
forum: Multimedia Software
---

### Post by xenocard on 2008-12-02
Hi,

when I'm playing mp3 files with either Totem or Rhythmbox I can't fast forward or fast rewind. After gliding the cursor it would jump back to the original position. I noticed that Totem puts 'streaming' in brackets at the bottom of the window, next to the time, although the file is locally stored on my hard drive.

I tested Totem with an ogg file and it works fine. I don't have any other multimedia formats at hand. Since it affects both Totem and Rhythmbox I suspect the issue is in gstreamer.

Google didn't give me noticeable results related to this issue. Does anyone else have the problem? Is it a know issue?

---

### Post by Izek on 2008-12-02
Try turning on repeat mode in totem. (I don't know if Rhythmbox has the same mode somewhere, or if it acts the same as totem when it is on that mode.)

---

### Post by xenocard on 2008-12-02
> **Izek said:**
> Try turning on repeat mode in totem. (I don't know if Rhythmbox has the same mode somewhere, or if it acts the same as totem when it is on that mode.)

That doesn't change anything.

---

### Post by swahalla on 2008-12-20
Install the following packs with 'Add/Remove apps'

GStreamer extra plugins
Ubuntu restricted extras

That's all

---

### Post by xenocard on 2009-01-09
Following your suggestion I searched for extra gstreamer plugins not yet installed on my machine, and I found the gstreamer-0.10-fluendo-mp3 package. After installing it I can fast forward and rewind as I wish. Thanks!

---

### Post by robEdw on 2009-05-14
Hi,

I've added the, GStreamer extra plugins and Ubuntu restricted extras through add/remove and apt added the gstreamer-0.10-fluendo-mp3. Still getting the same problem in Rhythm box.

Anything else I could be missing or could try?

Thanks,
Rob

---

### Post by tanoloco on 2010-03-16
ubuntu-restricted-extras is not needed fo that:

1. just remove anything apt installed with ubuntu-restricted-extra
```
sudo apt-get autoremove cabextract gstreamer0.10-pitfdll ttf-mscorefonts-installer unrar ubuntu-restricted-extra
```2. just remove any gstreamer not needed for this problem
```
sudo apt-get autoremove gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```3. reboot

4. reinstall Rhythmbox
```
sudo apt-get install -reinstall rhythmbox
```5. install needed gstreamer plugins:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
```the first is needed to play ape files and to have thumbnails of video files  (working great with vlc) while the second is needed for fast forward / rewind issue in rhythmbox

6. reboot

7. open rhythmbox and delete all entries, open a new mp3 files and pay attention that it must show the duration .. otherwise just drop all your list again and try again .. rhythmbox must start without any file (pre) loaded.

8. It's done

Just for reference I'm using rhytmbox on karmic koala and the list of my gstreamer plugins is:
> 
gstreamer0.10-alsa               gstreamer0.10-plugins-base-apps
gstreamer0.10-ffmpeg             gstreamer0.10-plugins-good
gstreamer0.10-fluendo-mp3        gstreamer0.10-pulseaudio
gstreamer0.10-nice               gstreamer0.10-tools
gstreamer0.10-x               gstreamer0.10-plugins-base 
I think this thread should have the tag [SOLVED]

Cheers

---

### Post by skrimpy on 2010-05-12
Thank you, the above fix worked for my UNR Lucid install :)

---

### Post by jays0n on 2010-09-14
tanoloco thank you, this was happening to me in 10.04 LTS and your instructions worked perfectly.

---

