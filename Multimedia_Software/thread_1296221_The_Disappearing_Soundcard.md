---
title: "The Disappearing Soundcard"
date: 2009-10-20
forum: Multimedia Software
---

### Post by realistik on 2009-10-20
No, it's not the title of some 21st-century Hardy Boys book, it's an actual, real problem I've encountered and I figured my last resort is a forum post!

I recently installed Xubuntu Karmic beta and set it up. When I did, I had no sound from the onboard sound (VIA 8237 chip) which is odd because all the pre-9.x versions of ubuntu/xubuntu I'd installed on this box before it worked fine out of the box. Anyway, I hassled with it for a few days and finally gave up and stuck a Soundblaster X-Fi card in it. When I rebooted with the onboard sound disabled, the Creative card worked like a charm.

Last Thursday night I was watching some Blender tutorial videos on here and everything was working fine. I turned off the monitor when I was done and when I started using the system the next day, there was no sound. This is without any updates being installed, without a reboot, just the system sitting idle overnight. When I clicked on the speaker in the notification area to get to the mixer and see what was going on, it gives me the "GStreamer was unable to detect any audio devices" dialog.

Since then I've installed all the updates that have been available, rebooted (and cold-booted) several times, and still I can't figure out why my sound disappeared. The card is almost new, and I'm pretty sure it's not dead. The snd-ctxfi driver errors out during boot or when I modprobe it. The card is still listed in lspci -v.

I've been running at least one linux box since about 1996, although I mainly use Windows. Earlier experiences trying to get X-Free-86 working right turned me off to X-based Linux for a long time, but I've been really happy with Ubuntu/Xubuntu since I first tried them. Anyway, long story short, I don't really have any experience troubleshooting things like this and would appreciate any help I could get. I was a little hesitant to switch from Januty to Karmic, but aside from not having sound, I'm having a really good experience with Karmic so far, and only expect it to get better.

Thanks for your time!

---

### Post by duanedesign on 2009-10-20
Sounds like their might be a problem associated with sleep/resume. I didn't come across anything for your particular setup that jumped out at me. There are a few good sound Troubleshooting guides that might help.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by realistik on 2009-10-21
Thanks for your reply. While I was unable to figure out what happened with my X-Fi, I did manage to finally get the onboard Via 8237 working after some strategic jumpering. I appreciate the ilnks, I think I actually learned something yesterday trying to figure that out. :)

---

