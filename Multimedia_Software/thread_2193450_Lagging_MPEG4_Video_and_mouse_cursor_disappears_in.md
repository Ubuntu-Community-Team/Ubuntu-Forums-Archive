---
title: "Lagging MPEG4 Video and mouse cursor disappears in 13.10"
date: 2013-12-12
forum: Multimedia Software
---

### Post by Sieges on 2013-12-12
Hello, 

I have a strange bug(s) that affects my system when playing MPEG4 files;
The Default Media Player plays the file, but slow (at half speed I think)
VLC laggs badly (almost stops) and the mouse cursor disappears (I have to Alt+F6 and then Alt+F7 to get it back)
SMPlayer does the same as VLC.

The file is a 1080p 50fps file from a GoPro. A 1080p .mkv file plays just fine in both VLC and SMPlayer - even over the local home network. But I have to Alt+F6 and then Alt+F7 to get the mouse cursor back.

I am running a Sony Vaio Pro Haswell Laptop with 13.10. 

Thanks for any help!

---

### Post by BubbaQ on 2013-12-29
So, it's not a real fix, but I have the same problem with both the 
default video player (Totem) and smplayer. It was driving my kids and my
wife nuts when we tried to play a video and the mouse pointer disappeared.
 
My workaround was to install VLC from the PPA, and set VLC as the default player, 
and not use the other players for now until there is a fix.

[FONT=courier new]add-apt-repository ppa:n-muench/vlc
apt-get update
apt-get install vlc
[/FONT]
I hope it helps.

(I'm running 13.10 on a 3rd gen i7, HP laptop).

---

