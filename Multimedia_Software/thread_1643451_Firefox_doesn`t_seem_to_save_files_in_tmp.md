---
title: "Firefox doesn`t seem to save files in /tmp"
date: 2010-12-11
forum: Multimedia Software
---

### Post by proggy on 2010-12-11
I`ve just noticed that when I play from a flash video site in Firefox it doesn`t save it to /tmp.
Anyone know where it goes now?

---

### Post by Krytarik on 2010-12-12
~/.mozilla/firefox/PROFILE/Cache ;)

---

### Post by proggy on 2010-12-12
I can`t seem to find cache could you give me the path please?

---

### Post by sgosnell on 2010-12-12
He gave you the path, but you need to replace /PROFILE/ with your profile, which is a series of random characters.

---

### Post by Krytarik on 2010-12-12
And the "~" means your "Home Folder".
Sorry, if you're new to Linux, you'd probably not know this.

The full path hence is: /home/YOUR_USERNAME/.mozilla/firefox/PROFILE/Cache .

EDIT: By the way, why don't you use this extension instead?: [Video DownloadHelper :: Add-ons for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/3006/")

---

### Post by chetancrasta on 2011-02-25
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

