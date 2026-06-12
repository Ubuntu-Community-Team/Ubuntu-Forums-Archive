---
title: "Lucid upgrade breaks dual monitor set up"
date: 2010-05-01
forum: Multimedia Software
---

### Post by steveu6 on 2010-05-01
When Karmic came along, I upgraded and it was possible for the first time to get a dual monitor display working using only the GUI apps supplied. (I think I used screen resolution) It worked out of the box and took no time whatsoever.

I had a dual monitor set up working with 2 1024 x 768 monitors, with a desktop spanning both, and a background picture doing the same.

The Lucid update has just spectacularly broken this, along with a large number of desktop type changes that were unwanted.

The version of Ubuntu was the usual vanilla, but with enough K stuff installed to make K3b work. The card is a Radeon 9250SE. 

Has anyone any ideas for an easy solution?

[LIST=1]
[*]Give up and re-install Karmic?
[*]Wait for some sort of upgrade to allow either Monitors or Multiple Screens to work - the option to remove cloning is greyed out in one and unticking clone in the other does nothing?
[*]Try some other distro?
[/LIST]

Does anyone know of a decision to remove any functionality from Lucid that existed in Karmic? Is there any useful background to this that is perhaps not obvious?

I'm wondering why when an upgrade will seriously break something that no warning is given? 

I'd advise anyone with dual monitors and this card to either back up before upgrading or hold off until the same card works elsewhere. Yes, I know I should have backed up, but then this was the trial for the laptop running Karmic which I will now not upgrade. Thankfully this is the PC that I check upgrades on before doing them on the more oft used laptop.

---

### Post by notquitemichael on 2010-05-01
I don't know if your using third party/restricted drivers, but I'm using an nvidia card and my dual-screen setup works now, but it needed some help with the configuration.

I've found that everytime I've upgraded I've had to restore/fiddle with the xorg.conf file.

---

### Post by WinterRain on 2010-05-01
> **steveu6 said:**
> 
[*]Give up and re-install Karmic?


I would clean install Lucid. Upgrades are iffy at best to begin with. My dual monitor set up is fine in lucid.

---

### Post by Niksko on 2010-05-01
My dual monitors are broken as well under Lucid. Both of my screens are detected but only the one that is connected directly to the VGA output of the card displays anything. The other screen which is connected via a DVI->VGA adapter doesn't work

Ideas?

-Nik

---

### Post by steveu6 on 2010-05-01
> **notquitemichael said:**
> I don't know if your using third party/restricted drivers, but I'm using an nvidia card and my dual-screen setup works now, but it needed some help with the configuration.

I've found that everytime I've upgraded I've had to restore/fiddle with the xorg.conf file.

Not using 3rd party or restricted drivers.

AFAIK the xorg.conf file is no longer used - the one from the upgrade to Karmic has only a few lines it to define the whole desktop - 2048 x 768.

Seeing as I don't know for sure that I'll get a working dual monitor set with Lucid a karmic re-install is the way to go?

---

### Post by pertti on 2010-05-01
I'm having a similar problem with my Dell 6400 laptop, which has an ATI x1400 video card. I installed Lucid from scratch (keeping the same home folder I had for Karmic), and when I tried to configure the second monitor I got a terrible image with waves all over the second monitor.

I am using the open source ATI drivers. In fact, the restricted drivers managers doesn't let me chose the driver from ATI for my card. The resolution of the laptop screen is 1680x1050 and the resolution of the external monitor is 1920x1080. With Karmic I had a small xorg.conf file, with just the resolution of the whole setup (3600x1080). With Lucid I have no xorg.conf file at all (I understand they were going to be unnecessary at some point), but I also tried using my old xorg.conf file to no avail.

I have found a similar report (same laptop, different external monitor resolution) in the Lucid development thread ([http://ubuntuforums.org/showthread.php?t=1451072](http://ubuntuforums.org/showthread.php?t=1451072)), but there were no answers.

Does anybody have a clue what could be wrong here? Should I try with the closed source driver from ATI? Is it still available?

Thanks in advance

---

### Post by end3rkid on 2010-05-02
I'm having some problems with video drivers on Lucid too :(.

---

### Post by shah_vm on 2010-05-02
i am also having display issue. When i play movie on external display thru vga which is set to 1920x1080 movie is truncated at half screen. it does not show in the full screen. however i can see the window covering entire screen. I can see all the windows in full screen only video is truncated to half screen. I on ati mobility x300 graphics card. I have not installed any graphics drivers yet. 

anyone having same issue?

---

### Post by ropic on 2010-05-02
I have exactly the same problem using a Dell Inspiron 6400, any solution ?

---

### Post by SergeiFranco on 2010-05-02
I have same video card and does exactly same.
I tried to set it to different refresh rates without any effect.
It looks like bad VHS tape. Or poor TV reception.

Right now dual screen is completely unusable.

The card is X1400 Mobility (piece of crap, but laptop comes with it and there is nothing I can do to change that).

This is how I set resolution "xrandr --output VGA-0 --off && xrandr --output VGA-0 --mode 1280x1024 -r 60 --right-of LVDS".
I also tried KDE system settings: same effect (although I am pleased that KDE now has "working" display settings).

Has some one submitted a bug?

---

### Post by SergeiFranco on 2010-05-02
Here it is:
[https://answers.launchpad.net/ubuntu/+question/108939](https://answers.launchpad.net/ubuntu/+question/108939)

---

### Post by SergeiFranco on 2010-05-02
And another one
[https://bugs.launchpad.net/ubuntu/+bug/573290](https://bugs.launchpad.net/ubuntu/+bug/573290)

---

### Post by pertti on 2010-05-02
It seems that is a problem that affects many ATI cards. I found a (partial) solution here: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096). Try using "nomodeset" in the boot command in GRUB (see comment [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5)). With this flag I get my dual monitor setup to work again. However, full screen video (or enlarged up to a certain size) looks weird.

---

### Post by SergeiFranco on 2010-05-02
This drives me insane, it also looks like the working screen is driven less than 60Hz as I can see it flickering (this is Laptop LCD screen I am talking about).
How does one switch video driver from crappy ati-xorg one to vesa, since there is no xorg.conf anymore?

---

### Post by SergeiFranco on 2010-05-02
> **pertti said:**
> It seems that is a problem that affects many ATI cards. I found a (partial) solution here: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096). Try using "nomodeset" in the boot command in GRUB (see comment [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5)). With this flag I get my dual monitor setup to work again. However, full screen video (or enlarged up to a certain size) looks weird.

Thanks, that has fixed my issue. At this stage I don't care about full screen video.
I made a big mistake jumping on "upgrade to 10.04" band wagon. Should have waited 6 months.

---

### Post by crankenstein on 2010-05-02
Hi All
 
same problem with a dell 6400 with an ATI x1400 video card. Cant output to TV (really blurry) and when i try and play AVI's in full screen it starts dropping frames (really Jerky) 
 
Switched back to Karmic all all sweet. Not sure on what happened with the upgrade :(

---

### Post by WinterRain on 2010-05-02
> **pertti said:**
> Should I try with the closed source driver from ATI? Is it still available?


Just go to the ATI (AMD) website and download the driver.

---

### Post by SergeiFranco on 2010-05-02
> **WinterRain said:**
> Just go to the ATI (AMD) website and download the driver.

There is no driver for X1400 series. It is "obsolete".

EDIT: what I meant to say the driver on website does not work with ubuntu due to some sort of version mismatch (last time I tried to go that path).

---

### Post by iblazev on 2010-05-03
Same thing here. ATI x1300 and opensource drivers that came with Lucid don't work very well when it comes to dual display.
Unfortunately ATI restricted drivers don't work on Lucid and I'm not that savvy with configuring kernel or restricted drivers to make it work.

It would be nice if anyone with more knowledge would give some points on what to try at least

---

### Post by janneman37 on 2010-05-06
Hi,

I have a laptop fujitsu siemens with ATI X1400 card and after a few minutes my laptop screen is flashing/flickering... ubuntu 10.04. i have the open source driver.

---

### Post by crackham on 2010-05-10
Same thing here, worked perfectly until the "upgrade" to 10.04.
Older ATI x1400 on a HP laptop.

Sidenote,.. upgrade also nuked my wireless.. thanks!!

---

### Post by ppyo on 2010-05-13
I have a slightly different problem with my Asus 1000HA netbook and an external Acer 18" monitor with the Lucid upgrade. My monitor configuration keeping the Asus screen off and the Acer on as sole monitor worked like a charm on Karmic, while after the upgrade the configuration won't stay set, it always reverts on boot to the dual monitor, extended desktop setting. When I set the configuration back to one monitor, it works, but if I play a video, it will turn back again to the dual monitor setting.
This is very annoying.
Other than this, Lucid has been great.

---

### Post by petersk on 2010-06-13
You know, I have an X1650 and had the same problem with ATI: their proprietary drivers are great, but don't stay up to date with our "older" cards.  The latest I can find that supports my card is the 9.3 and that doesn't support lucid.  So... I guess I'm going for the FOSS driver; who knows how dual monitor support on that will turn out.  I only want to do development on my linux machine and possible watch some vids/multimedia.
  That being said, I'm considering buying a gaming machine and although the ATI cards seem to be stomping nVidia right now, I think I'll buy one with an nVidia driver just to send my little message to ATI that their lack of support for "older" cards is unacceptable.

---

### Post by steveu6 on 2010-06-15
> **pertti said:**
> Try using "nomodeset" in the boot command in GRUB (see comment [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5)). With this flag I get my dual monitor setup to work again. 

Thank you very much Sir!

With this one word of code my dual monitor set up is now unhosed. I have the dual monitors back again!!!!!

I'm very pleased. :cool::cool:

I gksudo'ed gedit to alter /boot/grub/menu.lst, added the one word needed at the end of the line marked out and I was away.

---

