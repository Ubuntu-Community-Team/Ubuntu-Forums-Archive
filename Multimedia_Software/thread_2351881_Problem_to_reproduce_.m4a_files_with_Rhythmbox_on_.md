---
title: "Problem to reproduce .m4a files with Rhythmbox on Ubuntu 16.04.1"
date: 2017-02-07
forum: Multimedia Software
---

### Post by lukeraza on 2017-02-07
I just install Ubuntu 16.04.1 and i want to reproduce .m4a files with Rhythmbox because the ipod synchronization.

I google it, and i already tried   
[LIST=1]
[*]apt-get install ubuntu-restricted-extras
[*]apt-get install gstreamer1.0-plugins-bad
[*]apt-get install libavcodec-extra-54
[/LIST]

But nothing works. 

This is what i get from file command: 
john@john-ThinkPad-T420s:$ file 3-03\ I\ Miss\ You.m4a 
3-03 I Miss You.m4a: ISO Media, Apple iTunes ALAC/AAC-LC (.M4A) Audio

I can listen the files with vlc with out problems.  But vlc doesn't synchronize my ipod. 

Thanks in advance.

---

### Post by mc4man on 2017-02-07
If those are alac files then gstreamer uses the gstreamer1.0-libav plugin for decoding which  currently is totally broken.
bug - [https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842)

temp workaround - [https://ubuntuforums.org/showthread.php?t=2351490&p=13602837&viewfull=1#post13602837](https://ubuntuforums.org/showthread.php?t=2351490&p=13602837&viewfull=1#post13602837)

---

### Post by lukeraza on 2017-02-07
Thanks mc4man.

I tried that, but still is not working with Rhythmbox. 

I don't know if maybe is because i made many changes before and now something else is interfering. 

I'm going to tried with a fresh install in virtual box, and i will update tomorrow.

---

### Post by lukeraza on 2017-02-08
With the downgraded gstreamer1.0-libav package,  Rhythmbox is still not working, but others music players like Clementine are working correctly with m4a files.  
At least now i can listen my music.
But still i miss the way that Rhythmbox synchronize my ipod.

---

### Post by mc4man on 2017-02-08
Try removing the .bin file in ~/.cache/gstreamer-1.0
Then open Rb & see if improved.

---

### Post by lukeraza on 2017-02-10
I tried, but the same, it is not playing the .m4a files and each time i open Rhythmbox, the bin file is regenerated.

---

### Post by mc4man on 2017-02-10
> **lukeraza said:**
> I tried, but the same, it is not playing the .m4a files and each time i open Rhythmbox, the bin file is regenerated.
It's supposed to reappear, removing just sees if issue is with a corrupted .bin file.
Does Videos (totem) play these files?

If desired you could try an alac file I've here, note upload site rotates files so won't be there for an extended time
```
wget https://0x0.st/4z1.m4a
```
you'll find in Home folder if run from default terminal prompt..

---

### Post by lukeraza on 2017-02-11
I played your file in Rhythmbox without problems and while I was trying to upload one of my files to mega, I copied my file from the external hard drive to my desktop and accidentally i pushed 'enter' in the keyboard and Rhythmbox started playing the file.

Now i know that the files are not the problem.

So, the problem was  first the gst-libav package version. 

And in second place is that somehow Rhythmbox doesn't know how to deal with the symbolic links that i have in my pc.  

Thank you mc4man, you are amazing. 
God bless you!!!
Without your help I would never have done it.

:-({|=:-({|=:-({|=:-({|=:-({|=:-({|=:-({|=

---

