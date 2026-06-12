---
title: "Brasero does not burn disks"
date: 2010-07-28
forum: Multimedia Software
---

### Post by genux05 on 2010-07-28
Hi all,

I am trying to burn a DVD (4.7GB) with 1.2GB of data from my Hard Drive, it does not matter is the data is on a ext 4 or vfat directory.

I do keep on getting these messages in dmesg

  675.248890] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  675.248900] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  675.248919] end_request: I/O error, dev sr0, sector 0
[  675.266357] cdrom: This disc doesn't have any tracks I recognize!

which I assume means that I am inserting a blank disk, which is kinder correct :).

But every time I try to burn in either Brasero or via the Nautilus 2.30.1 disk burner part, it does not burn and says that there is not enough space on my disk.  I have tried with allot of different disks and nothing appears to work and they are all blank disks.

Any advice ? have I missed a option somewhere ? 

groups are
genux adm dialout cdrom plugdev lpadmin admin sambashare

Do I need to install anything else ?

Cheers

---

### Post by genux05 on 2010-07-29
just as a update, I am able to burn CD's fine, but DVD+R memorex are not able to  ?

any ideas ?

I used to be able to burn those types of DVDs or from the output of dmesg does not mean that the cdrom is not able to "read" the disk and thus cannot find out that there is nothing on it and also the space that is available to write to ?

---

### Post by genux05 on 2010-07-30
Also just checked and the same DVD's burn fine in Windows, so looks like a problem with either the driver for linux ? or could be that I have not installed all of the programs for this feature to work ?

---

### Post by tommcd on 2010-07-30
Just as a test, try a different brand of DVD if you can.
Also, have you tried using a different program to burn DVDs like **xfburn** or **gnomebaker**?

---

### Post by genux05 on 2010-07-30
Just to say that using the growisofs like so

growisofs -dvd-compat -Z /dev/sr0=brasero-0.iso

works so it is problem with cdrecord since that did keep on coming back with a error with wodim ? tsize needs to be defined with SAO (session at once), how can I make growisofs be the default program to use for a DVD disk ?

---

### Post by genux05 on 2010-07-30
just tried gnomebaker(thanks tommcd) and it works fine!..thanks :)

must just be the way that the brasero is trying to burn with a different application ?

---

### Post by tommcd on 2010-07-30
> **genux05 said:**
> Just to say that using the growisofs like so
growisofs -dvd-compat -Z /dev/sr0=brasero-0.iso
works so it is problem with cdrecord since that did keep on coming back with a error with wodim ? 
Using growisofs would have been my next suggestion.
Wodim is supposed to be just the same as cdrecord, except that it isn't. Cdrecord works much better than wodim does in my experience. But wodim is apparently more free (as in freedom) than cdrecord, so Debian and Ubuntu use it.
> just tried gnomebaker(thanks tommcd) and it works fine!..thanks
must just be the way that the brasero is trying to burn with a different application ?
I have always had bad luck with Brasero. Gnomebaker and even Xfburn have always worked better and been more problem free for me. There must be something different about the back end commands that Gnomebaker and Brasero each use to burn discs.
K3B is still the best CD / DVD recording app imo. But K3B requires a lot of KDE dependencies. This is not a problem on Ubuntu with Gnome, but I like to avoid the extra bloat of all the KDE deps, so I try to stick with Gnome and GTK+ apps in Ubuntu. Ubuntu is bloated enough as it is already.

Glad you had success with Gnomebaker!

---

### Post by HotShotDJ on 2010-07-30
Just a note -- I have NEVER gotten Brasero to burn anything (such as ubuntu-desktop-amd64.iso).  It just sits there with the dialog telling that it is starting to burn the image... forever -- well, until I cancel it.

K3b "just works" for me.

---

