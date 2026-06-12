---
title: "Ubuntu 11.04 ATI Driver Installation"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by trendyabinash on 2011-04-08
I have installed Ubuntu 11.04 after getting my new graphic card ATI Radeon HD 5450
I have downloaded the driver file ati-driver-installer-11-3-x86.x86_64.run

Now i am little confused about how to install it.

Any help in this regard is really appreciated

---

### Post by howefield on 2011-04-08
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by godhika on 2011-04-08
That driver won't be any use to you since it doesn't support the current xorg. If you want the proprietary driver go to system ---> administration ----> additional drivers. There you can install a (at the moment) Ubuntu exclusive version which works.
Cheers

---

### Post by Hakunka-Matata on 2011-04-08
> **trendyabinash said:**
> I have installed Ubuntu 11.04 after getting my new graphic card ATI Radeon HD 5450
I have downloaded the driver file ati-driver-installer-11-3-x86.x86_64.run

Now i am little confused about how to install it.

Any help in this regard is really appreciated

Now you're talking buddy, smart and responsible: starting a new thread on the current problem.  I have a similar problem but it's not with the graphics driver, rather with an audio driver under 11.04 32bit Desktop installed Release of Ubuntu running on my Acer Aspire One (Model A110) netbook, resulting in the inability of successfully executing a 'SKYPE TEST CALL.  
The AOA's internal mic does not activate, (IT works flawlessly on same machine with all previous Releases.)


It will get fixed, it may become the catalyst for me to force feed myself into writing (modifying) the code myself.  I'll have to be much older than I presently feel however before that will take place, as there are many tasks sitting @HIGHER priority in my personal processor's queue now.
HK

---

### Post by Hakunka-Matata on 2011-04-08
> **trendyabinash said:**
> I have installed Ubuntu [COLOR=Red]_**11.04 **_[/COLOR]after getting my new graphic card ATI Radeon HD 5450
I have downloaded the driver file ati-driver-installer-11-3-x86.x86_64.run

Now i am little confused about how to install it.

Any help in this regard is really appreciated

PLEASE (squared) INDICATE VERSION accurately - 32bit or .amd64

Thorough reading of your post reveals the desired information, but what I see (and presumably and other person reading the post) at first read, is the ambiguous description of your installed OS.  

ps, I'm an editor at large

---

### Post by trendyabinash on 2011-04-08
> **godhika said:**
> That driver won't be any use to you since it doesn't support the current xorg. If you want the proprietary driver go to system ---> administration ----> additional drivers. There you can install a (at the moment) Ubuntu exclusive version which works.
Cheers

Sir i tried that too, it is on;y showing me my wireless card drivers. There is no ATI drivers shown.

And Hi Hukana, as per the word given to you, i am testing this beta

Mine is 32bit OS.

---

### Post by godhika on 2011-04-08
> **trendyabinash said:**
> Sir i tried that too, it is on;y showing me my wireless card drivers. There is no ATI drivers shown.

And Hi Hukana, as per the word given to you, i am testing this beta

Mine is 32bit OS.

OK, then try via the command line: ```
sudo apt-get install fglrx
```

---

### Post by trendyabinash on 2011-04-08
I guess i have messed up my system.

I tried installing the file i downloaded with the following codes

```

sudo sh ./ati-driver-installer-11-3-x86.x86_64.run --listpkg (to find whether it has natty support)
i saw it said it supports Ubuntu/natty
so next was
sudo sh ./ati-driver-installer-11-3-x86.x86_64.run --buildandinstallpkg Ubuntu/natty

```
it showed many things, downloaded some packages automatically and at end it failed.

i shut down my system, when i came back to start it..... it is not working

It says starting GNOME ................[ok]
Starting Usersplash ...................[ok]
stopping Usersplash ...................[ok]

then nothing :(
i can switch to tty1 and login but can not go to Unity Display :(

---

### Post by godhika on 2011-04-08
> **trendyabinash said:**
> I guess i have messed up my system.

I tried installing the file i downloaded with the following codes

```

sudo sh ./ati-driver-installer-11-3-x86.x86_64.run --listpkg (to find whether it has natty support)
i saw it said it supports Ubuntu/natty
so next was
sudo sh ./ati-driver-installer-11-3-x86.x86_64.run --buildandinstallpkg Ubuntu/natty

```
it showed many things, downloaded some packages automatically and at end it failed.

i shut down my system, when i came back to start it..... it is not working

It says starting GNOME ................[ok]
Starting Usersplash ...................[ok]
stopping Usersplash ...................[ok]

then nothing :(
i can switch to tty1 and login but can not go to Unity Display :(

Please read my first post again: catalyst 11.3 (the version you try to install) won't work with an up to date natty install. The only version which works is the version in the repositories. Ubuntu always gets an exclusive pre-release version from amd usually around beta which is more up to date then the versions they offer on their homepage. In other words: your version is to old. See this instructions: [http://ubuntuforums.org/showpost.php?p=10618166&postcount=1](http://ubuntuforums.org/showpost.php?p=10618166&postcount=1)

---

### Post by trendyabinash on 2011-04-08
ok so is there anyway i can restore my previous situation? like uninstall any broken graphic drivers ?
Because i am not able to start Ubuntu Desktop now :(

Or do i have to reinstall Ubuntu completely again ?

---

### Post by jfernyhough on 2011-04-08
To remove fglrx:

$ sudo apt-get purge fglrx
$ sudo rm /etc/X11/xorg.conf

reboot.

---

### Post by trendyabinash on 2011-04-09
> **jfernyhough said:**
> To remove fglrx:

$ sudo apt-get purge fglrx
$ sudo rm /etc/X11/xorg.conf

reboot.

ty very much sir, atleast i can see my desktop screen now

And it has been 3 days now still couldn't install graphic driver for this Natty. Plus i am not enjoying the unity desktop.

Going back to 10.10, hopefully it can load my graphic drivers

tyvm guys for the support.

---

### Post by rajeev1204 on 2011-04-09
Try this:


sudo apt-get install fglrx

and critical step sudo aticonfig --initial -f (without this step the driver wont create the xorg file entries.




reboot.Should work.I have a 5750 card myself.

---

### Post by trendyabinash on 2011-04-10
ty rajeev but i came back to 10.10..... better compartibilty. Not blaming 11.04, its only in beta.
But i like gnome better than Unity... way more customizeable and easy...maybe b'coz i am used to it.

ty for the support

---

### Post by rbrick49 on 2011-04-10
> **trendyabinash said:**
> ty rajeev but i came back to 10.10..... better compartibilty. Not blaming 11.04, its only in beta.
But i like gnome better than Unity... way more customizeable and easy...maybe b'coz i am used to it.

ty for the support my friend if you cant use a terminal to apt-get purge fglrx or whatever wait till the final release it might be much easier,everyone appears to be getting short fused I have been on a couple of occasionally myself like you said its a beta hang in there it will improve

---

### Post by Hakunka-Matata on 2011-04-11
You all have missed the easiest method yet to USE NATTY (11.04), and not use Unity at the same time.  Simply choose "CLASSIC" dress before logging in.

What am I talking about?, do this:

Go back to 11.04 and when you first boot after installing, make sure you set 'login procedure" to require typing in password, do not choose 'automatic' login.  

Then when presented with the login screen, look at the bottom line of your display, change the Style? to CLASSIC, you'll enjoy your maverick desktop with natty snappiness

Good Luck, I'll reboot, get the terminology correct if it isn't correct here now.  Good Luck, natty ROCKS

---

### Post by beew on 2011-04-11
> **trendyabinash said:**
> Sir i tried that too, it is on;y showing me my wireless card drivers. There is no ATI drivers shown.
.


Same here. I don't see any ATI driver from Jockey even though I am on a computer with an ATI card.

> ~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:d0000000-dfffffff memory:cfdf0000-cfdfffff ioport:9000(size=256) memory:cfe00000-cfefffff

I am not planning on installing the closed source driver since I install Natty on an external drive and I test it on different computers, however, "Additional Drivers" should detect and show the proprietary graphic driver.

---

### Post by P-I H on 2011-04-11
The X1200 series cards are not supported by the proprietary driver.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

### Post by tembares on 2011-04-19
Thank you for reading my question.

When I have NOT installed the prop. ATI driver I can use vgaswitcheroo/switch which is in /sys/kernel/debug/vgaswitcheroo/switch.
When I use vgaswitcheroo/switch I see my 2 cards (Intel i915 and ATI HD5450), but by switching to the ATI I come into textmode and nothing works anymore. In my opinion this is normal, because the driver's not installed.

So I installed the prop. ATI driver, but then vgaswitcheroo/switch is disappeared.

When I go to System->Preferences I see 2 ATI Catalyst Control Centers: administrator and w/o admin. When I choose one of them (does not matter which one I choose) I get this message:
****************************
[I]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.[/I]
****************************

I removed xorg.conf and did 'sudo aticonfig --initial -f' after installation the prop. ATI driver.

I have a HPTM2T 2100 CTO Touchsmart with switchable graphics; Intel i915 and ATI HD 5450.

**My question is: how can I switch between my 2 cards in Natty (in Maverick it's not possible) and/or does VGA switching work under Natty?**
With Maverick there's Ubuntu Control Center (however I did not install and use it, so I do not know if it should have worked), but I cannot get it installed under Natty.
**2nd question: does your solution above also work for a laptop with 2 video cards?**

I have added 'xforcevesa' in the GRUB-line. **Can this cause this problem?** I'll test it now without it.
ANSWER after test: No, it does not matter. Still the same situation.

To continue the story and testing:
bla:~$ sudo aticonfig --initial=check
Check: No fglrx section.
bla:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.

It seems FGLRX is installed, SYSTEM/ADMINISTRATION/ADDITIONAL DRIVERS it is activated.

What is going on?

EDIT 2:
bla:~$ aticonfig --list-adapters
* 0. 01:00.0 ATI Mobility Radeon HD 5000 Series

* - Default adapter

So, this means I am working on the ATI card now?
Why is HDMI not working and why can't I switch to it?

Thank you in advance

---

### Post by screaminj3sus on 2011-04-20
> **rajeev1204 said:**
> Try this:


sudo apt-get install fglrx

and critical step sudo aticonfig --initial -f (without this step the driver wont create the xorg file entries.




reboot.Should work.I have a 5750 card myself.
You shouldn't even need a xorg.conf at all in natty. This should enable it:

sudo apt-get install fglrx
sudo update-alternatives --config gl_conf (and select the line with fglrx)
sudo update-initramfs -u

---

