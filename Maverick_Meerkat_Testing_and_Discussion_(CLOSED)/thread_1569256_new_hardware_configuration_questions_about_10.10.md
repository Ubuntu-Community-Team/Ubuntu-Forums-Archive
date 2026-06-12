---
title: "new hardware configuration questions about 10.10"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2010-09-06
Hello,

back from step one, I would like to ask some questions concerning the beta 10.10 version of ubuntu. I won't hassle so straight ahead:

1) I have a...graphics card...
```
lspci -nn | grep VGA
```
> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5670] [1002:68d8]

```
glxinfo | grep vendor
```
> server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project

```
fglrxinfo
```
> fglrxinfo: command not found

this card, without a xorg.conf file is working very smooth, testing it for a day, except if I try to use compiz. Doing so I get errors like:

```
compiz
```
> compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

Q1: Is it possible that compiz will work with this graphics card?

Q2: Do I need to install anything else?
(having already tried:
```
sudo apt-get purge nvidia*
```
```
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```) with no avail.

Q3: Is it that this card will work flawlessly with the final version of 10.10? I do ask because I'm completely new to ati cards.

2) Having:
```
aplay -l
```
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I can have a pretty good sound, yet I cannot hear the rear speakers. With:
```
alsamixer
```
I get:
> cannot open mixer: No such device

Does anyone have any similar problems? I would really like my rear speakers to work back again.

3) And something final:
Have you activated bluetooth support on maverick? Clicking that icon in the begging was starting the daemon, yet with some updates from synaptic this ceased to happen.

I would be very glad if someone with greater experience with this issues could lend a hand!

Regards!

---

### Post by cariboo on 2010-09-06
Are you offered a closed source drive in System->Administration->Hardware Drivers?

You don't have to do anything with Nvidia or Intel drivers.

The /etc/X11/xorg.conf file you created should show you what driver you are currently using.

---

### Post by Claus7 on 2010-09-06
Hello,

first of all thanks for your response.

The message I get when I choose:
System->Administration->Additional (and not hardware) Drivers is:
> No proprietary drivers are in use for this system.

As I mentioned, I removed xorg.conf so the result of the command:
```
less /etc/X11/xorg.conf
```
is
> /etc/X11/xorg.conf: No such file or directory

which is logical I guess.

*cariboo907* said:
You don't have to do anything with Nvidia or Intel drivers.

With nvidia drivers I might not have to do anything, yet with ati ones (ati and intel are the same?)?

Regards!

---

### Post by cariboo on 2010-09-06
No ATI/AMD is not the same as Intel. If you have an ATI/AMD chipset, use ATI/AMD drivers.

---

### Post by Claus7 on 2010-09-07
Hello,

so either using the fglrx like here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or just downloading the driver from the amd web site. 

Reading also here:
[http://ubuntuforums.org/showthread.php?t=1561685](http://ubuntuforums.org/showthread.php?t=1561685)

I think we might have to wait a little bit more rod 3D full support, yet is seems to be worth the wait.

Any ideas on the other questions?

Regards!

---

### Post by jppr on 2010-09-07
I can´t undestand why must configure X-systems cos system do it automatically. I installed today Nvidia-current driver and boot system and everything works fine without any conf systems.

---

### Post by VMC on 2010-09-07
> ATI Technologies Inc Redwood [Radeon HD 5670] [1002:68d8]
This is the only one you need to concerned yourself with at the moment.
Does 10.10 bot up? If not try adding "radeon.modeset=0" to linux line.

---

### Post by Claus7 on 2010-09-07
Hello,

> **jppr said:**
> I can´t undestand why must configure X-systems cos system do it automatically. I installed today Nvidia-current driver and boot system and everything works fine without any conf systems.

I think because with one open source driver you can comprise many different graphics cards to work with it.

> **VMC said:**
> This is the only one you need to concerned yourself with at the moment.
Does 10.10 bot up? If not try adding "radeon.modeset=0" to linux line.

It is booting more than ok. And the 3D (weak) test I do with the gears is working more than smoothly. What does not work is the compiz mode. I cannot enable it. I suppose that I have to install the proprietary drivers, except if I have to wait for the stable version of 10.10.

Regards!

---

### Post by Claus7 on 2010-09-07
Hello,

could I ask also the difference between fglrx and Catalyst? Both are ati proprietary drivers?

EDIT:ATI Catalyst is a utility software driver package for ATI Radeon products for Microsoft Windows operating systems and Linux, on 32- and 64-bit x86 processors. (source wikipedia) That way someone can make configurations on the ati cards.

Regards!

---

### Post by Claus7 on 2010-09-10
Hello,

about sound, things are that the configurations need a lot of tweaking. If things settle (restart a couple of times), then I think that I will have a clearer view of the issue, yet all my speakers now are working. 

Regards!

PS: Since my Desktop is working pretty well, I won't tamper with it for now, just for compiz. Maybe later...

---

### Post by Claus7 on 2010-09-12
Hello,

this is what I have come up, up to now...

Regards!

---

### Post by Claus7 on 2010-09-17
Hello,

in order to make microphone to work as well, then I had to choose the options listed in the attachments provided.

In mic2.png when I was touching my mic, I was able to see movement in the squares (bars) with blue colour.

Regards!

(Applications->Sound and Video-> Sound Recorder was an example of succeeding configuring mic as well).

---

### Post by Claus7 on 2010-09-17
Hello,

and finally...bluetooth...

Unfortunately I had not kept good notes on this so the steps would be a little bit vague, yet this is what I have come up to now:

1) Type the command:
```
lsusb | grep tooth
```

if this produces an output, that means that your usb blue-tooth device is recognised by your ubu box.

Here I have to say that in some ports of my motherboard (close to the mouse), this device was not always recognised, so I changed usb port.

2) Having this device recognised then I installed via synaptic the following packages:

> 2010-09-17 22:03:14 install samba <none> 2:3.5.4~dfsg-1ubuntu7
2010-09-17 22:03:17 install libpam-smbpass <none> 2:3.5.4~dfsg-1ubuntu7
2010-09-17 22:11:42 install libapr1 <none> 1.4.2-3ubuntu1
2010-09-17 22:11:43 install libaprutil1 <none> 1.3.9+dfsg-3build1
2010-09-17 22:11:44 install libaprutil1-dbd-sqlite3 <none> 1.3.9+dfsg-3build1
2010-09-17 22:11:45 install libaprutil1-ldap <none> 1.3.9+dfsg-3build1
2010-09-17 22:11:46 install apache2.2-bin <none> 2.2.16-1ubuntu3
2010-09-17 22:11:47 install libapache2-mod-dnssd <none> 0.6-2
2010-09-17 22:28:26 install gnome-user-share 2.30.0-0ubuntu2 2.30.0-0ubuntu3

found them from history of synaptic via the command: ```
cat /var/log/dpkg.log* | grep "\ install\ " | sort
```

Having done that and rebooted I was able to configure things from System-> Preferences-> Bluetooth and then Receive files without getting the message *personal file sharing* package was not properly installed or something (this package was found by synaptic by typing exactly the message I got in italics - check out if it is the same).

And somehow like that things worked.

Regards!

---

