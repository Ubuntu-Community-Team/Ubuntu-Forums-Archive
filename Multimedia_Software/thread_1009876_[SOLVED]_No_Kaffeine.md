---
title: "[SOLVED] No Kaffeine"
date: 2008-12-13
forum: Multimedia Software
---

### Post by TheValk on 2008-12-13
I'm using Ubuntu 8.10 and have both Kaffeine 0.87 and Amarok 1.4 installed.
Yesterday, in the spirit of adventure, I added 
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) to my software lists in order to try Amarok 2.0
It installed together with a few dependencies including what appeared to be a some KD4 libraries.
I didn't like it much and so I uninstalled it and reinstalled Amarok 1.4 which is now working well.
Kaffeine, however, refused to start even from the Terminal claiming 'The program 'kaffeine' is currently not installed'
I have uninstalled and reinstalled it from Synaptic and from the 'kaffeine_0.8.7-1ubuntu1~intrepid1_i386.deb', (which claims it IS installed).
I cannot find the kaffeine executable anywhere.
Any help would be much appreciated as kaffeine supports my WinTV dvb straight out of the box.

---

### Post by TheValk on 2008-12-13
Why is it, after you have struggled for hours, exhausted what can seem to be every avenue and then, in desperation, called for help, the darned thing fixes itself!!!!
An update from the backports just came through, I allowed it to update itself and kaffeine sprang back to life.
I now have a working  kaffeine 1.8.7 on KDE 3.5.10???

---

### Post by james_xxx on 2008-12-13
Your having added that repo may or may not be the issue.

Recently an "upgrade" to kaffeine came down from backports/universe, and this may be what broke your kaffeine. I just checked my laptop and discovered that kaffeine will no longer run on it, either. I have never used the repo you mentioned on this laptop.

Kaffeine appears to be horribly maintained in Kubuntu. From my experience, it eventually winds up completely broken at some point in every version of Kubuntu... sometimes sooner, sometimes later. After that happens, it is usually never fixed. If your kaffeine is working, then I recommend ALWAYS being cautious of any supposed upgrade you see for it from the repos.

That being said, it may be possible for you to downgrade to the older, working kaffeine by disabling backports/universe in your package manager, and running "sudo apt-get update && sudo aptitude install kaffeine". (I have not yet tried this myself.)

As for me, I have quit using kaffeine completely, due to the fact that it so often broken. In its place, I tend to use smplayer, vlc and mplayer. It's too bad, as kaffeine is nice when it works.

---

### Post by TheValk on 2008-12-13
> **james_xxx said:**
> 
That being said, it may be possible for you to downgrade to the older, working kaffeine by disabling backports/universe in your package manager, and running "sudo apt-get update && sudo aptitude install kaffeine". (I have not yet tried this myself.)

As for me, I have quit using kaffeine completely, due to the fact that it so often broken. In its place, I tend to use smplayer, vlc and mplayer. It's too bad, as kaffeine is nice when it works.

It's working OK now after the update came through.
I need kaffeine as it is the only media player I have found that supports my Hauppauge WinTV Nova-TD straight out of the box.

---

