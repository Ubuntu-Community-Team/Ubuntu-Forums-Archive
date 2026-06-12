---
title: "Kernel 2.6.17"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by xxrealmsxx on 2006-06-20
I have been hearing everywhere online that the 2.6.17 kernel provides better support for wireless.

Is this true?

If so how do I go about upgrading? :D

---

### Post by noname101 on 2006-06-20
You'll have to download it from [kernel.org]("http://kernel.org") and compile it yourself.

---

### Post by trenktaz on 2006-06-23
[http://ubuntu.mirrors.tds.net/pub/linux/ftp.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/](http://ubuntu.mirrors.tds.net/pub/linux/ftp.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/)

---

### Post by xxrealmsxx on 2006-06-23
[QUOTE=trenktaz][http://ubuntu.mirrors.tds.net/pub/linux/ftp.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/](http://ubuntu.mirrors.tds.net/pub/linux/ftp.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/)[/QUOTE]

Which one of those installers do i use?

Thanks btw!

---

### Post by stevejesus on 2006-06-23
> 
Which one of those installers do i use?

Thanks btw!
You will want to use the one that matches your architecture.  Those seem to be broken up into several different modules.  I don't know how to install these in this manner, but I am looking into it.  I need 2.6.17 so that I can finally use the Airport Extreme card in my Apple Powerbook.

---

### Post by xxrealmsxx on 2006-06-23
[QUOTE=stevejesus]You will want to use the one that matches your architecture.  Those seem to be broken up into several different modules.  I don't know how to install these in this manner, but I am looking into it.  I need 2.6.17 so that I can finally use the Airport Extreme card in my Apple Powerbook.[/QUOTE]


You can get the entire kernel right here: [http://www.kernel.org/](http://www.kernel.org/)

I just dont know how to compile it :???:

---

### Post by stevejesus on 2006-06-23
It would probably not be the best idea to compile a vanilla kernel from kernel.org.  That would break alot of features.  I am still researching on how to upgrade the kernel myself.  I am just afraid that I will break my configuration.

---

### Post by xxrealmsxx on 2006-06-23
[QUOTE=stevejesus]It would probably not be the best idea to compile a vanilla kernel from kernel.org.  That would break alot of features.  I am still researching on how to upgrade the kernel myself.  I am just afraid that I will break my configuration.[/QUOTE]


Yeah thats part of the reason i haven't looked into it that much.


I've been advised to just buy a new wifi card, i may do that or pray that the next ubuntu release will have better support.

---

### Post by stevejesus on 2006-06-23
No, don't waste your money.  If it is available then it will work.  I am dedicating myself to finding answers by the end of the day.
I notice that the link that was posted above were all .udebs.  I am not familiar with .udebs, but maybe it is as simple as just doing a sudo dpkg -i nameofkernelpackagesforarch.
Anyone have any answers on this?

---

### Post by stevejesus on 2006-06-23
also...  if you are unsure of which packages to get, do this
> uname -r
That will give you the name of your currently running kernel.  Compare that with the names of the kernel .udebs that you need to download from here.
> [http://ubuntu.mirrors.tds.net/pub/li...source-2.6.17/](http://ubuntu.mirrors.tds.net/pub/li...source-2.6.17/)
Go ahed and download them for now.  I am more than certain you will need them once an answer arises.

---

### Post by misha680 on 2006-06-24
Deleted

---

### Post by misha680 on 2006-06-25
Ok ,I got LEAP to work with my Intel PRO/Wireless 2100 without recompiling the kernel. Here's how:

* Go to ipw2100.sourceforge.net and download version 1.2.0 
* Go to ieee80211.sourceforget.net and download version 1.1.14
* Install the linux-headers appropriate for your kernel version (just use synaptic, that's what I did)
* Only tricky part, do:
    sudo ln -s /usr/src/linux-headers-$(uname -r)/include /lib/modules/$(uname -r)/include
* Unpack the .tgz files for ipw2100 and ieee80211 into /usr/src (they will make ipw2100 and ieee80211 subdirectories). Basically just do a make in each directory, adn then when it compiles successfully do a sudo make install for each one
* Now reboot your system (not sure if you absolutely have to do this, but it guarantees the new ones are loaded). Now
do a "dmesg | grep ipw" and make sure that version 1.2.0 is running
* The next tricky part is the LEAP configuration .There's a WPA HowTo on the Wiki, but basically you just need to mess
with your /etc/network/interfaces using various wpa-blah settings until it works. Here is what worked for my school's network, 
maybe it will help someone else too:

iface eth1 inet dhcp
    wpa-ssid ssid
    wpa-scan-ssid 1
    wpa-auth-alg OPEN
    wpa-key-mgmt IEEE8021X
    wpa-eap LEAP
    wpa-ap-scan 2
    wpa-identity login
    wpa-password password

wpa-ap-scan was especially critical for me.

Good luck everybody.

Misha

---

