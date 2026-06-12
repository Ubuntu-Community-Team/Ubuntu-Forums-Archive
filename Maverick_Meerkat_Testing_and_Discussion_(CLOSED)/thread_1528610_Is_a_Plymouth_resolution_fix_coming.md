---
title: "Is a Plymouth resolution fix coming?"
date: 2010-07-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-07-11
First of all, I'm aware that there are [ways to correct this problem](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml), but I'm more interested in getting this bug squashed.

This low resolution boot screen degrades the Ubuntu experience. Will this be fixed in Maverick for those of us using the proprietary graphics drivers?

---

### Post by cariboo on 2010-07-11
The quick answer is no. Until nvidia at least supports kms there will be no fix.

---

### Post by ranch hand on 2010-07-11
Have you tried using the OSS drivers from exor.edgers ppa?  They may do what you want.  They, at least let me boot to 10.04 and help on the UNE install of 10.10 with my ATI card.

If You do not want to do that remove "splash" from your boot instruction string in your menu.  You can try that by by hitting e when the menu comes up and editing it there.  If that is an improvement for you edit your /etc/default/grub file.

Plymouth is the real problem and it is not going to be fixed.  Learn to live with it.

---

### Post by gnomeuser on 2010-07-11
The default out of the box experience is likely to remain the same. Ubuntu ships KMS enabled ATI and nVidia drivers, those have no resolution problems. Your choice to enable an unsupportable driver is your own problem and one we can't do anything about.

With xorg-edgers (and the nouveau firmware package not to be forgotten), I have 3D acceleration, stability and modern features. With the exception of VDPAU support it is fully sufficient in addressing any such requirements out of the box without sacrificing supportability, security or progress.

So there is no requirement for a fix, you caused the problem by installing a driver which specifically stated upon installation that it was unsupportable. The out of the box experience remains xserver-xorg-driver-ati/nouveau which do not have any such issues.

---

### Post by MacUntu on 2010-07-11
Yes.

> **gnomeuser said:**
> without sacrificing supportability, security or progress

Yeah, except performance - performance which you pay for.

---

### Post by xeizo on 2010-07-11
I would like to see anyone actually play a modern 3D-shooter on the noveau-driver, the bare thought is laughable.  The proprietary Nvidia driver is even faster than it's Windows-cousin in some scenarios and is much, much preferable to use. Not everyone using Ubuntu abides to the strict open sauce of things.  And now, Steam is on it's way with a native client for Linux(even though I for one already use it under Wine). You can't use the content on Steam with the noveau driver.  Get used to it, the not so nerdy people out there waiting to adopt Linux want's a usable OS, not a strict one.  Any advice to use noveau should be postponed a few years until it's actually usable for more than hacking some text in gedit.  edit. btw the daily build of Ubuntu Studio from 7/7, which I installed, had plymouth removed in the default install. Great thinking there from the Studio-folks  :)

---

### Post by gnomeuser on 2010-07-11
> **xeizo said:**
> I would like to see anyone actually play a modern 3D-shooter on the noveau-driver, the bare thought is laughable.  The proprietary Nvidia driver is even faster than it's Windows-cousin in some scenarios and is much, much preferable to use. Not everyone using Ubuntu abides to the strict open sauce of things.  And now, Steam is on it's way with a native client for Linux(even though I for one already use it under Wine). You can't use the content on Steam with the noveau driver.  Get used to it, the not so nerdy people out there waiting to adopt Linux want's a usable OS, not a strict one.  Any advice to use noveau should be postponed a few years until it's actually usable for more than hacking some text in gedit.  edit. btw the daily build of Ubuntu Studio from 7/7, which I installed, had plymouth removed in the default install. Great thinking there from the Studio-folks  :)

Actually from a games point of view Nouveau is pretty far along. of the games we have access to that require 3D I believe all of them run acceptably now. Granted top of the line might be Enemy Territory, Quake 3 era games and modifications to these engines.

Regardless my point was that the out of the box experience remains the same. On an Ubuntu machine with an nvidia or ATI card you actively have to do something to get this supposedly huge problem with a misaligned and oversized splash. Big 3D games aren't available for Linux currently (a shame but reality beckons) and even at that gamers are a minuscule market which we currently have little hope of satisfying anyways. Out of the box Ubuntu will be able to provide sufficient support to run these cards accelerated in desktop situations. It will even support any game that Ubuntu ships with. 

There are bigger problems to attack, our extremely poor integration and support of SMB e.g. On the graphics side I think the lack of VDPAU or similar acceleration of video decoding is a bigger problem as that is genuinely useful especially on the lower end setups that often can end up shipping Linux. Additionally it is a problem since media centers also is a big market for Linux.

Regardless tons of bigger problems than this self inflicted wound of which people are warned when they opt in.

---

### Post by Half-Left on 2010-07-11
> **cariboo907 said:**
> The quick answer is no. Until nvidia at least supports kms there will be no fix.

It works in Fedora and it works using my wife's intel 915 but not Ubuntu. It's not luck either. Ubuntu disabled KMS in 10.04 for some Intel chipsets which stops the screen even showing.

I have to wonder what they were thinking.

---

### Post by gnomeuser on 2010-07-11
> **Half-Left said:**
> It works in Fedora and it works using my wife's intel 915 but not Ubuntu. It's not luck either. Ubuntu disabled KMS in 10.4 for Intel some chipsets which stops the screen even showing.

I have to wonder what they were thinking.

The problem is with the proprietary nvidia driver. Fedora uses Nouveau like Ubuntu out of the box. 

This requires kms support, which is in pretty much every open source video driver now. However if nvidia was to implement this support that would make their code unquestionably derived from the kernel, meaning it would be subject to it's gplv2 licensing... something nvidia are violently opposed (and legally unable) to doing.

Hence if users wishes to use that driver, plymouth isn't capable of enabling kms and it looks less sexy than normally. Considering that users see the regular plymouth on their first boot and then the non kms one after installing the driver they are prone to thinking, wrongly, that this is a bug in Ubuntu.

---

### Post by Half-Left on 2010-07-11
> **gnomeuser said:**
> The problem is with the proprietary nvidia driver. Fedora uses Nouveau like Ubuntu out of the box. 

This requires kms support, which is in pretty much every open source video driver now. However if nvidia was to implement this support that would make their code unquestionably derived from the kernel, meaning it would be subject to it's gplv2 licensing... something nvidia are violently opposed (and legally unable) to doing.

Hence if users wishes to use that driver, plymouth isn't capable of enabling kms and it looks less sexy than normally. Considering that users see the regular plymouth on their first boot and then the non kms one after installing the driver they are prone to thinking, wrongly, that this is a bug in Ubuntu.

I know about it but if I use the proprietary NVIDIA driver in Fedora, Plymouth shows just fine.

Again Why is the Intel 915 driver broken in Ubuntu, yet the fix is to enable KMS(which Canonical don't enable by default)?

---

### Post by exploder on 2010-07-11
Nice discussion here. I have plymouth working with the latest nvidea drivers in 10.04. I used the 2.6.35-6 kernel, nvidea 256.35 driver and fixed plymouth by hand, it works fine. I would have been perfectly happy with the open source drivers if 3D would have been just a little bit better. I should mention that I also turned off the disk check in /etc/fstab too.

If the open source drivers for Maverick have better 3D support I will use them.

---

### Post by glasen on 2010-07-11
> Again Why is the Intel 915 driver broken in Ubuntu, yet the fix is to enable KMS(which Canonical don't enable by default)? 

Because some chipsets don't work with KMS on kernel-version 2.6.32 (i830M) or have stability issues (i845 or i855). These chipsets are blacklisted in the kernel-image and must explicitly be activated (i915.modeset=1).

Other distributions don't blacklist these chips so KMS is activated OOtB.

---

### Post by aviramof on 2010-07-11
For me everything is working fine with the latest fglrx-installer from the x-swat ppa.

---

### Post by xeizo on 2010-07-11
For me personally, it's no big deal, I prefer high 3D performance over a nice looking boot screen every day in the week. I live perfectly happy without plymouth.  I very seldom reboot anyways. I very seldom use stable distributions anyways ;)  But there are many newbies installing the Nvidia proprietary driver because of the same wish for better performance, and their experience of Linux will be less than perfect if it looks strange when they boot. Just because, even if there's very good reasons as to why things are as they are, some sort of fix would be useful for giving new users the best impression.

---

### Post by Slug71 on 2010-07-11
Not sure if its already been done but as far as i know the nouveau drivers in Maverick will have Gallium3D support which i would imagine bring much improvement to Plymouth among others.

---

### Post by gnomeuser on 2010-07-12
> **Slug71 said:**
> Not sure if its already been done but as far as i know the nouveau drivers in Maverick will have Gallium3D support which i would imagine bring much improvement to Plymouth among others.

That would surprise me, the gallium driver is still not even officially released as I understand. I doubt we will see that come as the default. Much more likely we will continue to have this from the xorg-edgers ppa as the support matures.

The 2D driver is very solid now and with Gallium now getting state trackers for things like Cairo, openvg and vdpau.. I forsee performance increases across the board for the upcoming Ubuntu releases as support matures and expands.

---

### Post by sgage on 2010-07-12
The nouveau drivers might be coming along nicely, but they still don't adequately support Stellarium. And they still don't allow my computer to wake from sleep. 

If/when these two issues are addressed, I'll be happy to use nouveau. But for now it's no-go.

The nvidia drivers work perfectly. The boot-time ugliness doesn't matter to me, and it's easily worked around in any case.

---

### Post by gnomeuser on 2010-07-12
> **sgage said:**
> The nouveau drivers might be coming along nicely, but they still don't adequately support Stellarium. And they still don't allow my computer to wake from sleep. 

If/when these two issues are addressed, I'll be happy to use nouveau. But for now it's no-go.

The nvidia drivers work perfectly. The boot-time ugliness doesn't matter to me, and it's easily worked around in any case.

Bugs filed on these issues, I would love to follow them. I haven't tested suspend on my machine but everything else seems to work.

---

### Post by BigSilly on 2010-07-12
I'm not a technical person, but is there a reason that Ubuntu cannot use the Nouveau driver for boot and then switch to the proprietary driver afterwards if the user has elected to use it? I think it's a shame that the best option the Ubuntu team felt they could take was to pretend the proprietary driver isn't there. 

The fact is a great deal of users will be using the proprietary driver, and when they boot up their machines first time after enabling the driver to find a glitchy mess it reflects badly.:(  I'm not saying this because I'm a nasty person, I say it because I care. I can fix it no problem (though the solution isn't perfect), but other users are going to be very confused when Ubuntu plants the proprietary driver so easily in their lap after installing, then washes it's hands when you have the audacity to actually use it.

Obviously the answer is not to take away the proprietary driver from the user at the point of install (that would be silly), but surely there must be a better solution than what there is now? I agree there are many more important things to address within Ubuntu, but I do feel if things like this get ignored, then the polish is gradually taken off Ubuntu, and the potential end users are left with a poor impression that will further enhance the perception that Linux is just too fussy and technical for anyone but experienced users.

Yes it's just a boot screen, yes there are more important things going on. But if Ubuntu cannot get these simple things right for the wider audience, how can it ever be taken seriously as a genuine competitor?

---

### Post by TBABill on 2010-07-12
Let's not forget about the incredible heat the open source drivers inflict on a machine either. People don't just install proprietary drivers because they want better performance. The issue of heat was my driving factor to do so. My laptop was reaching temps over 80C very quickly under flash apps (just a short video clip) and other very light tasks. Even with CPU scaling the heat was far too high to be tolerable. Installing the proprietary driver provided a great deal of relief to the hardware on my machine, which runs very cool on Windows. It runs within 10C of its Windows temps once all efforts are made to scale CPU speed, setup proprietary driver and replace java with Sun Java.
 
It's not just the 3D that is impacted by open source drivers and until they are improved it is difficult to trust them to not harm my machines under extended use (greater than 30 continuous minutes). I would opt for the open source drivers if they worked well in all aspects of operation.

---

### Post by andrek on 2010-07-12
> **TBABill said:**
> Let's not forget about the incredible heat the open source drivers inflict on a machine either. People don't just install proprietary drivers because they want better performance. The issue of heat was my driving factor to do so. My laptop was reaching temps over 80C very quickly under flash apps (just a short video clip) and other very light tasks. Even with CPU scaling the heat was far too high to be tolerable. Installing the proprietary driver provided a great deal of relief to the hardware on my machine, which runs very cool on Windows. It runs within 10C of its Windows temps once all efforts are made to scale CPU speed, setup proprietary driver and replace java with Sun Java.
 
It's not just the 3D that is impacted by open source drivers and until they are improved it is difficult to trust them to not harm my machines under extended use (greater than 30 continuous minutes). I would opt for the open source drivers if they worked well in all aspects of operation.

Ditto, that's why I'm sticking with ati's fglrx driver rather than with the open source one, which doesn't have proper power management.

---

### Post by gnomeuser on 2010-07-12
> **andrek said:**
> Ditto, that's why I'm sticking with ati's fglrx driver rather than with the open source one, which doesn't have proper power management.

This is admittedly an issue, but I understand that the ati driver at least got some improvements in this area recently.

Especially for netbook deployments one could imagine this to be a showstopper. Hopefully work will progress nicely and it won't be an issue for long. I know Len Brown did some work in the kernel on power management and there seems to be interest in the work high up the food chain as well.

---

### Post by TBABill on 2010-07-12
I concur. Although sound, wireless and other hardware are still an issue for some equipment, video drivers are the most crucial because of the issues outside of normal display performance such as heat. That heat can cause irreparable damage to a machine, particularly laptops without the openness and air movement of the larger desktop machines. Proprietary drivers would not be much of an issue if there was an equivalent performance capability on the open source side. If we were there, or even close, there would be little point to opt for a closed source driver.

---

