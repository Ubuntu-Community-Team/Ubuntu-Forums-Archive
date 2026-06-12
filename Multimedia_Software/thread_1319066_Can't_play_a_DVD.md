---
title: "Can't play a DVD"
date: 2009-11-08
forum: Multimedia Software
---

### Post by OldGrantonian on 2009-11-08
I have a dual boot laptop with Vista and Ubuntu karmic.

I can play movies with Vista, but not Ubuntu. Here are the details. (I'm an Ubuntu newbie.)

Totem Movie Player 2.28.1, with GStreamer 0.10.25

The mounted DVDis on the desktop. It does not autoplay.

If I right-click the desktop icon and select "Open with Movie Player", nothing happens.

Open Movie Player manually. 

Click Movie > Play disc "movie_name". Nothing happens.

Do first command from the forum sticky:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

The command had one error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Do second command from forum sticky for 32-bit Ubuntu:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

This command ran without error until the Java license was shown. There was a <Ok> command at the foot of the license, but it wasn't clickable. (Maybe I was supposed to click ENTER?)

So, I closed the terminal, opened a new terminal, and ran the same command again. I got the message:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

Did that. Ran without problems.

For safety, repeat the cmd:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

Results:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alan@alan:~$ 
--------------------------------

So, try the command:

apt-get -f install

Results:

alan@alan:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alan@alan:~$


Any advice?

---

### Post by OldGrantonian on 2009-11-08
Bump :)

---

### Post by xc3RnbFO8P on 2009-11-08
sudo apt-get -f install

---

### Post by MelDJ on 2009-11-08
W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

you must add the gpg key for medibuntu. add it by following the steps here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

alan@alan:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alan@alan:~$

type sudo apt-get -f install
you must run apt-get with root priveleges. hence use sudo

---

### Post by OldGrantonian on 2009-11-08
Thanks for the advice :)

After executing the recommended commands, I was able to run the two commands from the sticky, no errors were reported.

Totem would still not play the DVD.

Open Totem from a terminal:

totem

In another terminal, type:
totem --help

This produces the output:

libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: BRAVEHEART
libdvdnav: DVD Serial Number: 29538842
libdvdnav: DVD Title (Alternative): BRAVEHEART
libdvdnav: Unable to find map file '/home/alan/.dvdnav/BRAVEHEART.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
** Message: no file info


The README from the above message says that I need the library "libdvdcss" from the website:

<http://www.debian-unofficial.org/>

I tried to add that line to System > Administration > Software Sources

but the "Add Source" button is greyed out.

I would be grateful for any advice on how to download and install the libdvdcss package.

---

### Post by OldGrantonian on 2009-11-09
Thanks for all the help. I worked it out for myself :)

---

