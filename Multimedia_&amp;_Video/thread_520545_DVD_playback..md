---
title: "DVD playback."
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by dioon on 2007-08-08
Followed the sticky "Enabling multimedia in Fiesty"got as far as" apt-get update",got message in Terminal "E: type"Medibuntu" is not known on line 40 in source list /etc/apt/sources.list.
What am I not doing right,thank's for any help.

---

### Post by nichipet on 2007-08-08
Can you give the output of:

```
cat /etc/apt/sources.list
```

Then we can look at line 40 of your sources list.

---

### Post by dioon on 2007-08-08
derek@derek-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted univ

---

### Post by nichipet on 2007-08-08
Is that the entire sources.list file? I don't see Medibuntu in there at all, nor are there 40 lines.

---

### Post by dioon on 2007-08-08
derek@derek-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
Medibuntu - Ubuntu 7.04 "feisty fawn"
Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free


derek@derek-desktop:~$ 

Sorry my mistake.

---

### Post by nichipet on 2007-08-08
> Medibuntu - Ubuntu 7.04 "feisty fawn"


That's line 40, I believe (when it happens with no # at the beginning, there is another a few lines later that does have ##). Try adding a # or two (doesn't matter how many) to the very beginning of that line. That will comment it out so the update won't look at it.

---

### Post by Bablefish on 2007-08-08
Make it easier on yourself Google Medibuntu and head on over to their site and look for the Terminal Command Lines to install Medibutnu that way. Believe me it is a hell of a lot easier.

---

### Post by nichipet on 2007-08-08
It will be a moot point to do that now. The sources.list already has Medibuntu in it and I think just the one line needs commenting out.

---

### Post by dioon on 2007-08-08
Nichipet how do I put # in front of the said line.
And Bablefish your suggestion bronght me straight back to my original problem.

---

### Post by RomeReactor on 2007-08-08
Hi. Open a terminal (Aplications->Accessories->Terminal) and enter this:
```
gksudo gedit /etc/apt/sources.list
```
when the text editor with the file opens, go near the end to the lines in bold:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
[B]Medibuntu - Ubuntu 7.04 "feisty fawn"
Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)[/B]
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
and add a **#** at the beginning of those two lines. Save the file, close the text editor, and enter in the terminal:
```
sudo apt-get update
```
Also, you have a duplicate entry of Medibuntu; if you notice, the last eight lines of the file are the two entries, four lines each. This is how a single entry should look like:
```
# Medibuntu - Ubuntu 7.04 "feisty fawn"
# Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
```
It would probably be okay to leave both there, but it would be best to remove one of the two.

---

### Post by dioon on 2007-08-08
Thank's everybody have installed Libdvdcss2,but still cannot play DVDs,it say's  I'm still missing some codec's.

---

### Post by nichipet on 2007-08-08
Which program did you try to play the DVD with and did it say which codecs are missing?

---

### Post by dioon on 2007-08-08
The program was Totem and no it did'nt say which codec's were missing.

---

### Post by RomeReactor on 2007-08-08
Are you using **totem-gstreamer** or **totem-xine**? If you're using totem-gstreamer, then see if the following packages are installed:
```
sudo apt-get install libdvdread0 libdvdcss2 libdvdread3 libdvdnav4 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-ffmpeg  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ugly-multiverse
```
If you have totem-xine:
```
sudo apt-get install libdvdread0 libdvdcss2 libdvdread3 libdvdnav4 libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by dioon on 2007-08-08
Installed all except Libdvdread0,said it could not find,still cannot play DVD's.

---

### Post by nichipet on 2007-08-08
That should be libdvdread0 with a zero, not an O. Did you do it with an "o" or a zero? And I think if you have the right repositories in your source.list, it should find libdvdread0, it's a fairly standard file when enabling multimedia.

---

### Post by dioon on 2007-08-08
I copied and pasted it from "RomeReactor's thread,and have just searched for it in Synaptic packet manager and that came up zero also.

---

### Post by nichipet on 2007-08-08
Although it's basically the same as searching in Synaptic, what does this give you:

```
sudo apt-cache search libdvd
```

Leave the read0 off the end and see if anything comes up with libdvd in it. Maybe it's under a slightly different name.

---

### Post by RomeReactor on 2007-08-08
> **dioon said:**
> Installed all except Libdvdread0,said it could not find,still cannot play DVD's.

Maybe there's another problem with sources.list; can you post it again, please?
```
cat /etc/apt/sources.list
```

---

### Post by dioon on 2007-08-08
derek@derek-desktop:~$ sudo apt-cache search libdvd
Password:
gxine - the xine video player, GTK+/Gnome user interface
gstreamer0.8-dvd - DVD plugin for GStreamer
libdvdnav-dev - The DVD navigation library, development package
libdvdnav4 - The DVD navigation library
libdvdplay0 - portable abstraction library for DVD menus support
libdvdplay0-dev - development files for libdvdplay0
libdvdread-dev - library for reading DVDs (development)
libdvdread3 - library for reading DVDs
ogle - DVD player with support for DVD menus
ogle-mmx - DVD player with support for DVD menus
cpdvd - transfer a DVD title to your harddisk
libdvdcss2 - Library for accessing DVDs like block device usind deCSS if needed
libdvdcss2-dev - development files for libdvdcss2
derek@derek-desktop:~$ sudo apt-cache search libdvd

---

### Post by nichipet on 2007-08-08
I'm guessing give libdvdread3 a shot.

```
sudo aptitude install libdvdread3
```

---

### Post by dioon on 2007-08-08
derek@derek-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#Medibuntu - Ubuntu 7.04 "feisty fawn"
#Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free



derek@derek-desktop:~$

---

### Post by RomeReactor on 2007-08-08
Sorry, my mistake. It *is* **libdvdread3** and **libdvdplay0**:
```
sudo apt-get install libdvdread3 libdvdplay0
```
Also, if you're using **totem-gstreamer** (the default in a fresh installation) try cahnging it to **totem-xine**:
```
sudo apt-get install totem-xine libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4 libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by dioon on 2007-08-08
Changing it to Totem-xine done the trick,thank's a lot guys for all your help this is a first class forum.
I have been experimenting will Linux for sometime now,looking for the best,Ithink I have found it.

---

### Post by andrew.46 on 2007-08-16
Hi,

 Glad to see that you have fixed your problem:

> **dioon said:**
> Changing it to Totem-xine done the trick,thank's a lot guys for all your help this is a first class forum.
I have been experimenting will Linux for sometime now,looking for the best,Ithink I have found it.

 If you want to try an arguably better player you could do worse than the vlc media player:

```
sudo apt-get install vlc
```

 You can run both vlc and totem quite successfully on the same computer.

                Andrew

---

