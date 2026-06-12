---
title: "Netflix w/o Emulator?"
date: 2010-07-10
forum: Multimedia Software
---

### Post by uRabbit on 2010-07-10
Using Oracle VM to run XP so I can watch Netflix. However, the VM doesn't go completely fullscreen, unfortunately. So this just doesn't cut it for watching movies. 

Anything else?

---

### Post by VeeDubb on 2010-07-10
Well, you've got a couple options.

1. Use a VM that supports fullscreen or a "blended" mode of some kind.  I know right off the top of my head that both the free VMware player and several of the open source VM's can do this just fine.  My personal favorite is VMware player.  It seems to do a much better job with netflix, which is just about the only thing I use it for.

2. Install MediaMall's "PlayOn" server on your windows VM, and use it to stream your netflix queue.  Any media app capable of playing UPnP streams will work.  Unfortunately, you'll be stuck at the lowest quality setting for netflix.

3. Wait.  Despite early reports to the contrary, it looks like netflix isn't planning on any immediate migration to HTML5, but they may down the road.  It's also possible that they could change from using microsoft's DRM to something else that might be more linux friendly.  Meanwhile, moonlight is getting better and better, and may eventually be able to play netflix provided that MS decides to share their DRM blob.

4. If we're talking about an HTPC, you could always get a roku, Seagate Theater HD+, or Western Digital HD Live + to sit next to it for netflix streaming.

---

### Post by uRabbit on 2010-07-10
Mkay, so I'll just add Netflix as another reason to boot into XP. >.< Haha

---

### Post by VeeDubb on 2010-07-10
> **uRabbit said:**
> Mkay, so I'll just add Netflix as another reason to boot into XP. >.< Haha

If you're willing to use a VM in general, why the reluctance to switch to a more powerful VM that is also completely free?

---

### Post by james_xxx on 2010-07-10
I assume that by Oracle VM, OP is referring to VirtualBox.

If that is the case, why is it that you cannot set it to full screen? I have run VirtualBox on a number of different machines with all manner of specs, and have never had that problem.

Firstly, you need to make sure that you have the 'Guest Additions' installed and up to date for the guest OS. Secondly, press the right control key + f. That should make the desktop of your guest OS go completely full screen. 

I am not sure how VMware player would supposedly be more powerful. IMHO, you will be much happier if you stay with VirtualBox, but to each his own.

There is also a blended mode. Just look at the menu bar when you open a VM, and all of this is very clearly explained there.

---

### Post by uRabbit on 2010-07-10
Full screen mode creates a box that is not as wide as my monitor, and won't stretch any further, but the tops and bottoms become inaccessible.

---

### Post by erilidon on 2010-07-10
Kinda of off target here - but I have been hoping on an update to moonlight, the firefox plugin for silverlight.

They did an update today but still no such luck. I am also using the user agent switcher to make the netflix server think I am running firefox on windows.

I get further this way, that is past the you aren't using a supported OS screen. But the video still does not start... So I am still using a VM (virtual box) for that reason alone, and I am able to get fullscreen with the guest additions plugin installed.

> 2. Install MediaMall's "PlayOn" server on your windows VM, and use it to  stream your netflix queue.  Any media app capable of playing UPnP  streams will work.  Unfortunately, you'll be stuck at the lowest quality  setting for netflix.Can VLC do this as well?

---

### Post by VeeDubb on 2010-07-10
> **erilidon said:**
> Can VLC do this as well?

I'm pretty sure it can.  If not, there's about a million other apps that can.

---

