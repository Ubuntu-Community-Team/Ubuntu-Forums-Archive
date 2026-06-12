---
title: "XMMS and Quickplay controls"
date: 2008-10-08
forum: Multimedia Software
---

### Post by fearful on 2008-10-08
Hello good morning, I'm using Ubuntu 8.04 on my HP DV6000 series. I am using xmms media player when just playing play list or certain files, and rythmbox for music manager. I was wondering how I could get my media or quickplay controls to work with XMMS, the Play, Pause, Next and Previous at the top of my keyboard, any suggestions? Thanks.

---

### Post by fearful on 2008-10-08
Any ideas, I'm desperate I have tried everything

---

### Post by tgalati4 on 2008-10-08
Yes! You can.  But it is not trivial.

For starters, make sure you add the XF86Audio Keys plug-in to xmms.  Try searching for XF86Audio in synaptic.

See if that enables your keys.  If not then you have to dig deeper.

Search my threads on enabling hp multimedia keyboards.  There are a few things to follow:

[http://ubuntuforums.org/showthread.php?t=921870](http://ubuntuforums.org/showthread.php?t=921870)

Good luck.  Post what finally works for you.

---

### Post by tgalati4 on 2008-10-08
Deleted repeated post--strange!

---

### Post by fearful on 2008-10-08
I tried installing the xf86 audio but I failed. It's not in synaptic

---

### Post by fearful on 2008-10-08
Any guidance on how to install this plug in and configuring it? Thanks in advanced.

---

### Post by fearful on 2008-10-08
Well I found a way of installing the plugin, but it says dependency error on libglib1.2, but I do have it to the newest version. Any ideas why?

---

### Post by tgalati4 on 2008-10-09
I'm running Dapper, Feisty and Gutsy on my machines.  It is my understanding that xmms was dropped for Hardy.  You can try xmms2, Audacious or Beep media player.  They may have working multimedia keys.

Some folks have compiled xmms for Hardy but I'm not sure about the plug-ins.

You have experienced "dependency hell" a situation where you are close, but yet so far from getting something to work.  You would need to download xmms source code, headers, plug-ins and compile from scratch.

I like xmms because it is low-overhead and works great on older machines.  But if it is not supported on newer versions of Ubuntu, then you either need to repair it yourself or try a newer player.  There are a lot of players available.

---

### Post by Brakkez on 2008-10-09
Hi,

I have a similar problem. I recently switched to Audacious for playing music files, but I can't find out how to set/configure my hotkeys and multimedia keys.

Is there some plugin needed or another way to configure hotkeys?

Thanks,
Brakkez

---

### Post by cozmicharlie on 2008-10-09
This should install all the dependencies:

```
sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev \libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev \
libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev build-essential make
```

If you need to re-install xmms from source you can follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)

---

