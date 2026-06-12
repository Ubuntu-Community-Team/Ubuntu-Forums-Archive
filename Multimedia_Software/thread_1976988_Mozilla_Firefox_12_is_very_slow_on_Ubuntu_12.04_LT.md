---
title: "Mozilla Firefox 12 is very slow on Ubuntu 12.04 LTS."
date: 2012-05-09
forum: Multimedia Software
---

### Post by Kreaninw on 2012-05-09
Mozilla Firefox 12 is very slow on Ubuntu 12.04 LTS. I'm saying this because I'm using it side by side with PC. I doubt that hardware acceleration was enabled with Firefox on Ubuntu, even with css animation, it lags just like my grand dad. So, how can I check it?

I have enabled the option in advance tab. I have installed my GPU driver, however my ATI Radeon HD5650 GPU on my laptop is VESA: MADISON in system detail, is this all right?

I still can't change to Chromium because it is very buggy unlike Chrome, and with its boring add-on/extension, I don't think I would want to change soon. Opera is a good deal but it can't render my language correctly. So, Firefox is my only choice, even on PC, and it's the fastest browser on PC, and the slowest browser on Ubuntu. Please help me fix this, thanks.

---

### Post by Kreaninw on 2012-06-10
[LEFT]From my investigation, it's slow because hardware acceleration is disable. See image below, about:support page in both platform, Ubuntu and Windows.

**On Windows - hardware acceleration enable.**

[[img=http://img39.imageshack.us/img39/4702/firefoxwindows.th.png]]("http://imageshack.us/photo/my-images/39/firefoxwindows.png/")
[[IMG]http://img39.imageshack.us/img39/4702/firefoxwindows.th.png[/IMG]]("http://imageshack.us/photo/my-images/39/firefoxwindows.png/")

**On Ubuntu - hardware acceleration disable.**

[[img=http://img52.imageshack.us/img52/3435/firefoxubuntun.th.png]]("http://imageshack.us/photo/my-images/52/firefoxubuntun.png/")
[[IMG]http://img52.imageshack.us/img52/3435/firefoxubuntun.th.png[/IMG]]("http://imageshack.us/photo/my-images/52/firefoxubuntun.png/")

The problem is, there is no way to enable hardware acceleration in Ubuntu's Firefox. My card is ATI/AMD Radeon HD5650, I installed my driver right with CCC usable(the one in Additional Drivers from Ubuntu.), force enable hardware acceleration won't work. 

I heard it also effects NVIDIA user with driver in Additional Drivers and upgrade the driver to latest version didn't fix a thing.

[http://askubuntu.com/questions/140007/firefox-12s-hardware-acceleration-on-ubuntu-12-04-lts](http://askubuntu.com/questions/140007/firefox-12s-hardware-acceleration-on-ubuntu-12-04-lts)

I read some test and found out that Linux and slow browser is nothing to surprise about.[SIZE=2]

[Hardware Acceleration Performance Benchmarks.]("http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129-12.html")[/SIZE]

However, you can test it yourself with [HTML5 Fish Bowl]("http://ie.microsoft.com/testdrive/Performance/FishBowl/"). I tested it myself, and found that on Windows, Firefox gave the best result even surpasses IE9, on Ubuntu it merely survive crash.

I'm using Firefox 13 on Ubuntu 12.04 LTS, updated every thing to date, there's nothing change. Is there a way to fix this? Thanks.
[/LEFT]

---

### Post by shymega on 2012-06-10
Hi,

I'm afraid I do not understand what you mean by 'Hardware Acceleration'. What jumps to mind is that you're talking about Vt-x and AMD-V technology. I know this is used for visualization but I've never heard of it being used in Firefox.

Have you tried Chromium or other browsers?

Please report back.
--
SM

---

### Post by Kreaninw on 2012-06-10
> **shymega said:**
> Hi,

I'm afraid I do not understand what you mean by 'Hardware Acceleration'. What jumps to mind is that you're talking about Vt-x and AMD-V technology. I know this is used for visualization but I've never heard of it being used in Firefox.

Have you tried Chromium or other browsers?

Please report back.
--
SM

Thank you but Hardware Acceleration is right at Firefox preference advanced tab since version 4. It's being use to let your GPU helps rendering web page. All the other browsers which can be use on Ubuntu didn't do better than Firefox, plus they has more bug.

---

### Post by shymega on 2012-06-10
Hm. I'm at a loss but are you sure you installed the right driver for your GPU?

Thanks,
SM

---

### Post by Kreaninw on 2012-06-10
> **shymega said:**
> Hm. I'm at a loss but are you sure you installed the right driver for your GPU?

Thanks,
SM

I'm very sure because CCC works fine and the browser itself detects my GPU right. The driver should work without a problem.

---

### Post by shymega on 2012-06-10
I'm afraid I have no idea what's going on here.

I hate to leave a task unfinished but I have no further suggestions.

May the best be with you.

--
SM

---

### Post by Kreaninw on 2012-06-10
> **shymega said:**
> I'm afraid I have no idea what's going on here.

I hate to leave a task unfinished but I have no further suggestions.

May the best be with you.

--
SM

Thanks for your suggestions, I'm glad you're trying to help. =D>

---

### Post by shymega on 2012-06-10
No thank **you** because I learned something new about Firefox!

--
SM :D

---

### Post by sakamoto on 2012-06-10
i can confirm this issue - firefox is indeed slower on ubuntu compared to windows (xp in my case)

---

### Post by coleix on 2012-06-10
Well for me it has always been like this or at least since 10.10 which is when I started using ubuntu and I also have slowish video but I didn't check on 10.10, so is from 11.04 until now. I think is just driver support from AMD, I have an amd card and at first I when everywhere to try and find some way to fix it with updating the drivers, installing x64 bit drivers but nothing ever worked, so I gave up after 2 or 3 weeks of searching the forums, googleing it and get help from the irc channels.

Hope that with steam coming to linux that it will put a little bit of pressure into gpu manufacturers to have better driver support.

---

### Post by Kreaninw on 2012-06-11
It's not just AMD, it's been report to effect NVIDIA user too. [[SIZE=2]Firefox 12's hardware acceleration on Ubuntu 12.04 LTS[/SIZE]]("http://askubuntu.com/questions/140007/firefox-12s-hardware-acceleration-on-ubuntu-12-04-lts")

I think it's Firefox problem. I have managed to use hardware acceleration in Google Chrome by enable all GPU relate feature in **chrome://flags/. **That way I got a much higher result in every hardware acceleration test. Unfortunately, it made Google Chrome very buggy to the level of unusable i.e. can't select text/text box, can't click link, rendering problem and so on.

This is not only Firefox problem, Google Chrome on Ubuntu by default is very slow. Opera feels less difference than its Windows version just because it's only one browser left on desktop platform that's not support hardware acceleration. 

However, Opera Mobile on Android is only browser that's support hardware acceleration by default and it's breezing fast. I still don't get any ICS device to test yet, but on Gingerbread Opera Mobile rules over default browser.

I think this is a critical problem on Ubuntu. In my opinion, a good OS must at least doing good in web surfing. Everyone use web browser anyway.

---

### Post by brainwash on 2012-06-11
Some more background information:

[No Hardware Acceleration Firefox for Linux Due to Buggy X Drivers]("http://www.osnews.com/story/24264/No_Hardware_Acceleration_Firefox_for_Linux_Due_to_Buggy_X_Drivers")

Looks like the proprietary NVIDIA driver has been blacklisted in the meantime to prevent faulty behavior.

---

### Post by D0natell0 on 2012-06-11
You haven't made it too clear the hardware you're using, but some modern motherboards have on-board graphics, which apparently can conflict with your GPU. This results in poor performance you're experiencing.

Usually you can turn off the motherboard graphics from the BIOS. I've proved this works with an Intel core-i7 and nVidia GPU.

Re-start the system and enter the BIOS settings (usually hitting the DEL key repeatedly will do the trick). Then tab through the BIOS pages until you find the [FONT=&quot]Chipset->North Bridge section, and [/FONT][FONT=&quot]turn off the internal video. Hit F10 to save and exit.
HTH.;)
[/FONT]

---

### Post by Kreaninw on 2012-06-11
> **D0natell0 said:**
> You haven't made it too clear the hardware you're using, but some modern motherboards have on-board graphics, which apparently can conflict with your GPU. This results in poor performance you're experiencing.

Usually you can turn off the motherboard graphics from the BIOS. I've proved this works with an Intel core-i7 and nVidia GPU.

Re-start the system and enter the BIOS settings (usually hitting the DEL key repeatedly will do the trick). Then tab through the BIOS pages until you find the [FONT=&quot]Chipset->North Bridge section, and [/FONT][FONT=&quot]turn off the internal video. Hit F10 to save and exit.
HTH.;)
[/FONT]

Thanks. I'm using Acer Aspire 4745G >>> Intel Core i5-460M + ATI/AMD Radeon HD5650. It has Intel graphic on board. I'm currently on discrete mode(disable Intel graphic). Nothing change.

---

### Post by Mia1990 on 2012-06-11
if you think Firefox 12 is slow then don't upgrade to Firefox 13 it's even slower and the copy and paste doesn't work after you open a new tab.

---

### Post by Ravi5kumar on 2012-06-13
When they will fix it? I love firefox but it is terrible slow on my ubuntu 12.04 LTS 64 bit!

---

### Post by Unicast on 2012-06-14
I don't think it's just limited to Firefox. 12.04 feels bloated and sluggish compared to Win XP on my setup here; Pentium D 3.4Ghz and 2.5Gb ram. Ubuntu should fly on this right?

---

### Post by Kreaninw on 2012-06-14
I'm a newly Ubuntu's user. But I can tell you Windows 7 will fly even on a 1GHz netbook. I guess Ubuntu can do the same too. And here on my machine, Ubuntu uses less RAM than Windows 7. 

The bad thing about Ubuntu is it gave me more crash and it heat my machine more than Windows 7. But it's not as bad as slowness browsers without any possible workaround. Firefox, Chrome, Opera, they're all slow on Ubuntu.

---

### Post by Kreaninw on 2012-06-19
With Opera 12 released, hardware acceleration and WebGL are new features of this release and they aren't enabled by default but you can turn them on yourself by going to opera:config. 

Opera 12 on Ubuntu, after I turned hardware acceleration on, I went to usual place, [HTML5 Fish Bowl]("http://ie.microsoft.com/testdrive/Performance/FishBowl/") The result's really impressive. I got higher fps than Firefox on Windows 7 which I said it's the fastest browser on Windows.

In short, the fix for lazy browser to Ubuntu/Linux users just available through Opera 12. All page I have visited render just fine and almost instantly. It would be nice if this'll happen to Firefox soon.

**UPDATE :** Today I have tested Opera 12 on Windows with hardware acceleration and WebGL turned on. At [HTML5 Fish Bowl]("http://ie.microsoft.com/testdrive/Performance/FishBowl/") I got lower result(11fps vs 14fps on Ubuntu at 2,000 fishes) on Windows. Opera really did something this time.

---

### Post by shantiq on 2012-09-04
[FONT=Century Gothic]hhmmmmmmmmmmm   yes it is heavy and slow   ....   maybe try [Midori]("http://twotoasts.de/index.php/midori/") for speed.... i know it has not got the gizmos/add-ons  of firefox but for speed   yeeeeeeeaaa:KS

> sudo apt-get install midori[/FONT] [FONT=Century Gothic]
one of the reasons it is fast is it has no history [no ctrl H] but dropdown box on url box will show you all you want with one or two keys

i only use firefox if i need an add-on that no one else has[/FONT]

---

### Post by vijayckk on 2012-09-17
Recently upgraded from 10.04 LTS to 12.04 LTS. Firefox was initially fine, but once i was done installing other apps it seems to have slowed down considerably.

[COLOR="Red"]Anyways, reading through a bunch of suggestions on the net and playing around I decided to try running firefox in safe mode, which basically disables all the add-ons. This seems to have fixed the issues and now my firefox is blazing again.[/COLOR]

Even though this fixes the issue, i do not quite understand why, i say this because i normally run my browser with all add-ons (plugins)  turned off to begin with.

---

### Post by razor7 on 2012-10-13
Forget about having a descent firefox experience with proprietary drivers!

If you have an ATi card, you can follow this thread [http://ubuntuforums.org/showthread.php?t=1980663](http://ubuntuforums.org/showthread.php?t=1980663)
and after that, follow this thread to uninstall the dribver (believe me you will need it) [http://ubuntuforums.org/showthread.php?t=1981057&page=3](http://ubuntuforums.org/showthread.php?t=1981057&page=3)

It's a shame to have a u$s200 video card and not been able to view a webpage descently!

Of course, we all wait for Steam on Ubuntu, but, think aboy it, maybe when we try to visit steam.com, we can't because hardware acceleration sucks!

Please, do something to have firefox running well on ubuntu.

If you want to support this motion, please suscribe to this bug report [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313)

---

### Post by Kreaninw on 2013-02-25
Even now on Firefox 19, there's still no HWA on Firefox for Linux. CSS 3D transforms look jagged and painfully slow. Even the Android version is a lot faster. I am not recommend anyone to use Firefox on Linux as it's really bad coding. It's like I'm running it on Wine instead of native application. Please use Google Chrome instead and you will see a major performance bost, even before you force enable GPU rendering in chrome:flags.

I don't know what's happened to Firefox. As the most openness browser,  it does support open OS poorly. Google Chrome supported HWA on Linux since age ago and made web experience on Linux machine comparable to Windows and Mac. Both HTML5/CSS3(support HWA) and Flash(newer version though Pepper API) run better on Google Chrome. And it brings NaCl games to Linux simply though their browser. I would gave up on Ubuntu long ago if Google Chrome wasn't this great.

---

### Post by kurt18947 on 2013-02-25
> **Kreaninw said:**
> Even now on Firefox 19, there's still no HWA on Firefox for Linux. CSS 3D transforms look jagged and painfully slow. Even the Android version is a lot faster. I am not recommend anyone to use Firefox on Linux as it's really bad coding. It's like I'm running it on Wine instead of native application. Please use Google Chrome instead and you will see a major performance bost, even before you force enable GPU rendering in chrome:flags.

I don't know what's happened to Firefox. As the most openness browser,  it does support open OS poorly. Google Chrome supported HWA on Linux since age ago and made web experience on Linux machine comparable to Windows and Mac. Both HTML5/CSS3(support HWA) and Flash(newer version though Pepper API) run better on Google Chrome. And it brings NaCl games to Linux simply though their browser. I would gave up on Ubuntu long ago if Google Chrome wasn't this great.


I guess user experiences vary.  I have Chromium (not Chrome) installed.  I don't see a noticeable speed difference between Firefox 19 and Chromium.  I tried Chrome and could never get it to run decently so uninstalled it.  Presumably it's hardware differences.

---

