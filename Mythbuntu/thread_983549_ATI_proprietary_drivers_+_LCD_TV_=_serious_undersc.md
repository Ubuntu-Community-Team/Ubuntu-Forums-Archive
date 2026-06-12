---
title: "ATI proprietary drivers + LCD TV = serious underscan"
date: 2008-11-15
forum: Mythbuntu
---

### Post by jape42 on 2008-11-15
Hi All,

I've got an ATI graphics chipset using the proprietary drivers connected to my 47LG70 TV via HDMI.  This results in serious underscan. ( ie a border about 1.5 inches all around the display.

The TV is reporting that it is getting a 1080p60 signal as I'd expect, and X seems to think it is running at the right resolution:

jape@vcr3:/var/log$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      60.0*    30.0     24.0

But something is screwey.  I've already set the TV to "just scan" and anyways I don't have this problem with the radeonhd drivers.  The readeonhd drivers work quite well ( and support HDMI audio too ) but my chipset is not accelerated under radeonhd ( so no xvideo ).

Anyone else seeing this?

jp

---

### Post by gungfujoe on 2009-02-15
> **jape42 said:**
> Anyone else seeing this?
This is one of a number of threads complaining about this problem, but so far, I don't see any solution.  It seems that with HDMI or DVI output, the proprietary drivers underscan, assuming you're using a crappy TV with forced overscan.  The Windows drivers allow you to fix this, but not the Linux drivers.

I'm using the latest drivers as of today (I just updated them to version 9.1, dated Jan 29th), and I'm seeing this same problem.

Hopefully someone has a solution.

---

### Post by jape42 on 2009-02-15
I gave up on the proprietary drivers.  Now I'm using the radeonhd driver, which allows pixel correct resolution (no over/under scan) and even audio over HDMI.

The down side is that there is no hardware acceleration for my HD3200, which means I have to configure myth to "change resolutions" to 640x480 for playback of recordings.

On the plus side, ATI has released info on how to program it's cards, so I'd expect things to improve over the next year.

regards,

jp

---

### Post by gungfujoe on 2009-02-15
> **jape42 said:**
> The down side is that there is no hardware acceleration for my HD3200, which means I have to configure myth to "change resolutions" to 640x480 for playback of recordings.

Unfortunately, that **completely** defeats my reason for using Mythbuntu - as an HD DVR.  If I have to run at 640x480, I wasted my money on a nice TV.  For this particular problem, simply turning overscanning on with my TV for HDMI PC input would be a much better solution.  The overscan on my Samsung LN51A750 seems to match up very well with the underscan on ATI's drivers.  It's obviously a sub-optimal solution, though (but better than dropping to 640x480).

Between audio problems, video problems, networking problems, and MythTV configuration problems, I'm actually contemplating spending $100 on a Windows license and running MediaPortal.  I _really_ want Linux to work, and really want to use AND like it.  Putting a $100 OS on a $400 computer to serve a single function seems like such a waste, but if the free option can't be made to work, I may have no alternative. :(

The ironic part is that I thought I was careful to buy hardware that would work well with Linux, and even taking that into consideration, I'm running into driver problems at every turn.

---

### Post by nickrout on 2009-02-15
> **gungfujoe said:**
> Unfortunately, that **completely** defeats my reason for using Mythbuntu - as an HD DVR.  If I have to run at 640x480, I wasted my money on a nice TV.  For this particular problem, simply turning overscanning on with my TV for HDMI PC input would be a much better solution.  The overscan on my Samsung LN51A750 seems to match up very well with the underscan on ATI's drivers.  It's obviously a sub-optimal solution, though (but better than dropping to 640x480).

Between audio problems, video problems, networking problems, and MythTV configuration problems, I'm actually contemplating spending $100 on a Windows license and running MediaPortal.  I _really_ want Linux to work, and really want to use AND like it.  Putting a $100 OS on a $400 computer to serve a single function seems like such a waste, but if the free option can't be made to work, I may have no alternative. :(

The ironic part is that I thought I was careful to buy hardware that would work well with Linux, and even taking that into consideration, I'm running into driver problems at every turn.

You shouldn't have bought a ATI card, replace it with a nVidia one.

---

### Post by jape42 on 2009-02-15
Yep.  I'd have to say ATI video is a bad choice for mythtv.  I got burned by this too, despite doing some research on the topic, and using nvidia cards in previous builds.

Things may be better a year from now, but right now, nvidia is the better choice.

regards,

jp

---

### Post by nickrout on 2009-02-15
I suspect given:

[LIST=1]
[*]the promise of nvidia's vdpau
[*]the seeming hopelessness of ati's ability to produce drivers that work; and
[*]intel's never never on accelerated playback
[/LIST]

That nVidia will remain the card of choice for a considerable time!

---

### Post by gungfujoe on 2009-02-15
> **nickrout said:**
> You shouldn't have bought a ATI card, replace it with a nVidia one.
Funny, a year or so ago, when Ubuntu's built-in driver wouldn't even display at all on my nVidia video card (pre-wubi, and I wanted to preview the OS with a Live CD), someone said just the opposite to me - that if I wanted to use Linux, I shouldn't have an nVidia card, and that I should've had an ATI card instead.

Regardless, either response speaks very poorly to Linux' viability as an OS beyond a very small niche market.

---

### Post by nickrout on 2009-02-15
> **gungfujoe said:**
> Funny, a year or so ago, when Ubuntu's built-in driver wouldn't even display at all on my nVidia video card (pre-wubi, and I wanted to preview the OS with a Live CD), someone said just the opposite to me - that if I wanted to use Linux, I shouldn't have an nVidia card, and that I should've had an ATI card instead.

Regardless, either response speaks very poorly to Linux' viability as an OS beyond a very small niche market.

You were wrongly advised. nVidia, even though they do not open source their drivers, have at least supplied drivers for linux for many years now.

Linux is incredibly viable as a computer for all users. I have sat many people down in front  of a linux machine and said "its a little different, the "start" menu is called "applications" and is at the top. Other than that its just like windows, you use firefox for 90% of what you do.

And away they go...

---

### Post by gungfujoe on 2009-02-15
> **nickrout said:**
> Linux is incredibly viable as a computer for all users. I have sat many people down in front  of a linux machine and said "its a little different, the "start" menu is called "applications" and is at the top. Other than that its just like windows, you use firefox for 90% of what you do.I truly, truly wish that were true, but it's not.  For one, as you yourself pointed out, ATI video cards aren't good under Linux.  There goes a huge portion of the general public.  As I discovered when trying to set Ubuntu up on my primary system, Creative Labs audio cards are incredibly problematic (I'm not going to downgrade my audio so that I can play with Linux).  There goes another significant portion of the market.  Linksys wireless NIC?  There's another group of users for whom Linux is a poor option.

Even with all of the hardware working, one kernel update can kill the drivers.  I applied a kernel update to Mythbuntu this afternoon and the screen was scrambled when I rebooted.  I'm a competent enough computer user that I can handle that.  Most people in the "all users" category are not.

Linux may be great for the neophyte user whose needs are very basic and who lives with an experienced computer user who can handle all of his system administration, but it has a long way to go before it's a usable, self-servicable operating system that the general public can use.  I really hope it gets there some day, preferably some day soon.

---

### Post by movieman on 2009-02-16
> **gungfujoe said:**
> Linux may be great for the neophyte user whose needs are very basic and who lives with an experienced computer user who can handle all of his system administration, but it has a long way to go before it's a usable, self-servicable operating system that the general public can use.

'Linux' can't do much about proprietary code from companies who refuse to release information about their hardware.

And, frankly, given the number of times I have people asking me how to fix their Windows PCs, I'd say that Windows has a long way to go before it's a usable, self-serviceable operating system that the general public can use. Even with everything I know, at times I've had to spend two or three hours getting my Windows PC to work again after updating ATI video drivers.

---

### Post by gungfujoe on 2009-02-16
> **movieman said:**
> 'Linux' can't do much about proprietary code from companies who refuse to release information about their hardware.You're absolutely right, but the "it's not our fault" aspect doesn't change the fact that the problem is there.  The fact that the hardware manufacturers haven't fully gotten onboard with Linux is one main reason that even the best distros (like Ubuntu, which does a great job at simplifying Linux setup) aren't ready for mainstream usage.  The fact that routine updates break hardware drivers is another reason (if a Windows hotfix breaks a driver, it's big news in even non-tech publications.  Updating the Linux kernel and having the video or audio driver crap out is a routine occurrence).  For the users who enjoy tweaking (and who have hardware that can be made to play nice with Linux), it's a great OS, but they're not "mainstream."

Windows has more than its share of issues, and there are a lot of people who are completely lost when it comes to administrating a Windows system (I married one of them).  But there are also many people in the notches above that, who can competently maintain a Windows system, but would be pulling their hair out with Linux.  I'm in no way trying to say "Windows is better than Linux."  For some users, it is.  For some, it's not.  Hopefully Linux distros will continue to improve and hardware support will continue to improve to the point where Linux is a better option for more and more users, and eventually to the point where it's a better option for the average user.  I'd love to see that happen, but the Linux evangelists who believe it has already happened are deluding themselves.

Personally, I'd jump at the chance to use it as my primary OS on my primary machine, but need working X-Fi drivers that don't require a kernel recompile and various other tweaks to make tenuously work.  Once that happens, or when I do my next system overhaul and no longer have that sound card, I'd love to use Windows for things like gaming and TaxCut, and do everything else in Ubuntu.

---

### Post by albertinacainh6 on 2011-01-16
> **jape42 said:**
> Hi All,I've got an ATI graphics chipset using the proprietary drivers connected to my 47LG70 TV via HDMI. This results in serious underscan. ( ie a border about 1.5 inches all around the display.The TV is reporting that it is getting a 1080p60 signal as I'd expect, and X seems to think it is running at the right resolution:jape@vcr3:/var/log$ xrandrScreen 0: [[COLOR=#000000]minimum[/COLOR]](http://www.powdershell.com/hr/science-and-technology/how-to-economize-on-your-phone-communication.html) 320 x 200, current 1920 x 1080, maximum 1920 x 1080default connected 1920x1080+0+0 0mm x 0mm1920x1080 60.0* 30.0 24.0But something is screwey. I've already set the TV to "just scan" and anyways I don't have this problem with the radeonhd drivers. The readeonhd drivers work quite well ( and support HDMI audio too ) but my chipset is not accelerated under radeonhd ( so no xvideo ).Anyone else seeing this?jpIt's good for reference, Many thanks to your description!

---

