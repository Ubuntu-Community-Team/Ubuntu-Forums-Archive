---
title: "Wireless the Latest of my troubles..."
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by ScottiePP7 on 2009-04-26
Hello All -

Thanks in advance for any help.

I have a lenovo s10 with a broadcom wireless.  My first ubuntu install was 8.04 and my wireless worked fine, I then upgraded to 8.10 and 9.04 and wireless worked flawlessly throughout the process.

Sounds good right?

Well, good wasn't good enough for me.  Since I was dual-booting with XP and no longer wanted XP anymore, I decided to tinker.....

I loaded 9.04 iso onto ubenetbootin and did a clean install, make my full 160 disk drive ubuntu.  Then my issues started:

First the laptop wouldn’t display anything, I mean anything at all.  When I booted it up I didn't even get the nice bios screen with Lenovo on it and hit f-whatever to get into system setup.

I unpluged and then re-inserted my ram, bing bang boom - I am up and running.

Now, no wireless.  It seems to be reading the card ok, just cant pick up any networks.

Any help would be greatly appreciated.

---

### Post by kerry_s on 2009-04-26
sounds like a borked install, since it's fresh anyways try to install again.
make sure you format the usb before you unpack the iso on it with unetbootin.

---

### Post by ScottiePP7 on 2009-04-26
Just reinstalled... still no wireless networks

---

### Post by throke on 2009-04-26
hey scottie, seems to me most people are having an issue like this. I've been watching the forum since my install of Jaunty(more like janky) on the 24th. I was able to get my drivers via lan, but once installed could not get past the WPA encryption part. I gave up and went back to 8.10 since my wireless works just fine(Broadcom BCM4306-Linksys) with that edition. I know crap about Linux, so can be of no help. Really just wanted to say that this does not seem to be hardware specific- more like how Ubuntu is handling WPA encryption and with that I couldnt tell what has changed.Although there are MANY threads here with similar problem, noone seems to have fixed it yet.

---

### Post by ScottiePP7 on 2009-04-26
Here is what I can gather so far...

I think when I had a dual boot system ubuntu was using the xp drivers via ndiswrapper and when I did a fresh install getting rid of XP this caused all of my problems.  If i try to go back to a fresh install of 8.04 it still doesn't work.

So now I think my next step may be the scour the interwebs and look for the XP drivers not in any exe format so I can put them on my netbook and try to use ndiswrapper....

Thanks for the help and support so far

---

### Post by adamsu on 2009-04-27
I don't think this is necessarily a problem with uninstalling XP or windows drivers versus linux drivers, I have the same problem on a lappy that hasn't had windows installed for a long time and has never had a wireless problem until this upgrade. This seems to be an issue with Jaunty. It is quite frustrating. One thing you can try is to search through some of the bug reports and try any fixes that people mention. I haven't found anything useful to me as of yet however... We just have to be patient I suppose.:(

---

