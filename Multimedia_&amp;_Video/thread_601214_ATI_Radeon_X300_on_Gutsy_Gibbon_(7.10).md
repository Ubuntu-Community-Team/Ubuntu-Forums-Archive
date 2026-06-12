---
title: "ATI Radeon X300 on Gutsy Gibbon (7.10)"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by GordonFrohm on 2007-11-03
Please help me get my X300 running on Ubuntu 7.10 !!
And don't just tell me "Huh, noob loot at teh sticky u idiot it tellz u wut 2 do..."
Cause none of the tutorials I've found have worked. Tell me **exactly** what to do!!

---

### Post by kwagster on 2007-11-03
what's running?


my x300 ran out of the box...

---

### Post by GordonFrohm on 2007-11-04
I've no idea what you are talking about. Sorry.

---

### Post by Unnicknamed on 2007-11-04
I got this card and It's working great with me.

Could you elaborate and tell us what problem are you experiencing?

---

### Post by GordonFrohm on 2007-11-04
Well, I want to have some 3d Eyecandy for my Ubuntu. (compiz fusion, you know)

But I need to activate the drivers for my ATI card, the Radeon X300 first.
But every time I try to do that, I get this error:
[img]http://i78.photobucket.com/albums/j101/GordonFrohm/Screenshot.png[/img]

I've tried to follow all of the available Tutorials, but they've all failed for me at some point. (first I needed to manually download and install the packages and then with some I couldn't even install them because they were incompatible or something...)

---

### Post by cjbailey1 on 2007-11-04
I had that a couple of days ago and it turned out that the synaptic package manager was not set up to use the proxy where I was.  Go into Synaptic Package Manager and check the network settings in there, making sure you can download and install packages.

Regards,
   Chris.

---

### Post by GordonFrohm on 2007-11-04
But I've no Idea what I'm supposed to put in as Proxy... :confused:

Also this will just help me download the Packages right?

---

### Post by cjbailey1 on 2007-11-04
Apologies.  Do you use a proxy at all?  If not then you won't have to fill anything in there - that was just the problem with my setup.

If you go to:
System --> Administration --> Synaptic Package Manager

Can you download any packages in there?

---

### Post by BrandonBan6 on 2007-11-05
GordonFrohm

I am experiencing a similar problem with my ATI X300. If I enable the ATI Restricted Drivers I can adjust my resolution, pick any graphic screen saver and most things work just fine. The exception in "most things" being compiz. If I disable the restricted drivers, compiz runs.....but only in an 800X600 res and high graphic screensavers and such do not run. I realize this is a n00b question.......but I'm missing a link and needs some help!

Any thoughts/Advice out there?

---

### Post by pmorton on 2007-11-07
Advice:
This card is a big headache. Dump it and buy  NVIDIA. Try the NX7300.

---

### Post by Yellow Pasque on 2007-11-07
> **BrandonBan6 said:**
> I am experiencing a similar problem with my ATI X300. If I enable the ATI Restricted Drivers I can adjust my resolution, pick any graphic screen saver and most things work just fine. The exception in "most things" being compiz.
Any thoughts/Advice out there?
Compiz and AIGLX are only supported in the latest ATI driver (8.42.3). You'll need to get it off ATI's site, because it's not in the Ubuntu repo. If you do get Compiz running, don't expect it to be miraculously smooth. This is ATI's first attempt at it and performance isn't that great.

> Advice:
This card is a big headache. Dump it and buy NVIDIA. Try the NX7300.
Nonsense. If one was choosing between the two, this might apply, but there's no reason to ditch perfectly good hardware. The ATI driver has lagged behind nvidia for a long time, but it's made some big strides lately.

---

### Post by Yellow Pasque on 2007-11-07
To answer Gordon's question, you need to enable the restricted/proprietary repo in your Software Sources options, found under System -> Administration -> Software Sources

---

### Post by eye208 on 2007-11-07
> **GordonFrohm said:**
> Well, I want to have some 3d Eyecandy for my Ubuntu. (compiz fusion, you know)

But I need to activate the drivers for my ATI card, the Radeon X300 first.
Your screenshot looks like Compiz is already running. I can see drop shadows and transparent window borders.

---

### Post by GordonFrohm on 2007-11-09
that's because I have this turned on:
[img]http://i78.photobucket.com/albums/j101/GordonFrohm/Screenshot-1.png[/img]

Also thanks, I will try your advice Temüjin.

---

### Post by GordonFrohm on 2007-11-09
Okay, so I took the advice and tried [this](http://ubuntuforums.org/showthread.php?t=575843) tutorial again.
Last time I was stuck at Step3 Line2 because it gave me this Error saying "Couldn't find package dh-make".
This time I got pas that line. Only to be stuck at the next.
I typed in this:
```
debconf libstdc++5 linux-headers-generic
```
and as a response got this:
```
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat: Permission denied
```
So I thought:"Heh, 'Permission denied' eh? The good old 'Sudo' command should do the job.
```
sudo debconf libstdc++5 linux-headers-generic
```
Well I was wrong.
```
Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm 

line 58
```

Any ideas??

---

### Post by eye208 on 2007-11-09
> **GordonFrohm said:**
> that's because I have this turned on:
I am not sure whether it is clear to you: Ubuntu's desktop effects _is_ Compiz. You are already running it (through the open source Radeon driver).

Are you sure you want to switch to the binary driver? Its AIGLX support might be a bit flakey at this point.

---

### Post by macmils on 2007-11-09
Have you tried using Envy by Alberto Milone?

It's a graphical app and will install the lastest ATI and NVidia drivers for you (depending which you select).
I used it to get my x300 working and it worked straight off.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) is the project page for it and tells you how to use it and what to download

---

### Post by GordonFrohm on 2007-11-09
> **eye208 said:**
> I am not sure whether it is clear to you: Ubuntu's desktop effects _is_ Compiz. You are already running it (through the open source Radeon driver).

Are you sure you want to switch to the binary driver? Its AIGLX support might be a bit flakey at this point.

Well I meant Compiz Fusion. You know, the one where you have the 3d Desktop-cube and other effects.
I want to use it to get Emeralds Theme Manager to get the Vista Theme.

I'm kind of confused but I think people also call it Beryl and not Compiz Fusion...

Also macmils, yes I have tried it before, but back then I didn't have the restricted/proprietary repo enabled. So I'll give it a try.

---

### Post by eye208 on 2007-11-09
> **GordonFrohm said:**
> Well I meant Compiz Fusion. You know, the one where you have the 3d Desktop-cube and other effects.
Compiz Fusion is just a collection of plugins for Compiz. You are already running Compiz, i.e. you can enable the Fusion effects at any time. You don't have to switch video drivers to do so. The Radeon driver will do just fine.

There are several tools to help configure Compiz, e.g. "compizconfig-settings-manager". Use it to enable additional eye candy. The Radeon X300 is not exactly the world's fastest video card, but it will handle most of the effects well.

---

### Post by pmorton on 2007-11-11
> **Temüjin said:**
> Compiz and AIGLX are only supported in the latest ATI driver (8.42.3). You'll need to get it off ATI's site, because it's not in the Ubuntu repo. If you do get Compiz running, don't expect it to be miraculously smooth. This is ATI's first attempt at it and performance isn't that great.


Nonsense. If one was choosing between the two, this might apply, but there's no reason to ditch perfectly good hardware. The ATI driver has lagged behind nvidia for a long time, but it's made some big strides lately.

Sorry, but  there is a reason to dump 'perfectly good' hardware. I took me a very long time some weeks ago to get this card working.  And then last week it all broke, for no reason. Compiz and the X300 screwed up X, and I spend the whole day once more with how-to's, flgx's, proprietory drivers, Envy, compiling ATI modules, editing xorg.conf, blah-de-blah - but got nowhere. I then spent  $40 on a NVidia GEFORCE 7200GS 128MB PCI-E.  It works with Compiz Fusion perfectly - Gutsy even invites you to click-install the proprietary 3-D driver.

Whatever strides AMD is making, they aren't helping X300 owners. The original poster can save himself  a lot of the pain and time - unless of course he can take a fair measure of the first and possesses any amount of the second - in which case he can continue  trying to sort out this card.  Personally, I'd give it to someone with Windows.

---

### Post by eye208 on 2007-11-12
> **pmorton said:**
> I then spent  $40 on a NVidia GEFORCE 7200GS 128MB PCI-E.  It works with Compiz Fusion perfectly - Gutsy even invites you to click-install the proprietary 3-D driver.
With an ATI card you needn't install any driver at all to make Compiz work. It will run out of the box with the OSS driver. The "problem" here was that the OP was running Compiz without even knowing.

Nvidia drivers break all the time. You can read the stories right here in the forum. The version included with Gutsy has Xvideo in a half-broken state. I can point you to the Launchpad bug report if you are interested. Unless Nvidia releases their GPU specs the way ATI/AMD did, ATI cards will soon become the #1 choice on Linux. Dumping them right now would be stupid.

The Radeon X300 wasn't made for games anyway, so it is pointless to install the binary driver right now. Ubuntu 8.04 will include the latest fglrx with stabilized AIGLX support anyway, but until then, going with the OSS Radeon driver makes perfect sense.

---

### Post by jkblacker on 2007-11-12
I think parts of this thread are in danger of turning into a flamewar.

As for my x300 card, well... I had compiz fusion running very well on the open driver, but switched to the restricted driver from the repos to get ET running fine, although this for some reason meant losing all compiz effects with no way to get them back! (Every time I do, I get the error 'Composite extension not available'.)

---

### Post by eye208 on 2007-11-12
> **jkblacker said:**
> I think parts of this thread are in danger of turning into a flamewar.
It's because of the Nvidia fanboys who see every ATI-related thread as an opportunity to advertise their favorite brand. I am an Nvidia user myself (7900 GS), but this fanboy attitude makes me sick. Those guys should focus on fixing their own driver problems first.

---

### Post by Cochise on 2007-11-12
I also have an ATi x300, i have compiz running using ATi's newest driver, 8.42.3, im able to run Enemy Territory:Quake Wars, Doom3, Quake4, etc. What i did is below, the instructions are taken from various blogs:

1. Remove Xgl.

      sudo apt-get remove xserver-xgl

2. Remove the old driver.

      Go to System &#8594; Administration &#8594; Restricted Drivers Manager and choose disable.

      Alternatively remove it yourself:

      sudo apt-get remove xorg-driver-fglrx

3. Delete old fglrx debs.

      sudo rm -f /usr/src/fglrx-kernel*.deb

4. Blacklist old fglrx module.

      sudo gedit /etc/default/linux-restricted-modules-common

      And insert fglrx - it should look like this then:

      DISABLED_MODULES="fglrx"

5. Download the driver installer to your home folder.

      wget [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)

6. Install necessary packages.

      sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

7. Create .deb packages.

      bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

8. Install .deb packages.

      sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb 

     (Your .deb names may be different, check first)

9. Compile kernel module.

      sudo m-a prepare,update

      sudo m-a build,install fglrx-kernel

      sudo depmod

10. Set up the driver.

      sudo gedit /etc/X11/xorg.conf

      Make sure "fglrx" is set for the Driver in the Section "Device".

      if present, remove

      Section "Extensions"

              Option        "Composite"        "0"     # or "Disable"

      EndSection

      &

      Section "ServerFlags"

              Option        "AIGLX"            "off"

      EndSection

11. Run the aticonfig tool.

      sudo aticonfig --overlay-type=Xv

12. Add the driver to compiz whitelist.

      sudo gedit /usr/bin/compiz

      Change:

      # Driver whitelist
      WHITELIST="nvidia intel ati radeon i810"

     # Driver whitelist
     WHITELIST="fglrx nvidia intel ati radeon i810"

13. Reboot.

This works perfectly for me so hopefully it'll help others.

---

### Post by pmorton on 2007-11-14
..

---

### Post by pmorton on 2007-11-14
> **eye208 said:**
> . Unless Nvidia releases their GPU specs the way ATI/AMD did, ATI cards will soon become the #1 choice on Linux. Dumping them right now would be stupid. The Radeon X300 wasn't made for games anyway, so it is pointless to install the binary driver right now....The Radeon X300 wasn't made for games anyway, so it is pointless to install the binary driver right now.

I have nothing against AMD/ATI and most certainly not against their recent steps to open up their specs. But that doesn't suddenly cure all  the problems with existing hardware. I've no illusions about NVidia, but I can tell you the 7200GS is cheap and it works.  I'm a 'fanboy'  (what a nasty word) of nothing  - apart perhaps of Ubuntu - and even then I'm a promiscuous admirer.  I'm not enamoured, though, of the X300 card, which has given me such trouble in the past.

In fact, the last sentence I quote above, if correct, confirms what I've said. If you want 3D acceleration, use something else. Or stick with the open driver until U8 comes along. Or keep reading the forum. All fine by me.

---

### Post by eye208 on 2007-11-14
> **pmorton said:**
> In fact, the last sentence I quote above, if correct, confirms what I've said. If you want 3D acceleration, use something else.
That's not what the sentence said. If you want games, use something else. The X300 is running Compiz with the OSS driver just fine. That's what the OP was asking for. Your suggestion to dump the card is a solution looking for a problem.

---

