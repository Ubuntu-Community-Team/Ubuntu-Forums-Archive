---
title: "DVD Player Error Message - Totem"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by thistlebrae on 2006-08-12
Did an install from Ubuntu 6.06 LTS alternate iso image.

Everything seems to be working fine now except I get an error when attempting to play a DVD.  even after installing the libraries for encrypted DVDs.  And BTW this DVD is not even encrypted.


Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".

Background--

Used Synaptics Manager to load libdvdread3 which successfully installed.

Then ran the following script per instructions (looks successful / per instructions)

tmiller@ubuntu:~$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh
Password:
--16:37:32--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        24.42K/s

16:37:40 (24.39 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

(Reading database ... 73095 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...


tmiller@ubuntu:~$
______________________________________

Is it because the system thinks that the device is actually a DVD?  Then another interesting tidbit.  The drive disappears from the drive list on teh Places|Computer listing until I log out and then log back in again.

Any help would be most appreciated

---

### Post by thistlebrae on 2006-08-12
Update...

Replaced the Totem DVD Player package with Totem-xine based on a recommendation from the Ubuntu book by O'Reilly.  Now the movies play (most of them).  There is one lingering problem that is more of a nit.  

The Eject feature does not work.  Quitting the movie ends the application but the DVD drive is locked up and Eject button on the drive does not work (I think it has to do with the volume being mounted by Totem-xine application and not unmounting when exiting the application - but purely a guess.  This is because if you mount the volume then Totem-xine throws an error saying that the volume is already mounted).  In this case I have to let the app handling the mounting..which it does fine.  But seems its not so good at unmounting or releasing the drive.

The work around is to Logoff, Logon and then eject the DVD with the hardware button immediately after loggin on.  A pain..but it does work..

Suggestions anyone?

---

### Post by thistlebrae on 2006-08-13
I am gettting the feeling that not too many Ubuntunites must care about DVD of the lack thereof.  There seem to be a dearth of replies on DVD related issues.

Everyone else feel the same way?

---

### Post by nightmare03 on 2006-08-13
Im sure you could just manually unmount the drive by right clicking the drive in Computer and selecting unmount volume.

---

### Post by thistlebrae on 2006-08-13
The problem with that is that the drive disappears from the list once Totem-xine starts up and mounts the drive.  But thanks for the reply.  Do you have any ideas as to why the drive disappears?

---

### Post by Allrab on 2006-08-30
I still have hopes for the Movie Player but I get the same problem as you posted in the beginning.
I have been checking the forum but some wies guy just directs to the restricted formats page. I have followed the istructions but still get the URI handler issue.

I also find it disturbing that this does not seem to be an issue that people want to investigate.

If someone can give us help with the Movie Player and the DVD problem I would be glad.

/Allrab

---

### Post by adds2one on 2006-08-30
I have been trying to play DVD's for over a week and have met with no success trying everything I can find. At first I couldn't find much mention of people unable to play DVDs but eventually I started to find A LOT of people unable to play DVDs and 99% of them HAVE NOTHING TO DO with the restricted formats issue. Many postings by people have few replies or unhelpful remarks to read about restricted formats even though most of the people with problems have already used Automatix or Easy Ubuntu to install the support for restricted formats.

There seems to be several major problems. Here are two of the most common problems I have found on these forums, these are known bugs that should be resolved ASAP as far as I am concerned. 

[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)

[https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939](https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939)

Ubuntu plays DVDs perfectly on my laptop on which I installed all the same stuff as my desktop.

It seems crazy that there are so many people that can't play DVDs in Ubuntu. I will sadly have to go back to Windows on my desktop if I cannot get DVDs to play in Ubuntu, which seems likely as no one has responded to any of my posts on the subject and as I have tried every solution I have found on other threads that are full of similarly frustrated people who have also not found a solution.

I hate windows, I don't want to go back. :(

---

### Post by JNowka on 2006-08-31
Hello,

I don't know if this will help but I got my dvd player working by installing the libdvdcss2, libdvdnav4, libdvdplay0, libdvdread3 and installing the totem-xine.  I also reinstalled the ubuntu-desktop that is removed with the uninstalling of totem when transistioning between gstreamer and xine.  So far I have not experianced any of the troubles you are describing.

I hope this helps.

---

### Post by adds2one on 2006-08-31
Thanks, but I do already have all of those things installed.

---

### Post by Maxtorm on 2006-09-03
Not sure if this is going to be of any assistance to anyone, but I just got mine working after a few frustrations:

Installed DVD Restricted Format requirements as per:
[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

Installed libdvdnav4, libdvdplay0, libdvdread3.

Uninstalled totem-gstreamer and totem.

Enabled universe and backport repositories.

Installed totem-xine.

DVD Playback now works flawlessly.  I have the same issue as above with the icon disappearing from the desktop and, therefore, no means of soft ejecting.  However, the tray's eject button works fine.

---

