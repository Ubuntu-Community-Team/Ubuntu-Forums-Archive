---
title: "remove (&quot;crop&quot;?) end of MPEG2 video without re-encoding"
date: 2008-05-28
forum: Multimedia Software
---

### Post by FSHero on 2008-05-28
Hi all, I am running Kubuntu Feisty i386. I have some home videos on my disk in MPEG2 format. The way I took it off my camcorder (it was a long time ago!) was: to plug the camcorder into the red/white/yellow analogue inputs on the front of my computer. I used Cyberlink something-or-other (in Windows XP) to start capturing video from the video capture device. I pressed play on my camcorder and let the tape run through.

However, I often overran, and thus there is a screen of blue for a few minutes at the end of every video. I was wondering: is there a way to remove this?

I tried using Avidemux 2.3.0 and I was able to select the end part then do Edit --> Delete. However, when I attempted to save it (File --> Save --> Save video) and typed in a new file name, it began re-encoding! This would have taken long, since the original file was 2GB in size!! Plus, I didn't want to lose quality by re-encoding. Therefore I cancelled the re-encoding operation.

Thus is there a way to remove the end of the videos without having to re-encode the video? I have a feeling that the solution to this is simple, but I don't know where to start... I am willing to use any program (including command-line if it's not too complicated!), preferably FOSS from the Feisty repository.

---

### Post by jjgomera on 2008-05-28
its easier with edit/set marker to fix the begin and end of video, at left video and audio stay on "copy", finally File/save and there isn't recoding.

---

### Post by FSHero on 2008-05-28
Thanks very much! I knew the solution would be simple... I can't believe I didn't see it myself!

What I did was firstly select the part that I wanted. I ensured that on the 'left bar', both video and audio were at copy, and then I went to Video --> Encoder and selected Copy from the drop-down list (I think that nothing was selected before this). I went to File --> Save --> Save Video... I typed in a file name and it worked! The selected part was saved in a separate video.

However... I had some problems. The output video plays in Kaffeine properly, but I cannot 'skip' through the video using the progress bar. Also, every time I try to open the output video in Avidemux, it asks me if I want to re-index (or something) the video. If I do so everything is okay, but if I don't, there are some serious artefacts in the video (e.g. looks like the video moves 'up and down' across the screen).

These are minor problems, however... could it be codec problems? I think I installed some stuff from Medibuntu repositories... could this be the problem? Hopefully the problem will go away when I upgrade to Hardy in the very near future.

---

### Post by jjgomera on 2008-05-29
> **FSHero said:**
> 
However... I had some problems. The output video plays in Kaffeine properly, but I cannot 'skip' through the video using the progress bar. Also, every time I try to open the output video in Avidemux, it asks me if I want to re-index (or something) the video. If I do so everything is okay, but if I don't, there are some serious artefacts in the video (e.g. looks like the video moves 'up and down' across the screen).

These are minor problems, however... could it be codec problems? I think I installed some stuff from Medibuntu repositories... could this be the problem? Hopefully the problem will go away when I upgrade to Hardy in the very near future.
Do you have problem to play the original video too?
And with other player, vlc, mplayer, totem, too?

The message "The index is not update" is normal, simply say yes

---

### Post by JEDIDIAH on 2008-05-29
> **FSHero said:**
> 
However, I often overran, and thus there is a screen of blue for a few minutes at the end of every video. I was wondering: is there a way to remove this?


The commandline tool for firewire import will split the incoming file on
scene boundaries by default.

If you're using avidemux to cut this bit off of an MPEG2 video then the
resulting "encode" when you save it shouldn't really be "encoding" at
all. As long as the encode options for audio and video are set to "copy" 
then you should be OK. 

This was the default when I installed avidemux and it didn't seem to 
"mess" with the MPEG2 content I edited. Although it did seem to do
something to h264 input when saving it back out through the "copy"
encoder.

---

