---
title: "newbie - no audio at all in mythbuntu...plz help"
date: 2009-07-12
forum: Mythbuntu
---

### Post by hayt.atreides on 2009-07-12
Please help.  I have searched tons of forums to try and fix my problem, but to no avail.  I am a first time linux OS user, and really want to get this to work.  I do not get any sound at all in MythTV or in any app in mythbuntu.  If i try and open a file in MPlayer, i get the AO: [pulse] connection refused error.

At one point i followed instructions to remove pulseaudio, and MPlayer then gave me the AO: [alsa] connection refused error.

I have mythbuntu 8.10 installed (if i try and install 9, i get a blank screen for mythTV with the pre-scaling box in the middle, which is also blank, and it just sits there.....very annoying).   

I have reinstalled mythbuntu 8 twice, and version 9 three times.  i have all the updates to the OS.  I tried putting in a sound card (was originally using the integrated sound on my mobo), but that had no effect.  I have messed with so many settings, that i eventually FFR'ed the system.  Still no luck.

my sys specs are as follows:

Mobo: MSI K7N2 Delta2 with nvidia nforce 2 ultra 400 /igp chipset
AMD Athlon XP 3.2 GHZ
1 gig ram
120gig HDD

I have no idea why i do not get sound....

If anyone can help me, I will gladly name my first born after you!!!!!

thanks!

---

### Post by Andrew U.K. on 2009-07-12
i know where you are coming from, the frustration can be almost to much.

I get no sound with either 8.10 or 9.04 but 8.04 works. No idea why, you would think with the later version things like audio would work.

Good luck and hang in there,  I have a half finished system and enjoy it.

---

### Post by trevs.bronco on 2009-07-13
I have had the same issue. in my instance it turned out to be the nvida drivers iirc it was the 177 one that didn't work. when I down graded to the previous version, 173, the sound came back. 


I also noticed a post with a fix for the blank screen on install issue which i can't seem to find now, but iff you search, the answer is out there for it. one solution may be to try a different display for thr initial install.

hope this helps,

Trev

---

### Post by auferret on 2009-07-14
I feel your pain. I started my Linux voyage with Linuxmce 7.10 and my sound worked but other things did not. I then tried Mythbuntu 8.04 and 8.10 and the other problems went away but so did my sound. When 9.04 was released, I started over with the desktop version and my sound was back. Then I installed Mythbuntu Control Centre and it went away again. Apparently that program has not changed since 8.04.

In my experience so far, it appears that there are many hardware and software issues that can cause this. I found this guide that helped me troubleshoot my problems. 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I also saw this one today that looks promising.
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by hayt.atreides on 2009-08-05
I solved my issue.  It turns out that my desire to have some rather unique hardware for my old gaming system several years ago meant that the drivers for mythbuntu just would not work.  I ended up changing my sound card and video card, and *poof* it all works now.


thanks,

Hayt

---

### Post by HW_Hack on 2009-08-05
> **hayt.atreides said:**
> I solved my issue.  It turns out that my desire to have some rather unique hardware for my old gaming system several years ago meant that the drivers for mythbuntu just would not work.  I ended up changing my sound card and video card, and *poof* it all works now.


thanks,

Hayt

Great to hear it - with Linux in general its best to stay away from exotic HW or mobos. In your case I was going to say find or borrow a basic SoundBlaster card ...

---

