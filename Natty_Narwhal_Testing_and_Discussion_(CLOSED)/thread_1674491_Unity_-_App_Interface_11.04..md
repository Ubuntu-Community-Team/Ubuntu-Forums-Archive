---
title: "Unity - App Interface 11.04."
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Roasted on 2011-01-24
I have 10.10 installed, and I found a PPA for 2D Unity, which ran great on my netbook (the 3D one ran horribly). 

When I went to applications, it brought up a slick semi see thru black menu to sift through.

I installed 11.04, and when I did it seemed much more basic. In fact, I wasn't a big fan of it at all. I know it's in alpha or beta or whatever but I was just curious, is this a temporary mock up of the final release? I just found it kind of blah to be in the application launch menu and it's basically nautilus with a bunch of icons, whereas the Unity I ran on 10.10 was very slick and intuitive with its interface.

Also - is anybody running 11.04 on an Acer Aspire One? I'm having some issues with 11.04, so I ended up putting my 10.10 image back on. It ran fast, but with some strange issues. For example, I couldn't open anything in the applet in the upper right. I couldn't bring up wireless networks, volume, calendar, etc. Everything I clicked just did nothing.

Just curious. Thanks guys!

---

### Post by VeeDubb on 2011-01-24
Alpha.  Alpha 1 in fact.  We've still got at least one more Alpha, then all the Beta testing before we even get to a release candidate. 

What you see is not a reflection of what the finished product will be like.  The latest update, which just dropped in the last 24-48 hours and probably isn't on all the mirrors yet, does show a slightly more finished looking app menu, but it's almost completely non-functional so all the various links still just launch the window you were describing.

When I followed the development of netbook unity, the first appearance of anything that looked like part of the dash was the kick-off of some very rapid development as far as UI was concerned, which then settled down into polish and bug-fix mode for the last month or two of development.

I would expect to see something similar here.

---

### Post by Peter09 on 2011-01-24
There is a bug at the moment which results in a transparent window in the top left corner of the screen, which is why you cannot click in there. As a work around open the dash (click on the top left ubuntu icon) and close it again by doing the same. This will get rid of the transparent blocking window.

---

### Post by Roasted on 2011-01-24
Okay - I was just curious. I'm currently running it from a flash drive on my laptop, and it's incredibly smooth. Since it's a *work* laptop I won't be trying this out just yet, however I'd love to install it on my netbook, but like I said above, that's put me against a brick wall. :(

---

### Post by Peter09 on 2011-01-24
I'm running on an aspire one - no problems.

---

### Post by Roasted on 2011-01-24
> **Peter09 said:**
> I'm running on an aspire one - no problems.

Which particular Asire One are you using? Is it a ZG5 8.9" by chance?

Can you run LSPCI and tell me which video card you have? I have an Intel GMA 945 I believe.

---

### Post by Peter09 on 2011-01-24
Yes its the ZG5

I'm not near it at the moment but will look at the video card when I can.

---

### Post by snkiz on 2011-01-25
Aspire One D260 here. Haven't had the chance to really test natty. (little to unstable still.) But I do have it installed, I had read the open broadcom drivers were supposed to be in the next kernel, but natty doesn't have'em yet. Still have a wierd bug where the screen shuts off for a bit durring boot, but its less now. In maverick I *almost eliminated the problem by using the framebuffer durring boot. (My other ride is an Nvidia rig. :) ) 

That's all I've been able to test so far, Unity boots are unpredictable still, but so far when it does work, it seems to work as intended at the moment. Things I hope get fixed from 10.10 include The above mentioned boot issue, non-functional onboard mic and card reader. I haven't looked into the last two, but the D260 has been out long enough I'm sure there are reports. On my wishlist are mutitouch for the mouse pad, and something that I only recently noticed. There is no visual feedback in the nm-applet if you use the hardware wireless switch. uTouch is still a little new, so thats fine. But the switch I need to look into.

---

### Post by mihaitudorpopescu on 2011-01-25
Is Unity going to remain like this or are functions going to be added? I remember that in 10.10, it had a search feature and all the features that are also in the gnome menu, in classic gnome interface. Just wondering. :-/

---

### Post by mihaitudorpopescu on 2011-01-25
One other thing: Unity has trouble handling multiple tasks. Is that problem going to be solved any time soon?

I will give you my configuration:
ASUS Eee PC 901
Intel Atom N270 CPU with hyperthreading
2GB DDR 2 RAM
20 GB SSD

---

### Post by cariboo on 2011-01-25
> **mihaitudorpopescu said:**
> One other thing: Unity has trouble handling multiple tasks. Is that problem going to be solved any time soon?

I will give you my configuration:
ASUS Eee PC 901
Intel Atom N270 CPU with hyperthreading
2GB DDR 2 RAM
20 GB SSD

What do you mean, I currently have, xchat on one desktop, chromium on another and synaptic on a third, my system has the same specs except it only has 1Gb ram, and a 160Gb sata hdd.

---

### Post by VeeDubb on 2011-01-25
> **mihaitudorpopescu said:**
> Is Unity going to remain like this or are functions going to be added?

More features and functions will be added.  This is an alpha testing release of Ubuntu.  That means that there are numerous "known bugs" and missing features.  Unity is being rewritten from what it was in 10.10 to being a compiz plugin, AND it is being redesigned in several areas to make it more desktop friendly.

---

