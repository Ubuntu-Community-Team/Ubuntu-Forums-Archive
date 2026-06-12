---
title: "Flash Player 10 Issues"
date: 2009-02-10
forum: Multimedia Software
---

### Post by kenosando on 2009-02-10
I have had troubles with the new flash player I downloaded from Adobe's site. I usually use tar files to install most of my packages, but I saw Adobe offered a DEB package file, so I figured it would save a few minutes. However, although GDebi acknowledges that the package is installed correctly, it is not connecting with Firefox as a plugin. I restarted Firefox, my machine, and flash sites still request a Flash plugin. This might either need to be reported as a bug, or if there would be further configuration to have Firefox utilize the plugin, but installation using the tar file option worked just fine, all flash pages work great. 

Has anyone come across this issue, as the DEB package(s) not working correctly?

---

### Post by gandaran on 2009-02-10
the .deb package works for ubuntu 8.04 and above only, what is your version?

---

### Post by kenosando on 2009-02-10
I am running 8.04. GDebi shows it to be installed, but Firefox doesn't.

---

### Post by gandaran on 2009-02-11
> **kenosando said:**
> I am running 8.04. GDebi shows it to be installed, but Firefox doesn't.
where did you install that flash from the tar.gz package, in /home/user/.mozilla/plugins? firefox will look for flash there first then /usr/lib/mozilla/plugins if it finds flash there it will ignore any other flash installed, maybe you also have some other flash packages installed that prevented firefox finding flash from the adobe-flashplugin package!
post the out of **locate libflash** here

---

### Post by khisanth75 on 2009-05-27
I have this problem too. Just downloaded the latest version of Ubuntu, did all the updates and I get exactly the same problem!

says flash is installed but firefox doesnt see it :(

---

### Post by spoilingmyself on 2009-08-05
hey ppl!!
i too am having the same problem. about:plugins shows that flash player 10 is installed and but adobe's site and all other sites show that flash 9 is installed but ie6 can detect flash player 10 on the same machine... dont know what to do.. the tar package on extraction only gives libflashplayer.so file and not a folder... i am stuck badly please help me...
any and every help will be appreciated!!!

---

### Post by befana on 2009-08-05
I had the same problem after installing Adobe Flash 10 from Synaptic. I found in Synaptic swfdec-mozilla, swfdec-gnome and libswfdec-0.8-0 were installed. I have removed these three packages and now Mozilla works with Adobe Flash player 10. Hope this help for you too.

---

### Post by spoilingmyself on 2009-08-05
hey folks wat worked for me was just disabling flash 9 from add-ons and then flash 10 was working... actually flash 10 was also installed along with flash 9 and that is why some issues were arising..
thanks anyways

---

### Post by crictor on 2009-08-08
I was having the same problem with flash not being recognized so I tried disabling flash 10 under addons in the browser, going back to youtube to get the message of not having a player, then turning it back on under addons.   Worked fine after that.

---

### Post by haydemon on 2009-10-07
> **crictor said:**
> I was having the same problem with flash not being recognized so I tried disabling flash 10 under addons in the browser, going back to youtube to get the message of not having a player, then turning it back on under addons.   Worked fine after that.

No Flash Player version shows up in my Firefox plugin list, so I cannot disable any of them. System checks thru Adobe shows I'm running an old version of Flash Player (9.0..), when I'm actually running the latest version provided thru Synaptic (10.0.32.18). It's not recognized by FF at all! I've tried uninstalling & reinstalling, at the console level, as well as thru Synaptic, and also through the .deb file provided by Adobe, but to no avail. I'm frustrated because some games, etc., don't work in Firefox right now. I have recently updated to the FF 3.5 version, thinking the problem was due to using FF 3.0, but same problem still. HELP!

Please be VERY SPECIFIC with any instructions, because I know enough about Linux to do damage, but not very proficient in general. Thx!:confused:

---

### Post by Frank Castle on 2009-10-07
> **befana said:**
> I had the same problem after installing Adobe Flash 10 from Synaptic. I found in Synaptic swfdec-mozilla, swfdec-gnome and libswfdec-0.8-0 were installed. I have removed these three packages and now Mozilla works with Adobe Flash player 10. Hope this help for you too.

Thanks! I removed swfdec-mozilla and libswfdec-0.8-0 which did it for me. Google maps streets view works now!

---

