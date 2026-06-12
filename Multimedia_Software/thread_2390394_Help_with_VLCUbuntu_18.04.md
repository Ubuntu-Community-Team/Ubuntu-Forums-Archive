---
title: "Help with VLC/Ubuntu 18.04"
date: 2018-04-28
forum: Multimedia Software
---

### Post by DrPL on 2018-04-28
Hi,
I used to run Ubuntu 15.10 and at some point last year, VLC stopped working. I didn't use VLC that much so ignored the problem.

However, I have just upgraded to 18.04 and still have the same problem. 

I've followed the instructions which mentions installing libdvdcss,  libdvdread4 and libdvdnav4 and Ubuntu confirms that I have the latest  versions of these. Still not luck. Then I saw a post which says to try  deleting the ~./dvdcss directory, but still no luck.

When I run VLC and select the Disc option, I get the following in the dialog box:

Playback failure:
DVDRead could not open the disc "/dev/dvdrw".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvdrw'. Check the log for details.


(It doesn't matter what I select, /dev/dvd, /dev/cdrw etc., I get the same problem).

Can anyone help?

---

### Post by TheFu on 2018-04-28
What are the permissions for the device? ls -al
What groups is your account in? id

---

### Post by ajgreeny on 2018-04-28
If 18.04 has the same naming protocols as 16.04 for the DVD drive, (I have not yet tried to play a DVD on my 18.04 system), I suspect that you need to ask vlc to play **/dev/sr0** when you get to the dialogue box from Media ->Open Disk not **/dev/dvdrw**.

---

### Post by DrPL on 2018-04-28
lrwxrwxrwx 1 root root 3 Apr 28 16:31 dvd -> sr0

Selecting sr0 produces:

[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#000000]
[/COLOR]

---

### Post by TheFu on 2018-04-28
And what are the permissions  for sr0? 
Also, need the output from 'id'.

I'm assuming this is purely a permissions problem based on the error.

For example, 
```
$ ll /dev/sr0 
brw-rw----+ 1 root cdrom 11, 0 Apr 26 11:51 /dev/sr0 
```

Shows that only root or userids in the cdrom group can read my DVD drive.
If I don't login onto the console, my userid isn't added to the cdrom group, so access isn't possible. But if I add myself to the cdrom group, I can access it local and remote.  Happiness.

---

### Post by DrPL on 2018-04-28
lpaul@paul-HP-Pavilion-Notebook:/dev$ id
uid=1000(paul) gid=1000(paul) groups=1000(paul),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)

ls -al /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 Apr 28 19:26 sr0

---

### Post by ajgreeny on 2018-04-28
What does the one word command **groups** show you as output?
Perhaps you are not in a needed group.

This is what I get
```
~$ groups
*username* adm cdrom sudo dip plugdev lpadmin sambashare minidlna vboxusers plex
``` though you will not get the final three if you don't use those apps.

---

### Post by DrPL on 2018-04-28
I just did a 
sudo usermod -a -G cdrom paul

and I got paul adm cdrom sudo dip plugdev lpadmin sambashare

I think I may need to reboot my laptop!

---

### Post by DrPL on 2018-04-28
Just rebooted and I got the same error in VLC >:(

---

### Post by DrPL on 2018-04-28
I've gone right back to basics, checking what I have installed and reconfiguring if necessary

paul% sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.

I've never seen this one before.

---

### Post by mc4man on 2018-04-28
> **DrPL said:**
> I've gone right back to basics, checking what I have installed and reconfiguring if necessary

paul% sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.

I've never seen this one before.
Try again now with the sudo dpkg-reconfigure libdvd-pkg command. It could have been that the annoying unattended-upgrades was running

---

### Post by DrPL on 2018-04-28
I've removed all the packages and started afresh, using the details on this page: [https://sites.google.com/site/easylinuxtipsproject/multimedia](https://sites.google.com/site/easylinuxtipsproject/multimedia)

...and still no luck :(

(mc4man, I didn't see your reply until after I'd done this)

---

### Post by monkeybrain20122 on 2018-04-28
Did you install vlc from the software center? It seems that you got the snap package. Just uninstall it from the software center and install the apt package

```
sudo apt install vlc
```

I suggest using synaptic as your package manager instead of the software center. SC pushes half baked snap packages, I think snap should only be offered if there is no .deb version available. But if you install vlc or gimp you get snap and people are having issues accessing peripheral devices. In synaptic you get the normal deb packages, also the SC's software catalog is only a fraction of what you'll find in synaptic, many packages are missing.

---

### Post by DrPL on 2018-04-28
I tried sudo dpkg-reconfigure libdvd-pkg, it ran but it produced the same error

---

### Post by mc4man on 2018-04-28
> **DrPL said:**
> I tried sudo dpkg-reconfigure libdvd-pkg, it ran but it produced the same error
not sure why you get that, ck. & see if libdvdcss2 is installed
```
apt-cache policy libdvdcss2
```

---

### Post by TheFu on 2018-04-28
Well, not that it helps, but I don't see any permissions problem. ;(

---

### Post by ajgreeny on 2018-04-29
You have not yet told us if your vlc version is from the snap package; I also wonder if that is the root of your problem as vlc from the standard repos is working fine for me.

---

### Post by DrPL on 2018-04-29
> **monkeybrain20122 said:**
> Did you install vlc from the software center? It seems that you got the snap package. Just uninstall it from the software center and install the apt package

```
sudo apt install vlc
```

I suggest using synaptic as your package manager instead of the software center. SC pushes half baked snap packages, I think snap should only be offered if there is no .deb version available. But if you install vlc or gimp you get snap and people are having issues accessing peripheral devices. In synaptic you get the normal deb packages, also the SC's software catalog is only a fraction of what you'll find in synaptic, many packages are missing.


Sorry for this late reply, I had gone to bed :)
I've tried this, to no avail.

---

### Post by DrPL on 2018-04-29
> **mc4man said:**
> not sure why you get that, ck. & see if libdvdcss2 is installed
```
apt-cache policy libdvdcss2
```

paul@paul-HP-Pavilion-Notebook:~$ apt-cache policy libdvdcss2
libdvdcss2:
  Installed: 1.4.2-1~local
  Candidate: 1.4.2-1~local
  Version table:
 *** 1.4.2-1~local 100
        100 /var/lib/dpkg/status

---

### Post by DrPL on 2018-04-29
Does it matter if there's no ~/.dvdcss directory?

---

### Post by mc4man on 2018-04-29
So you have libdvdcss2, now see if the snap vlc is installed. What do these  show?
```
snap info vlc |grep installed
```
```
apt-cache policy vlc
```

---

### Post by mc4man on 2018-04-29
To note: the snap version of vlc can not play dvdcss encoded dvd's as it can't access the system libdvdcss2 lib & it doesn't include libdvdcss2
( and even if allowed access to libdvdcss2 it still wouldn't work

---

### Post by DrPL on 2018-04-29
paul@paul-HP-Pavilion-Notebook:~$ snap info vlc | grep installed
paul@paul-HP-Pavilion-Notebook:~$ 

Nothing!

------


apt-cache policy vlc
vlc:
  Installed: 4.0.0~rc1~~git20180425+r75411+133~ubuntu18.04.1
  Candidate: 4.0.0~rc1~~git20180425+r75411+133~ubuntu18.04.1
  Version table:
 *** 4.0.0~rc1~~git20180425+r75411+133~ubuntu18.04.1 500
        500 [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     3.0.1-3build1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages

---

### Post by mc4man on 2018-04-29
So you are using the master ppa version, maybe it's broken on dvd playback.
Try this, 
open a terminal, run this
```
export DVDCSS_VERBOSE=2
```
In same terminal
```
vlc > css_output.txt 2>&1
```
When vlc opens go Media > Open disc  Make sure Device disk is set to /dev/sr0 then click play
After vlc does what ever it does close vlc.
Attach css_output.txt to a reply here. (will be in home folder

---

### Post by DrPL on 2018-04-29
paul@paul-HP-Pavilion-Notebook:~$ more css_output.txt
[000055cce1ab7570] main libvlc: Running vlc with the default interface. Use 'cvl
c' to use vlc without interface.
[000055cce1abb560] main playlist: playlist is empty
libdvdnav: Using dvdnav version 6.0.0
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc API for access
libdvdcss error: failed to open device /dev/sr0 (No medium found)
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc API for access
libdvdcss error: failed to open device /dev/sr0 (No medium found)
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[00007f5014000f80] dvdread access error: DVDRead cannot open source: /dev/sr0
QObject::~QObject: Timers cannot be stopped from another thread

---

### Post by mc4man on 2018-04-29
> **DrPL said:**
> paul@paul-HP-Pavilion-Notebook:~$ more css_output.txt
[000055cce1ab7570] main libvlc: Running vlc with the default interface. Use 'cvl
c' to use vlc without interface.
[000055cce1abb560] main playlist: playlist is empty
libdvdnav: Using dvdnav version 6.0.0
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc API for access
libdvdcss error: failed to open device /dev/sr0 (No medium found)
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc API for access
libdvdcss error: failed to open device /dev/sr0 (No medium found)
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[00007f5014000f80] dvdread access error: DVDRead cannot open source: /dev/sr0
QObject::~QObject: Timers cannot be stopped from another thread
That's indicating no media found so nothing to play.
With the dvd in the drive run & post this, only interested in the *-cdrom section(s)
```
sudo lshw -c disk
```

---

### Post by DrPL on 2018-04-29
*-cdrom
       description: DVD-RAM writer
       product: DVDRW  SU208GB
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: HH00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by mc4man on 2018-04-29
> **DrPL said:**
> *-cdrom
       description: DVD-RAM writer
       product: DVDRW  SU208GB
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: HH00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
      [COLOR="#FF0000"] configuration: ansiversion=5 status=nodisc[/COLOR]
Your drive is not recognizing that dvd as a volume that can be mounted. You can try other dvds if you have any, if they are also not  mounted then not much to do. You could try cleaning, it could be the drive is on it's way out.

When the drive does recognize you'd see something like this with a video dvd
*-cdrom                   
       description: DVD-RAM writer
       product: DVDRAM SP80NB60
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       logical name: /media/doug/PULP_FICTION
       version: RA00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       [COLOR="#0000CD"]configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready[/COLOR]
     [COLOR="#0000CD"]*-medium
          physical id: 0
          logical name: /dev/cdrw
          logical name: /media/doug/PULP_FICTION
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted
[/COLOR]

---

### Post by DrPL on 2018-04-29
I'll see if I can a DVD drive (probably a removable USB one). Funnily, when I put the disk in the drive, it does grind and whirr for a few seconds, but nothing after that.

---

### Post by mc4man on 2018-04-29
> **DrPL said:**
> I'll see if I can a DVD drive (probably a removable USB one). Funnily, when I put the disk in the drive, it does grind and whirr for a few seconds, but nothing after that.
Here on my laptop the built-in dvd drive will no longer play commercial dvd's, a little activity, then nothing. It does play audio cd's, data dvd's also work.
I believe for the commercial dvd movies the drive needs to go to the very inner ring area & focus correctly. If not then from the drive's  point of view there's nothing there.
 I resolved by buying  a usb dvd drive, probably cost 30 bucks, works fine.

---

### Post by MibunoOokami on 2018-05-10
I'm having the same problem. I tried the steps from [this]("https://askubuntu.com/questions/302632/vlc-wont-run-dvds") thread, in step three, the second to last code doesn't work because the most recent number is 57 not 53. The last code doesn't work either but I don't know why.
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdcss2 libdvdnav4 libdvdread4
sudo apt-get install libavformat-extra-53 libavcodec-extra-53 libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I installed vlc via software centre first, then via terminal but still get the same message. As far as I can tell my permissions are all correct. Hopefully there is a suitable workaround as I don't want to use an external DVD player.
```
[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 
```

---

