---
title: "MP3 VBR Issue"
date: 2011-05-04
forum: Multimedia Software
---

### Post by petronell on 2011-05-04
Hi Everyone,

I know the answer to the question is going to be a simple one, but I can't find it and it is really annoying me - so hopefully one of you helpful people will be able to point me in the right direction.

I am ripping my cd collection to MP3, and have done a fair bit of research. I have decided on RubyRipper which I have installed from the getdeb site and I am ripping using the parameter "-V 0" which is meant to give me the highest quality vbr rips (roughly 235kbps). 

When I bring the ripped album into Rhythmbox it shows the bit rate as 96kbps, and if I choose the properties of one of the MP3's that also says 96kbps.

When I play one of the MP3s in vlc it shows under the codec information as the track being 235kbps as you would expect.

Just to check I am not going mad I have also installed RipperX and done an identical rip and that is coming back with the same results as RubyRipper.

So what am I doing wrong?

Thanks for any help that can be offered... :popcorn:

daveR

---

### Post by Steeperton on 2011-05-04
Don't worry, it seems to be the way the fluendo codec calculates it... It is actually the correct bit rate, just Ubuntu is reading it "wrong". You can see this by playing it in VLC, and viewing media information, which gives you the actual bitrate.

If it bothers you (like it did me!), you can do the following. This sorted it for me:

```
sudo apt-get remove gstreamer0.10-fluendo-mp3
sudo apt-get install ubuntu-restricted-extras
```

worked for me (after a reboot)

---

### Post by petronell on 2011-05-04
Thanks a lot that has worked like a dream.

:guitar:

daveR

---

