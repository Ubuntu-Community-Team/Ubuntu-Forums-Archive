---
title: "[SOLVED] Restoring smb.conf file"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by ttoolin on 2008-12-26
Is it possible to force the system to download a fresh copy of the Samba configuration file: smb.conf?

I don't have a fatal flaw in it, but I did make some unsuccessful changes to it, and would like to start fresh.  I thought that using the synaptic package manager to 'completely remove' samba would work, but it did not.  While I really know better than to play around without first making a backup, I got lazy, this time.

There are a couple of minor annoyances that have gotten to be a thorn in my side.  One is that my floppy drive disappeared when I installed intrepid (I've tried many of the suggestions in the forums, without luck, yet).

The other annoyance (which I wrestled with all day, yesterday, and never tackled) is I have an HP Laserjet 1000 plugged in and working as a local printer on my ubuntu box.  I want to print to it, over my home wireless network, from a vista home basic box.

Neither one of these are 'must haves'.  But, on the other hand, they should both be possible(?).  I can plug the printer back into the Vista box (it worked there, before), but something tells me that I shouldn't need to do that.  The same with the floppy.  Even though I might only use it once a year, it's installed in the box . . .

The ubuntu box is an older Dell XPS T450 Pentium 3 with ubuntu 8.10 installed.  I have installed the latest HPLIP driver for the HP printer, and as a local printer, the printer works fine.

My next project is a flatbed scanner.  It became instantly obsolete when I bought by vista machine.  The ubuntu docs say it will probably work out of the box.  It's still a scary prospect . . . LOL . . . so much of what I've done with my ubuntu box has involved a lot of tinkering and tweaking.  That's fine. if I keep the right frame of mind, I enjoy it most of the time.  I'm very, very confident that I can switch from windows to linux.  It'll likely be a personal switchover, though.  I'm finding that the system is not user-friendly enough to turn my family loose on it.

Thanks!

---

### Post by cdwillis on 2008-12-26
try this:

sudo apt-get purge samba
sudo apt-get install samba

That might get you the smb.conf file, but I'm not so savvy with setting up your shares or helping with the floppy problem.:)

---

### Post by Iowan on 2008-12-26
[Here]("http://ubuntuforums.org/showthread.php?t=844490") (post #3) is a copy I posted awhile back.

---

### Post by ttoolin on 2008-12-26
> **cdwillis said:**
> try this:

sudo apt-get purge samba
sudo apt-get install samba

That might get you the smb.conf file, but I'm not so savvy with setting up your shares or helping with the floppy problem.:)

Thanks for the idea.  I tried it, and still have the same modified smb.conf file.

As far as the other stuff, there is a lot of forum traffic on both issues, so I'm sure a solution will show up eventually.  My wife mentioned that she's been thinking that she wanted the printer back on her machine (the vista box).  Moving it back to that machine would make the printing problem a non-issue.

My scanner is not supported in linux or MS vista.  Visioneer has abandoned it as end-of-life.  I can't win, at all, this week LOL.

Thanks again for the idea.

terry

---

### Post by ttoolin on 2008-12-26
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=844490") (post #3) is a copy I posted awhile back.


Thank you!!!!!

---

