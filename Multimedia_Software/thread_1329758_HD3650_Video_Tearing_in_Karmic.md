---
title: "HD3650 Video Tearing in Karmic"
date: 2009-11-17
forum: Multimedia Software
---

### Post by JCoster on 2009-11-17
Hi guys, I'm running an ATI HD3650 card in my Sony Vaio FW-31ZJ laptop and have experienced problems with video tearing ever since installation.  Even with Compiz and desktop effects turned off it is unwatchable.  This occurs when watching full-screen flash videos (YouTube, iPlayer, etc.) and also in VLC (x11 as codec).

I've tried just about everything I can think of and just can't seem to get anywhere.  What is going on?  Is it a problem with settings or just an incompatibility? 

Also, just as a quick question, but what ATI driver is used in Karmic?  When would it be beneficial to change to the proprietary drivers?

Cheers,
JC

---

### Post by JCoster on 2009-11-19
Bump

---

### Post by JCoster on 2009-11-22
(for what it's worth, I hate myself for doing this too...) 

bump.

Also though, it may be worth noting that my installation was originally jaunty and then have been running karmic since alpha 4 so i'm wondering if something got screwed up along the dev process (although it has to be said, i did have video tearing with jaunty).

EDIT: and one more thing, it still happens when using Gnome-Shell so therefore i'm ruling out a Compiz issue?

---

### Post by Zibex on 2009-11-22
I see Ubuntu still has the video(window moving) tearing problem :(

After spending few hours with compiz i noticed something strange: tearing disappears if in conpiz-config i use benchmark plugin.

Here are the steps that i did:
- Fresh 9.10 install
- Installed suggested drivers for ATI 3650 
- Installed compiz-config settings manager

- Checked Normal/Extra in System - Preferences - Appearence - Visul Effects
- In Compiz-Config only checked "Benchmark"

Now try to watch videos or play with windows with the feature turned on/off (default keyboard shortcut to turn on/off is - Super+F12)

On ati 3650 card if the benchmark is running there is absolutely no tearing. Any ideas how to make ubuntu run smooth without that feature turned on? :)

---

### Post by JCoster on 2009-11-27
Yeah, this seems to work.  This is incredibly odd.  Surely there's another way around it?  It's the only thing keeping my dual-boot setup from just Ubuntu.

---

### Post by JCoster on 2009-12-03
Ok well turns out I was wrong in the original post description- with Compiz turns off full-screen BBC iPlayer and other videos seem to work fine. 
For now, I'm going to test solely with iPlayer as it works without Compiz.
With Compiz turned on (even with Benchmark running i'm sorry to say) I still get tearing, but it turns out that the frame rate drops to less than 25 when video is on full screen?
I'm not really sure where to go from here, so any advice is greatly appreciated.

---

### Post by siabost on 2009-12-07
Karmic running on AMD Athlon 7750 Dual-core/Onboard nVidia graphics.

It does seem to be a Compiz thing. Changing Window Manager from Compiz to Metacity via Compiz Fusion Icon cures the tearing for me on videos at least.

Hope the bug gets sorted as it's a pest having to switch.

;)

---

### Post by mbuller10 on 2009-12-08
Okay I had the exact same problem with the Benchmark plugin fixing it and stuff, here's what I did, open up the Compiz settings manager and check sync to Vblank and also check Unredirect Fullscreen Windows, have and Nvidia 105G M

---

### Post by JCoster on 2009-12-22
So none of this has actually worked for me so far.  

Still having terrible video tearing whenever Compiz is enabled and even slight tearing when effects are off.

Is there no one else having this problem?  It really is the final thing preventing me from removing my Win7 partition..

---

### Post by JCoster on 2009-12-22
Quick update- now using ATI driver 9.12 and still no improvement- getting a Compiz benchmark of 20fps whenever viewing iPlayer in fullscreen.

---

### Post by Melcar on 2009-12-22
For video playback, set your player to use opengl instead of X11/Xv and set vsync in your Catalyst Control Center to always on.

---

### Post by JCoster on 2009-12-22
Thanks for your reply, however I've set it to OpenGL in VLC and I still get tearing even with it always waiting for v-sync.  Also, how would I get video tearing to fix in flash fullscreen videos?

Cheers,
JC

---

### Post by Melcar on 2009-12-22
Are you forcing vsync in AMDCCCLE to always on?  If you're using Compiz you need to also set vsync there.  For flash videos there isn't a way to do it; we will have to wait until adobe allows you to use opengl rendering for their flash videos or ATI learns how to apply vsync to Xv on their drivers.

---

### Post by JCoster on 2009-12-28
Yep- still no luck.

I even get a bit of tearing with Compiz turned off.  I don't understand why at all.

I'm attempted to try a reinstall and see if this works with nothing installed- afterall I did upgrade to Karmic from Jaunty.  Is there any chance this would make a difference?

---

### Post by JCoster on 2009-12-29
Ok so i've just done a complete reinstall of Karmic from scratch.  The only thing I have installed is Catalyst 9.12, the xserver-no-backfill patch and VLC- same problem, but **only** with desktop effects enabled.  Without any desktop effects, I get no tearing in iPlayer or VLC (even with iPlayer HD).

With SMPlayer and effects at 'normal', I get a framerate of 60fps which is correct, however, I still get tearing so I'm not sure whether it's to do with the frame rate (obviously in VLC where my frame rate fullscreen is 40fps this is the main issue).  

Cheers,
JC

---

### Post by JCoster on 2010-01-08
So, still not got anywhere with this.  Would the xorg-edgers PPA do anything to help this?  I read about it all the time on this forum but have had a hard time finding out information about it; what's it used for?  does it provide 3d support?

Cheers,
JC

---

### Post by Zakhafr on 2010-01-10
> **mbuller10 said:**
> Okay I had the exact same problem with the Benchmark plugin fixing it and stuff, here's what I did, open up the Compiz settings manager and check sync to Vblank and also check Unredirect Fullscreen Windows, have and Nvidia 105G M

Thanks, this worked for me (I had the problem also with VLC + Karmic/Compiz + **nVidia** 8600M GT).

For those who won't find it is under :
**General Options** (Options générales)
- Unredirect fullscreen thing is on the first tab (**General**)
- Sync to VBlank is on the second tab (**Display parameters** / *Paramètres d'affichage*)


*Note: the english name I gave for the tabs might be a little bit different as I just guessed them (I'm running on a French interface)*

**@JCoster** and others ATI users, we had the same report several months ago (at the time of Intrepid) on the French forum. We saw that the ATI interface lacks the critical ***Sync to VBlank*** parameter. This is obviously what was triggering the problem (easy to understand when you know what Sync to VBlank is!). So do you have this parameter now ?
On nVidia settings it has been there for long.
With no Sync To VBlank, you can have as many FPS you like you'll still have tearing. Of course, the more FPS the less tearing is noticeable... but it is still there.

---

### Post by markbuntu on 2010-01-11
In compiz config settings manager/utility/workarounds make sure you have the following checked

Legacy full screen support
Java window fix
AIGLX Fragment Parameter Fix
Fix screen updates in XGL with fglrx
Force synchornization between X and GLX

---

### Post by JCoster on 2010-02-11
After finding no resolution to this program in almost a year, I'm shouting from the hills...  Just upgraded to Lucid A2 and guess what..:

[SIZE="5"]IT'S FIXED![/SIZE]

Genuinely, I couldn't be happier.  I can now **FINALLY** delete Windows 7, and all I can say is good riddance.

Now I just have to hope that no Lucid updates bork up my install or my perfectly non-tearing video!

Got to love alphas...

Cheers for all your help guys, much appreciated.

JC

---

### Post by chronniff on 2010-02-12
Hey what's up, I have one of the new HD5770 cards and I too have been having video tearing issues.  For me it was mostly when it came to playing any kind of video content that there seemed to be tearing no matter what I did, not so much in the 3d realm though.  I seemed to have fixed it with the unredirect fullscreen windows option being checked in compiz settings.  the sync to vblank option in compiz and in the control center never worked, despite that being the only advice I ever heard.  I am truely glad to hear that the issue might be fixed altogether in the next release...its very encouraging

---

