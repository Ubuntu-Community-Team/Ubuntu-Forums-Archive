---
title: "MMSH Protocol? HUH?"
date: 2010-10-27
forum: Multimedia Software
---

### Post by EddieNYC on 2010-10-27
Hi All.

I recently installed Ubuntu on my old man's Gateway netbook. I was going through all the initial steps needed to get the machine running accordingly and make sure everything on it works. So far so good...except:

He listens to a radio station live stream from Colombia, S.A. on a daily basis. I had to make sure that the stream works in Ubuntu. I went to the site and its a no-go.

Ubuntu searches for the appropriate driver/software to be able to stream correctly.

Search returns nothing. I wiped out his XP and would prefer he stick to Ubuntu.

MMSH Protocol is what Ubuntu searches for but there is nothing out there.

I am an Ubuntu newbie so if there is something that can be done to make this work, Please give me the step by step LOL.

For reference, here is a direct link to the stream/player. I'm sure those of you who click it will see what I am talking about in how Ubuntu returns no results for something compatible:

[http://www.caracol.com.co/player.aspx?id=zfE%2bcCh18sD9EE%2bR2mxN1%2bKL2LM5%2fV6ai46xP3IeVFPYRO9bI9aHJAzsylYH4a5Vo0E36eL911o%3d](http://www.caracol.com.co/player.aspx?id=zfE%2bcCh18sD9EE%2bR2mxN1%2bKL2LM5%2fV6ai46xP3IeVFPYRO9bI9aHJAzsylYH4a5Vo0E36eL911o%3d)

Thank you all for your help!!!

---

### Post by mc4man on 2010-10-27
Seems to work ok from the site in in firefox with the totem-mozilla plugin - takes a few to buffer and start playing.

make sure you have totem-mozilla installed and the basic gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

This location also works fine in any player here on maverick and lucid (totem, totem-xine, vlc, ect.
```

mmsh://66.165.172.171/cocarcol?MSWMExt=.asf
```

Or creating a .m3u - Ex. - a text file named caracol.m3u

```
#EXTM3U
#EXTINF:0,Caracol S.A. - CARACOL RADIO
mmsh://66.165.172.171/cocarcol?MSWMExt=.asf
```

---

### Post by jjpcexpert on 2010-12-19
If you want to paste this:```
mmsh://66.165.172.171/cocarcol?MSWMExt=.asf
```
into Rhythmbox, you need to do this first:```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```
In fact, since I have those pkgs, I will try pasting it into Rhythmbox.
I'm English LOL.

---

