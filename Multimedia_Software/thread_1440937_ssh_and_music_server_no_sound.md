---
title: "ssh and music server no sound"
date: 2010-03-28
forum: Multimedia Software
---

### Post by atomizer on 2010-03-28
Hi, I just started to play with ssh so I connected to my media-pc with ssh from my laptop. I was always able to start a music player and play the music on the media-pc. Since yesterday the sound is gone. When I do top on the mediapc, I see my player running.
When I open my player locally on the mediapc, I can hear the music.

I think the sound dissapeared after a update, but maybe it dissapeard because I opened a player locally (on the mediapc) I don't know.

The laptop and mediapc both use a fully updated 9.10

update: when I connect from mediapc to laptop, I can play music on my laptop

---

### Post by coolcaseley67 on 2010-03-28
hi

- I see your using Ubuntu Development Release 10:04 make sure your up to date and have back port's and proposed enabled .

- if you move your post to to the ubuntu   Development bit of this forum , more people can help you !!

form your update bit i see it is fix ?? 
hope it helps

---

### Post by atomizer on 2010-03-28
Unforunally I haven't fixed it (have 1 pc ubuntu 10.4 and 2 with 9.10)

alsamixer shows that PCM channel is muted, cannot unmute it (but it gives sound loccaly?) 

I do remember I did gnome-volume-control over ssh, but that never connected.

I had a problem with gnome-panel over ssh, maybe the gnome-programs do not like to be invoked remote.

---

### Post by coolcaseley67 on 2010-03-28
-sounds like one of those anointing  bugs !!!!:o

---

### Post by atomizer on 2010-03-28
Tried to fix it the windows way... so I reinstalled my mediapc (left /home intact).
Still no sound...
But that means it is a configuration file somewhere in my /home

Anyone have an idea?

---

### Post by coolcaseley67 on 2010-03-28
Hi

no i do not but move it to ubuntu testing bit in the forums then more people can help!!!

---

### Post by atomizer on 2010-03-28
Both use 9.10

Found out that the problem is client side... can connect with putty on other pc and make sound.

---

### Post by atomizer on 2010-03-30
reinstalled both systems and still no sound.... going to try mpd

---

### Post by coolcaseley67 on 2010-03-30
hi
 
do you mean [**Music Player Daemon** ]("http://http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki")?.....

---

### Post by atomizer on 2010-03-31
yes thats the one.......

Still figuring out how to get it working (no audio device found)

but found how-to's enough, so in time it will work (and if not, there is the forum ^^)

---

### Post by atomizer on 2010-04-02
It's working.

Mpd on the mediapc, ario on the laptop.

Friend of mine helped a bit. (Gentoo and Sabayon user, so he can dream config files ^^), but he also couldn't figure out why I can't get no sound with ssh connection.

---

### Post by coolcaseley67 on 2010-04-02
so you have problem still ???

---

### Post by atomizer on 2010-04-03
Yes , I can not get sound on my server when I connect with ssh and start a musicplayer.

When I connect with my Windows machine with putty, I get sound.

---

### Post by coolcaseley67 on 2010-04-03
sorry i  can not think of any thing !!!

---

