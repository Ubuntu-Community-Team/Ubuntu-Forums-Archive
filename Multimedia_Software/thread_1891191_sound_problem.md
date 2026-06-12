---
title: "sound problem"
date: 2011-12-05
forum: Multimedia Software
---

### Post by treepete on 2011-12-05
hey, i'm having problems and i've tried stuff from other threads but a) it doesn't work or b) it makes no sense to me. so... if someone could help me, please, that would be rad.

i originally had problems but fixed them. then a system update brought them back. i've tried the original fix (which was upgrading the alsa script) among other things... but somewhere in there :) i screwed something up.

now it seems like the soundcard is not recognized. (it's a conexant something or other). i've looked in the bios but see nowhere to change anything to do with this.

where do i go from here?

thank you very much in advance.
V

ubuntu 10.10 on lenovog470

---

### Post by aeiah on 2011-12-05
where are the instructions you previously used? if they involved blacklisting a default module and loading your own compiled module, then you'd need to recompile it against the new kernel. or you could remove the blacklist entry - perhaps the newer kernel doesn't have the same issue. posting a link to the tutorial will make things clearer

---

### Post by treepete on 2011-12-06
thanks aeiah,

sorry... i should know by now to keep track of what i do... as it is i don't really know but here's something:

this is the original fix, that did not work this time
[http://ubuntuforums.org/showthread.php?t=1689548&highlight=update+alsa+driver](http://ubuntuforums.org/showthread.php?t=1689548&highlight=update+alsa+driver)

i believe things started to go wrong when i downloaded the driver from here [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)
(sorry, i can't find the thread)

when i tried to reinstall the linux image package it would not complete because of that.

when i uninstalled that driver, the linux image reinstalled.. but did not fix anything.

now, 
when i click the sound applet, it says "there are no devices to control..."
trying to open alsamixer results in a "no such file or directory" message
VLC says:  p, li { white-space: pre-wrap; } [COLOR=#FF0000]Potential ALSA version problem:[/COLOR]
 [COLOR=#000000]VLC failed to initialize your sound output device (if any).[/COLOR]
 [COLOR=#000000]Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue.[/COLOR]
[COLOR=#000000]banshee closes itself.[/COLOR]
[COLOR=#000000]sound recorder says: your audio capture settings are invalid[/COLOR]
[COLOR=#000000]etc[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]i really appreciate your help if you can. thanks again[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]V
[/COLOR]

---

### Post by treepete on 2011-12-07
this is the terminal readout from doing sudo apt-get upgrade:

Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-31-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3613.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up apt-utils (0.8.3ubuntu7.3) ...
Setting up apt-transport-https (0.8.3ubuntu7.3) ...
Setting up python-papyon (0.5.1-0ubuntu2.1) ...
Setting up update-manager-core (1:0.142.23.1) ...
Setting up update-notifier-common (0.105ubuntu1.1) ...
Setting up xserver-xorg-input-wacom (1:0.10.8-0ubuntu1.1) ...
Processing triggers for python-central ...
Setting up update-manager (1:0.142.23.1) ...
Processing triggers for python-central ...
Setting up update-notifier (0.105ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

(ps. how do i make one of those scroll windows within a thread?)

i don't know if this stuff is helping... just trying to provide as much info as i can. 

V

---

### Post by treepete on 2011-12-10
found a fix ^^^ 
i had to install linux-backports-modules-alsa-maverick-generic-pae through synaptic.
phew

V

---

