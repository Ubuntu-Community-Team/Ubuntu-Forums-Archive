---
title: "Xorg-server 1.10 will soon be out"
date: 2011-01-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-12
Right now a snapshot 1.9.99.901 is available from xorg-edgers PPA (Natty).
Of course that will bring a new ABI breakage.
Xserver-xorg-core provides new virtual packages:
- xorg-input-abi-12.1
- xorg-video-abi-9
All drivers now in repo (also in xorg-edgers PPA) still depend on
- xorg-input-abi-11 (input drivers)
- xorg-video-abi-8 (video drivers).

So, the coming week will be interesting.

The stable release xorg-server 1.10 will perhaps be released in late February.

---

### Post by ronacc on 2011-01-12
a good opertunity to sharpen our console skills :P

---

### Post by ronacc on 2011-01-12
a good opportunity to sharpen our console skills :P

double post, sorry

---

### Post by andrek on 2011-01-12
Oh boy, ati fglrx breakage is coming.

---

### Post by plun on 2011-01-12
Broken for the moment for me......

```
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo

```

---

### Post by Harry33 on 2011-01-12
> **plun said:**
> Broken for the moment for me......

```
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo

```

Right, exactly this.
The ABI breakage: means every driver will have to be built for new ABI.
And yes, that means nvidia-current and fglrx too.
However, nvidia-current might work if the lines:

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

is added into xorg-conf.

---

### Post by Harry33 on 2011-01-12
Here you will find more about the xorg-server 1.10:
[http://www.phoronix.com/scan.php?page=news_item&px=ODg3OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODg3OQ)

---

### Post by Harry33 on 2011-01-13
An update to xorg-edgers PPA.

Xserver-xorg-core provides new virtual packages:
- xorg-input-abi-12.1
- xorg-video-abi-9
All new input and video drivers now depend on virtual packages:
- xorg-input-abi-12.1 (input drivers)
- xorg-video-abi-9 (video drivers).

This means you can upgrade to
xserver-xorg-core, xserver-common (1.9.99.901)
and all input and video drivers must be upgraded too (synaptic does this automatically).

But the fun goes on.
Package xserver-xorg depends on virtual packages:
xserver-xorg-video-9 and xserver-xorg-input-12
which are not provided anywhere.
There is also an error: xserver-xorg-input-12 should be xserver-xorg-input-12.1.

So as those dependencies are not met, the optional dependencies are
xserver-xorg-input-all and xserver-xorg-video-all.
Installing this means all input and video drivers are installed whether you need them or not.
And the packages xserver-xorg-input-all and xserver-xorg-video-all cannot then be uninstalled.
In a normal system they should be.

---

### Post by plun on 2011-01-14
Well.... still broken for me...

Aptitude gives this.  (compiz is known, I am running the GIT version instead)

```
The following packages have unmet dependencies:
  unity: Depends: compiz-core-abiversion-20101111 which is a virtual package.
  xserver-xorg-video-openchrome: Depends: xorg-video-abi-8.0 which is a virtual package.
  nvidia-current: Conflicts: nvidia-current-modaliases but 260.19.29-0ubuntu1~xup1 is installed.
  libwebkitgtk-1.0-common: Conflicts: libwebkit-1.0-common but 1.2.5-0ubuntu3 is installed.
  xserver-xorg-video-siliconmotion: Depends: xorg-video-abi-8.0 which is a virtual package.
  libindicator2: Breaks: libindicator1 but 0.3.15-0ubuntu3 is installed.
  compiz-fusion-plugins-extra: Depends: compiz-core-abiversion-20101111 which is a virtual package.
  xserver-xorg-video-vmware: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-input-wacom: Depends: xorg-input-abi-11.0 which is a virtual package.
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-11.0 which is a virtual package.

```

---

### Post by Harry33 on 2011-01-14
Plun, do you need all these:
 xserver-xorg-video-openchrome: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-video-siliconmotion: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-video-vmware: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-input-wacom: Depends: xorg-input-abi-11.0 which is a virtual package.
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-11.0 which is a virtual package.

---

### Post by Harry33 on 2011-01-14
OK, I tried this new xorg-server_1.9.99.901.
I do not have any drivers installed I don't need.
So I have only these:
nvidia-current_260.19.29
xserver-xorg-input-evdev
xserver-xorg-video-fbdev
xserver-xorg-video-vesa

What I found out was that nvidia-current does not support the new ABI (video ABI 9).
Not even if put "IgnoreABI" "True" in xorg.conf.
I had to use recovery mode to reverse the xorg installation. 

So, because I am not going to install nouveau nor nv, I will wait. :D

---

### Post by plun on 2011-01-14
> **Harry33 said:**
> Plun, do you need all these:
 xserver-xorg-video-openchrome: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-video-siliconmotion: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-video-vmware: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-input-wacom: Depends: xorg-input-abi-11.0 which is a virtual package.
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-11.0 which is a virtual package.

No... 

Only the Synaptics and nVidia package troubles me.

I am too lazy for a tty ppa-purge if it fails.;)

Does it work for you ?

---

### Post by plun on 2011-01-14
Followup.....

Well... xorg-edgers and xorg 1.10 is pure crap for an nVidia owner for this moment.

Vesa seems also be broken... ??

Downgraded with an ppa-purge.

This happens

[http://paste.ubuntu.com/554182/](http://paste.ubuntu.com/554182/)

---

### Post by Harry33 on 2011-01-14
> **plun said:**
> Followup.....
Well... xorg-edgers and xorg 1.10 is pure crap for an nVidia owner for this moment.
Vesa seems also be broken... ??
Downgraded with an ppa-purge.
This happens
[http://paste.ubuntu.com/554182/](http://paste.ubuntu.com/554182/)

Hi Plun,

No it definitely does not work. Not even if I use "IgnoreABI" "true" in xorg.conf.
Nvidia-current_260.19.29 simply does not support xorg-server 1.10 series.
I can see the segfaulting from your log.

Xorg-edgers are updating right now xorg_7.5-6ubuntu8 packages. There are errors in numbering the ABI on those packages (ought to be input ABI 12.1, but it is 12).

I will not try this before there is a new nvidia driver.
This 260.19.29 works damn well this xserver 1.9 series.

---

### Post by plun on 2011-01-14
> **Harry33 said:**
> Hi Plun,

No it definitely does not work. Not even if I use "IgnoreABI" "true" in xorg.conf.
Nvidia-current_260.19.29 simply does not support xorg-server 1.10 series.
I can see the segfaulting from your log.

Xorg-edgers are updating right now xorg_7.5-6ubuntu8 packages. There are errors in numbering the ABI on those packages (ought to be input ABI 12.1, but it is 12).

I will not try this before there is a new nvidia driver.
This 260.19.29 works damn well this xserver 1.9 series.

As you can see from my logfile I used ignoreABI..... I knows that..;)
(nvidia-freak)

I also tested with vesa as driver but it also failed.....  so its crap for the moment for an nvidia-owner.

(Nouveau is nothing for me)

---

### Post by Harry33 on 2011-01-14
> **plun said:**
> 
...
(Nouveau is nothing for me)

Same here, only nvidia-current will do.

---

### Post by plun on 2011-01-15
Xorg-Edgers desription changed

> == New in Xserver 1.10 - 2011/01/14 ==

This ppa now contains Xserver 1.10 RC1. This comes with a new input and video ABI. The open drivers have been rebuilt against these new ABIs, but the proprietary drivers cannot be. **Furthermore, a packaging bug in the nvidia & fglrx drivers means that X will happily upgrade, leaving you with broken proprietary drivers.**

Solutions often comes up within this forum from more advanced Gentoo users.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by cariboo on 2011-01-15
I got this email yesterday.

> Corrected, via a combination of rebuilds, a new wacom upstream version,
and (temporarily) dropping -siliconmotion and -openchrome from
xserver-xorg-video-all.

The proprietary fglrx and nvidia drivers obviously don't work against
this new Xserver.  Due to packaging bugs, they *also* won't prevent the
upgrade going through, leaving a non-functioning X until they are
removed.

Please remove the fglrx or nvidia drivers before testing.

If you're not using a proprietary driver, -siliconmotion, or
-openchrome, xorg-edgers is good to go.


---

### Post by Harry33 on 2011-01-15
> **cariboo907 said:**
> I got this email yesterday.

I just don't get this playing with meta packages
xserver-xorg-video-all and xserver-xorg-input-all.
Edgers PPA I am talking about is for Natty dev.
I don't think any beginner will install edgers PPA. It really is for experienced users.

So why don't they build more carefully their packages.
Right now the package xserver-xorg_7.5-6ubuntu8~raof2 depends on either
xserver-xorg-video-all or xserver-xorg-video-9 and either
xserver-xorg-input-all or xserver-xorg-input-12.

That means you have to have one of those both.
If only one video driver would provide virtual package xserver-xorg-video-9, you don't need to have xserver-xorg-video-all installed.
Likewise, if only one input driver would provide virtual package xserver-xorg-input-12, you do not have to have xserver-xorg-input-all installed.

However,
edgers PPA offers video drivers that do not provide xserver-xorg-video-9 (instead they provide the old ABI xserver-xorg-video-8) and
edgers PPA offers input drivers that do not provide xserver-xorg-input-12 (instead they provide the old ABI xserver-xorg-input-11.
This is simply a mistake/error.

Now both packages xserver-xorg-video-all and xserver-xorg-input-all must be installed and with them all video drivers and input drivers.

Well I have only one graphics card (Nvidia) and I do not need any of those 25 graphics drivers that are now compulsory because of the damn dependency there.

---

### Post by zika on 2011-01-16
```
~$ sudo apt-get dist-upgrade 
[sudo] password for ****..***: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  empathy nautilus-sendto-empathy xserver-xorg-input-all xserver-xorg-input-synaptics
The following NEW packages will be installed:
  yelp-xsl
The following packages have been kept back:
  gimp libseed0 python-webkit rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins yelp
The following packages will be upgraded:
  empathy-common xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa
12 upgraded, 1 newly installed, 4 to remove and 7 not upgraded.
Need to get 4,246 kB of archives.
After this operation, 397 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
```
~$ sudo aptitude dist-upgrade 
The following NEW packages will be installed:
  libwebkitgtk-1.0-0{a} libwebkitgtk-1.0-common{ab} yelp-xsl{a} 
The following packages will be upgraded:
  empathy empathy-common gimp libseed0 nautilus-sendto-empathy python-webkit rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati 
  xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa yelp 
21 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.8 MB of archives. After unpacking 29.5 MB will be used.
The following packages have unmet dependencies:
  libwebkitgtk-1.0-common: Conflicts: libwebkit-1.0-common but 1.2.5-2~mmwkt2 is installed.
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-11.0 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     epiphany-browser            
2)     libwebkit-1.0-2             
3)     libwebkit-1.0-common        
4)     midori                      
5)     xserver-xorg-input-all      
6)     xserver-xorg-input-synaptics



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

I'm, still, waiting...
Any advice?

---

### Post by plun on 2011-01-16
> **zika said:**
> 

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.[/code]

I'm, still, waiting...
Any advice?

Well.... for me it broke.....;)

input-all and synaptics.....:confused:



If it brakes, from a tty  (network connected)

```
sudo ppa-purge xorg-edgers
```

---

### Post by zika on 2011-01-16
> **plun said:**
> Well.... for me it broke.....;)

input-all and synaptics.....:confused:



If it brakes, from a tty  (network connected)

```
sudo ppa-purge xorg-edgers
```
I'll, still, wait a bit longer...

---

### Post by Harry33 on 2011-01-16
> **zika said:**
> 
...
```
~$ sudo aptitude dist-upgrade 
The following NEW packages will be installed:
  libwebkitgtk-1.0-0{a} libwebkitgtk-1.0-common{ab} yelp-xsl{a} 
The following packages will be upgraded:
  empathy empathy-common gimp libseed0 nautilus-sendto-empathy python-webkit rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati 
  xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa yelp 
21 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.8 MB of archives. After unpacking 29.5 MB will be used.
The following packages have unmet dependencies:
  libwebkitgtk-1.0-common: Conflicts: libwebkit-1.0-common but 1.2.5-2~mmwkt2 is installed.
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-11.0 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     epiphany-browser            
2)     libwebkit-1.0-2             
3)     libwebkit-1.0-common        
4)     midori                      
5)     xserver-xorg-input-all      
6)     xserver-xorg-input-synaptics

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

I'm, still, waiting...
Any advice?

You can very well upgrade the libwebkitgtk-packages (which will remove the old libwebkit-packages and possibly the old epiphany) + also upgrade rhythmbox, empathy and yelp (now using libwebkitgtk and not any more xulrunner).

But where do those xserver-xorg packages come from?
Do you have xorg-edgers PPA enabled?
What is the version of the new xserver-xorg-core to upgrade to?

If you have desktop pc, you don't need any other input driver than xserver-xorg-evdev.

---

### Post by zika on 2011-01-16
> **Harry33 said:**
> You can very well upgrade the libwebkitgtk-packages (which will remove the old libwebkit-packages and possibly the old epiphany) + also upgrade rhythmbox, empathy and yelp (now using libwebkitgtk and not any more xulrunner).

But where do those xserver-xorg packages come from?
Do you have xorg-edgers PPA enabled?
What is the version of the new xserver-xorg-core to upgrade to?

If you have desktop pc, you don't need any other input driver than xserver-xorg-evdev.Yes, epiphany and the rest is not important. Yes, xorg-edgers...Waiting for 1.10 to get complete...
I'm on verge of (m)ending this myself, but...
2:1.9.99.901

---

### Post by Harry33 on 2011-01-16
> **zika said:**
> Yes, epiphany and the rest is not important. Yes, xorg-edgers...Waiting for 1.10 to get complete...
I'm on verge of (m)ending this myself, but...
2:1.9.99.901

Right, edgers version (xserver 1.0 rc1) may work if you have one the open drivers installed. It seems you have an AMD-ATI graphincs card, so the newest xserver-xorg-video-radeon from edgers PPA is what you need.

I have Nvidia card and ATM it is a strong no-no to xserver 1.10.

---

### Post by Harry33 on 2011-01-16
> **zika said:**
> Yes, epiphany and the rest is not important. Yes, xorg-edgers...Waiting for 1.10 to get complete...
I'm on verge of (m)ending this myself, but...
2:1.9.99.901

Right, edgers version (xserver 1.0 rc1) may work if you have one the open drivers installed. It seems you have an AMD-ATI graphincs card, so the newest xserver-xorg-video-radeon from edgers PPA is what you need.

I have Nvidia card and ATM it is a strong no-no to xserver 1.10.

---

### Post by plun on 2011-01-16
Well, I tried it again.....:D

First I read this:
[http://www.phoronix.com/scan.php?page=news_item&px=OTAxNg](http://www.phoronix.com/scan.php?page=news_item&px=OTAxNg)

And then Bryce Harringtons mailing-list message
[https://lists.ubuntu.com/archives/ubuntu-x/2011-January/001022.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-January/001022.html)

And then I filed a bug.....:---)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/703688](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/703688)

---

### Post by zika on 2011-01-16
Duplicate due to some problem at UF...

---

### Post by zika on 2011-01-16
> **Harry33 said:**
> Right, edgers version (xserver 1.0 rc1) may work if you have one the open drivers installed. It seems you have an AMD-ATI graphincs card, so the newest xserver-xorg-video-radeon from edgers PPA is what you need.

I have Nvidia card and ATM it is a strong no-no to xserver 1.10."I am" completely up-to-date with xorg-edergs, for a quite a lot time ago, and nothing other than open-source drivers on my machine for a long time...
1.9.99.901 is the latest available (not yet applicable) for Natty...

---

### Post by zika on 2011-01-17
Took a a dive with aptitude dist-upgrade, installed xserver-xorg-input-{all, synaptic} afterwards, and... survived...

---

