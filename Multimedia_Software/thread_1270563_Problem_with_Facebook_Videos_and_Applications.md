---
title: "Problem with Facebook Videos and Applications"
date: 2009-09-19
forum: Multimedia Software
---

### Post by serhat on 2009-09-19
Hello,
I cannot watch most videos in facebook and some applications (like farmviile) does not work. 


What might be the reason of this problem?

OS: Ubuntu 9.04
Web Browser: Firefox 3.5.3

i have installed "ubuntu-restricted-extras", "adobe-flashplugin" and "sun-java6-bin"

---

### Post by rtyb on 2009-09-20
.

---

### Post by ubunyou on 2009-09-27
I had this problem on hardy heron 8.04 and just fixed it by:

1) Removing existing install

Use Synaptic (System > Administration > Synatptic Package Manager) to remove flash plugins currently installed. Search around for flashplugin. I had adobe-flashplugin, flashplugin-nonfree installed.

I also found a libflashplugin.so in my mozilla plugins directory (i.e., /home/moops/.mozilla/firefox/plugins) which i deleted, just so i was starting fresh.

I tried reinstalling flashplugin-nonfree using both Synaptic and apt-get because the package is recommended in a few posts and it sounds like it is 'the right way' to install the firefox flash plugin.

The flashplugin-nonfree install using both synaptic and apt-get was failing with a HTTP 404 (the file is not there so you cant download it) when attempting to download from:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

A working version of the .deb package can be downloaded from the adobe website. This one worked for me.

2) So either follow the links on the adobe site and download the .deb package, or 
download it using wget:

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb

```

3) Once the file is saved somewhere you have to install it manually using the dpkg command and the path to the downloaded .deb file.
I will assume you saved it in your home directory and your username is moops.

```

dpkg -i /home/moops/install_flash_player_10_linux.deb

```

4) This might say there are missing dependancies. 
dpkg doesn't install dependencies for you, so you'll have to do it yourself.
The dependencies can be found by looking at the output of the dpkg command. See below, I was missing libnspr4-dev and libnss3-dev:

```

root@kyle-ubuntu:~# dpkg -i /home/kyle/downloads/flash/install_flash_player_10_linux.deb
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 217866 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../install_flash_player_10_linux.deb) ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libnspr4-dev; however:
  Package libnspr4-dev is not installed.
 adobe-flashplugin depends on libnss3-dev; however:
  Package libnss3-dev is not installed.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin

```


In my case there were two missing dependencies.
There could be more or less missing dependencies on your system.
Just note them and then run apt-get to install them:

```

agt-get install libnspr4-dev libnss3-dev

In my case this command also correctly identified that adobe-flashplugin needed to be configured and everthing worked. output below:

root@kyle-ubuntu:~# apt-get install libnspr4-dev libnss3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  libnspr4-dev libnss3-dev
0 upgraded, 2 newly installed, 0 to remove and 33 not upgraded.
1 not fully installed or removed.
Need to get 514kB of archives.
After this operation, 2900kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libnspr4-dev libnss3-dev
Install these packages without verification [y/N]? y
Get:1 http://security.ubuntu.com hardy-security/main libnspr4-dev 4.7.5-0ubuntu0.8.04.1 [259kB]
Get:2 http://security.ubuntu.com hardy-security/main libnss3-dev 3.12.3.1-0ubuntu0.8.04.2 [255kB]
Fetched 514kB in 2s (181kB/s)
Selecting previously deselected package libnspr4-dev.
(Reading database ... 217871 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.5-0ubuntu0.8.04.1_i386.deb) ...
Selecting previously deselected package libnss3-dev.
Unpacking libnss3-dev (from .../libnss3-dev_3.12.3.1-0ubuntu0.8.04.2_i386.deb) ...
Setting up libnspr4-dev (4.7.5-0ubuntu0.8.04.1) ...
Setting up libnss3-dev (3.12.3.1-0ubuntu0.8.04.2) ...
<b>Setting up adobe-flashplugin (10.0.32.18-1) ...</b>

```

If adobe-flashplugin was not configured when you installed the dependencies, then run the dpkg command again.

```

dpkg -i /home/moops/install_flash_player_10_linux.deb

```

Hope this helps.

---

