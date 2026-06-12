---
title: "DVD won't play."
date: 2010-06-21
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-06-21
Forgive me for being a little drunk, but my dvd's don't play in mythbuntu.

On the backend/front, I think the dvd drive is busted not sure, it kind of reads.

But on another system running 10.04 frontend, dvd's play fine in VLC but not in myth. It works all the way to root menu but fails to play the actual movie, drops me back to myth menu or blanks black. On the other hand "Planet 51" played fine in myth but an older Disney movie "My Favorite Martian" won't play but plays fine in VLC.

I'm not sure whats wrong, I do have xubuntu-restricted-extras, and libdvdread4 installed, but I think I'm missing something.

Anyone have any ideas?

---

### Post by larsolav on 2010-06-21
I don't think you are doing anything wrong as long as at least one DVD plays in Mythtv. Disney adds stuff (in addition to CSS encryption) to their DVDs to confuse computer software like Mythtv from playing them. Some software can play them, but the internal player in Mythtv struggles, and will often quit after the copyright warnings (kinda ironic). I am having a horrible time playing The Princess and the Frog for my kids at the moment...

---

### Post by kja999 on 2010-06-23
Not part of the 'unified' myth solution, but generally you can go round the route of ripping the dvd (Handbrake), or more morally acceptable, buy the fluendo dvd player software. I haven't found a disk this has problems with yet ...

---

### Post by LowSky on 2010-06-23
do you have libdvdcss installed?

you can get it from the medibuntu repos

---

### Post by Mad_Professor on 2010-06-28
haha... Man I was so drunk that I forgot about this thread and it took this long for me to remember it.

I don't remember if I installed libdvdcss, but when I have some time later today I'll check.

---

### Post by guyverix on 2010-06-28
There was a bug post about this problem with Mythbuntu..

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/566003](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/566003)

Update the repo, and use the PPA, or there is a link at the bottom for a fix as well.

---

### Post by Mad_Professor on 2010-07-06
so busy damn it.


libdvdcss was already install.


anyways, I don't want to update with daily builds since I got something somewhat stable, unlike the 9.04/.10 releases. But I do want to use the fix, how do I use a .cpp file?

---

### Post by Rocko262c on 2010-08-30
Hey Everyone,

I am having similar troubles.
 
Mythbuntu 9.10 played DVD's with no problems.

I upgraded to 10.04, installed updates, and even installed libdvdread4 package again ([https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)), but I now have trouble playing DVD's.  Some DVD&#8217;s won't play at all and those that do play returns back to the "Optical Disk" Mythbuntu directory when I try to fast-forward.

I can exit the front end and play DVD&#8217;s just fine via VLC Media Player.

Any help/recommendations?

Cheers,
Rocko262c

---

### Post by Rocko262c on 2010-12-01
Dear Everyone,

I finally enabled Autobuilds by the following:
1.0 Go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
2.0 Click on "Install the Mythbuntu-repos package"
3.0 Opening the deb package and then following the instructions
4.0 Reopen Update Manager and then installed the updates

This did fix the DVD player, but it still has lots of errors.

The video player has the following errors:
-Freezes when fast forwarding or skipping chapters, then exits out of the Mythbuntu Frontend to the desktop or gives an error that says "Video frame buffering failed too many times"
-Can't properly display the Disk Menu when disk is in play and selecting the menu, then selecting "Navigate", then selecting "DVD Root Menu". The menu is flashing and seems to be stretched and displayed twice over itself.

Anyways, I am much happier that I finally took the time to enable the Autobuilds.

Cheers,
Rocko262c

---

