---
title: "Loving 11.04 so far"
date: 2010-10-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-10-20
Just rebooted into the new kernel and, lo and behold, changing the display brightness works, on my Lenovo Y450, this is the first time ever that it's automatically worked! Bonus!

Yar, bring on the breakage!

---

### Post by inportb on 2010-10-21
Congratulations. Y'know, even though Maverick works for me so far, I'm going to upgrade for giggles ;p

---

### Post by MilkeySUFC on 2010-10-21
> **inportb said:**
> Congratulations. Y'know, even though Maverick works for me so far, I'm going to upgrade for giggles ;p

So, how does one upgrade to Natty? I have had 10.10 on a small test partition since Alpha 2 and everything worked fine until the final release updates broke my 802.11n wi-fi connection.

How do I upgrade this test partition to Natty? Would like to test my wi-fi on Natty.

MilkeySUFC

---

### Post by DougieFresh4U on 2010-10-21
> **MilkeySUFC said:**
> So, how does one upgrade to Natty? I have had 10.10 on a small test partition since Alpha 2 and everything worked fine until the final release updates broke my 802.11n wi-fi connection.

How do I upgrade this test partition to Natty? Would like to test my wi-fi on Natty.

MilkeySUFC

You can open sources list and change all 'Maverick' to 'Natty' save and close. I am sure there are other ways, but this is how I manage it.
then:
[B]sudo apt-get update
sudo apt-get dist-upgrade[/B]

---

### Post by jppr on 2010-10-21
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade :popcorn:

---

### Post by ubername on 2010-10-21
Also, [http://ubuntuforums.org/showthread.php?t=1595893](http://ubuntuforums.org/showthread.php?t=1595893) to make sure you can get to your software sources.

---

### Post by JCoster on 2010-10-21
> **Arla said:**
> Just rebooted into the new kernel and, lo and behold, changing the display brightness works, on my Lenovo Y450, this is the first time ever that it's automatically worked! Bonus!


I wasn't planning to upgrade until alpha 1, but having read your post I just upgraded with hope that my screen brightness would work on 2.6.36 and I can gladly report it does!  On Vaio FW-31ZJ.

Cheers!

---

### Post by JOHNNYG713 on 2010-10-21
I was having no issues until today's update! I can boot to the desktop but have lost "out the box" 3D graphics drivers (ATI 9600) and can get no task bars! safe mode works! Hmmm maybe the next update will repair it! this is no big deal 11.04 is on a "test partition"! :)

---

### Post by cariboo on 2010-10-21
I got some wierd  things happening with chromium and firefox after yesterdays updates. On one system when I enter a search term in the url bar, when I hit enter nothing happens. If I enter a url, it works as it should.

On the other system, using chromium or firefox causes the system to lock up hard.  It may be due to some extensions we use for moderating, as if I remove the greasemonkey addon from Firefox the lockups don't happen.

---

### Post by MacUntu on 2010-10-21
Just had my first system freeze without any error messages. SysRq worked, probably could have connected remotely, but no other system around. :(

---

### Post by cariboo on 2010-10-21
The lock ups I was getting totally froze the system, even pings weren't being returned.

---

### Post by Starks on 2010-10-21
Anyone else getting openjdk package errors?

---

### Post by MacUntu on 2010-10-21
> **Starks said:**
> Anyone else getting openjdk package errors?

Had it on one machine, but "apt-get install -f" fixed it (or was it just running the update a second time? - I don't remember).

---

### Post by cariboo on 2010-10-21
The latest update I just did fixed the error, and the new kernel seems to have fixed the lockup problem I was having. [[IMG]http://imgur.com/YuzCr.png[/IMG]](http://imgur.com/YuzCr.png)

---

### Post by jppr on 2010-10-22
Just upgraded Kubuntu 10.10 - > 11.04 and system runs without problems like Ubuntu :)

I have 2 HD, Ubuntu is sda 1 and Kubuntu sdb1. There´s now new Grub2 and system work fine.

---

### Post by NightwishFan on 2010-10-22
I will have to install a daily build in vbox to keep up. :) I think natty will be a must for the netbook crowd.

---

### Post by terry_gardener on 2010-10-22
11.04 has seemed to have fixed with a problem booting properly. 

with 10.10 when i selected ubuntu boot option from grub it would stay at the flashing cursor until i pressed the left or right arrow key. sometimes the left would work and start the system but other times it was the right arrow keys. it was very weird and very annoying. 

guessing the .36 kernel fixed this.

---

### Post by Kevbert on 2010-10-23
Just downloading the first 259 updates now with a sudo apt-get upgrade after changing sources.list, let's hope for breakages...

Just had too update problems:
```
Setting up speech-dispatcher (0.7.1-0ubuntu1) ...
Installing new version of config file /etc/speech-dispatcher/modules/ibmtts.conf ...
Installing new version of config file /etc/speech-dispatcher/modules/espeak-mbrola-generic.conf ...
Installing new version of config file /etc/speech-dispatcher/speechd.conf ...
update-rc.d: warning: speech-dispatcher stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
speech-dispatcher disabled; edit /etc/default/speech-dispatcher]
```

and

```
(gtk-update-icon-cache:7718): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory
```
which repeats a few times (but can't find it in logs?)
Anyone else seen this ?

Natty is installed...
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu natty (development branch)
Release:	11.04
Codename:	natty

```

---

### Post by Quackers on 2010-10-23
Installed, fully updated - no problems at all! I can't break it yet! Will keep trying :-)

Edit: I've been getting pixbuf errors by the bucket full since 10.04 Sadly, I don't even know what it is, but it doesn't seem to have impacted on anything.

---

### Post by sgage on 2010-10-24
Another successful update from Maverick... I just finished an uneventful update, rebooted, and everything seems fine. Early days, though ;-)

---

