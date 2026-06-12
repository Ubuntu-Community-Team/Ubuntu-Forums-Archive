---
title: "[SOLVED] Rhythmbox failed to create image buffer..."
date: 2008-05-22
forum: Multimedia Software
---

### Post by xjgnsdof on 2008-05-22
When I try to play an mp3 in Rhythmbox under Linux Mint 5 Elyssa Beta, the song doesn't play, and I see the following message when I look at the song's properties: "Failed to create output image buffer of 60x60 pixels"

I can play mp3s just fine in Totem on the same computer, and the album art shows up as usual in Rhythmbox. What's going on? I know I'm using a beta , but I thought that Linux Mint was the media-friendly Ubuntu.

---

### Post by nohandll on 2008-05-23
I am having this same problem. I have a mini-note 2133, it works on my hp tx1000 though with what i think are the same updates. on the mini-note sound will play in all other applications, even if it is the same file that won't play in rhythmbox. I used totem, which uses gstreamer, and it playes the file. I am confused.:confused:

---

### Post by xjgnsdof on 2008-05-24
up

---

### Post by xjgnsdof on 2008-05-25
up

---

### Post by xjgnsdof on 2008-05-27
up

---

### Post by xjgnsdof on 2008-05-30
up

---

### Post by xjgnsdof on 2008-05-31
up

---

### Post by benmhall on 2008-09-18
> **elgilicious said:**
> When I try to play an mp3 in Rhythmbox under Linux Mint 5 Elyssa Beta, the song doesn't play, and I see the following message when I look at the song's properties: "Failed to create output image buffer of 60x60 pixels"

I can play mp3s just fine in Totem on the same computer, and the album art shows up as usual in Rhythmbox. What's going on? I know I'm using a beta , but I thought that Linux Mint was the media-friendly Ubuntu.


Here's a workaround from Launchpad bug: 
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/236201](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/236201)


I, too, had this problem on my HP 2133 with a Via Chrome driver. I can confirm that fiddling with the visualizations did indeed allow me to play MP3s.

Since I don't like visualizations anyway, I found that just disabling them with the gconf editor worked. Here's what I changed:

1) Open terminal
2) Run gconf-editor
3) Go to /apps/rhythmbox/plugins/visualizer/
4) Unchecked Active, checked hidden
5) Close gconf-editor

Now Rhythmbox plays MP3s, no errors.

Very odd bug, very odd workaround. Who'd have thought that enabling visualizations (not even using them) would affect MP3 playback.

---

### Post by xjgnsdof on 2008-10-23
Since my original post, I switched to Ubuntu 8.04, as I wanted to use the newer kernels and didn't feel like compiling one myself. After using your workaround, I can play music in Rhythmbox just fine. Mini-Note users be advised.

---

### Post by 666porcondissaum on 2008-11-29
Thank you very much!

---

### Post by sgarib on 2009-03-04
This worked for me! On HP MiniNote 2133 Also...
Thanks!

---

