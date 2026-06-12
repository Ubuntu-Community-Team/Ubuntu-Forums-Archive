---
title: "Does ATI Catalyst work yet?"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Cam! on 2011-04-11
I haven't been up on Ubuntu for a while. I installed a fresh daily build of Natty a few days ago, and noticed that a popup for restricted drivers was available. I'm still using the default FOSS drivers, but after many OS updates that had Xorg in them, what's the status on official ATI Radeon HD drivers for 11.04? If it helps, I'm using an ATI Radeon HD 6850 (1GB) graphics card.

---

### Post by Harry33 on 2011-04-11
> **Cam! said:**
> I haven't been up on Ubuntu for a while. I installed a fresh daily build of Natty a few days ago, and noticed that a popup for restricted drivers was available. I'm still using the default FOSS drivers, but after many OS updates that had Xorg in them, what's the status on official ATI Radeon HD drivers for 11.04? If it helps, I'm using an ATI Radeon HD 6850 (1GB) graphics card.

Those ATI high-end cards can be difficult with open source drivers.
You may try the fglrx (8.840) in Natty repos. It is a prerelease of the Catalyst 11.4 and specially made for Ubuntu. That should support xserver 1.10.

Here is some more info from Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ)

---

### Post by PaulW2U on 2011-04-11
Post deleted.

---

### Post by Cam! on 2011-04-11
> **Harry33 said:**
> Those ATI high-end cards can be difficult with open source drivers.
You may try the fglrx (8.840) in Natty repos. It is a prerelease of the Catalyst 11.4 and specially made for Ubuntu. That should support xserver 1.10.

Here is some more info from Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ)

How do I install them properly, without anything going wrong? Do I have to disable my current drivers or do something first?

---

### Post by Harry33 on 2011-04-11
> **Cam! said:**
> How do I install them properly, without anything going wrong? Do I have to disable my current drivers or do something first?

You can use Jockey for the installation.
So for gnome desktop (Ubuntu) install the packages jockey-gtk and jockey-common.

---

### Post by godhika on 2011-04-11
> **Harry33 said:**
> You can use Jockey for the installation.
So for gnome desktop (Ubuntu) install the packages jockey-gtk and jockey-common.

Those packages should be installed by default. Go to system--->administration or search via the dash in Unity for Additional drivers. Everything else is self-explanatory.

---

### Post by screaminj3sus on 2011-04-12
They work as long as you use the version in the ubuntu repos. Its a special pre release version. So just use that restricted drivers pop-up you did, its the proper way to do it. Systam > Administration > Additional Drivers, hit activate.

---

### Post by janaro on 2011-04-12
I tried the jockey command and it only came up with a modem drivers.

Do I need to have installed the ATI foss drivers on previously?

My ATI problem is the followin: I need to install the drivers because my screen is too dark and when putting up the brightness on the keyboard, I loose that brightness each time the portable goes into sleep...

---

### Post by rbrick49 on 2011-04-12
> **Cam! said:**
> I haven't been up on Ubuntu for a while. I installed a fresh daily build of Natty a few days ago, and noticed that a popup for restricted drivers was available. I'm still using the default FOSS drivers, but after many OS updates that had Xorg in them, what's the status on official ATI Radeon HD drivers for 11.04? If it helps, I'm using an ATI Radeon HD 6850 (1GB) graphics card.
default foss drivers i thought they were mesa drivers jut do in a terminal sudo apt-get install fglrx and see what happens if it doesnt work post the results from the terminal here copy paste

---

### Post by flying_surprise on 2011-04-12
The performance in compiz using this special version of fglrx isn't good, or what do you say?

For me it is very laggy, although it is workable. Also when switching workspace, windows are not getting updated when switching back. I have to minimize/maximize everything after a workspace switch in order to get any updates in windows.

Anyone else having this problem?

In maverick everything worked like a charm, even 1080p x264 video playback.

My graphics card:
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

---

### Post by qamelian on 2011-04-12
My netbook with a a 6850HD won't even boot to GDM with the FGLRX driver in Natty. It worked fine in Maverick though. Fortunately, the performance of the open source drivers is just fine for my purposes on this little beast.

---

### Post by janaro on 2011-04-13
sudo apt-get install fglrx says 0 updates, 0 will install, 0 to be delete and 0 no updates...

I did a fglrxinfo to see if the Ati drivers were installed and got a segment violation.

Pls help!

---

### Post by flying_surprise on 2011-04-16
I saw today when updating that there were a new version of fglrx.

Still the same lag after reboot though.

---

### Post by rbrick49 on 2011-04-16
sudo apt-get purge fglrx

---

### Post by Harry33 on 2011-04-16
> **flying_surprise said:**
> I saw today when updating that there were a new version of fglrx.


Fglrx_8.840-0ubuntu2 is not a new version, merely a new build with some changes.
One of which is the prevention from building module for any new "non-ubuntu" kernel.

> Changelog:
* debian/dkms.conf.in:
    - Prevent DKMS builds with kernels newer 2.6.38.
  * debian/fglrx-dev.links:
    - Remove links to libfglrx_pp.so and libfglrx_tvout.so since we
      don't ship these libraries any more.
  * debian/rules:
    - Get rid of add-fglrx-prefix or remove-fglrx-prefix targets.


---

### Post by screaminj3sus on 2011-04-16
> **flying_surprise said:**
> The performance in compiz using this special version of fglrx isn't good, or what do you say?

For me it is very laggy, although it is workable. Also when switching workspace, windows are not getting updated when switching back. I have to minimize/maximize everything after a workspace switch in order to get any updates in windows.

Anyone else having this problem?

In maverick everything worked like a charm, even 1080p x264 video playback.

My graphics card:
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

Turn off sync to vblank in compiz. It is on my default in natty (was off in mav I believe) and I found it to cause a lot of lag with fglrx, especially if you have tear-free desktop enabled in catalyst.

I have a mobility 2600 and everything is running great in natty. The only performance issue I have is smooth scrolling in every browser is terrible compared to maverick with catalyst 11.3.

---

### Post by ELD on 2011-04-16
Well hopefully the ati 11.4 driver with have at least "early look" as they call it support for ubuntu 11.4, most likely 11.5 though for true support.

---

### Post by screaminj3sus on 2011-04-16
hmm, regarding my smooth scrolling issue that seems to have been solved after I got an update today for syntactics touchpad drivers, so it may not have been fglrx at all.

---

### Post by Starks on 2011-04-16
can fglrx be installed with abi patches if xserver gets updated?

---

### Post by Harry33 on 2011-04-16
> **Starks said:**
> can fglrx be installed with abi patches if xserver gets updated?

Well that depends on how big changes are concerned in a given ABI change.
Typically a lot of source code must be rewritten to fully work with the new xserver.
So no patch is going to work anyway.
We will be having the next ABI change when xserver 1.11 is introduced (Oneiric Ocelot).

---

### Post by Starks on 2011-04-16
i hear oneiric might be 1.10.x instead of 1.11.

doesn't really matter since there will be an abi change between now and august anyway.

---

### Post by Harry33 on 2011-04-16
> **Starks said:**
> i hear oneiric might be 1.10.x instead of 1.11.
doesn't really matter since there will be an abi change between now and august anyway.

Xserver 1.11 is planned for Mid-August '11, merge window closing on late May '11.
That will fit the release schedule of Oneiric.

---

### Post by flying_surprise on 2011-04-16
Turning vsync helped a lot.
Now I only have problems with freezing windows when switching with alt+tab.
They start to work again when I press win+d.

---

### Post by hornedfiend on 2011-04-17
My Natty beta 2 install only works with fglrx drivers; the default radeon ones can only start my X server with the option "nomodeset".
I've used the ubuntu "additional drivers" feature and everything runs very smooth and way faster than 10.10. 
My video card is a mobility radeon 3470 with 256 vram.

---

### Post by flying_surprise on 2011-04-18
This failure to redraw windows after alt+tab is annoying. Let's file a bug.

---

### Post by flying_surprise on 2011-04-19
My problem is clearly the fglrx driver. Using radeon driver, compiz works like a charm, but there is a big drawback: No video offload which makes all hd material playback impossible.

---

