---
title: "Video player problems"
date: 2008-11-05
forum: Multimedia Software
---

### Post by theicescorpion on 2008-11-05
I have a strange problem. I am new to ubuntu and i fresh installed 8.10. I installed VLC Media Player. Then I updated the system as requested by the "update manager" (i'm new and i don't know the exact name). Now i don't know what the problem is everytime i want to play a media file the player (vlc or any other player) automatically closes. Can someone plese help me...

---

### Post by Vl@d on 2008-11-05
Try changing the video output on the options panel. 

PD: Run vlc fron a terminal and post what it displays ;)

---

### Post by theicescorpion on 2008-11-05
and how do i do that? i'm really a noob at linux. It is my 1st time i'm using it.

---

### Post by Vl@d on 2008-11-05
The video output can be changed at the vlc options, i have not it here at the momment so i don't really remember aswell...

To your second issue, open a terminal (Applications > Accessories > Terminal) and write vlc . If you see any error there paste it here.

---

### Post by malleus74 on 2008-11-05
If I like a video on youtube, etc, I use videodownloadhelper to get it. I was able to watch them using VLC with Hardy perfectly. I have the exact same problem as the original poster.

I'll try the fix tonight... I think it might have something to do with the audio, too, but I'm not even getting a preview in nautilus anymore.

I was able to get the video to preview using another program... "a" something... avidemux ? idk, slept since then and stuck using Windows 2000 at work, but the audio errored.

---

### Post by theicescorpion on 2008-11-05
mdb:13, lastbuf:0 skipping granule 0
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

---

### Post by malleus74 on 2008-11-05
> **theicescorpion said:**
> mdb:13, lastbuf:0 skipping granule 0
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  **BadAlloc (insufficient resources for operation)**  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

 I'm can't get to my Ubuntu system until tonight, but this sounds EXTREMELY similar to what I saw when I ran VLC from a terminal.

---

### Post by malleus74 on 2008-11-05
Anyone see this problem or know what to do?
The player literally closes in a second or two after you open it.

---

### Post by malleus74 on 2008-11-05
I've been bored at work today so I started researching this problem in a couple different ways, and apparently the BadAlloc error is known.

Like stated in a post above, you are supposed to switch the output to x11 in vlc according to the other posts. A lot of people seemed to get a flicker effect going after they did this. Then they were told to enable the restricted drivers for their graphics card to fix that. Only a few people had problems after that.

From [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357) :

o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

---

### Post by theicescorpion on 2008-11-06
Tried and still not working

---

### Post by malleus74 on 2008-11-06
The fix worked perfectly for me last night with VLC. I still have a bit of a memory lag, so I'm thinking I'm still going to have to add the restricted ati drivers.

Apparently this is a known bug with x11. You can do a search for BadAlloc and you'll get hundreds of posts.

At the moment your output in the player is X11? 

Have you added the restricted drivers for your video card? 

If you've done both of those, I think I saw something you could do with x... I'll do a bit more research on it if no one beats me to it :)

---

### Post by malleus74 on 2008-11-07
Here's the bug, and it talks about a possible fix.

[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/269357](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/269357)

Let us know if changing this helps. :)

---

