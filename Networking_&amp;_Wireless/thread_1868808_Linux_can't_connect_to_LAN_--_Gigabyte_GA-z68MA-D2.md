---
title: "Linux can't connect to LAN -- Gigabyte GA-z68MA-D2H-B3"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by TastemyHouse on 2011-10-24
Hello,

I have a Gigabyte GA-Z68MA-D2H-B3 motherboard. I am able to connect to my LAN (and thus the internet) just fine on Windows and OS X, but under Linux, I cannot connect. I have tried this under Arch 2011.08.19, Ubuntu 10.04 64 bit, Ubuntu 11.10 64 bit, and Ubuntu 11.10 32 bit. I haven't tried 10.04 32 bit yet because I thought I'd ask her for help before I went through the trouble. the motherboard uses a Realtek RTL8111E NIC, so I went to the realtek website to see if they had working drivers. I found this [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2) and tried to install it. It worked -- once. After I rebooted, network didn't work again, and if I tired to insert the kernel module again the computer would hang, then crash.

Google shows that some other people have been having trouble with this issue, but I was unable to find a fix that worked for me.

If there's any help anyone can give, I'd appreciate it. I'm going to try Ubuntu 10.04 32 bit now, and report back if that helps. If anyone needs any further information, please let me know and I'll be happy to provide it.

---

### Post by frdrx on 2011-11-19
I've just built a computer using this motherboard and managed to get the ethernet card working by following these [http://ubuntuforums.org/showthread.php?t=1022411]("http://ubuntuforums.org/showthread.php?t=1022411") instructions.

---

### Post by dramos on 2011-11-21
This is weird, I have the same motherboard. I am able to connect but the speed in Ubuntu is slower that the speed in Windows.

Here is a a thread about my problem, I am still waiting for help.

[http://ubuntuforums.org/showthread.php?t=1884577]("http://ubuntuforums.org/showthread.php?t=1884577")

---

### Post by praseodym on 2011-11-21
Hi,

the Realtek 8168B card often makes problems with the driver r8169. Alternatively the "real" driver r8168 can be installed via:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2
tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
sudo modprobe -rfv r8169
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
sudo depmod -a
sudo modprobe -v r8168
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by ZaHACKieL on 2012-02-01
Thanx a lot mate! It worked beautifully in Ubuntu 11.10 now I'll try it in 11.04. I hope it works too

---

### Post by praseodym on 2012-02-01
I created a file which can be installed by "dkms", so you dont need to compile again after a kernel upgrade:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3005217/r8168-dkms-8.027.00.tar.gz
sudo tar xvf r8168-dkms-8.027.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.027.00
sudo dkms build -m r8168-dkms -v 8.027.00
sudo dkms install -m r8168-dkms -v 8.027.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168 
```

---

