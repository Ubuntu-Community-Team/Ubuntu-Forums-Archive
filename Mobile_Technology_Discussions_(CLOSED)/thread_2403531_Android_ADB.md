---
title: "Android ADB"
date: 2018-10-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by trose-0928 on 2018-10-12
I am wanting to install Android ADB on my laptop, but I don't know how to do that on Ubuntu 18.04. Anyone know how to? I tried to look it up online, but found nothing.

---

### Post by yetimon_64 on 2018-10-13
According to [[COLOR=#0000ff]--this xda-devellopers.com link--[/COLOR]]("https://www.xda-developers.com/install-adb-windows-macos-linux/") you should be able to install adb from the repositories with the apt command. The link also has instructions for use with linux towards the end of the article.

In the terminal first do a check for the package in 18.04 ...
```
apt-cache policy adb
```
If there is an installation candidate available simply use the next command to install it ...
```
sudo apt install adb
```
The adb package should be in the universe repository, if you cannot find it with the above apt-cache command ensure you have all the repositories enabled in "software sources".

[[COLOR="#0000FF"]--Here--]("https://www.xda-developers.com/adb-fastboot-any-directory-windows-linux/")[/COLOR] is another link to the xda-devellopers site and another, more infomative, tutorial for adb. The Linux section has some further instructions towards the end of the article.

---

### Post by bijayalaxmi1808 on 2018-10-28
You should be able to install the ADB and fastboot binaries on Ubuntu using the apt command as explained in the last reply.

If it still does not work for you then you can try the following link:
[How to install ADB and Fastboot on Linux]("https://www.cyanogenmods.org/forums/topic/install-adb-fastboot-linux-mac-os-x/")

The above link contains downloadable zip files that has some scripts which will install the ADB and Fastboot binaries on Ubuntu.

---

### Post by coffeecat on 2018-11-19
Since this thread is now attracting spammers (spam posts removed)...

Thread closed.

---

