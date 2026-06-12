---
title: "problem running videos."
date: 2010-05-24
forum: Multimedia Software
---

### Post by irv on 2010-05-24
I am having problem running video files no matter what program I use. Take for example: I have a file on my desktop named "output.mkv" If I try to open it in VLC from the terminal here is the error I am getting. I am not sure what it is telling me.
```
irv@irv-desktop:~/Desktop$ vlc output.mkv
VLC media player 1.0.6 Goldeneye
[0x8a99148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x8d9f4e0] pulse audio output: No. of Audio Channels: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102
irv@irv-desktop:~/Desktop$ 

``` 
anyone got an idea what is going on. This is the first time I tried this since I installed 10.04. I have played movies but just can't run a file from my PC.

---

### Post by irv on 2010-05-24
If I try to run it out of xine, I get the following:
```
irv@irv-desktop:~/Desktop$ xine output.mkv
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2475
  Current serial number in output stream:  2476

```
It appears I do not have sufficient resources for this operation. I am not sure what resources they are talking about.
Here is my system from the Monitor:
[ATTACH]158132[/ATTACH]

---

### Post by Failboat88 on 2010-05-24
Is that a blue ray rip? If you don't know check the file size; if it is huge it might be. Your processor and/or video card may not be able to handle high quality HD.

---

### Post by irv on 2010-05-24
It a real small video I made with ffmpeg.
```
irv@irv-desktop:~/Desktop$ ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
FFmpeg version SVN-r23289, Copyright (c) 2000-2010 the FFmpeg developers
  built on May 24 2010 14:13:57 with gcc 4.4.3
..............
frame=   31 fps=  1 q=12980555.0 Lsize=    2664kB time=20.68 bitrate=1055.2kbits/s  

```
Here is the property of the file.
[ATTACH]158139[/ATTACH]

---

### Post by irv on 2010-05-24
Just to make sure it wasn't the video file I downloaded a small video off of youtube and I got the same results. Here is the following:
```
irv@irv-desktop:~/Desktop$ vlc testvideo
VLC media player 1.0.6 Goldeneye
[0x9a68148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
mdb:58, lastbuf:0 skipping granule 0
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9ec2640] pulse audio output: No. of Audio Channels: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102
irv@irv-desktop:~/Desktop$ 

```
File property. [ATTACH]158140[/ATTACH]

---

### Post by xc3RnbFO8P on 2010-05-25
You can try to chance the output driver in (Vlc) Preferences> Video> Output

---

### Post by Failboat88 on 2010-05-25
> **Ringi said:**
> You can try to chance the output driver in (Vlc) Preferences> Video> Output

Change it to opengl.

---

### Post by irv on 2010-05-25
Thanks to both Failboat88 and Ringi, This did the trick.
I tried OpenGL and X11 and they both work. I will keep it on OpenGL.
Thanks again 
This problem is solved.

---

### Post by qwerty57 on 2010-05-30
I'll say thanks too!  I had the same problem and this solution works for me too.:)

---

