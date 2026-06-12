---
title: "Myspace music player not appearing/youtube stuttering"
date: 2009-06-06
forum: Multimedia Software
---

### Post by taytayflyfly on 2009-06-06
I have been unable to find a working solution from google, so I thought I'd ask here. When going to myspace profiles, the music player does not load at all. Is this a problem with flash or something else? Also, youtube videos(maybe others, haven't checked) stutter with computer usage taking place while playing. 

Are there any fixes for these problems? And sorry if this in the wrong section.

---

### Post by fatbyte on 2009-06-06
I am having the same issue. I just switched to Ubuntu last night, trying to get a handle on it.

---

### Post by fatbyte on 2009-06-10
I seriously spent hours trying to figure this out and it turned out what my problem was (or so I think) was that I had several flash programs running which caused them to conflict. After staring at the terminal for hours, slowly losing my mind, I threw in a 

> sudo apt-get remove flashplugin-nonfree gnash
then I reinstalled gnash and it seems to be working fine.

Now on to the next problem

---

### Post by damiga on 2009-06-10
Thanks a lot for the hours you spend on this problem, Fatbyte. Since I have the same issue, I tried the following commands

> sudo apt-get remove flashplugin-nonfree gnash
> sudo apt-get install flashplugin-nonfree gnash

But this did not solve the problem for me.

Is there something I can do to make this player appear? My life depends on it!

---

### Post by taytayflyfly on 2009-06-14
I don't know how to fix this exactly, but I had to re-install Ubuntu and it is now fixed. Not sure what I did differently, but youtube videos go a lot smoother and I can see/listen to the myspace music player.

---

### Post by damiga on 2009-06-14
I did re-install my ubuntu 9.04 on my amd64 but it did not change anything. I do not have any problem with flash movie though. I tried to work something with "Swfdec" but I did not manage to resolve the problem this way either. I guest I will have to wait for an update...

---

