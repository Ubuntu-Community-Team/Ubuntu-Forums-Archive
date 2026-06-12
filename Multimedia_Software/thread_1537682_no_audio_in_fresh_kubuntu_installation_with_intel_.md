---
title: "no audio in fresh kubuntu installation with intel HDA card (cannot un-mute?)"
date: 2010-07-23
forum: Multimedia Software
---

### Post by spagan on 2010-07-23
Hi guys,
 shortly: after a fresh install of kubuntu lucid (64bit) i can't hear anything either from speakers or headphones.
 I attach to this post the `ubuntu-bug alsa-base` output to give you few details on my hardware and configuration.
 One thing that could be related is that I cannot make the mute/unmute switch work.. or better I do not see them in kMix and alsamixer. I attach a screenshot of alsamixer to show you that (no box with 'MM' or 'OO' I was familiar with is present). The result is that I'm not sure channels are properly un-muted. Of course I tried to just blindly unmute but it did not work.
 Do someone of you have any idea of what is going on?
Any help is greatly appreciated. 
Since I'm not sure if this is a bug or just my fault I wanted to post here before opening something on launchpad and see if someone (and I'm sure you will ;) ) have good suggestions.
 Thanks a lot!
Simone

P.s. of course let me know if you need any other info!

---

### Post by spagan on 2010-07-25
Problem solved thanks to the launchpad guys. 

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/118863](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/118863)

Upgrade to alsa 1.0.23 following this link:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Simone

---

### Post by tore on 2010-12-01
That link works well, but it is a tedious upgrade run to carry out as soon as the kernel has got any minor update.

When will Alsa be upgraded in the repository for Kubuntu 10.04? 

Please upgrade to Alsa 1.0.23 ! How do we initiate an update? 
Why not updated already after almost half a year?

---

