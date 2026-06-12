---
title: "Latitude D600 HD playback"
date: 2007-10-07
forum: Mythbuntu
---

### Post by tyce on 2007-10-07
Has anyone gotten HD playback to work on a Dell Latitude D600 from within the mythfrontend?  If so, if you don't mind sharing the howto, I'd be grateful.

Thanks,

ty|er.

---

### Post by tgm4883 on 2007-10-07
HD playback will require at least a 2.5Ghz processor.  Looks like the D600 is only around 1.5Ghz which is way under powered.  Please let me know if the D600 has a faster processor.

---

### Post by laga on 2007-10-08
If it's got an Nvidia VGA card, you might be able to use XvMC.

However, all attempts to help you are bound to fail unless you provide hardware specs of your laptop.

---

### Post by tgm4883 on 2007-10-08
> **laga said:**
> If it's got an Nvidia VGA card, you might be able to use XvMC.

However, all attempts to help you are bound to fail unless you provide hardware specs of your laptop.

I don't think it would work even with that.  I could almost do HD with xvmc and my Athlon XP 2000+.

---

### Post by rusty0101 on 2007-10-09
HD content will play back through the celeron M 1.6 ghz processor, but I think that's dual core. That's what is in my acer laptop and I have had esentially no problems at all playing any HDTV content on that system. (In fact it was anoying that I could play through the intel processor and video chips on that while I was having so many problems with my 2.66 ghz processor in the IBM Netvista box. (single core Pentium 4 I believe, and an earlier intel video chipset as well)

However I am generally in agreement that the 1.5 ghz processor (unless it is known to be multi-core) is probably not going to give you good HDTV video, even with a nVidia graphics card that supports XvMC.

Now if only I could get the s-video out interface to work on that laptop...

---

### Post by tyce on 2007-10-10
Ok, that's what I was afraid of.  I've got it barely working on my XP2100 with XvMC, thought there might be a way to pre-scale the video to make it work on weaker procs.

Thanks for the information guys.

On that note...   Does any one know if either a mac mini or appletv is fast enough to decode HD?

---

### Post by rusty0101 on 2007-10-10
The mac-mini apparently is fast enough. There's a thread on getting that to work here some place, and information related to that. The magic appears to be to select the i810 xorg video driver and set the linearalloc option in /etc/X11/xorg.conf appropriate for the system. People have had good luck at both 16 meg, and 32 meg. But I've not tried it.

---

