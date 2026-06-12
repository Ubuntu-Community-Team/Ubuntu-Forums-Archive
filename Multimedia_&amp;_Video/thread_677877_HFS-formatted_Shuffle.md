---
title: "HFS-formatted Shuffle?"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Canew on 2008-01-25
Hi:

I'm a relative newbie to Ubuntu (I know enough to be dangerous, but I still need stuff explained to me like I'm a 5-year-old), and I just got a Shuffle for Xmas (my first iPod!), and I'm having some trouble figuring it out.

I've had intermittent problems accessing and/or deleting/adding mp3s to the Shuffle from my Linux box, though I have been able to sync it with my gf's Win XP computer using iTunes.

I've had other problems, too ($#^@#% encrypted iTunes purchases!), but after giving up on Rythmbox and switching to Floola, I think I've identified the problem, but I still don't understand it, and would appreciate any explanation.

Apparently, Floola has trouble recognizing it (if it's recognized at all), and now Rythmbox just crashes when I try to open it with the Shuffle connected. According to Floola's troubleshooting, it seems I don't have read/write permission on it anymore. Not sure if I ever did, or how I lost it, but I've tried several times to change permissions, both through the GUI and in terminal, and confirmed my syntax is correct, but the changes simply aren't there.

An inquiry into the Floola forums indicates it is likely I have "HFS-formatted" my Shuffle, and that I need to consult support for my distro, hence my post here.

Googling the term got me this, on O'Reilly's Mac site:

"If you're adventurous and you try formatting your shuffle as an HFS disk, you won't be able to use it as a music player again until you use iPod Updater to restore it to iPod-hood."

My questions:

1) So to fix it, I need to hook it up to iTunes on my gf's computer again, "restore factory settings," and maybe download one or more songs to it to make sure it works, right?

2) Just what the heck IS HFS formatting? Can someone explain it to me? 

3) How did I HFS-format the Shuffle? I remember taking one somg off the Shuffle by double-clicking the icon on the desktop and manually moving a song into a directory on my PC. Did that do it? Does this mean I can't ever manually move files? That's fine. I guess I can live with that. I just want to make sure.

4) Will my Linux box (Gutsy, BTW) ever work with the Shuffle when it's in HFS format? 

5) On a slightly unrelated note, how do I keep Rythmbox from automatically popping up every time I mount the Shuffle?

Thanks,
Canew

---

### Post by tgalati4 on 2008-01-25
HFS+ is the Mac iTunes formatting.  If you used Windows, then chances are it was formatted as FAT32.  Ubuntu can work with HFS+ if journaling is turned off.  You need the Mac Disk Utility to do this.  It works with an older iPod shuffle, don't have a newer one yet to test with. 

To stop rythmbox from opening, you need to bring up the Multimedia Devices (in a terminal:  gnome-volume-properties) and change rythmbox to something else, or leave it blank.

---

### Post by Canew on 2008-01-25
But I don't use Macs. If it's FAT32 formatted, why would HFS-formatting even factor in, or would it? Man, I just want this thing to WORK!

---

