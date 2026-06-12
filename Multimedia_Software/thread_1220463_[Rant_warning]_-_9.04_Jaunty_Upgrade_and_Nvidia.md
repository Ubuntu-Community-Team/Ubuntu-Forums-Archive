---
title: "[Rant warning] - 9.04 Jaunty Upgrade and Nvidia"
date: 2009-07-22
forum: Multimedia Software
---

### Post by tumblebug on 2009-07-22
Hello All

No actual help required here (unless you want to) - just letting off steam)

[rant]

An open letter to the linux community...

3 months earlier.....

Had Ubuntu 8.04 working happily with Nvidia Geforce MX440 and 22' Chimei widescreen LCD

Got a USB HD TV dongle based on the Alfa-tech 9013/9015 chip. Plugged it in - it didnt work. Wasnt surprised and started the hunt for the drivers, firmware, etc. 2-3 days later, couldn't get it working so I thought maybe it was time for a upgrade of Kubuntu. So I upgraded to 8.10 with no issues. TV dongle still didnt work but I was able to get the drivers and firmware to load and the card finally started working! Yay!

Fast forward to today....

3 days ago, after a fairly large update through the normal Adept updater, the dongle stopped working - linux just didnt didnt want to know about it. I had read that the af9013/af9015 support was built into 9.04 and since I'd pretty much gone through hell to get the dongle working in 8.10, I thought I'd upgrade the entire system - the computer is only used for email, web surfing, a bit of web dev and some TV watching, nothing really earthshattering so if it stopped me from farting around with the TV card, then I thought it would be worth it.

well....

Did the upgrade (using adept) to 9.04 and lo and behold, the graphics is busted. I've got a Nvidia Geforce mx440 card and I've been through just about every guide, how-to, forum, archive I can google to get this running. I've downloaded all of the drivers (both recommended and not recommended) and installed them in various ways (commandline, Envy, Adept, etc) but the best I can get is having it start with the "vesa" driver (atleast it gets the resolution right 1280x1024). I have multitudes of backed up xorg.conf files and rebooted with recovery more times than I can count but THE only to have my system running is with the vesa/nv drivers only.

...and I havent seen if the dongle is working (tho I did notice in the booting messages that the firmware is getting loaded...I think...)

Am considering blowing away linux and making a fresh install of 9.04, but frankly, after spending 2-3 days to get this working, and with little or no garrantee of either the graphics or the dongle coming back to life, I find myself slipping back to the darkside and going back to Windows.

Ok, upgrading the entire system to make a piece of hardware work is excessive, and yes, you could say that since I'm not using my card to do anything strenuous that I could just settle for the "vesa" drivers, or even the "nv", but what is the point of that? I have a perfectly good 3D card in my system so in the event that I run something that requires 3D, the system can do it.

Why is it so difficult to make it work? Ubuntu even knows the right driver is there 'cos it tells me that in "Hardware Driver" but if I activiate it and reboot...boom..."x server cannot be started"...and back to the commandline I go. Same thing if I use Envy - it recommends the right driver, I click apply, it thinks for a while, tell me to reboot...bam....commandline. I've manually edited the xorg file, regenerated it so many times, and in so many different ways. I even got one result where everything appeared to load, but the screen appeared with multicolored and blinking dos characters that changed as the loading process continued.

I am at a time in my life where I dont have the time (or the energy) to spend 2-3 days chasing down configuration problems and typing arcane commands into the commandline, when I can go to Windows, plug in whatever I have and can be 99% sure that it will work....WITHOUT going anyway near the commandline. Of course, Windows has it's own issues (and lots of them), but sometimes...better the devil you know.

I love Ubuntu/Linux and the ideas of opensource, and I also understand that linux issues with hardware are also down to the developers of the hardware (esp. in the case of Nvidia drivers). I really believe the linux community is in a real bind with this stuff - people need those drivers to get full use out their hardware, but if the companies don't want their hardware to work with linux, or don't care about linux, they'll keep it closed up....and that will eventually frustrate ppl like me (a web developer with better things to do) back to Windows....or god forbid...a Mac :)

If you read this far, thanks for reading :)

[/rant]

---

