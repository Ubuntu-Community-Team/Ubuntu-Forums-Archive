---
title: "Automount in Ubuntu but not in Xubuntu"
date: 2012-12-10
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Rodney9 on 2012-12-10
How come Ubuntu 12.10 sees and auto mounts my Sony Xperia S mobile phone but Xubuntu 12.10 does not see it at all ?

I wish to use Xubuntu as my laptop is to slow .

Rodney

---

### Post by typhoon_tip on 2012-12-11
I think it has more to do with Nautilus File Manager than Ubuntu itself. Ubuntu uses Nautilus, whereas Xubuntu uses Thunar if I'm not wrong. Find some guidelines to install Nautilus in Xubuntu instead of Thunar, should not slow things down much.

---

### Post by mörgæs on 2012-12-11
Changed the thread title to a more informative one.

---

### Post by Rodney9 on 2013-03-08
Anyone found an answer for how to mount Sony Xperia S in Xubuntu ?

lsusb outputs - Bus 004 Device 003: ID 0fce:0169 Sony Ericsson Mobile Communications AB 

mtp-detect
libmtp version: 1.1.4

Listing raw device(s)
Device 0 (VID=0fce and PID=0169) is a SONY Xperia S.
   Found 1 device(s):
   SONY: Xperia S (0fce:0169) @ bus 4, dev 3
Attempting to connect device(s)
LIBMTP PANIC: Could not open session! (Return code 8195)
  Try to reset the device.
Unable to open raw device 0
OK.

---

### Post by Rodney9 on 2013-03-08
I tried [https://launchpad.net/~langdalepl/+archive/gvfs-mtp](https://launchpad.net/~langdalepl/+archive/gvfs-mtp) ppa's but they don't work either.

At least I found a work around by using [WiFi Explorer]("https://play.google.com/store/apps/details?id=com.dooblou.WiFiFileExplorer&hl=en") also trying Airdroid.

Rodney

---

### Post by Rodney9 on 2013-03-08
[AirDroid]("https://play.google.com/store/apps/details?id=com.sand.airdroid") works very well, much easier to use and more secure.

Rodney

---

### Post by S X S on 2013-03-12
> **Rodney9 said:**
> I tried [https://launchpad.net/~langdalepl/+archive/gvfs-mtp](https://launchpad.net/~langdalepl/+archive/gvfs-mtp) ppa's but they don't work either.

At least I found a work around by using [WiFi Explorer]("https://play.google.com/store/apps/details?id=com.dooblou.WiFiFileExplorer&hl=en") also trying Airdroid.

Rodney

hi,

** installed this ppa:**

** $ sudo add-apt-repository ppa:langdalepl/gvfs-mtp **

**installed all gvfs packages** exept for the debug and development packages

** rebooted**

** i connected my xperia s lt26i**

**opened a terminal** and typed:

** $ gvfs-mount -li**

wich showed me the device and some info:

[COLOR=#008000]Volume(0): LT26i
  Type: GProxyVolume (GProxyVolumeMonitorMTP)
  ids:
   unix-device: '/dev/bus/usb/001/015'
  [/COLOR][COLOR=#0000ff]activation_root=[/COLOR][COLOR=#ff0000]mtp://[usb:001,015]/[/COLOR][COLOR=#008000]
  themed icons:  [multimedia-player]
  symbolic themed icons:  [folder-remote-symbolic]  [folder-remote]  [folder]
  can_mount=1
  can_eject=0
  should_automount=1[/COLOR]

[B]copied the[COLOR=#0000ff] activation_root[/COLOR] value:
[/B]
[COLOR=#ff0000]mtp://[usb:001,015]/[/COLOR]

and **opened thunar **

**opened the menu "go" en then the menu option "open location"**

[B]pasted the copied [COLOR=#0000ff]activation_root[/COLOR] value:
[/B]
 [COLOR=#ff0000]mtp://[usb:001,015]/[/COLOR]

and_ thunar opened my** [COLOR=#40e0d0]xperia s[/COLOR]** and showed the directory [COLOR=#40e0d0]**"internal memory"**[/COLOR]_ with all the content of the device

[COLOR=#00ff00]_** so it works for me **_[/COLOR]

but you have to check the **[COLOR=#ff8c00]correct[/COLOR] [COLOR=#0000ff]root_activation[/COLOR] value [COLOR=#ff8c00]every time[/COLOR] you connect the phone** and have to do this manually every time you want to access the phone because it can change

---

### Post by Rodney9 on 2013-03-12
Well done and Thank You, I just tried that and yes indeed it works.

Rodney

---

### Post by S X S on 2013-03-12
nice.

you can also try this:

[http://forum.xda-developers.com/showthread.php?t=1744878](http://forum.xda-developers.com/showthread.php?t=1744878)

it is an app that makes your internal storage appear as a mass storage device  but it requires a rooted device 

wich i have but you maybe not 

i also tested it and it works well it is like putting a usb-memorystick in your usb port and the storage immediatly shows up

:-)

---

### Post by seshomaru samma on 2013-04-05
S X S's solution worked for me as well. Maybe a script could be written to automated it

---

