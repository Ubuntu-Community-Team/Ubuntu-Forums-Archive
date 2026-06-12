---
title: "Black Magic Intensity Pro output video won't play audio"
date: 2016-05-25
forum: Multimedia Software
---

### Post by dexter8 on 2016-05-25
Okay, so in Ubuntu 14.04 I was able to use my capture card to record video and put it straight into kdenlive for editing. In 16.04 when I import it into Kdenlive, it reads the file as having no audio. Videos/Mplayer? will play the file if I click play, but also shows it as having no audio. VLC will play the file just fine - audio included. Mediainfo doesn't tell me too much about the file unfortunately. Ubuntu-restricted-extras have begrudgingly been installed, but have not solved the issue.  Any ideas? [IMG]http://s33.postimg.org/fh3alygv3/Screenshot_from_2016_05_25_12_07_23.png[/IMG]

Cheers

---

### Post by myromance123 on 2016-10-02
I'm in the same boat as you are. I'm on the experimental version of Kdenlive (16.11.70) and even though my recordings with Media Express through my Intensity Pro 4k have audio, Kdenlive cannot see it. This is on Ubuntu 16.04, and I'm certain this has something to do with Gstreamer.

Back in Ubuntu 15.10, I was able to play the video files with their audio in Totem. Totem would first load up the file, find the right Gstreamer needed and I'd install it and I'd be good to go. In 16.04, Totem can't find any Gstreamer to play the audio and it's the exact same file as in 15.10.

It's definitely codec related, as ONLY VLC can play the audio (since VLC comes pre-bundled with it's own set of codecs). MPV, Smplayer, Totem and all other video players I've tried can't play the audio.

Media Info shows me this:
[img]http://i.imgur.com/6QYGAUV.png[/img]

If anyone has any idea which Gstreamer files were removed from 16.04 but were present in 15.10 and earlier, please let us know! It'd be greatly appreciated.

---

### Post by myromance123 on 2016-10-04
Alright, I think I've got a temporary solution to this.

Since VLC is the only program that can play the audio, we'll use VLC to extract the audio. 

1. Open up VLC, then click Media -> Open Multiple Files.

2. Under File Selection, click Add... and chose the video file you've just recorded using Media Express.

3. Next to the Play button, there is a small arrow pointing downwards. Press this, and click Convert. A new window will pop up.

4. Under Profile, scroll down until you find the Audio section. Your choice here, but I personally have only tested Audio - Vorbis (OGG).

5. Choose a destination for the file, and click Save.

6. You should be able to click Start.

Now, I've noticed VLC can get buggy doing this. It'll want to keep repeating the process. So, after the first time it's done, just copy that audio file into a separate folder and then force close VLC. You can now play this audio file in anything, and it should be as crisp and clean as if it were playing directly through Media Express.

I hope that helps you and anyone else who stumbles onto this problem!

---

