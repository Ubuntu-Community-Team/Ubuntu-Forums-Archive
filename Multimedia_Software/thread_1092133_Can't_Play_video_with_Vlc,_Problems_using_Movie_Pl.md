---
title: "Can't Play video with Vlc, Problems using Movie Player"
date: 2009-03-10
forum: Multimedia Software
---

### Post by kwabena39 on 2009-03-10
Hello,

I am using Ubuntu 8.10, the 64 bit version, on a new computer.  I just got this new computer, and just installed Ubuntu 8.10, 64bit for the first time

When I try to play downloaded youtube videos, I get an error message:

 "No suitable decoder module:
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this."

On my old computer, I was using Crunchbang Linux, based on Ubuntu 8.04, 32 bit (because it was an older computer.)  I had Vlc on that computer, and when I would download Youtube files and play then in Vlc, they would play just fine.

Now, I can't play Vlc at all.  What is going on?  (I'm still somewhat of a noob)


When I try Movie Player, the audio plays fine at normal speed, but the video is sped up, so that the video track doesn't match the audio track, ending early.

---

### Post by sp176 on 2009-03-10
Did the error message seriously say "Unfortunately there is no way for you to fix this", cause that is just creepy.

It sounds like you need to install vlc and its codecs.  Go to system/administration/synaptic package manager and do a search for vlc.

Or you can go to terminal and enter
sudo apt-get install vlc

---

### Post by markbuntu on 2009-03-10
Use Synaptic package manager. get

ubuntu-restricted-extras

The follow the multimedia thingy at the top of this forum for everything else you need.

---

### Post by kwabena39 on 2009-03-11
Yes, the error message did say, "Unfortunately there is no way to fix this.

I just installed ubuntu restricted extras

I just reinstalled "vlc" in synaptic, this time installing ALL plugins that go under the heading of "vlc" (I don't know what they mean, so I just clicked on everything that said "vlc"

Doesn't work.  Nothing has changed.

---

