---
title: "I give up:  How do I license DVD player software that works"
date: 2011-11-04
forum: Multimedia Software
---

### Post by jcobban on 2011-11-04
I give up.  I have tried to play DVDs on Ubuntu for several releases now.  I am on 11.10 now.  I follow all of the instructions and it never works.  Movie player complains that the disk is encrypted and VLC just sits there doing nothing.

I am not running Linux because I am cheap.  All of my computers have licenses for Windoze and are set up to either dual boot or run Windoze as a virtual machine.  I am running Linux because it provides the tools that I need in the most convenient and secure manner.  I am perfectly willing to pay for a license to view these DVDs, but that does not appear to be an option.

---

### Post by haqking on 2011-11-04
> **jcobban said:**
> I give up.  I have tried to play DVDs on Ubuntu for several releases now.  I am on 11.10 now.  I follow all of the instructions and it never works.  Movie player complains that the disk is encrypted and VLC just sits there doing nothing.

I am not running Linux because I am cheap.  All of my computers have licenses for Windoze and are set up to either dual boot or run Windoze as a virtual machine.  I am running Linux because it provides the tools that I need in the most convenient and secure manner.  I am perfectly willing to pay for a license to view these DVDs, but that does not appear to be an option.

I have never once had an issue on any version of Linux with DVD.

both players you mention should play fine.

see here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

so you have the restricted extras package installed ?

---

### Post by ubuntukid on 2011-11-04
There is a commercial DVD player in the ubuntu appstore by Fluendo which lets you watch dvd's without using methods that might be considered iffy depending on which part of the world you live in.

---

### Post by jcobban on 2011-11-08
> **haqking said:**
> I have never once had an issue on any version of Linux with DVD.

both players you mention should play fine.

see here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

so you have the restricted extras package installed ?

Yes I appreciate that I have to load the restricted extras package because the code to bypass the encryption is illegal in some countries. As far as I can tell without paying a copyright attorney for a definitive decision my systems are licensed to run DVDs because I have licenses for Windoze, and I can play the DVDs on those systems.  But I do not want to stop working on Linux while I watch a DVD.  I tried running Media Player in a virtual machine running Win7 but the virtualbox emulated display adapter croaked.

Every 6 months I go back to the community documentation in the vain hope that someone has found a way to make this work.  I have been doing that for several years now through at least 5 releases of Ubuntu.  Over and over I see posts that start with a description of exactly the symptoms I am observing and end with words to the effect "It just started working one day."  Unfortunately for me that "one day" is NEVER.  Also note that this is on two different computers with significantly different hardware configurations, and currently running different releases of Ubuntu, so it is not a peculiarity of one piece of equipment.

I also cannot watch, and more importantly record, television programs using MythTV even though on the exact same hardware I can if I just reboot to Windoze.  As a media platform I have to conclude that Linux is a bust.

All I want to do is watch TV on my computer.  I do not have the time or energy to become a guru in any of these technologies.

---

### Post by ubuntu-freak on 2011-11-08
> **ubuntukid said:**
> There is a commercial DVD player in the ubuntu appstore by Fluendo which lets you watch dvd's without using methods that might be considered iffy depending on which part of the world you live in.

Only iffy in Germany I think. But you also need a licence to play golf there, so yeah.

---

### Post by Chronon on 2011-11-08
I have been watching DVDs in Ubuntu since 8.04.  Did you consult this page?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mc4man on 2011-11-08
> **jcobban said:**
> Yes I appreciate that I have to load the restricted extras package ...

Would be useful if you did this - 
Put a dvd in the drive, **quit** any player or pop up. Then open a terminal

```
rm -R .dvdcss
```

Below is one complete command, copy & paste all of it
```
sudo apt-get -y install vlc; \
sudo /usr/share/doc/libdvdread4/install-css.sh; \
vlc
```

Click on Media > Open Disc > play

Post the terminal output (all) if the dvd doesn't play

(if vlc says it can't find the device then pick another one from the dropdown seen in screen that has a 1 at the end

If it doesn't play also post these  - 
What release of ubuntu are you using
result of this -
```
sudo lshw -C disk
```

---

### Post by coldraven on 2011-11-09
> **Chronon said:**
> I have been watching DVDs in Ubuntu since 8.04.  Did you consult this page?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

+1 The only time a DVD would not play was when the lens was dirty

---

### Post by clymbon on 2011-11-14
I had the same problem, so I tried following the instructions given by mc4man.  See below...

> **mc4man said:**
> Would be useful if you did this - 
Put a dvd in the drive, **quit** any player or pop up. Then open a terminal

```
rm -R .dvdcss
```

duncant@duncant-Latitude-D600:~$ rm -R .dvdcss
rm: cannot remove `.dvdcss': No such file or directory

> 
Below is one complete command, copy & paste all of it
```
sudo apt-get -y install vlc; \
sudo /usr/share/doc/libdvdread4/install-css.sh; \
vlc
```Click on Media > Open Disc > play
duncant@duncant-Latitude-D600:~$ sudo apt-get -y install vlc; \
> sudo /usr/share/doc/libdvdread4/install-css.sh; \
> vlc
[sudo] password for duncant: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2011-11-14 15:19:34--  [http://packages.medibuntu.org/dists/oneiric/free/binary-i386/Packages](http://packages.medibuntu.org/dists/oneiric/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.127.22, 2a01:e0b:1:127:ca0a:a9ff:fec8:ec19
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7889 (7.7K) [text/plain]
Saving to: `/tmp/dvdcss-6hRIYj/Packages'

100%[======================================>] 7,889       43.0K/s   in 0.2s    

2011-11-14 15:19:35 (43.0 KB/s) - `/tmp/dvdcss-6hRIYj/Packages' saved [7889/7889]

--2011-11-14 15:19:35--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.127.22, 2a01:e0b:1:127:ca0a:a9ff:fec8:ec19
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-6hRIYj/libdvdcss.deb'

100%[======================================>] 38,036      67.3K/s   in 0.6s    

2011-11-14 15:19:36 (67.3 KB/s) - `/tmp/dvdcss-6hRIYj/libdvdcss.deb' saved [38036/38036]

(Reading database ... 154450 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-6hRIYj/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9c00914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:2322): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
[0xa0fd37c] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0xa0f97ac] main input error: open of `dvd:///dev/dvd' failed: (null)

> 
Post the terminal output (all) if the dvd doesn't play

(if vlc says it can't find the device then pick another one from the dropdown seen in screen that has a 1 at the end
See above.

> 
If it doesn't play also post these  - 
What release of ubuntu are you using
result of this -
```
sudo lshw -C disk
```
duncant@duncant-Latitude-D600:~$ cat /proc/version
Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011
duncant@duncant-Latitude-D600:~$ cat /etc/issue
Ubuntu 11.10 \n \l
duncant@duncant-Latitude-D600:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: HITACHI_DK23FB-4
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 00M1
       serial: 2ZZ623
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005d5e4
  *-cdrom
       description: DVD reader
       product: DVD+RW ND-5100A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 10AC
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc




Any help much appreciated!

---

### Post by JayKay3OOO on 2011-11-14
**Read:**

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

**Or if you cba to click a link then this is what it says:**

Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line:

sudo apt-get install libdvdread4
Then open a terminal window and execute:

sudo /usr/share/doc/libdvdread4/install-css.sh

[I]I did this a minute ago as I forgot I'd not setup DVD playb[I]ack on my laptop and popped in a random DVD. Happened to be 'alien'. This DVD would not work before doing these two commands and now it does as does every other DVD I own.

I did not bother installing VLC or nothing. I just loaded the DVD using the default player. In my case dragon player as I'm on Kubuntu.[/I][/I]

---

### Post by mc4man on 2011-11-14
> **clymbon said:**
> 
  *-cdrom
       description: DVD reader
       product: DVD+RW ND-5100A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 10AC
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 [COLOR="Red"]status=nodisc[/COLOR]

Any help much appreciated!
If you got the result in red with a dvd in the drive then you won't be able to playback, nothing to do with codecs, players, plugins, ect.
You can't play a disc that's not there...

Typically you'd see this 
> capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready

If you got just this, while not ideal, playback could be done by pointing vlc @ the device, in your case /dev/sr0 or even /dev/dvd should work
(A dvd's filesystem does not need to be 'mounted' for the dvd to be played back
> logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 [COLOR="Blue"]status=ready[/COLOR]


There have unfortunately be a number of cases where some hardware seems to have this issue, typically most other removable media is fine, commercial dvds aren't detected.
You could try searching out some threads though I'm not sure how many solutions are to be found

Edit: just curious - what does this show, if anything
```
cat /etc/group |grep cdrom
```

---

### Post by clymbon on 2011-11-15
> **mc4man said:**
> If you got the result in red with a dvd in the drive then you won't be able to playback, nothing to do with codecs, players, plugins, ect.

Yeah, I get "status=nodisc" but there IS a DVD disc in there.  Doesn't seem to matter what kind of DVD I put in there.  But if I put a CD in there I get: 

```

  *-cdrom
       description: DVD reader
       product: DVD+RW ND-5100A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 10AC
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

> 
There have unfortunately be a number of cases where some hardware seems to have this issue, typically most other removable media is fine, commercial dvds aren't detected.
You could try searching out some threads though I'm not sure how many solutions are to be found
Hmmm...  Guess I'll try to search.  Perhaps I have an incompatibility between this particular DVD drive and linux?

> Edit: just curious - what does this show, if anything
```
cat /etc/group |grep cdrom
``````

duncant@duncant-Latitude-D600:~$ cat /etc/group | grep cdrom
cdrom:x:24:duncant

```Thanks for the help!

---

### Post by mc4man on 2011-11-15
> **clymbon said:**
> Yeah, I get "status=nodisc" but there IS a DVD disc in there.  Doesn't seem to matter [COLOR="Blue"]what kind of DVD [/COLOR]I put in there.  But if I put a CD in there I get: 

That would likely narrow the scope of what's wrong. The most common would be an issue with the drive itself. 
How old is the drive & does it currently work with another Os or ubuntu version on dvd detection?
(or did it recently work & stopped with a new ubuntu install

It's not uncommon for a drive to partially  fail, can read cd's but not dvd's or the other way around.

Otherwise it would fall under a UDF read issue though haven't seen posts about that in quite some time.

---

### Post by beew on 2011-11-15
I have started a thread about dvd playback issue in the absolute beginner talk section without getting much help there (tried getting the mods to move the thread here but that has gone unnoticed as well)

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Not trying to high-jack the thread, but if anyone has an idea about my question please help.

Basically it plays most dvds, but some won't even mount. However, if I stick in a different DVD and mount it first, the not mounting one would play immediately (conversely playing some dvd seems to have the effect of making some other ones not mountable, which can then be unlocked by mounting yet a third dvd)

It is not a huge problem because this is not a common situation and I can always watch them, if having to mount a random dvd first. I am more curious to understand this odd ball situation than being desperate.

Thanks and sorry for the disruption.

---

