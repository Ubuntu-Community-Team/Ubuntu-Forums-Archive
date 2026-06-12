---
title: "XOrg (Opensource) Drivers for ATI Radeon Cards"
date: 2010-01-04
forum: Multimedia Software
---

### Post by frogotronic on 2010-01-04
Hello,

   For those of us who were stung last year by ATI's decision to drop support for <= R500 series cards from their closed source, or proprietary driver (known as the FGLRX driver), we are now forced to use the opensource ATI XORG driver.
   This is not as bad as it sounds, as in doing so, ATI has released a lot of the hardware specs on these older cards and the opensource driver has improved *dramatically* in the last year as a result.

  Ubuntu includes both the ATI and the FGLRX driver install capacities in recent releases (since Intrepid(?)).  If one can install the FGLRX driver, you should be able to do this by choosing **System>Administration>Hardware Drivers** and choosing to activate the ATI drivers; or you can manually install them using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

  However, if you have a card that is or below the R500 series (i.e. not R600+) DO NOT install the FGLRX drivers - you will break your X server (video display).  If you don't know what series chipset you have, try the following:

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M64-S [Mobility Radeon X2300]
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
```

From this, we can see that my card is:

**01:00.0 VGA compatible controller: ATI Technologies Inc M64-S [Mobility Radeon X2300]**

A Mobility Radeon X2300 using the M64-S chipset.

Then, look up the code name (RXXX) here: [http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

If you are below R600, you can only use the xorg drivers.

The xorg driver included in Ubuntu are very stable.  If you want updated drivers, there are a few options if you want to get the latest and greatest (according to your risk comfort level) straight from the XORG developers.

The description is here:

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

If you're like me and need a production machine, but just want updated drivers, try this link: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

To add the PPA (Guide): [http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)

These are fairly easy to remove (as described on the site); just remove the PPA from your Software Sources and downgrade the drivers.

- CH

---

### Post by AKADAP on 2010-01-04
I have run into some problems with the open source ATI drivers.

On both an ATI radion all in wonder, and an ATI radion 7000, The "system monitor" application window was complete garbage.

On the ATI radion all in wonder (R100), using a Sony FW-900 monitor, the default resolution was 2304x1440. At this resolution, the screen image was split into 9 columns with the data from the left most column duplicated 8 more times across the screen. (oddly the mouse was not part of this duplication and could be moved across the entire screen). I had to reduce the resolution to 2048x1280 before it would display properly. Unfortunately, the login screen is still at 2304x1440 and still screwed up, so I must login blind.

---

### Post by frogotronic on 2010-01-04
> **AKADAP said:**
> I have run into some problems with the open source ATI drivers.

On both an ATI radion all in wonder, and an ATI radion 7000, The "system monitor" application window was complete garbage.

I don't understand.  You are using more than one video card per machine?  Or are you talking about two machines?

Do you mean the Display Settings?  **System>Preferences>Display**
Or do you actually mean **System>Administration>System Monitor**?

> **AKADAP said:**
> On the ATI radion all in wonder (R100), using a Sony FW-900 monitor, the default resolution was 2304x1440. At this resolution, the screen image was split into 9 columns with the data from the left most column duplicated 8 more times across the screen. (oddly the mouse was not part of this duplication and could be moved across the entire screen). I had to reduce the resolution to 2048x1280 before it would display properly. Unfortunately, the login screen is still at 2304x1440 and still screwed up, so I must login blind.

You'll need to open up **System>Preferences>Display** and set up the individual screen resolutions (you should see a window dialogue like the attached screenshot).  If that doesn't work, you might have to manually add an xorg.conf file.  If the Display settings doesn't work - post back and I'll tell you how to manually set it up (likely your monitor isn't reporting its display resolution to the video card correctly).

Don't worry; we can fix it...:)

- CH

---

### Post by frogotronic on 2010-01-04
Hi,

  Okay, Here's where the problem might be...The GDMFW900 monitor from Sony has a MAXIMUM resolution of 2304x1440 resolution, but a RECOMMENDED resolution of 1920x1200.  Maybe try 1920x1200 and see what happens then...

- CH

Or you can download the manual and make sure your refresh is set correctly: [http://www.docs.sony.com/release/GDMFW900.PDF](http://www.docs.sony.com/release/GDMFW900.PDF)

---

### Post by virtual reality on 2010-01-05
still lost.

system > administration > hardware drivers
just tells me that no proprietary drivers are installed.

does
this [https://launchpad.net/~xorg-edgers/+archive/drivers-only]("https://launchpad.net/%7Exorg-edgers/+archive/drivers-only")
or this [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
hold the safe non-beta (or non-dev / non-alpha) release?

which links (or link sequence) need(s) to be followed?

why would I want to add a ppa guide (whatever that is): [http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html) ? how does this help ?

why can't I use the GUI of the "synaptic package manager" ? - it seems to display the relevant drivers I think.

newbie lost in translation.

vr.

---

### Post by frogotronic on 2010-01-05
> **virtual reality said:**
> still lost.

system > administration > hardware drivers
just tells me that no proprietary drivers are installed.

Okay, that means that you cannot use the FGLRX drivers (proprietary drivers)

> **virtual reality said:**
> does
this [https://launchpad.net/~xorg-edgers/+archive/drivers-only]("https://launchpad.net/%7Exorg-edgers/+archive/drivers-only")
or this [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
hold the safe non-beta (or non-dev / non-alpha) release?

Both do.  The "drivers-only" (i.e. the first PPA repo link) will just replace ATI video drivers (xserver-xorg-video-ati & xserver-xorg-video-radeon).  The second link will replace a lot of things related to the video drivers and xserver and may break you X server (as the warning on the PPA xorg edgers site states).

I would recommend trying only the drivers, they are much better than the stock Ubuntu (Karmic) drivers and its a simple one/two package downgrade (via Synaptic) to revert.

Okay, here's the step-by-step:

1) Open Synpatic.  **Settings>Repositories**

2) Go to the **Other Software** tab.

3) Click on the **+ ADD** button.

4) Type **ppa: xorg-edgers/drivers-only** (_**no**_ space between the ppa, the colon and the next word) into the box labelled **APT LINE:** 

5) Click **ADD SOURCE**

6) Reload your repositories

7) Mark Changes

8 ) Reboot

- CH

---

### Post by AKADAP on 2010-01-05
> **cement_head said:**
> I don't understand.  You are using more than one video card per machine?  Or are you talking about two machines?

two different machines
> 
Do you mean the Display Settings?  **System>Preferences>Display**
Or do you actually mean **System>Administration>System Monitor**?

The window that gets corrupted on both machines is system->administration->system monitor. It makes this tool completely unusable. (I think it may have worked at low res, one of the machines monitors was upgraded to a 1920x1080 LCD, and that window would no longer draw correctly after that. Both machines are running 1920x1080 or higher now).
> 


You'll need to open up **System>Preferences>Display** and set up the individual screen resolutions (you should see a window dialogue like the attached screenshot).  If that doesn't work, you might have to manually add an xorg.conf file.  If the Display settings doesn't work - post back and I'll tell you how to manually set it up (likely your monitor isn't reporting its display resolution to the video card correctly).

Don't worry; we can fix it...:)

- CH

What are you asking me to do here? with the exception of the system monitor window and the login screen, both displays are working properly now after I reduced the resolution on the ATI radion all in wonder. The real problem is that ubuntu picks the bad resolution by default on installation, and it is rather difficult to access the menus to change the resolution to one that actually works when using the broken one.

---

### Post by AKADAP on 2010-01-05
> **cement_head said:**
> Hi,

  Okay, Here's where the problem might be...The GDMFW900 monitor from Sony has a MAXIMUM resolution of 2304x1440 resolution, but a RECOMMENDED resolution of 1920x1200.  Maybe try 1920x1200 and see what happens then...

- CH

Or you can download the manual and make sure your refresh is set correctly: [http://www.docs.sony.com/release/GDMFW900.PDF](http://www.docs.sony.com/release/GDMFW900.PDF)

No, this is not the problem. The problem is that the 2304x1440 resolution is broken in the ATI driver for the ATI radion all in wonder. When this mode is selected the monitor scans perfectly. The mouse moves over the whole screen perfectly, the left edge of the screen displays perfectly, but the rest of the screen is eight duplicates of the left edge of the screen. It is the kind of thing you see when the memory is not getting mapped to the screen correctly.

---

### Post by frogotronic on 2010-01-05
> **AKADAP said:**
> two different machines

The window that gets corrupted on both machines is system->administration->system monitor. It makes this tool completely unusable. (I think it may have worked at low res, one of the machines monitors was upgraded to a 1920x1080 LCD, and that window would no longer draw correctly after that. Both machines are running 1920x1080 or higher now).


What are you asking me to do here? with the exception of the system monitor window and the login screen, both displays are working properly now after I reduced the resolution on the ATI radion all in wonder. The real problem is that ubuntu picks the bad resolution by default on installation, and it is rather difficult to access the menus to change the resolution to one that actually works when using the broken one.

Hi,

  That's a different issue.  Logon screen resolution is controlled somewhere else - I can't remember where offhand, but it is different than the regular xserver.

  Did the updated drivers help?

- CH

---

### Post by frogotronic on 2010-01-05
> **AKADAP said:**
> No, this is not the problem. The problem is that the 2304x1440 resolution is broken in the ATI driver for the ATI radion all in wonder. When this mode is selected the monitor scans perfectly. The mouse moves over the whole screen perfectly, the left edge of the screen displays perfectly, but the rest of the screen is eight duplicates of the left edge of the screen. It is the kind of thing you see when the memory is not getting mapped to the screen correctly.

Hmmm, did you check the Sony manual's Appendix that talks about the correct refresh rate?  Sounds as if that parameter is very influential.

- CH

---

### Post by AKADAP on 2010-01-06
> **cement_head said:**
> Hmmm, did you check the Sony manual's Appendix that talks about the correct refresh rate?  Sounds as if that parameter is very influential.

- CH

I don't see how the monitors refresh rate can corrupt the drivers memory.

The monitor was scanning correctly even when the displayed data was corrupted. This is demonstrated by the cursor being able to move over the entire screen without being duplicated or distorted.

Do I need to take a picture of the corrupted display to prove that this is a driver problem and has nothing to do with the monitor?

---

### Post by frogotronic on 2010-01-06
Easy...I'm just trying to help - no need to get snippy.

I believe your image is distorted.

I was thinking that if the card isn't outputting the signal in "GTF" compliant mode [due to the driver] (page 20 and Appendix page I of the Sony manual) that this might be the source or the distorted image.

You might have to specify GTF compliancy in the xorg.conf file(?)  I don't know - never seen this problem before.

Good Luck.  :(

- CH

---

### Post by AKADAP on 2010-01-07
> **cement_head said:**
> Easy...I'm just trying to help - no need to get snippy.
> This is demonstrated by the cursor being able to move over the entire screen **without being duplicated or distorted**
**I believe your image is distorted.**

I was thinking that if the card isn't outputting the signal in "GTF" compliant mode [due to the driver] (page 20 and Appendix page I of the Sony manual) that this might be the source or the distorted image.

You might have to specify GTF compliancy in the xorg.conf file(?)  I don't know - never seen this problem before.

Good Luck.  :(

- CH
I get snippy when people repeatedly misunderstand what I say.

There is NO distortion.
There is NO timing problem.
The timing sent to the display is WITHIN the specs for the monitor.
The image being sent to the monitor is broken.

Attached is a photo of the problem.

I had to scale the image down to fit within the restrictions of this forum, but in the image you can clearly see the left edge of the display is properly rendered. 

This left edge is duplicated 8 more times across the screen. The mouse pointer is NOT duplicated, it is clearly visible over on the lower right of the display.

I have turned on the monitors menu, you can see that it is also being properly displayed, Below the monitors menu you can see the timing that is being used and it is well within the capabilities of the monitor. 

If there was a timing problem, this monitor would display an error message and not attempt to display the image.

---

### Post by AKADAP on 2010-01-08
Since I have been having such difficultly making myself understood in this thread, I have taken a photo of the other problem, the garbage window that "system monitor" displays:

---

### Post by frogotronic on 2010-01-08
> **AKADAP said:**
> Since I have been having such difficultly making myself understood in this thread, I have taken a photo of the other problem, the garbage window that "system monitor" displays:

I see what you mean - that's definitely bizarre.  Does this happen with another/other monitors attached to the same machine?

- CH  :-k

----------------

P.S.  You could try the fully experimental XORG ATI drivers, straight from GIT ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ), then report the bug to the XORG CRACK/EDGERS and see what they recommend.  If these drivers complete bonk your system, you can revert to the vanilla Karmic drivers but using their purge command.

```

To revert to official packages, you can install the ppa-purge package and run "sudo ppa-purge xorg-edgers". Note that you will want to reinstall linux-libc-dev afterwards if you had libdrm-dev installed on karmic and newer.
```

---

### Post by AKADAP on 2010-01-08
> **cement_head said:**
> I see what you mean - that's definitely bizarre.  Does this happen with another/other monitors attached to the same machine?

- CH  :-k




This happens on two completely different machines with different ATI cards and different monitors.
One system has the ATI Radion All in Wonder video card with the Sony FW900 monitor.
The other system has an ATI 7000 series card with a 1920x1200 LCD monitor.

This does NOT happen with my main computer that has an ATI 4850HD card and is running the ATI proprietary drivers.

---

### Post by frogotronic on 2010-01-09
I'd file a bug report with Xorg Edgers

---

### Post by virtual reality on 2010-01-14
in synaptic > settings > repositories > other software, now only { [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu) karmic main } has a tick in its checkbox. There are five other entries which don't have a tick.

Is that good / normal / ok ?

(I didn't pay attention to what it was before I added these new drivers).

thanks!

vr.

---

### Post by virtual reality on 2010-01-14
hi again,

this is slightly disappointing... after reboot (again, having an extended desktop, dual head, two monitors), I changed the settings of "visual effects" in "appearance" from "none" to normal":

first, it was looking for drivers for 10-12 seconds, then it accepted "normal". however the result being that the (occasionally flickery) orange-streaky lines are back on my panels. :(

So this finger exercise so far was pretty useless here. :(

What is "X Server" ? Can you post me a link to a good and succinct description of it ?

Is this one helpful ? [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)
And this one relevant ? [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

~.~.~

ok.

1)
given that there's no perceivable advantage (but no apparent disadvantage, either) of the new repo (yet), would you suggest to revert back to old "stock Ubuntu (Karmic) drivers", as "it's a simple one/two package downgrade (via Synaptic) to revert" ?

~.~.~

so now I could try your suggested plan b:

"The second link will replace a lot of things related to the video drivers and xserver and may break you X server (as the warning on the PPA xorg edgers site states)."

2)
would you recommend me to do so ?

thanks for now,

vr.

---

### Post by frogotronic on 2010-01-15
> **virtual reality said:**
> hi again,

this is slightly disappointing... after reboot (again, having an extended desktop, dual head, two monitors), I changed the settings of "visual effects" in "appearance" from "none" to normal":

first, it was looking for drivers for 10-12 seconds, then it accepted "normal". however the result being that the (occasionally flickery) orange-streaky lines are back on my panels. :(

So this finger exercise so far was pretty useless here. :(

What is "X Server" ? Can you post me a link to a good and succinct description of it ?

Is this one helpful ? [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)
And this one relevant ? [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

Yep those are both good.  The quick and dirty explaination is that the X server is the GUI (what you are starting at right now).

> **virtual reality said:**
> ~.~.~

ok.

1)
given that there's no perceivable advantage (but no apparent disadvantage, either) of the new repo (yet), would you suggest to revert back to old "stock Ubuntu (Karmic) drivers", as "it's a simple one/two package downgrade (via Synaptic) to revert" ?

No, I run the new repo all the time - its very stable and it will give any improvements much earlier than regular repos - only revert if you have a **new** problem.

~.~.~

> **virtual reality said:**
> so now I could try your suggested plan b:

"The second link will replace a lot of things related to the video drivers and xserver and may break you X server (as the warning on the PPA xorg edgers site states)."

2)
would you recommend me to do so ?

You could try and then run the purge script is things get really screwed-up 

```
To revert to official packages, you can install the ppa-purge package and run "sudo ppa-purge xorg-edgers". Note that you will want to reinstall linux-libc-dev afterwards if you had libdrm-dev installed on karmic and newer.
```

---

