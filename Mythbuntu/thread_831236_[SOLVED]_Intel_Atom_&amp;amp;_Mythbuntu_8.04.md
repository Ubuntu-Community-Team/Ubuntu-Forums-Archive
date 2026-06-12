---
title: "[SOLVED] Intel Atom &amp;amp; Mythbuntu 8.04"
date: 2008-06-16
forum: Mythbuntu
---

### Post by xykevinr on 2008-06-16
Hi All,

has anyone got an Intel Atom to work with 8.04 ?

I recently bought a D945GCLF board, with a 1.6HGz Atom(230) on it - seemed ideal for a cheap frontend.

New install of Mythbuntu 7.10 worked fine. Doing all the upgrades / updates available makes it able to work with by 8.04 backend - all was good.

Upgrading the above to 8.04 LTS causes a problem when re-booting - I get some kind of modprobe error.

A new install of 8.04 from distro CD (yes I checked the disk)cases a similar problem (modprobe error) when trying to boot following the install.

Just for a laugh, I tried using the diskless frontend feature in 8.04. On the backend I built a boot image on a pendrive. When booting on the frontend - guess what - modprobe error.

I've done quite some google-ing but cant find anything - might be i've not worked out the best keywords though.

(obviously I can post more details if anyone can help).

thanks for your time... Kev

---

### Post by mrsteveman1 on 2008-06-16
If you can, post the specific errors you are seeing.

It might also help if you could post the entire kernel log (dmesg) in a pastebin like [http://code.bulix.org/](http://code.bulix.org/)

---

### Post by encode on 2008-06-16
I also have the same thing happening to me, but I'm at work currently and I didn't write down the error message.

Both Xubuntu and Ubuntu 8.04 failed, not surprisingly.  I was able to successfully boot an opensolaris live cd called [Milax]("http://www.milax.org/").

I hope there is a relatively easy solution to this.

---

### Post by encode on 2008-06-16
There's a [thread ]("http://www.linuxquestions.org/questions/linux-kernel-70/intel-atom-d945gclf-kernel-problems-646190/")on linux questions that sounds promising regarding this issue.  I'll have to give it a try when I get home.

Basically, disable the onboard ethernet in BIOS, and booting should work fine.

Edit: Another thread [here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg879194.html").

---

### Post by kogz on 2008-06-17
And another: [http://ubuntuforums.org/showthread.php?t=812817](http://ubuntuforums.org/showthread.php?t=812817)

---

### Post by superm1 on 2008-06-17
A lot of the Atom based boards have realtek controllers for their ethernet.  Try grabbing a hardy daily image as there are a few fixes in the 2.6.24-19 kernel included in the daily images.

see cdimages.ubuntu.com

---

### Post by superm1 on 2008-06-17
Also, you really are better off using an lpia kernel on these.  We haven't rolled lpia disks as of yet, but we can see how difficult it ends up being.

---

### Post by deltateam2 on 2008-06-18
> **encode said:**
> Both Xubuntu and Ubuntu 8.04 failed, not surprisingly.  I was able to successfully boot an opensolaris live cd called [Milax]("http://www.milax.org/").

Milax booted?  Did the new ethernet card work?  If it does, I guess that means it works with current nevada?  If so, my zfs nas dream is about to begin. :guitar:

Does this board supports WOL?

---

### Post by xykevinr on 2008-08-13
These problems just go away with 8.04.1

cheers, Kev:guitar:

---

