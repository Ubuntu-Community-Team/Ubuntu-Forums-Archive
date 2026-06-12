---
title: "Uploading pictures to various sites"
date: 2008-12-07
forum: Multimedia Software
---

### Post by rplogue on 2008-12-07
Hello, I use firefox and I have flash installed and enabled. I have a problem with just about every site that I try to upload a picture to. When I browse to the location on my hd and then click ok nothing happens. Anybody have any idea why this would be? Is it a firefox issue? a ubuntu issue? a combination? or maybe there are some settings i need to tweak?

Thanks for any help.

---

### Post by jakobtritten on 2008-12-08
I'm having the same problem.  You're not alone.  I'm interested to hear what anybody has to say as well.  Thank you.

---

### Post by jakobtritten on 2008-12-10
Bump

---

### Post by robomoon on 2008-12-30
Here's a message at [http://ohioloco.ubuntuforums.org/showthread.php?p=6401412#post6401412](http://ohioloco.ubuntuforums.org/showthread.php?p=6401412#post6401412) about multi file uploading, also mentioned at [http://ubuntuforums.org/showthread.php?t=1015859&page=2](http://ubuntuforums.org/showthread.php?t=1015859&page=2) where further issues with Firefox are explained. This problem appeared in Xubuntu Hardy, but not in Puppy Linux which I installed to HD one year ago. It may be Adobe Flash 10 in Firefox 3 which is causing the error at sites where multi file uploading with Flash and JavaScript is required.

For testing, I made a frugal install of flexxxpup v.1.4 Serene to a harddisk partition where Xubuntu is located as well. In Puppy Linux, I removed Flash 10 on Firefox 3 including the "/usr/lib/firefox" directory and installed lower versions of these packages. Chosen from [http://www.puppylinux.ca/tpp/bugs/](http://www.puppylinux.ca/tpp/bugs/) were the following packages: adobe_flash_player-9.0.124.0.pet and firefox-2.0.0.17.pet which enable multi file uploading at sites where Flash with JavaScript trigger the opening of a window for file selection. These file uploads work well in my downgraded flexxxpup.

There may be a mistake I made within the deinstallation of Flash 10 and Firefox 3 in Xubuntu which rendered my effort to downgrade to earlyer versions unsuccessful.

---

