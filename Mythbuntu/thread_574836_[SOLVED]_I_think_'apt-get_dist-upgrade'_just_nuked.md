---
title: "[SOLVED] I think 'apt-get dist-upgrade' just nuked ivtv's audio..."
date: 2007-10-13
forum: Mythbuntu
---

### Post by obscure411 on 2007-10-13
I could have sword that when I ran that this morning I saw something about a new ivtv package whiz by...

Pro:

The video jittering I was having before is *GONE*.  Sweet!

Con:

I now have no audio from the PVR-150, nor from the PVR-500 sitting next to it.

MythVideo still works fine, so I know it can play audio still.

Any ideas?  Just when I thought I was done setting this thing up... :)

---

### Post by deffcon on 2007-10-13
YEP,

Same problem here with 2x an pvr-500 mce, nou sound after dist-upgrade, anyone tried to confirm this?

Deffcon

---

### Post by superm1 on 2007-10-13
IVTV Utilities may have been upgraded, but that shouldn't have touched anything here.

Can you guys try to run an older kernel (i'm guessing that is what got upgraded) and see if the problem persists?

---

### Post by obscure411 on 2007-10-13
How would I do that?

Still a bit green on this whole ubuntu/linux thing...

---

### Post by obscure411 on 2007-10-13
Nevermind - I thought I had removed the previous kernels, but they were still in the grub boot menu...

Problem is still there with the 2.6.22-13-generic kernel.  Checking all the outputs now.

---

### Post by superm1 on 2007-10-13
Well when you restart the computer there will be a screen that comes up before the mythbuntu splash.

It says "Press ESC to see boot menu" or something similar.  Try hitting escape and see if any other kernels are listed.

Also, you may consider posting your /var/log/dpkg.log.  We can look at exactly what got installed and upgraded since things broke.

---

### Post by obscure411 on 2007-10-13
Yep.  Definitely still there with the old kernel.  Tried on the 150 and the 500 both ... no dice.

---

### Post by superm1 on 2007-10-13
> **obscure411 said:**
> Yep.  Definitely still there with the old kernel.  Tried on the 150 and the 500 both ... no dice.
Yeah post your dpkg.log, and lets see which package is indeed causing this then.

---

### Post by obscure411 on 2007-10-13
Dpkg log output for today:

2007-10-13 07:43:05 startup archives unpack
2007-10-13 07:43:15 upgrade linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.35 2.6.22-14.37
2007-10-13 07:43:15 status half-configured linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.35
2007-10-13 07:43:15 status unpacked linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.35
2007-10-13 07:43:15 status half-installed linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.35
2007-10-13 07:43:18 status half-installed linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.35
2007-10-13 07:43:19 status unpacked linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37
2007-10-13 07:43:19 status unpacked linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37
2007-10-13 07:43:20 upgrade mysql-common 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:20 status half-configured mysql-common 5.0.45-1ubuntu2
2007-10-13 07:43:20 status unpacked mysql-common 5.0.45-1ubuntu2
2007-10-13 07:43:20 status half-installed mysql-common 5.0.45-1ubuntu2
2007-10-13 07:43:20 status half-installed mysql-common 5.0.45-1ubuntu2
2007-10-13 07:43:21 status unpacked mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:21 status unpacked mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:21 upgrade mysql-server 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:21 status half-configured mysql-server 5.0.45-1ubuntu2
2007-10-13 07:43:21 status unpacked mysql-server 5.0.45-1ubuntu2
2007-10-13 07:43:21 status half-installed mysql-server 5.0.45-1ubuntu2
2007-10-13 07:43:25 status half-installed mysql-server 5.0.45-1ubuntu2
2007-10-13 07:43:25 status unpacked mysql-server 5.0.45-1ubuntu3
2007-10-13 07:43:25 status unpacked mysql-server 5.0.45-1ubuntu3
2007-10-13 07:43:25 upgrade mysql-client 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:25 status half-configured mysql-client 5.0.45-1ubuntu2
2007-10-13 07:43:25 status unpacked mysql-client 5.0.45-1ubuntu2
2007-10-13 07:43:26 status half-installed mysql-client 5.0.45-1ubuntu2
2007-10-13 07:43:26 status half-installed mysql-client 5.0.45-1ubuntu2
2007-10-13 07:43:26 status unpacked mysql-client 5.0.45-1ubuntu3
2007-10-13 07:43:26 status unpacked mysql-client 5.0.45-1ubuntu3
2007-10-13 07:43:26 upgrade libmysqlclient15off 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:26 status half-configured libmysqlclient15off 5.0.45-1ubuntu2
2007-10-13 07:43:26 status unpacked libmysqlclient15off 5.0.45-1ubuntu2
2007-10-13 07:43:26 status half-installed libmysqlclient15off 5.0.45-1ubuntu2
2007-10-13 07:43:27 status half-installed libmysqlclient15off 5.0.45-1ubuntu2
2007-10-13 07:43:28 status unpacked libmysqlclient15off 5.0.45-1ubuntu3
2007-10-13 07:43:28 status unpacked libmysqlclient15off 5.0.45-1ubuntu3
2007-10-13 07:43:28 upgrade mysql-client-5.0 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:28 status half-configured mysql-client-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:28 status unpacked mysql-client-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:28 status half-installed mysql-client-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:30 status half-installed mysql-client-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:30 status unpacked mysql-client-5.0 5.0.45-1ubuntu3
2007-10-13 07:43:31 status unpacked mysql-client-5.0 5.0.45-1ubuntu3
2007-10-13 07:43:31 startup packages configure
2007-10-13 07:43:31 configure mysql-common 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:43:31 status unpacked mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:31 status unpacked mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:31 status half-configured mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:31 status installed mysql-common 5.0.45-1ubuntu3
2007-10-13 07:43:32 startup archives unpack
2007-10-13 07:43:32 upgrade mysql-server-5.0 5.0.45-1ubuntu2 5.0.45-1ubuntu3
2007-10-13 07:43:32 status half-configured mysql-server-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:32 status unpacked mysql-server-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:32 status half-installed mysql-server-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:40 status half-installed mysql-server-5.0 5.0.45-1ubuntu2
2007-10-13 07:43:42 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:43:43 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:43:43 upgrade liblircclient0 0.8.2-0ubuntu7 0.8.2-0ubuntu8
2007-10-13 07:43:43 status half-configured liblircclient0 0.8.2-0ubuntu7
2007-10-13 07:43:43 status unpacked liblircclient0 0.8.2-0ubuntu7
2007-10-13 07:43:43 status half-installed liblircclient0 0.8.2-0ubuntu7
2007-10-13 07:43:43 status half-installed liblircclient0 0.8.2-0ubuntu7
2007-10-13 07:43:44 status unpacked liblircclient0 0.8.2-0ubuntu8
2007-10-13 07:43:44 status unpacked liblircclient0 0.8.2-0ubuntu8
2007-10-13 07:43:44 upgrade lirc 0.8.2-0ubuntu7 0.8.2-0ubuntu8
2007-10-13 07:43:44 status half-configured lirc 0.8.2-0ubuntu7
2007-10-13 07:43:45 status unpacked lirc 0.8.2-0ubuntu7
2007-10-13 07:43:45 status half-installed lirc 0.8.2-0ubuntu7
2007-10-13 07:43:46 status half-installed lirc 0.8.2-0ubuntu7
2007-10-13 07:43:46 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:43:46 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:43:47 upgrade python-apt 0.7.3.1ubuntu2 0.7.3.1ubuntu3
2007-10-13 07:43:47 status half-configured python-apt 0.7.3.1ubuntu2
2007-10-13 07:43:48 status unpacked python-apt 0.7.3.1ubuntu2
2007-10-13 07:43:48 status half-installed python-apt 0.7.3.1ubuntu2
2007-10-13 07:43:48 status half-installed python-apt 0.7.3.1ubuntu2
2007-10-13 07:43:49 status unpacked python-apt 0.7.3.1ubuntu3
2007-10-13 07:43:49 status unpacked python-apt 0.7.3.1ubuntu3
2007-10-13 07:43:49 upgrade guidance-backends 0.8.0svn20070928-0ubuntu5 0.8.0svn20070928-0ubuntu6
2007-10-13 07:43:49 status half-configured guidance-backends 0.8.0svn20070928-0ubuntu5
2007-10-13 07:43:50 status unpacked guidance-backends 0.8.0svn20070928-0ubuntu5
2007-10-13 07:43:50 status half-installed guidance-backends 0.8.0svn20070928-0ubuntu5
2007-10-13 07:43:50 status half-installed guidance-backends 0.8.0svn20070928-0ubuntu5
2007-10-13 07:43:50 status unpacked guidance-backends 0.8.0svn20070928-0ubuntu6
2007-10-13 07:43:50 status unpacked guidance-backends 0.8.0svn20070928-0ubuntu6
2007-10-13 07:43:51 upgrade displayconfig-gtk 0.3.3 0.3.7
2007-10-13 07:43:51 status half-configured displayconfig-gtk 0.3.3
2007-10-13 07:43:51 status unpacked displayconfig-gtk 0.3.3
2007-10-13 07:43:51 status half-installed displayconfig-gtk 0.3.3
2007-10-13 07:43:52 status half-installed displayconfig-gtk 0.3.3
2007-10-13 07:43:52 status unpacked displayconfig-gtk 0.3.7
2007-10-13 07:43:52 status unpacked displayconfig-gtk 0.3.7
2007-10-13 07:43:52 upgrade pidgin-data 1:2.2.1-1ubuntu3 1:2.2.1-1ubuntu4
2007-10-13 07:43:52 status half-configured pidgin-data 1:2.2.1-1ubuntu3
2007-10-13 07:43:52 status unpacked pidgin-data 1:2.2.1-1ubuntu3
2007-10-13 07:43:52 status half-installed pidgin-data 1:2.2.1-1ubuntu3
2007-10-13 07:43:54 status half-installed pidgin-data 1:2.2.1-1ubuntu3
2007-10-13 07:43:54 status unpacked pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:43:54 status unpacked pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:43:54 upgrade libpurple0 1:2.2.1-1ubuntu3 1:2.2.1-1ubuntu4
2007-10-13 07:43:54 status half-configured libpurple0 1:2.2.1-1ubuntu3
2007-10-13 07:43:55 status unpacked libpurple0 1:2.2.1-1ubuntu3
2007-10-13 07:43:55 status half-installed libpurple0 1:2.2.1-1ubuntu3
2007-10-13 07:43:56 status half-installed libpurple0 1:2.2.1-1ubuntu3
2007-10-13 07:43:56 status unpacked libpurple0 1:2.2.1-1ubuntu4
2007-10-13 07:43:57 status unpacked libpurple0 1:2.2.1-1ubuntu4
2007-10-13 07:43:57 upgrade pidgin 1:2.2.1-1ubuntu3 1:2.2.1-1ubuntu4
2007-10-13 07:43:57 status half-configured pidgin 1:2.2.1-1ubuntu3
2007-10-13 07:44:02 status unpacked pidgin 1:2.2.1-1ubuntu3
2007-10-13 07:44:02 status half-installed pidgin 1:2.2.1-1ubuntu3
2007-10-13 07:44:03 status half-installed pidgin 1:2.2.1-1ubuntu3
2007-10-13 07:44:03 status unpacked pidgin 1:2.2.1-1ubuntu4
2007-10-13 07:44:03 status unpacked pidgin 1:2.2.1-1ubuntu4
2007-10-13 07:44:03 upgrade gaim 1:2.2.1-1ubuntu3 1:2.2.1-1ubuntu4
2007-10-13 07:44:03 status half-configured gaim 1:2.2.1-1ubuntu3
2007-10-13 07:44:04 status unpacked gaim 1:2.2.1-1ubuntu3
2007-10-13 07:44:04 status half-installed gaim 1:2.2.1-1ubuntu3
2007-10-13 07:44:04 status half-installed gaim 1:2.2.1-1ubuntu3
2007-10-13 07:44:04 status unpacked gaim 1:2.2.1-1ubuntu4
2007-10-13 07:44:05 status unpacked gaim 1:2.2.1-1ubuntu4
2007-10-13 07:44:05 upgrade gdm 2.20.0-0ubuntu3 2.20.0-0ubuntu4
2007-10-13 07:44:05 status half-configured gdm 2.20.0-0ubuntu3
2007-10-13 07:44:05 status unpacked gdm 2.20.0-0ubuntu3
2007-10-13 07:44:05 status half-installed gdm 2.20.0-0ubuntu3
2007-10-13 07:44:07 status half-installed gdm 2.20.0-0ubuntu3
2007-10-13 07:44:07 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:44:07 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:44:07 upgrade libartsc0 1.5.7-1ubuntu3 1.5.8-0ubuntu1
2007-10-13 07:44:07 status half-configured libartsc0 1.5.7-1ubuntu3
2007-10-13 07:44:07 status unpacked libartsc0 1.5.7-1ubuntu3
2007-10-13 07:44:07 status half-installed libartsc0 1.5.7-1ubuntu3
2007-10-13 07:44:08 status half-installed libartsc0 1.5.7-1ubuntu3
2007-10-13 07:44:08 status unpacked libartsc0 1.5.8-0ubuntu1
2007-10-13 07:44:08 status unpacked libartsc0 1.5.8-0ubuntu1
2007-10-13 07:44:08 upgrade libarts1c2a 1.5.7-1ubuntu3 1.5.8-0ubuntu1
2007-10-13 07:44:08 status half-configured libarts1c2a 1.5.7-1ubuntu3
2007-10-13 07:44:08 status unpacked libarts1c2a 1.5.7-1ubuntu3
2007-10-13 07:44:09 status half-installed libarts1c2a 1.5.7-1ubuntu3
2007-10-13 07:44:10 status half-installed libarts1c2a 1.5.7-1ubuntu3
2007-10-13 07:44:10 status unpacked libarts1c2a 1.5.8-0ubuntu1
2007-10-13 07:44:10 status unpacked libarts1c2a 1.5.8-0ubuntu1
2007-10-13 07:44:10 upgrade kdelibs4c2a 4:3.5.7-1ubuntu15 4:3.5.8-0ubuntu1
2007-10-13 07:44:10 status half-configured kdelibs4c2a 4:3.5.7-1ubuntu15
2007-10-13 07:44:11 status unpacked kdelibs4c2a 4:3.5.7-1ubuntu15
2007-10-13 07:44:11 status half-installed kdelibs4c2a 4:3.5.7-1ubuntu15
2007-10-13 07:44:13 status half-installed kdelibs4c2a 4:3.5.7-1ubuntu15
2007-10-13 07:44:14 status unpacked kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:44:14 status unpacked kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:44:14 upgrade kdelibs-data 4:3.5.7-1ubuntu15 4:3.5.8-0ubuntu1
2007-10-13 07:44:14 status half-configured kdelibs-data 4:3.5.7-1ubuntu15
2007-10-13 07:44:14 status unpacked kdelibs-data 4:3.5.7-1ubuntu15
2007-10-13 07:44:15 status half-installed kdelibs-data 4:3.5.7-1ubuntu15
2007-10-13 07:44:21 status half-installed kdelibs-data 4:3.5.7-1ubuntu15
2007-10-13 07:44:22 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:44:22 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:44:23 upgrade libgl1-mesa-glx 7.0.1-1ubuntu2 7.0.1-1ubuntu3
2007-10-13 07:44:23 status half-configured libgl1-mesa-glx 7.0.1-1ubuntu2
2007-10-13 07:44:23 status unpacked libgl1-mesa-glx 7.0.1-1ubuntu2
2007-10-13 07:44:23 status half-installed libgl1-mesa-glx 7.0.1-1ubuntu2
2007-10-13 07:44:23 status half-installed libgl1-mesa-glx 7.0.1-1ubuntu2
2007-10-13 07:44:23 status unpacked libgl1-mesa-glx 7.0.1-1ubuntu3
2007-10-13 07:44:23 status unpacked libgl1-mesa-glx 7.0.1-1ubuntu3
2007-10-13 07:44:24 upgrade ttf-dejavu-core 2.19-1ubuntu2 2.19-1ubuntu3
2007-10-13 07:44:24 status half-configured ttf-dejavu-core 2.19-1ubuntu2
2007-10-13 07:44:24 status unpacked ttf-dejavu-core 2.19-1ubuntu2
2007-10-13 07:44:24 status half-installed ttf-dejavu-core 2.19-1ubuntu2
2007-10-13 07:44:24 status half-installed ttf-dejavu-core 2.19-1ubuntu2
2007-10-13 07:44:25 status unpacked ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:44:25 status unpacked ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:44:25 upgrade ttf-dejavu-extra 2.19-1ubuntu2 2.19-1ubuntu3
2007-10-13 07:44:25 status half-configured ttf-dejavu-extra 2.19-1ubuntu2
2007-10-13 07:44:25 status unpacked ttf-dejavu-extra 2.19-1ubuntu2
2007-10-13 07:44:25 status half-installed ttf-dejavu-extra 2.19-1ubuntu2
2007-10-13 07:44:26 status half-installed ttf-dejavu-extra 2.19-1ubuntu2
2007-10-13 07:44:26 status unpacked ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:44:26 status unpacked ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:44:26 upgrade ttf-dejavu 2.19-1ubuntu2 2.19-1ubuntu3
2007-10-13 07:44:26 status half-configured ttf-dejavu 2.19-1ubuntu2
2007-10-13 07:44:27 status unpacked ttf-dejavu 2.19-1ubuntu2
2007-10-13 07:44:27 status half-installed ttf-dejavu 2.19-1ubuntu2
2007-10-13 07:44:27 status half-installed ttf-dejavu 2.19-1ubuntu2
2007-10-13 07:44:27 status unpacked ttf-dejavu 2.19-1ubuntu3
2007-10-13 07:44:27 status unpacked ttf-dejavu 2.19-1ubuntu3
2007-10-13 07:44:27 upgrade xserver-xorg-input-synaptics 0.14.6-0ubuntu9 0.14.6-0ubuntu10
2007-10-13 07:44:27 status half-configured xserver-xorg-input-synaptics 0.14.6-0ubuntu9
2007-10-13 07:44:27 status unpacked xserver-xorg-input-synaptics 0.14.6-0ubuntu9
2007-10-13 07:44:27 status half-installed xserver-xorg-input-synaptics 0.14.6-0ubuntu9
2007-10-13 07:44:28 status half-installed xserver-xorg-input-synaptics 0.14.6-0ubuntu9
2007-10-13 07:44:28 status unpacked xserver-xorg-input-synaptics 0.14.6-0ubuntu10
2007-10-13 07:44:28 status unpacked xserver-xorg-input-synaptics 0.14.6-0ubuntu10
2007-10-13 07:44:28 upgrade xserver-xorg-video-intel 2:2.1.1-0ubuntu7 2:2.1.1-0ubuntu8
2007-10-13 07:44:28 status half-configured xserver-xorg-video-intel 2:2.1.1-0ubuntu7
2007-10-13 07:44:28 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu7
2007-10-13 07:44:28 status half-installed xserver-xorg-video-intel 2:2.1.1-0ubuntu7
2007-10-13 07:44:29 status half-installed xserver-xorg-video-intel 2:2.1.1-0ubuntu7
2007-10-13 07:44:29 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu8
2007-10-13 07:44:29 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu8
2007-10-13 07:44:29 upgrade libglu1-mesa 7.0.1-1ubuntu2 7.0.1-1ubuntu3
2007-10-13 07:44:29 status half-configured libglu1-mesa 7.0.1-1ubuntu2
2007-10-13 07:44:29 status unpacked libglu1-mesa 7.0.1-1ubuntu2
2007-10-13 07:44:29 status half-installed libglu1-mesa 7.0.1-1ubuntu2
2007-10-13 07:44:29 status half-installed libglu1-mesa 7.0.1-1ubuntu2
2007-10-13 07:44:30 status unpacked libglu1-mesa 7.0.1-1ubuntu3
2007-10-13 07:44:30 status unpacked libglu1-mesa 7.0.1-1ubuntu3
2007-10-13 07:44:30 upgrade mesa-utils 7.0.1-1ubuntu2 7.0.1-1ubuntu3
2007-10-13 07:44:30 status half-configured mesa-utils 7.0.1-1ubuntu2
2007-10-13 07:44:30 status unpacked mesa-utils 7.0.1-1ubuntu2
2007-10-13 07:44:30 status half-installed mesa-utils 7.0.1-1ubuntu2
2007-10-13 07:44:30 status half-installed mesa-utils 7.0.1-1ubuntu2
2007-10-13 07:44:30 status unpacked mesa-utils 7.0.1-1ubuntu3
2007-10-13 07:44:31 status unpacked mesa-utils 7.0.1-1ubuntu3
2007-10-13 07:44:31 startup packages configure
2007-10-13 07:44:31 configure linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37 2.6.22-14.37
2007-10-13 07:44:31 status unpacked linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37
2007-10-13 07:44:31 status half-configured linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37
2007-10-13 07:45:12 status installed linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37
2007-10-13 07:45:12 configure libmysqlclient15off 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:45:12 status unpacked libmysqlclient15off 5.0.45-1ubuntu3
2007-10-13 07:45:12 status half-configured libmysqlclient15off 5.0.45-1ubuntu3
2007-10-13 07:45:12 status installed libmysqlclient15off 5.0.45-1ubuntu3
2007-10-13 07:45:12 status triggers-pending libc6 2.6.1-1ubuntu9
2007-10-13 07:45:12 configure mysql-client-5.0 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:45:12 status unpacked mysql-client-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status half-configured mysql-client-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status installed mysql-client-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 configure mysql-server-5.0 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:13 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:14 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:14 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:14 status unpacked mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:14 status half-configured mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:22 status installed mysql-server-5.0 5.0.45-1ubuntu3
2007-10-13 07:45:22 configure mysql-server 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:45:22 status unpacked mysql-server 5.0.45-1ubuntu3
2007-10-13 07:45:22 status half-configured mysql-server 5.0.45-1ubuntu3
2007-10-13 07:45:22 status installed mysql-server 5.0.45-1ubuntu3
2007-10-13 07:45:22 configure mysql-client 5.0.45-1ubuntu3 5.0.45-1ubuntu3
2007-10-13 07:45:22 status unpacked mysql-client 5.0.45-1ubuntu3
2007-10-13 07:45:22 status half-configured mysql-client 5.0.45-1ubuntu3
2007-10-13 07:45:23 status installed mysql-client 5.0.45-1ubuntu3
2007-10-13 07:45:23 configure liblircclient0 0.8.2-0ubuntu8 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked liblircclient0 0.8.2-0ubuntu8
2007-10-13 07:45:23 status half-configured liblircclient0 0.8.2-0ubuntu8
2007-10-13 07:45:23 status installed liblircclient0 0.8.2-0ubuntu8
2007-10-13 07:45:23 configure lirc 0.8.2-0ubuntu8 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:23 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status unpacked lirc 0.8.2-0ubuntu8
2007-10-13 07:45:24 status half-configured lirc 0.8.2-0ubuntu8
2007-10-13 07:45:25 status installed lirc 0.8.2-0ubuntu8
2007-10-13 07:45:25 configure python-apt 0.7.3.1ubuntu3 0.7.3.1ubuntu3
2007-10-13 07:45:25 status unpacked python-apt 0.7.3.1ubuntu3
2007-10-13 07:45:26 status half-configured python-apt 0.7.3.1ubuntu3
2007-10-13 07:45:26 status installed python-apt 0.7.3.1ubuntu3
2007-10-13 07:45:26 configure guidance-backends 0.8.0svn20070928-0ubuntu6 0.8.0svn20070928-0ubuntu6
2007-10-13 07:45:26 status unpacked guidance-backends 0.8.0svn20070928-0ubuntu6
2007-10-13 07:45:26 status half-configured guidance-backends 0.8.0svn20070928-0ubuntu6
2007-10-13 07:45:28 status installed guidance-backends 0.8.0svn20070928-0ubuntu6
2007-10-13 07:45:28 configure displayconfig-gtk 0.3.7 0.3.7
2007-10-13 07:45:28 status unpacked displayconfig-gtk 0.3.7
2007-10-13 07:45:28 status half-configured displayconfig-gtk 0.3.7
2007-10-13 07:45:29 status installed displayconfig-gtk 0.3.7
2007-10-13 07:45:29 configure pidgin-data 1:2.2.1-1ubuntu4 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status unpacked pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status unpacked pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status half-configured pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status installed pidgin-data 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 configure libpurple0 1:2.2.1-1ubuntu4 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status unpacked libpurple0 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status half-configured libpurple0 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status installed libpurple0 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 configure pidgin 1:2.2.1-1ubuntu4 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status unpacked pidgin 1:2.2.1-1ubuntu4
2007-10-13 07:45:29 status half-configured pidgin 1:2.2.1-1ubuntu4
2007-10-13 07:45:30 status installed pidgin 1:2.2.1-1ubuntu4
2007-10-13 07:45:31 configure gaim 1:2.2.1-1ubuntu4 1:2.2.1-1ubuntu4
2007-10-13 07:45:31 status unpacked gaim 1:2.2.1-1ubuntu4
2007-10-13 07:45:31 status half-configured gaim 1:2.2.1-1ubuntu4
2007-10-13 07:45:31 status installed gaim 1:2.2.1-1ubuntu4
2007-10-13 07:45:31 configure gdm 2.20.0-0ubuntu4 2.20.0-0ubuntu4
2007-10-13 07:45:31 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:31 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:31 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:31 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:32 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status unpacked gdm 2.20.0-0ubuntu4
2007-10-13 07:45:33 status half-configured gdm 2.20.0-0ubuntu4
2007-10-13 07:45:37 status installed gdm 2.20.0-0ubuntu4
2007-10-13 07:45:37 configure libartsc0 1.5.8-0ubuntu1 1.5.8-0ubuntu1
2007-10-13 07:45:37 status unpacked libartsc0 1.5.8-0ubuntu1
2007-10-13 07:45:37 status half-configured libartsc0 1.5.8-0ubuntu1
2007-10-13 07:45:37 status installed libartsc0 1.5.8-0ubuntu1
2007-10-13 07:45:37 configure libarts1c2a 1.5.8-0ubuntu1 1.5.8-0ubuntu1
2007-10-13 07:45:37 status unpacked libarts1c2a 1.5.8-0ubuntu1
2007-10-13 07:45:37 status half-configured libarts1c2a 1.5.8-0ubuntu1
2007-10-13 07:45:37 status installed libarts1c2a 1.5.8-0ubuntu1
2007-10-13 07:45:37 configure kdelibs-data 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2007-10-13 07:45:37 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:38 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status half-configured kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status installed kdelibs-data 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 configure kdelibs4c2a 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2007-10-13 07:45:39 status unpacked kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:45:40 status unpacked kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:45:40 status half-configured kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:45:40 status installed kdelibs4c2a 4:3.5.8-0ubuntu1
2007-10-13 07:45:40 configure libgl1-mesa-glx 7.0.1-1ubuntu3 7.0.1-1ubuntu3
2007-10-13 07:45:40 status unpacked libgl1-mesa-glx 7.0.1-1ubuntu3
2007-10-13 07:45:40 status half-configured libgl1-mesa-glx 7.0.1-1ubuntu3
2007-10-13 07:45:40 status installed libgl1-mesa-glx 7.0.1-1ubuntu3
2007-10-13 07:45:40 configure ttf-dejavu-core 2.19-1ubuntu3 2.19-1ubuntu3
2007-10-13 07:45:40 status unpacked ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:45:40 status unpacked ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:45:40 status half-configured ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:45:42 status installed ttf-dejavu-core 2.19-1ubuntu3
2007-10-13 07:45:42 configure ttf-dejavu-extra 2.19-1ubuntu3 2.19-1ubuntu3
2007-10-13 07:45:42 status unpacked ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:45:42 status unpacked ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:45:42 status half-configured ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:45:42 status installed ttf-dejavu-extra 2.19-1ubuntu3
2007-10-13 07:45:43 configure ttf-dejavu 2.19-1ubuntu3 2.19-1ubuntu3
2007-10-13 07:45:43 status unpacked ttf-dejavu 2.19-1ubuntu3
2007-10-13 07:45:43 status half-configured ttf-dejavu 2.19-1ubuntu3
2007-10-13 07:45:43 status installed ttf-dejavu 2.19-1ubuntu3
2007-10-13 07:45:43 configure xserver-xorg-input-synaptics 0.14.6-0ubuntu10 0.14.6-0ubuntu10
2007-10-13 07:45:43 status unpacked xserver-xorg-input-synaptics 0.14.6-0ubuntu10
2007-10-13 07:45:43 status half-configured xserver-xorg-input-synaptics 0.14.6-0ubuntu10
2007-10-13 07:45:43 status installed xserver-xorg-input-synaptics 0.14.6-0ubuntu10
2007-10-13 07:45:43 configure xserver-xorg-video-intel 2:2.1.1-0ubuntu8 2:2.1.1-0ubuntu8
2007-10-13 07:45:43 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu8
2007-10-13 07:45:43 status half-configured xserver-xorg-video-intel 2:2.1.1-0ubuntu8
2007-10-13 07:45:43 status installed xserver-xorg-video-intel 2:2.1.1-0ubuntu8
2007-10-13 07:45:44 configure libglu1-mesa 7.0.1-1ubuntu3 7.0.1-1ubuntu3
2007-10-13 07:45:44 status unpacked libglu1-mesa 7.0.1-1ubuntu3
2007-10-13 07:45:44 status half-configured libglu1-mesa 7.0.1-1ubuntu3
2007-10-13 07:45:44 status installed libglu1-mesa 7.0.1-1ubuntu3
2007-10-13 07:45:44 configure mesa-utils 7.0.1-1ubuntu3 7.0.1-1ubuntu3
2007-10-13 07:45:44 status unpacked mesa-utils 7.0.1-1ubuntu3
2007-10-13 07:45:44 status half-configured mesa-utils 7.0.1-1ubuntu3
2007-10-13 07:45:44 status installed mesa-utils 7.0.1-1ubuntu3
2007-10-13 07:45:44 trigproc libc6 2.6.1-1ubuntu9 2.6.1-1ubuntu9
2007-10-13 07:45:44 status half-configured libc6 2.6.1-1ubuntu9
2007-10-13 07:45:51 status installed libc6 2.6.1-1ubuntu9
2007-10-13 11:03:48 startup archives unpack
2007-10-13 11:03:54 install libdvdcss2 <none> 1.2.9-2medibuntu4
2007-10-13 11:03:54 status half-installed libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:54 status unpacked libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:54 status unpacked libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:55 startup packages configure
2007-10-13 11:03:55 configure libdvdcss2 1.2.9-2medibuntu4 1.2.9-2medibuntu4
2007-10-13 11:03:55 status unpacked libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:55 status half-configured libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:55 status installed libdvdcss2 1.2.9-2medibuntu4
2007-10-13 11:03:55 status triggers-pending libc6 2.6.1-1ubuntu9
2007-10-13 11:03:55 trigproc libc6 2.6.1-1ubuntu9 2.6.1-1ubuntu9
2007-10-13 11:03:55 status half-configured libc6 2.6.1-1ubuntu9
2007-10-13 11:03:58 status installed libc6 2.6.1-1ubuntu9

---

### Post by obscure411 on 2007-10-13
Also, just did a echo `uname -r` to verify I am running on the 2.6.22-13-generic kernel right now.

---

### Post by superm1 on 2007-10-14
Folks,

I just popped an ivtv card (PVR-250MCE) in my mythbuntu install that is fully up to date (with archive.ubuntu.com as a mirror).  Sound works exactly as expected.  

Perhaps you need to check out if something has gone wonky in myth, or where things went south.

A quick test is to install ivtv-utils.

In one terminal window open up

```
mplayer /dev/video0
```

In another, type

```
ivtv-tune -c NUMBER
```

You may need to set the appropriate broadcast/cable table though still in addition to the -c.

---

### Post by laga on 2007-10-14
I wonder if this is related: [https://bugs.launchpad.net/bugs/152494](https://bugs.launchpad.net/bugs/152494)

---

### Post by superm1 on 2007-10-14
> **laga said:**
> I wonder if this is related: [https://bugs.launchpad.net/bugs/152494](https://bugs.launchpad.net/bugs/152494)
Well this being the case, any of you guys encountering the audio issue can you check dmesg?
Do this, and paste its output:

```
dmesg | grep ivtv
```

---

### Post by obscure411 on 2007-10-15
My primary hard drive went south late Saturday night.  I'm going to rebuild with a new HD after work today - I'll let you know what I find.

---

### Post by obscure411 on 2007-10-18
Just an FYI - since the rebuild yesterday post-HD failure, everything is good with IVTV.

---

