---
title: "HP Mini 110 audio stopped working with kernel 2.6.32.28 update"
date: 2011-01-29
forum: Multimedia Software
---

### Post by kuckunniwi on 2011-01-29
Hi,

First of all, I'm quite a newbie, so please be patient with me! 

 I'm running Kubuntu 10.04 amd64 on an HP Mini 110 3050ss. The audio didn't work out-of-the box, but I was able to find a solution ([http://elblogdeparq.blogspot.com/2010/09/sonido-en-hp-mini-110-ubuntu-1004.html]("http://elblogdeparq.blogspot.com/2010/09/sonido-en-hp-mini-110-ubuntu-1004.html") > page in Spanish)

I installed ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```, and found somewhere that it would be a good idea to block updates for this package to prevent having problems in the future:

```
sudo aptitude hold linux-backports-modules-alsa-lucid-generic
```

I'm starting to think this wasn't a very good idea...but live and learn, right? In the last security update, my kernel header were updated to v. 2.6.32.28. After reboot, I got the following message:

```
KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Output: HDA Intel (STAC92xx Digital)
Output: HDA Intel, STAC92xx Digital (IEC958 (S/PDIF) Digital Audio Output)
```

I tried to unblock alsa backport updates and update:
```

sudo aptitude unhold linux-backports-modules-alsa-lucid-generic
```

```
sudo aptitude update
```

After reboot, problem persisted, so I uninstalled linux-backports-modules-alsa-lucid-generic and went for reinstall, but get the following message:

```
$ sudo apt-get install linux-backports-modules-alsa-lucid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic: Depends: linux-backports-modules-alsa-2.6.32-28-generic but it is not installable
```

As the info already suggests, installation of "linux-backports-modules-alsa-2.6.32-28-generic" isn't possible:

```
$ sudo apt-get install linux-backports-modules-alsa-2.6.32-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-backports-modules-alsa-2.6.32-28-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-backports-modules-alsa-2.6.32-28-generic has no installation candidate

```

I tried uninstalling "linux-backports-modules-alsa-lucid-generic" andj running ```
$ sudo apt-get autoremove
```

then trying installation again, with no success. 

I've even tried falling back from kernel 2.6.32.28-generic to the old 2.6.32.27 version, under which I had no problems with the drivers, but still nothing.

I switched over to Ubuntu (from windows) about a year ago. I've been using a dual boot with Vista and Ubuntu since then, venturing less and less into Windows as I gained confidence in Ubuntu. For the last 6 months I have only used Windows for video edition & DVD authoring, tasks for which there are no GPL alternatives that suit my requirements. As fond as I've grown of Ubuntu & Kubuntu, switching over to Windows (even if it's just temporary) just because I can't resolve a driver issue is out of the question. I shall persist until the problem is solved! (with your help)

Any suggestions/workarounds would be terribly helpful 

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

```

```
$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


**[COLOR="Red"]Edit:[/COLOR]** When updating system (I updated kernel headers to current version), I get 1 blocked update:

```
linux-backports-modules-alsa-lucid-generic - 2.6.32.28.31(amd64)

Type: Blocked update
Issued: 01/14/11
New version: linux-backports-modules-alsa-lucid-generic-2.6.32.28.31
Updates: linux-backports-modules-alsa-lucid-generic-2.6.32.27.29 
```

Snooping around the web, I found this: [http://kubuntuforums.net/forums/index.php?topic=3103678]("http://kubuntuforums.net/forums/index.php?topic=3103678")

From what I understood, this means that one of its dependencies is not satisfied yet, and the full update hasn't yet been released...right? Why would they release the kernel images and header packages but not the alsa backport modules? Audio is unusable until the update can be installed...

I've also tried:

```
sudo aptitude safe-upgrade

```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get check
```

```
sudo apt-get -f install
```

```
$ sudo echo "linux-backports-modules-alsa-lucid-generic install" | dpkg --set-selections
dpkg: operation requires read/write access to dpkg status area
$ sudo echo "linux-backports-modules-alsa-2.6.32-28-generic install" | dpkg --set-selections
dpkg: operation requires read/write access to dpkg status area
```

```
$ sudo apt-get purge linux-backports-modules-alsa-lucid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-backports-modules-alsa-lucid-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I know I'm messing around blindly, but I'm pretty lost here. Does anyone have any ideas of what I could try? I hope the information I've provided is useful and either helps to discard possibilities, or clearly points out a mistake of mine that has caused all of this in the first place :P

Thanks!!!

---

### Post by fhj on 2011-01-30
See bug report [https://bugs.launchpad.net/ubuntu/+bug/708586](https://bugs.launchpad.net/ubuntu/+bug/708586)

This problem has been widely reported.

A work around is to default to the previous kernel:

If you add these lines to /etc/default/grub:

```
[INDENT]GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true[/INDENT]
```

Then run update-grub2.  
Reboot
Select the previous kernel

Then that kernel will be selected by default on next reboot.

I needed this work around as the machines my family support run Skype/ Google Talk.  Sound is sort of needed for that ;)

Now too wait patiently for the alsa backports ...

- frank

---

### Post by kuckunniwi on 2011-01-30
Thanks for the info, frank! I tried it, but it didn't work. 

I had a little trouble with the GRUB kernel selection, as I'm running a clean install of Kubuntu with no other installed operating systems, so Grub2 boots directly to login prompt. As it turns out, holding down the "shift" key interrupts the boot process and displays the menu ([http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")).

The problem being, although I've successfully defaulted to the previous kernel, before posting on ubuntuforums I had already uninstalled *linux-backports-modules-alsa-lucid-generic*, thinking a reinstall might fix the problem, and am currently unable to install them:

```
 $ sudo apt-get install linux-backports-modules-alsa-lucid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic: Depends: linux-backports-modules-alsa-2.6.32-28-generic but it is not installable
E: Broken packages 
```

I guess it's no audio for me 'til the alsa backports...

(My card reader has also stopped working, so I'll just have to be patient...)

Thanks for the assistence and patience!

---

### Post by lidex on 2011-01-30
I'm thinking that if you have the meta-package installed, it will always try to update to the latest kernel version of backports. You can do a couple of things. I would recommend (if you don't want to upgrade to maverick) using your package manager to find any instances of that kernel, kernel headers, and backports, including the meta-package and completely removing them. then reboot and do this. Try updating your alsa-driver-modules.
Using a Terminal,add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**

---

### Post by kuckunniwi on 2011-01-31
Thanks Lidex! That worked like a charm! I'll copy the repository & alsa driver modules installation command to my "Ubuntu code collection" :-)

---

### Post by kuckunniwi on 2011-01-31
> Thanks Lidex! That worked like a charm! I'll copy the repository & alsa driver modules installation command to my "Ubuntu code collection"

No one fix is perfect (although I'm thankful all the same, don't get me wrong!). Before, I could control speaker and headphone volumes independently from Kmixer: I had a channel for speakers (front) and one for headphones (mysteriously, the "surround" channel - odd but functional); now (and I've tried all channels, adding the ones that weren't visible by default)) I cannot, so If I listen to anything on headphones, audio output comes through the speakers too (as I figured out based on the not-so-pleased looks on other train passengers' faces).

But for now, I have audio, and for that I thank you, Lidex :)

I'm guessing I'll have to wait 'til the alsa backport modules update is released to get my audio running entirely back to normal (or are there any better options?) When the time comes, I may need a few pointers removing current drivers and installing the other ones.

Would this be correct?

```
sudo apt-get remove linux-alsa-driver-modules-$(uname -r)
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

**Thanks, once again, for your help!** Each day that goes by, I'm gladder and gladder I switched over from MS Windows. Hopefully, as time goes by, I'll be able to give others a hand too in exchange for all the tremendously helpful feedback I'm getting... :D

---

### Post by lidex on 2011-01-31
That might be solved by adding a model quirk to alsa-base.conf
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output

---

### Post by kuckunniwi on 2011-02-01
Lidex,
Thanks so much for your help. Having used nothing but windows until little over a year ago, and never having received any proper tech support (for hardware OR software I had paid for!), nor from microsoft of hardware vendors, it still comes as quite a shock to me when people so altruistically take their own time to help someone out. I know I'm beginning to repeat myself, but I wouldn't feel comfortable if I didn't at least show some appreciation; and more importantly, a certain degree of commitment to learn the ways of Linux so I can begin to solve problems by my own means and not always have to rely on other people helping me out :)

Here's the output from the alsa info script:

[URL="http://www.alsa-project.org/db/?f=ecf668d758609623a9d588i890817d62d3c602c0c"]


http://www.alsa-project.org/db/?f=ecf668d758609623a9d588890817d62d3c602c0c[/URL]

By the way...have I already said thank you? ;)

---

### Post by kuckunniwi on 2011-02-01
Issue has been solved in last update. Was able to install *```
linux-backports-modules-alsa-2.6.32-28-generic
```*, default to current kernel (Lucid), and audio is back to normal.  

Now, all I have left is to resolve the SD card reader functionality, which also stopped working under kernel 2.6.32-28. But that's another story...:-p

Thanks! All the best from Barcelona, Spain!

---

