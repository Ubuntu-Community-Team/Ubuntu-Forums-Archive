---
title: "DVD Playback HOWTO"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by prodezigner on 2007-07-26
This HOWTO is my first, doing this all from memory as I've tried EVERYTHING and well... I've searched high and low, mixed some answers and came with one to make DVD playback out of box pretty much happen with Feisty Fawn.

First, you need to make sure these libs are installed:
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

In a terminal type in: sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3

Out of box my install needed to update one of those, on your install it may be different.

Under the Applications menu, click on Add/Remove

On the drop-down menu 'Show' you'll want to select "All available applications" then do a search for XINE.

Out of the box, Feisty Fawn comes with Totem (aka Movie Player), but is missing codecs, etc. so you'll want to install from the list 'Xine extra plugins' as well as a program called 'Movie Player Totem (xine backend)

This is a replacement for the default, this is a COMMUNITY program, but functions no differently while bringing features of XINE to the table in this program. When you install it, it will remove the default version and replace it with this version.

THERE YA HAVE IT! If these steps don't work for you, please post your responses here and I'll correct the posts, as I've added repos and will hafta drudge those up.

---

### Post by prodezigner on 2007-07-27
Giving this a bump.

Can ANYONE verify this works correctly for me so I can make revisions to it?

---

### Post by psoplayer on 2007-07-27
This got things working for me in 6.04. Thanks a lot!

---

### Post by prodezigner on 2007-07-28
Awesome, glad I could help.

Knowing I'm using *The Fawn* and it worked with an older distro it's more than likely fail-safe for 7.04.

---

### Post by RomeReactor on 2007-07-28
Hi. You would also need to install **libxine1-ffmpeg** in Feisty. **libdvdcss2** can be found through the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu"), which I think provides a more up to date version than the one you can install by running the script in **libdvdread3**'s folder:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
That is the script you run if you have Edgy instead of Feisty; for Dapper, run this script after installing **libdvdread3**:
```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

=============================================================

So, to enable DVD playback in Feisty, run:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the Medibuntu repository; then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to add the repository's gpg key and update the package manager's information on the repositories; and lastly
```
sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine libxine1-ffmpeg
```
to install the necessary packages.

---

### Post by prodezigner on 2007-07-28
Yeah, I just recently added Medibuntu, forgot about that, like I said, I don't know if some or all of those files were from the standard Ubuntu repos or other added repos.

Thanks for correcting me and clarifying more :)

---

### Post by ckaya on 2007-07-28
This still doesn't work for me. Having same problems with [http://ubuntuforums.org/showthread.php?t=510695&highlight=dvd](http://ubuntuforums.org/showthread.php?t=510695&highlight=dvd)

---

### Post by The Judderman on 2007-07-30
Worked beautifully for me (with the medibuntu repos...) in Feisty. Cheers for that!!!!!

---

### Post by nikoPSK on 2007-12-01
In gusty, it says is cant find:

libdvdplay0

---

### Post by nikoPSK on 2007-12-01
Nevermind, I got it working.:)

---

### Post by bluedragon436 on 2007-12-01
I have this same issue...how were you able to fix it???  I am using VLC player, which has no issue with playing any DVD's thus far.  I don't mind using VLC to play, but would rather fix whatever I need to fix to make it work normally...

---

### Post by OzDad on 2007-12-01
But HOW did you get it working?
I also am using Gutsy Gibbon and it cannot find libdvdplay0 (tried zero and alpha O)

---

### Post by Znort_Ubern00b on 2007-12-01
followed all instructions and get message saying

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

even though i get this in terminal

 sudo /usr/share/doc/libdvdread3/install-css.sh
--10:33:41--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-RU5799/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178       134.59K/s             

10:33:41 (134.41 KB/s) - `/tmp/dvdcss-RU5799/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu2+build1 to 1.2.5-1.
(Reading database ... 149883 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using .../dvdcss-RU5799/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...


Ok scratch that...all i did was eject the dvd put it in again and it works...ty for all the info peeps.

---

### Post by ataxicwolf on 2008-01-10
yes!

thanks so much for this man!

I got it working, took like 5 seconds. (I'd tried a few other guides and none seemed to work)

Thanks again!

---

