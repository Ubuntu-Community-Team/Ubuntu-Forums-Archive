---
title: "No candidate version found for vlc ... and ... mplayer"
date: 2010-01-31
forum: Multimedia Software
---

### Post by boondocks on 2010-01-31
This is a **Ubuntu 8.04.4 LTS** desktop. I wanted to install vlc and mplayer, so I did:
 
> sudo aptitude install   vlc   mplayer

It responds with: 
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[COLOR="Blue"]No candidate version found for vlc
No candidate version found for mplayer
No candidate version found for vlc
No candidate version found for mplayer[/COLOR]
The following packages have been kept back:
  language-pack-en
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

How should I resolve this?

---

### Post by chewearn on 2010-01-31
Enable universe and multiverse repositories.  Go to:
Top Panel Menu > System > Administration > Software Sources

Make sure the checkboxes are enabled for universe and multiverse.

---

### Post by boondocks on 2010-01-31
Thanks.
That did it.
VLC and mplayer are now installed.

---

### Post by boondocks on 2010-01-31
On the above [COLOR="Blue"]Ubuntu 8.04.4 LTS desktop[/COLOR], I am trying to view an "event_2.mpg" file.
So I start VLC and open the "event_2.mpg" file.
VLC starts playing the file, the progress slider is moving but there is no video.
What am I missing?

I copied the same "event_2.mpg" file to a 2nd [COLOR="Magenta"]Ubuntu 8.04.3 LTS desktop[/COLOR].
Started VLC and open the "event_2.mpg" file.
VLC starts playing the file, the video is fine.

So the "event_2.mpg" file is fine.
The issue is with the 1st [COLOR="Blue"]Ubuntu 8.04.4 LTS desktop[/COLOR].
What should I do?

---

### Post by chewearn on 2010-01-31
It's probably missing the restricted codec to decode the video.  Click [here]("apt://ubuntu-restricted-extras") to install available non-free codec. plus a bunch of other non-free stuff (Windows fonts, Java, Flash, etc).

Or this command, if you prefer CLI:
```
sudo apt-get install ubuntu-restricted-extras
```

Note:
If you don't want to install so many things at once, you would need to find out the codec required and install those.

---

### Post by boondocks on 2010-01-31
To find out which Codec I need, I did ...

> **boondocks said:**
> I copied the same "event_2.mpg" file to a 2nd [COLOR="Magenta"]Ubuntu 8.04.3 LTS desktop[/COLOR].
Started VLC and open the "event_2.mpg" file.
VLC starts playing the file, the video is fine.

On this 2nd [COLOR="Magenta"]Ubuntu 8.04.3 LTS desktop[/COLOR] in VLC, I clicked on:
View
-> Stream and Media Info ...
--> Advanced Information
---> Stream 0
----> Codec: mpgv

So I assume that I need the "mpgv" Codec.  Correct?
Which package should I install?

---

### Post by chewearn on 2010-01-31
That's probably a mpeg format.  You need to install libmpeg2 and ffmpeg.
```
sudo apt-get install libmpeg2 ffmpeg
```

[http://wiki.videolan.org/VLC_Features_Formats](http://wiki.videolan.org/VLC_Features_Formats)

---

### Post by boondocks on 2010-01-31
** sudo apt-get install libmpeg2 ffmpeg**
returns:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libmpeg2

---

### Post by chewearn on 2010-01-31
Sorry, the correct name is [libmpeg2-4]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libmpeg2")

---

