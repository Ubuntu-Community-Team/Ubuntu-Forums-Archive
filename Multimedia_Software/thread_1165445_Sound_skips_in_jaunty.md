---
title: "Sound skips in jaunty"
date: 2009-05-20
forum: Multimedia Software
---

### Post by jezza1972 on 2009-05-20
I upgraded the wifes toshiba equium l20 laptop online from 8.10 to 9.04. The problem is since upgrading all sounds, regardless of source, skips or gets stuck, rather like a badly scratched cd. Sound is there and have fully working volume control. All was well in 8.10. Can anyone help?

---

### Post by riebling on 2009-05-31
I read on another forum where Ubuntu and pulseaudio folks admit they botched the 'configuration' of pulseaudio in versions 8.x of Ubuntu.  I regret to report that it has not been fully corrected in version 9.  Since upgrading, I, also experience 'skipping' of audio in Rhythmbox and other apps.

It may not be that pulseaudio itself is broken, but simply misconfigured, but it is a crying shame that sound playback has been compromised in a supposed 'upgrade' - these things happen.  I can't wait for a resolution for this, but in the meantime I'm pointing the accusing finger of blame at pulseaudio and very tempted to use harsh language.

Ok I will use it anyway, but only in jest.  Pulseaudio sucks!  - only because it's producing unsmooth playback now, where before it didn't.  In the meantime I'm trying this guide which seems to have helped many people:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

---

### Post by Lantesh on 2009-06-30
I had this issue too in Mint 7 (based on Jaunty).  Here is my reply/fix from another thread:

I found a solution that works, but it's not for the squeamish. Therefore I'm going to keep this guide brief, and if you understand what I'm talking about then you will have no issues. If you don't then well...don't try this. If you do this wrong your system will be hosed.

Ok so what you need to do is edit your sources.list file and add the Karmic Koala repos. Sudo apt-get update and then install the 2.6.30-10 kernel via Synaptic. Don't forget the headers too. While you are in there upgrade ALSA, the Gstreamer codecs, and Pulse Audio. Be very careful what packages you mark for upgrade. Pay particular attention to what packages will be removed, and don't upgrade a package if you think it's going to mess something up. There were one or two things I had marked, but then unmarked. Just be careful and use common sense.

If you've got an Nvidia graphics card: Reboot, and start up in to low graphics mode. Next go back into synaptic and upgrade from the 180 to the 185 drivers. You need the 185 drivers for this kernel. You have to do this. Now go into the Hardware drivers tool in the administrative menu, and enable the drivers. It's only going to show 173 and 180. Just pick 180 and it will enable the 185 drivers.

Reboot and choose the new kernel. Everything should load fine. As long as you didn't mess with your xorg.conf file video should work correctly now that the 185 drivers are enabled.

Finally remove the Karmic repos from your sources.list file and sudo apt-get update again.

If you've got an ATI graphics card I can't help you. I've never used one with Linux.

I can tell you with 99.9% certainty that this fixed all my audio issues. I leave the .1% to chance, because hey you never know.

Good luck. 8)

---

### Post by jstnhickey on 2009-07-05
I have this problem suddenly after a regular routine update.  Sound was working fine last weekend.  Over the week I restarted and I think I did an update and now I have skipping in all sound.  I have tried every tutorial I could find and understand with no luck.  I'm asuming this is a pulse audio problem.  Currently my pulse audio says connection refused... is that the problem?  Any help would be great... I'm really confused as to why this just happened suddenly.  I have had jaunty since it was released.

---

### Post by jstnhickey on 2009-07-05
top, any suggestions

---

### Post by jstnhickey on 2009-07-06
any ideas?

---

### Post by jstnhickey on 2009-07-09
top

---

### Post by Lantesh on 2009-07-16
Yes I have a suggestion.  I posted it before your last 4 posts. ;)  Try it.  It works.

---

