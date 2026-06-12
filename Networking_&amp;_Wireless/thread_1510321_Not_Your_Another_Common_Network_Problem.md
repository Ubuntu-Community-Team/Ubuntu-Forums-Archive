---
title: "Not Your Another Common Network Problem"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Lockheed on 2010-06-15
The head-scratcher is this: 

My atheros-based laptop cannot connect to wireless networks running on low channels. 
The lower the channel, the worse the connection. At channel 1, I cannot even ping local routers. It starts at 400ms and after few retries reaches 50 000ms, then times out indefinitely.

On channel 11 everything works flawlessly, on 9 and 10 - moderately good.


Before you jump to obvious conclusions, let me rule out some obvious conclusions:

**1. Hardware fault:**
- everything works fine under Windows, live CD of Ubuntu 9.10 and 10.04, BackTrack liveCD

**2. Settings problem:**
- it first occurred on ubuntu 9.04 (few months after installation) and after upgrading to 10.04 problem continues
- it also occurs on freshly installed Arch which has NO settings nor files imported from old linux
- occures on gnome (Ubuntu) and pure xfce4 (arch)

**3. Location, router, overloaded band**
- it occurs in various countries, various cities, various networks
- it occurs even if all wifis are running on 11 and only one on channel 1

**4. Drivers**
- tried ath5x and madwifi

**5. Kernel**
- it keeps happening with every kernel since Oct 2009. Before, I did not test it.
- it works on kernel supplied on livecds of Ubuntu 9.10 and 10.04
- it is happening at least since 2.6.31 onwards (2.6.34 included)

**6. Network Manager and WICD**
- happens using either of them

So, give it your best shot. I have been trying to find an answer to it on various forums since October last year and yet came up with a solution.

---

### Post by Lockheed on 2010-06-16
Here is logs taken few seconds after "connecting" to a low-channel wifi network:
```

$ tail -f /var/log/*.log
==> /var/log/AlsaUpgradeRev-1.0.21-4-121109-20.39.log <==
./drivers/opl3/snd-opl3-lib.ko
./drivers/opl3/snd-opl3-synth.ko
./drivers/pcsp/snd-pcsp.ko
./drivers/snd-virmidi.ko
./drivers/snd-mtpav.ko
./drivers/snd-aloop.ko
./drivers/vx/snd-vx-lib.ko
./drivers/snd-serial-u16550.ko
./drivers/snd-dummy.ko
chmod: cannot access `/dev/midi': No such file or directory

==> /var/log/AlsaUpgradeRev-1.0.21-4-121109-21.50.log <==
./drivers/opl3/snd-opl3-lib.ko
./drivers/opl3/snd-opl3-synth.ko
./drivers/pcsp/snd-pcsp.ko
./drivers/snd-virmidi.ko
./drivers/snd-mtpav.ko
./drivers/snd-aloop.ko
./drivers/vx/snd-vx-lib.ko
./drivers/snd-serial-u16550.ko
./drivers/snd-dummy.ko
chmod: cannot access `/dev/midi': No such file or directory

==> /var/log/AlsaUpgradeRev-1.17-060109-23.04.log <==

-------------------------------------------------------------
-  Installation successfully finished!
-------------------------------------------------------------


-------------------------------------------------------------
-  Your new ALSA version will be loaded after the next reboot...
-------------------------------------------------------------


==> /var/log/auth.log <==
Jun 16 21:24:04 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-get install opera*
Jun 16 21:25:58 Beyond2000 sudo:     juha : TTY=unknown ; PWD=/home/juha ; USER=root ; COMMAND=/usr/sbin/synaptic
Jun 16 21:27:21 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-key add -
Jun 16 21:27:24 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-get install debian-archive-keyring
Jun 16 21:27:39 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-get install debian-archive-keyring
Jun 16 21:28:58 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-get update
Jun 16 21:29:08 Beyond2000 sudo:     juha : TTY=pts/0 ; PWD=/home/juha ; USER=root ; COMMAND=/usr/bin/apt-get install opera
Jun 16 22:15:01 Beyond2000 CRON[24643]: pam_unix(cron:session): session opened for user juha by (uid=0)
Jun 16 22:17:02 Beyond2000 CRON[25074]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 16 22:17:02 Beyond2000 CRON[25074]: pam_unix(cron:session): session closed for user root

==> /var/log/boot.log <==
Error connecting to ftp: Couldn't resolve host 'gavbiz.co.uk'
mountall: mount /media/d/wwws/gavbiz_online [3221] terminated with status 1
Invalidating stale software suspend images... done.
 * Setting sensors limits                                                [ OK ] 
 * Starting system log daemon...                                                acpid: starting up with proc fs

init: apport pre-start process (3314) terminated with status 1
init: apport post-stop process (3345) terminated with status 1
                                                                         [ OK ]
 * Starting kernel log daemon...                                         [ OK ] 

==> /var/log/bootstrap.log <==
Setting up libio-string-perl (1.08-2) ...
Setting up libclass-accessor-perl (0.31-2) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up tasksel (2.73ubuntu18) ...

Setting up libparse-debianchangelog-perl (1.1.1-2ubuntu1) ...
Setting up ubuntu-minimal (1.140) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...

==> /var/log/checkbox.log <==

==> /var/log/daemon.log <==
Jun 16 21:07:45 Beyond2000 cpupowerd[32291]: WARNING: This program could cause damage to your Hardware! 
Jun 16 21:07:46 Beyond2000 cpupowerd[32292]: CPU frequency should be 1600 MHz, but is 800 MHz. Frequency changing failed! 
Jun 16 21:07:46 Beyond2000 cpupowerd[32292]: Change cpu step failed! 
Jun 16 21:28:59 Beyond2000 ntpd[3829]: synchronized to 130.149.17.21, stratum 1
Jun 16 21:28:59 Beyond2000 ntpd[3829]: kernel time sync status change 6001
Jun 16 21:31:00 Beyond2000 ntpd[3829]: synchronized to 130.88.202.49, stratum 2
Jun 16 21:31:00 Beyond2000 ntpd[3829]: kernel time sync status change 2001
Jun 16 21:47:28 Beyond2000 ntpd[3829]: synchronized to 130.149.17.21, stratum 1
Jun 16 22:09:01 Beyond2000 ntpd[3829]: synchronized to 193.62.22.98, stratum 1
Jun 16 22:28:39 Beyond2000 ntpd[3829]: sendto(213.222.193.35) (fd=18): Invalid argument

==> /var/log/dpkg.log <==
2010-06-16 21:30:13 status unpacked opera 10.10.4742.gcc4.qt3
2010-06-16 21:30:13 status half-configured opera 10.10.4742.gcc4.qt3
2010-06-16 21:30:22 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/opera 90 --slave /usr/share/man/man1/x-www-browser.1.gz x-www-browser.1.gz /usr/share/man/man1/opera.1.gz
2010-06-16 21:30:22 update-alternatives: link group x-www-browser updated to point to /usr/bin/opera
2010-06-16 21:30:24 status installed opera 10.10.4742.gcc4.qt3
2010-06-16 21:30:24 status triggers-pending menu 2.1.43ubuntu1
2010-06-16 21:30:24 status triggers-awaited menu 2.1.43ubuntu1
2010-06-16 21:30:24 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2010-06-16 21:30:24 status half-configured menu 2.1.43ubuntu1
2010-06-16 21:30:26 status installed menu 2.1.43ubuntu1

==> /var/log/fontconfig.log <==
/usr/share/fonts/truetype/ttf-symbol-replacement/symbol-replacement.ttf: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: skipping, existing cache is valid: 4 fonts, 0 dirs
/usr/share/fonts/truetype/unifont: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/type1: skipping, existing cache is valid: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: skipping, existing cache is valid: 35 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/texmf/fonts/type1/public/lm: skipping, existing cache is valid: 92 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
fc-cache: succeeded
tail: cannot open `/var/log/hibernate.log' for reading: Permission denied

==> /var/log/jockey.log <==

==> /var/log/kern.log <==
Jun 16 22:28:18 Beyond2000 kernel: wlan0: deauthenticated from 00:12:17:4a:10:ae (Reason: 7)
Jun 16 22:28:19 Beyond2000 kernel: eth0: no link during initialization.
Jun 16 22:28:34 Beyond2000 kernel: eth0: no link during initialization.
Jun 16 22:28:37 Beyond2000 kernel: wlan0: direct probe to AP 00:12:17:4a:10:ae (try 1)
Jun 16 22:28:38 Beyond2000 kernel: wlan0: direct probe responded
Jun 16 22:28:38 Beyond2000 kernel: wlan0: authenticate with AP 00:12:17:4a:10:ae (try 1)
Jun 16 22:28:38 Beyond2000 kernel: wlan0: authenticated
Jun 16 22:28:38 Beyond2000 kernel: wlan0: associate with AP 00:12:17:4a:10:ae (try 1)
Jun 16 22:28:38 Beyond2000 kernel: wlan0: RX AssocResp from 00:12:17:4a:10:ae (capab=0x431 status=0 aid=3)
Jun 16 22:28:38 Beyond2000 kernel: wlan0: associated

==> /var/log/lpr.log <==

==> /var/log/mail.log <==

==> /var/log/MountManager.log <==

==> /var/log/nvidia-installer.log <==
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 195.36.24)
   is now complete.

==> /var/log/pacman.log <==
[2010-05-07 22:00] synchronizing package lists

==> /var/log/pm-powersave.log <==
sudo: /etc/init.d/preload: command not found

ERROR: The control display is undefined; please run `nvidia-settings
       --help` for usage information.


ERROR: The control display is undefined; please run `nvidia-settings
       --help` for usage information.

Returned exit code 1.

==> /var/log/pm-suspend.log <==
/usr/lib/pm-utils/sleep.d/91wicd resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.

==> /var/log/pycentral.log <==
2010-05-27 13:52:21 2 pycentral cleanup-pkgprepare-updates: found 3 dangling symlinks
2010-05-27 13:52:21 2 pycentral cleanup-pkgprepare-updates: checking for links owned by packages (this may take some time)
2010-05-27 13:52:30 2 pycentral cleanup-pkgprepare-updates: removed %d dangling symlinks not owned by any package
2010-05-27 14:20:10 3 pycentral pkginstall: error byte-compiling files (1)
2010-05-27 14:26:27 3 pycentral pkginstall: error byte-compiling files (1)
2010-05-27 14:29:13 3 pycentral pkginstall: error byte-compiling files (1)
2010-05-27 14:34:08 3 pycentral pkginstall: error byte-compiling files (1)

==> /var/log/soundon.log <==
crw-rw-rw- 1 root root 251,  2 Jun 16 17:47 /dev/mixer
lrwxrwxrwx 1 root root      26 Jun 16 17:47 /dev/mixer0 -> /dev/oss/oss_hdaudio0/mix0
crw-rw-rw- 1 root root 250,  3 Jun 16 17:47 /dev/oss/oss_hdaudio0/mix0
crw-rw-rw- 1 root root 250,  4 Jun 16 17:47 /dev/oss/oss_hdaudio0/pcm0
crw-rw-rw- 1 root root 250,  6 Jun 16 17:47 /dev/oss/oss_hdaudio0/pcm1
crw-rw-rw- 1 root root 250, 10 Jun 16 17:47 /dev/oss/oss_hdaudio0/pcmin0
crw-rw-rw- 1 root root 250, 12 Jun 16 17:47 /dev/oss/oss_hdaudio0/pcmin1
crw-rw-rw- 1 root root 250,  8 Jun 16 17:47 /dev/oss/oss_hdaudio0/spdout0

Loading mixer settings from /usr/lib/oss/etc/mixer.save

==> /var/log/user.log <==

==> /var/log/vbox-install.log <==
vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.33.5-colombo/updates/dkms/

depmod....

DKMS: install Completed.

==> /var/log/wpa_supplicant.log <==

==> /var/log/Xorg.0.log <==
(**) Logitech USB RECEIVER: Device: "/dev/input/event8"
(II) Logitech USB RECEIVER: Found 20 mouse buttons
(II) Logitech USB RECEIVER: Found scroll wheel(s)
(II) Logitech USB RECEIVER: Found relative axes
(II) Logitech USB RECEIVER: Found x and y relative axes
(II) Logitech USB RECEIVER: Configuring as mouse
(**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
(**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
(II) Logitech USB RECEIVER: initialized for relative axes.

==> /var/log/Xorg.1.log <==

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

==> /var/log/Xorg.2.log <==

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.2.log" for additional information.

 ddxSigGiveUp: Closing log

==> /var/log/Xorg.3.log <==

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.3.log" for additional information.

 ddxSigGiveUp: Closing log

==> /var/log/Xorg.4.log <==

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log

==> /var/log/Xorg.5.log <==

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

==> /var/log/Xorg.99.log <==

==> /var/log/Xorg.failsafe.log <==
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

And pings from this period:
```
$ ping 192.168.7.1
PING 192.168.7.1 (192.168.7.1) 56(84) bytes of data.
64 bytes from 192.168.7.1: icmp_seq=1 ttl=64 time=19771 ms
64 bytes from 192.168.7.1: icmp_seq=2 ttl=64 time=18858 ms
64 bytes from 192.168.7.1: icmp_seq=3 ttl=64 time=18246 ms
64 bytes from 192.168.7.1: icmp_seq=4 ttl=64 time=17504 ms
64 bytes from 192.168.7.1: icmp_seq=5 ttl=64 time=16551 ms
64 bytes from 192.168.7.1: icmp_seq=6 ttl=64 time=15644 ms
64 bytes from 192.168.7.1: icmp_seq=7 ttl=64 time=14686 ms
64 bytes from 192.168.7.1: icmp_seq=8 ttl=64 time=13711 ms
64 bytes from 192.168.7.1: icmp_seq=9 ttl=64 time=12738 ms
64 bytes from 192.168.7.1: icmp_seq=10 ttl=64 time=11752 ms
64 bytes from 192.168.7.1: icmp_seq=11 ttl=64 time=5711 ms
64 bytes from 192.168.7.1: icmp_seq=12 ttl=64 time=5449 ms
64 bytes from 192.168.7.1: icmp_seq=13 ttl=64 time=5149 ms
64 bytes from 192.168.7.1: icmp_seq=14 ttl=64 time=4819 ms
64 bytes from 192.168.7.1: icmp_seq=15 ttl=64 time=4512 ms
64 bytes from 192.168.7.1: icmp_seq=16 ttl=64 time=5000 ms
64 bytes from 192.168.7.1: icmp_seq=17 ttl=64 time=4755 ms
64 bytes from 192.168.7.1: icmp_seq=18 ttl=64 time=4454 ms
64 bytes from 192.168.7.1: icmp_seq=19 ttl=64 time=4318 ms
64 bytes from 192.168.7.1: icmp_seq=20 ttl=64 time=4071 ms
64 bytes from 192.168.7.1: icmp_seq=21 ttl=64 time=4123 ms
64 bytes from 192.168.7.1: icmp_seq=22 ttl=64 time=4081 ms
64 bytes from 192.168.7.1: icmp_seq=23 ttl=64 time=3344 ms
64 bytes from 192.168.7.1: icmp_seq=24 ttl=64 time=2759 ms
64 bytes from 192.168.7.1: icmp_seq=25 ttl=64 time=2488 ms
64 bytes from 192.168.7.1: icmp_seq=26 ttl=64 time=2042 ms
64 bytes from 192.168.7.1: icmp_seq=27 ttl=64 time=1381 ms
64 bytes from 192.168.7.1: icmp_seq=28 ttl=64 time=1773 ms
64 bytes from 192.168.7.1: icmp_seq=29 ttl=64 time=1651 ms
64 bytes from 192.168.7.1: icmp_seq=30 ttl=64 time=1772 ms
64 bytes from 192.168.7.1: icmp_seq=31 ttl=64 time=1520 ms
64 bytes from 192.168.7.1: icmp_seq=32 ttl=64 time=759 ms
64 bytes from 192.168.7.1: icmp_seq=33 ttl=64 time=42.4 ms
64 bytes from 192.168.7.1: icmp_seq=34 ttl=64 time=71.3 ms
64 bytes from 192.168.7.1: icmp_seq=35 ttl=64 time=397 ms
64 bytes from 192.168.7.1: icmp_seq=36 ttl=64 time=6.13 ms
64 bytes from 192.168.7.1: icmp_seq=37 ttl=64 time=1.47 ms
64 bytes from 192.168.7.1: icmp_seq=38 ttl=64 time=571 ms
64 bytes from 192.168.7.1: icmp_seq=39 ttl=64 time=250 ms
64 bytes from 192.168.7.1: icmp_seq=40 ttl=64 time=97.9 ms
64 bytes from 192.168.7.1: icmp_seq=41 ttl=64 time=17.3 ms
64 bytes from 192.168.7.1: icmp_seq=42 ttl=64 time=8.66 ms
64 bytes from 192.168.7.1: icmp_seq=43 ttl=64 time=794 ms
64 bytes from 192.168.7.1: icmp_seq=44 ttl=64 time=630 ms
64 bytes from 192.168.7.1: icmp_seq=45 ttl=64 time=590 ms
64 bytes from 192.168.7.1: icmp_seq=46 ttl=64 time=337 ms
64 bytes from 192.168.7.1: icmp_seq=47 ttl=64 time=1.68 ms
64 bytes from 192.168.7.1: icmp_seq=48 ttl=64 time=179 ms
64 bytes from 192.168.7.1: icmp_seq=49 ttl=64 time=456 ms
64 bytes from 192.168.7.1: icmp_seq=50 ttl=64 time=13.7 ms
64 bytes from 192.168.7.1: icmp_seq=51 ttl=64 time=78.8 ms
64 bytes from 192.168.7.1: icmp_seq=52 ttl=64 time=1031 ms
64 bytes from 192.168.7.1: icmp_seq=53 ttl=64 time=652 ms
64 bytes from 192.168.7.1: icmp_seq=54 ttl=64 time=1020 ms
64 bytes from 192.168.7.1: icmp_seq=55 ttl=64 time=1352 ms
64 bytes from 192.168.7.1: icmp_seq=56 ttl=64 time=3012 ms
64 bytes from 192.168.7.1: icmp_seq=57 ttl=64 time=3448 ms
64 bytes from 192.168.7.1: icmp_seq=58 ttl=64 time=3881 ms
64 bytes from 192.168.7.1: icmp_seq=59 ttl=64 time=3139 ms
64 bytes from 192.168.7.1: icmp_seq=60 ttl=64 time=2364 ms
64 bytes from 192.168.7.1: icmp_seq=61 ttl=64 time=1733 ms
64 bytes from 192.168.7.1: icmp_seq=62 ttl=64 time=1670 ms
```
It is remarkable it actually kept pinging. Every other time it just timed out after several retries and I wasn't even able to access router's config page.

Here is pings after going back to channel 11:
```
64 bytes from 192.168.7.1: icmp_seq=84 ttl=64 time=2.02 ms
64 bytes from 192.168.7.1: icmp_seq=85 ttl=64 time=5.14 ms
64 bytes from 192.168.7.1: icmp_seq=86 ttl=64 time=3.24 ms
64 bytes from 192.168.7.1: icmp_seq=87 ttl=64 time=2.02 ms
64 bytes from 192.168.7.1: icmp_seq=88 ttl=64 time=1.41 ms
64 bytes from 192.168.7.1: icmp_seq=89 ttl=64 time=9.08 ms
64 bytes from 192.168.7.1: icmp_seq=90 ttl=64 time=58.4 ms
64 bytes from 192.168.7.1: icmp_seq=91 ttl=64 time=14.1 ms
64 bytes from 192.168.7.1: icmp_seq=92 ttl=64 time=1.23 ms
64 bytes from 192.168.7.1: icmp_seq=93 ttl=64 time=28.8 ms
64 bytes from 192.168.7.1: icmp_seq=94 ttl=64 time=1.40 ms
```

---

### Post by bigmojo74 on 2010-06-16
So you've had it in multiple areas, presumably on multiple networks, and are seeing the same results with multiple operating systems? The only constant at this point is your hardware. You could always try getting (another) wireless device that's either an expansion card or USB dongle, might even be able to talk a sales clerk into letting you try it out in store quick if you have a nice shop near by.

I'm sure given the length you've been looking at this you've noted that the lower the channel the lower the frequency, found a nice little break down of the channels here [http://en.kioskea.net/faq/2142-choosing-the-best-wi-fi-channel](http://en.kioskea.net/faq/2142-choosing-the-best-wi-fi-channel)

Doesn't explain the level of degradation you're seeing, but it's nifty information. Also quite curious, if you travel with this laptop do you have a cell phone on you too? What happens if you move away from the phone?

---

### Post by djeikyb on 2010-06-16
So, you're saying all channels work flawlessly in some version of Windows, as well as Ubuntu livecd's?

---

### Post by Lockheed on 2010-06-16
> **bigmojo74 said:**
> So you've had it in multiple areas, presumably on multiple networks, and are seeing the same results with multiple operating systems? The only constant at this point is your hardware.
Nope. Look at point 1. And I know about different frequencies.


> Also quite curious, if you travel with this laptop do you have a cell phone on you too? What happens if you move away from the phone?
No relation to cell phone proximity, either. Besides, point 1 again.

> **djeikyb said:**
> So, you're saying all channels work flawlessly in some version of Windows, as well as Ubuntu livecd's?
That is correct. Windows XP 64bit, 7 64bit and those liveCDs.

---

### Post by bigmojo74 on 2010-06-16
My apologies on that, second day not smoking... yeah I'll blame that - anyhow about the only other useful thing I can think of is to check what driver the live CD loads and which the local install is using - I'd figure they'd be the same but lord knows.

---

### Post by Lockheed on 2010-06-16
Yes, they are. ath5x. Besides, I already tried madwifi as well.

---

