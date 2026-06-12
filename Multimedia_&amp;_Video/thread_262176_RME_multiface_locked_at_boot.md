---
title: "RME multiface locked at boot"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by damu on 2006-09-21
Most of the time , when I boot on Ubuntu, my RME multiface seems to be locked. It is not mounted , and the red led of 'host error" is on.
Normally, this red led is flashing till the RME multiface is recognised and mounted by the system.
The only way I have to go round that is to boot on Win XP, and then boot again in Ubuntu. If I boot twice in a row on  Ubuntu, it gest locked again.:confused: 

Any clue?

---

### Post by damu on 2006-12-06
I still have the same problem and didn't find any answer to it. I'd really like to solve this, as it seems to be really naf to dual boot just for that! 

Here is what I get with hdsploader in the console :

> damu@ubuntu:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : VIA 8237 with ALC850 at 0xe800, irq 209
Card 1 : Generic USB Audio Device    at usb-0000:00:10.0-2, full speed
Card 2 : RME Hammerfall DSP at 0x8a000000, irq 169
Upload firmware for card hw:2
Unable to open file '/usr/share/alsa/firmware/hdsploader/multiface_firmware_rev11.bin' for reading
damu@ubuntu:~$ 

---

### Post by damu on 2007-01-09
The last version of alsa that I could test on another distro solve the problem. For Ubuntu, let's hope that alsa wil be upgraded in feisty.

---

### Post by kijjaz on 2007-05-29
I was not sure what I did for the RME Multiface.. but it worked for me now in Ubuntu Feisty! -_-"
But what I did was:
I went to the main ALSA site ([http://www.alsa-project.org/](http://www.alsa-project.org/)),
downloaded Library, Utilities, Tools, Firmware sources from the page,
and compile them
(mainly by** ./configure**, **make**, **sudo make install** them)
I guess i was trying **sudo alsaconf **also (and choose hdsp)

then when i reboot, it seems ok -_-"
i'm not sure which parts are required to get it right -_-
i tried to do the whole process again, but still confused in its concepts.

---

### Post by kijjaz on 2007-05-31
I've got a new answer for loading RME Hammerfall Multiface successfully.

I'm on Ubuntu Feisty (new install this time! hahah)
what I did was this:

install **alsa-firmware-loader**, then restart -> firmware loading error.
(so the updated Multiface really needs a new version of Alsa Firmware)

visit [ALSA Website]("http://alsa-project.org"), from **Latest Software Releases** get the development release of **firmware**.
(currently version 1.0.14rc4)

unpack it and then comile & install by
[B]./configure
make
sudo make install[/B]

then restart -> Firmware loaded correctly.

---

### Post by jaskah on 2007-07-10
hello
i´m having the same problem in feisty, though it seemed that the hammerfall was booting ok for a while...but now it´s not.
anyways, my question is how exactly did you install the new firmware loaders? 
i ask because in the READ ME FILE of thealsa-firmware-1.0.14rc4 package the following is stated:

¨The recent ALSA driver supports the hotplug firmware loader.
As default, the package will install firmware data to the places for
both the old ALSA fw loader and the hotplug fw loader.  To disable
the installation of old ALSA fw loader data (if both ALSA and hotplug
fw loaders are available), pass --disable-loader to configure.
Similarly, to disable the hotplug fw loader data, pass
--disable-hotplug option.
For the old ALSA fw loader, specify the same prefix option given to
the alsa-tools configure script, too, in order to keep the
installation directories consistent.
The default directory for hotplug firmware data files is /lib/firmware.
(or if existing /lib/hotplug/firmware or /usr/lib/hotplug/firmware are 
found they are used)
You can change to another path via --with-hotplug-dir option.¨

did you first un-install the old loaders? if yes, how?

thanks for your help!

---

### Post by damu on 2007-07-10
----
edit 12/07/07 : nop doesn't work. I didn't reboot for a while on Ubuntustudio and gave it another try today to prepare a musical workshop coming soon, but no luck with my RME Hammerfall and cardbus. I am pretty sure it's been working at a point though. Perhaps an upgrade broke it...


[I]
I did a fresh install of Ubuntustudio a while ago to monitor this project and its evolution. I installed with synaptic the relevant package for RME (hdsploader, ect), reboot and that was it, my RME with cardbus was mounted. 

I have to mention though that I didn't upgrade to the latest drivers delivered by RME, which would definitely improve the performances (latency) of the soundcard on my WinXP sound studio but would probably brake the linux support...[/I]

---

### Post by jaskah on 2007-07-10
thanks for your reply.
i´ve installed the most current drivers (alsa-driver-1.0.14) and the most current firmware (alsa-firmware-1.0.14rc4).
now, the card loads at boot but the sound quality is bad, with lots of clicks. it sounds like a problem with the sample rate, but i can´t be sure.
i even get these clicks when i test the sound in the sound preferences panel. how can i change the system sample rate?
has anyone else experienced this?
by the way, the card works fine--without clicks and whatnot--in os x, so i know it´s not a problem with the multiface or the pcmcia card.

---

### Post by audiofill on 2007-07-11
I'm using RME Hammerfall and I'm not able to get ubuntustudio loading. The monitor says "no signal" an it freezes!! It's not the first time I'm using a "kind" of linux. I've used suse from 8.2 up to 10.1 and ubuntu from 5 up to now. All the times I don't have any problems up to now (7...). No chance to get a working system (in none of the modes...don't talking about the low latency mode,which causes a hang-up).
Please give me inspiration to come to your (the others) part of the installation.

TO SAY IT VERY CLEAR: IT'S THE FIRST TIME THAT I'VE GOT A BLACK MONITOR AFTER ALL THE UBUNTU AND OTHER LINUX DISTRIBUTORS:(

---

### Post by damu on 2007-07-11
I managed to get it working this way (already explained in this forum but with some few missing points :

-open synaptic (system/administration/synaptic) and search for the file 'libc6-dev' and install it if not alreday installed
-Once installed, close synaptic
-download the latest firmware from [alsa's website]("ftp://ftp.alsa-project.org/pub/firmware/")  in your home folder. For now it is the version  1.0.14.
-right click on the downloaded file and 'extract here'
-open a terminal ( applications/accessories/terminal)
-cd /the-path-to-the firmware-folder      (to make sure you get it right, go into your home folder, clic on the firmware folder that you just got, and on any of the files right-click/properties. In the window of properties, select and copy the location. Then paste this location in the terminal . Don't forget to leave a space in between cd and the-path-...
-./configure --prefix=/usr &&
-make
-make install
-reboot

Now you should be fine.

---

### Post by jaskah on 2007-07-12
hi
thanks for your reply.
i ended up doing a new install of feisty and with synaptic installed the following
alsa-firmware-loaders 1.0.13
alsa-tools-gui 1.0.13
the rme sounds really bad: lots of clicks and distortion. 
i know that i can solve the firmware-loader problem. 
what worries me is the poor sound quality. do you know what this could be?
one other thing: when i rollover the volume control applet above the desktop i get this strange message: System Sample Rate: -2147483648%
when i open the sound preferences panel (under system) down below under Default Mixer Tracks, below device (which is Hammerfall DSP (alsa mixer) there is listed System Sample Rate, as one of the tracks to control with the keyboard. strange.
i´m on a mac titanium g4 powerbook (ppc platform). in osx the card works flawlessly; good sound quality.

---

