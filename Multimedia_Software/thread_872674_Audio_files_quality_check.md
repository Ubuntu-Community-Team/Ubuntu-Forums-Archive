---
title: "Audio files quality check"
date: 2008-07-28
forum: Multimedia Software
---

### Post by talbain on 2008-07-28
Hi, does anyone know if there is an application that would show me the quality on downloaded music files?

I can get a general idea by looking at the files properties, but, how do i know know for example if the file is vbr or cbr? or other encoding settings used?

Thanks

---

### Post by talbain on 2008-07-28
Anyone?

---

### Post by vanadium on 2008-07-28
ogginfo for ogg files, encspot for mp3 files

---

### Post by talbain on 2008-07-28
Gonna try that, thanks!

---

### Post by talbain on 2008-07-29
Oh, i see...
Any linux native app for that?

---

### Post by vanadium on 2008-07-30
> 
Oh, i see...
Any linux native app for that? 


You are probably referring to encspot ;) There is a linux binary available at rarewares.org. To install the software you wil need to add (at least temporarily) their repos in your /etc/apt/sources.list.

```

gksudo gedit /etc/apt/sources.list

```

Add the following lines to the end of the file:

```

 ## RareWares/Debian Multi-Media Repository for Unstable 
deb http://www.rarewares.org/debian/packages/unstable/ ./ 

## RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging 
deb http://www.rarewares.org/debian/packages/experimental/ ./ 

## Christian Marillat's Mult-Media Repository for Unstable 
deb http://www.debian-multimedia.org sid main 

## Christian Marillat's Mult-Media Repository for Unstable - Experimental Staging 
deb http://www.debian-multimedia.org experimental main 

```

Then:

```

sudo apt-get update
sudo apt-get install encspot

```

Remove or comment the lines you added to /etc/apt/sources.list if you do not want to remain subscribed to these repos.

---

### Post by talbain on 2008-07-30
Yeah, encspot or any app to get the info i need about my music files, i guess i want something thats native so i dont have to deal with the hassle of displaying info about files in japanese, for some reason i assume it would support unicode or something, thanks for that, im gonna try it.

---

### Post by FakeOutdoorsman on 2008-07-30
I use ffmpeg to get info about all types of media files:
```
[frink@hedron]$ ffmpeg -i kwyjibo.mp3 
Input #0, mp3, from 'kwyjibo.mp3':
  Duration: 00:02:55.10, start: 0.000000, bitrate: 96 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, 96 kb/s
```
Unfortunately it doesn't tell you if it's CBR or VBR.

---

