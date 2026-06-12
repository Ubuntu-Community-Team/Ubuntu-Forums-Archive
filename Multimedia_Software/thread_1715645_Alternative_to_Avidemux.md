---
title: "Alternative to Avidemux?"
date: 2011-03-27
forum: Multimedia Software
---

### Post by chome4 on 2011-03-27
Can anyone recommend a good video editor? When editing an MP4 file from YouTube with Avidemux, the editing works perfectly but the resulting video sound is speeded up but the image runs at normal speed. The resulting mess is out of synch video/sound.

Any ideas?

---

### Post by JoshLukas on 2011-03-28
Try to install specific codecs. Add the medibuntu-repository to your /etc/apt/sources.list then install w64codecs (64bit platform), or w32codecs if using 32bit platform.

Otherwise you can have a look on kdenlive. It's a very good video editing software.

---

### Post by Enigmapond on 2011-03-28
Try either Handbrake or Auteur. The latter being the best IMHO.

---

### Post by rgb1701 on 2011-03-28
Avidemux is very good for linear editing.  The A/V sync issue is common is video editing/conversion tasks, and crops up when using a lot of apps, not just Avidemux.

The key is knowing the workarounds.

A common workaround I use is to first convert the video to an .mkv container using its native video codec plus PCM audio.

So for your example, you would first write out an intermediate .mkv file containing the original MP4 video (unchanged, not re-encoded) plus PCM audio (Uncompressed, no codec).

The MKV file container and PCM audio will ensure good A/V sync, as the .mkv container has good timing control, plus converting the audio to PCM eliminates audio packet alignment issues with lossy compressed audio.

Do all your edits using the PCM .mkv file and save again to an .mkv with native video and PCM.  Check for A/V sync once more, then open the final edited .mkv file and write out an .mkv with the video and audio formats you want.  You can select another file container (avi, mp4, etc), but mkv generally is a good choice for A/V sync.

Working with intermediate files like this is common practive in A/V editing, regardless of OS or apps used.

Re: Auteur-  thanks for the headsup, always nice to find another FOSS video editor alternative.  Hadn't heard of that one!

---

### Post by chome4 on 2011-03-29
> **Enigmapond said:**
> Try either Handbrake or Auteur. The latter being the best IMHO.

Do you have a link for the installation for Jaunty of Auteur?

---

### Post by Enigmapond on 2011-03-29
Well first of all there is no more support for 9.04 and I suggest you do a fresh install of 10.04 or 10.10. After that, in the terminal... do:

```
sudo add-apt-repository ppa:rowinggolfer/ppa
sudo apt-get update
sudo apt-get install auteur
```

---

