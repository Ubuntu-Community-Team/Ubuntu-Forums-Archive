---
title: "WARNING: -e needs -E or -F ??"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by ad libitum on 2011-03-16
Greetings,

I'm patching my RTL8187L driver for use with Aircrack, following aircrack's instructions (taken from [http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=4058613f8aec9794204642e1816fd213](http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=4058613f8aec9794204642e1816fd213) ):

```
ifconfig wlan0 down    
rmmod r8187 rtl8187 2>/dev/null
wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget http://patches.aircrack-ng.org/rtl8187_2.6.27.patch
wget http://patches.aircrack-ng.org/rtl8187_2.6.32.patch
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.27.patch
patch -Np1 -i rtl8187_2.6.32.patch
make
make install
```

Everything is fine until "make install", which tells me "WARNING: -e needs -E or -F", and I am at a dead end and don't know how to proceed.

```


user1@user1-HP-Pavilion-dv6000-GA456UA-ABA:~/rtl8187_linux_26.1010.0622.2006$ sudo make install
install -d /lib/modules/2.6.35-27-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -d /lib/modules/2.6.35-27-generic/kernel/drivers/net/wireless/rtl8187
install -m 644 ./ieee80211/*.ko /lib/modules/2.6.35-27-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -m 644 ./beta-8187/*.ko /lib/modules/2.6.35-27-generic/kernel/drivers/net/wireless/rtl8187
depmod -ae
WARNING: -e needs -E or -F
user1@user1-HP-Pavilion-dv6000-GA456UA-ABA:~/rtl8187_linux_26.1010.0622.2006$
```

Anyone know what "WARNING: -e needs -E or -F" means? I'm a total noob, not really good for much besides following simple instructions... and thus I have no idea what the warning means. I'm running Ubuntu 10.10, all current updates, 2.6.35-27-generic. Maybe the depmod -ae command needs changing?

Cheers

---

### Post by Delebre on 2011-04-22
I am having this same issue. Both in Fedora 14 and Ubuntu 10.10.

What I do is download Madwifi-ng from here:
```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

It grabs revision 4136.
I do a make and make install.

Rebooting at this step doesn't do anything

If I run
```
depmod -ae
```

It responds:
```
WARNING: -e needs -E or -F
FATAL: Could not open /lib/modules/2.6.35-22-generic/modules.dep.temp for writing: Permission denied
```

If I run:
sudo depmod -ae

Same thing, however it doesn't display the FATAL message. 

Is there an issue with this build and my kernel? 
```
2.6.35-22-generic
```
It was the same revision of Madwifi-ng and the same kernel I used in Fedora 14.

I am at a loss. Help!

---

### Post by Delebre on 2011-04-22
Bump

Can anyone help please? The original poster put this up weeks ago, and the problem still exists for multiple people. 

I really appreciate the forums and the people in it, please don't think I'm being pushy without a good reason.

---

### Post by Delebre on 2011-04-22
Well for anyone that runs into this in the future, by omitting -e and just running depmod -a

That seemed to have worked fine. :)

Thanks to the boys on IRC!

---

