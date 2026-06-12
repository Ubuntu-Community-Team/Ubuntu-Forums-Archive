---
title: "very slow network configuration"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by wpollans on 2006-01-09
Hello,

I'm running Breezy on a Dell 700m laptop.  Everything seems to be working fine.  

My problem is that it takes about 30-40 seconds for "Configuring Network Interfaces" to complete on boot.  It also take this much time if I enable & activate the ethernet interface (eth1) from networking panel - it tries a couple of times to get the dhcp info before it finally succeeds - eth0 is the wireless interface, which is not enabled right now.  I have a work station (fedora 3) and a G3 ibook (OSX.3.9) that run on this same network - both are able configure their ethernet interfaces quite quickly.

This isn't normal, is it?  Any suggestions would be appreciated.

Thanks,

Warren

---

### Post by zahidism on 2006-01-09
so you've disabled the eth0 (wireless...weird name btw..mine is wlan0) and with eth1 (ethernet) enabled it takes 30-40 seconds to configure?

---

### Post by wpollans on 2006-01-10
[QUOTE=zahidism]so you've disabled the eth0 (wireless...weird name btw..mine is wlan0) and with eth1 (ethernet) enabled it takes 30-40 seconds to configure?[/QUOTE]

Yes, that's correct.  

Who/what determines the interface names?  wlan instead of eth?

The wireless connection works, via wifi-radar - with the wireless connection established I can fire up vmware with XP in a VM and use IE with no aparent problems.  I disabled eth0 to try to simplify things.

Are there logs, other than syslog, that would help me figure this out?

---

### Post by wpollans on 2006-01-10
OK, fixed interface names - unfortunately, it help the slow configuration problem - I'll keep at it - checking the logs (that I can find) more closely

---

### Post by Seanuntu on 2006-01-25
I am having this exact same problem.  I have a gateway 7422gx.  I am using ndiswrapper to emulate the windows broadcom drivers.

---

### Post by FLeiXiuS on 2006-01-25
Yikes, broadcom drivers.  When using ndiswrapper be sure to include both the INF and the SYS files in the same directory when installing.  This is a BIG time problem with Broadcom's BM* chipsets.  

Also, what happens when you try to initiate the interface manually.  

$ sudo ifconfig eth1 down && sudo ifconfig eth1 up

With that in mind, also check:

$ iwconfig eth1

Just be sure the information in there looks correct.  The SSID // AP MAC Address.  


NOTE: For those who are wondering how the device names are chosen, it's based upon the wireless chipset.  Some wi-fi cards define their device as wlan, ath, eth, wifi, cisco, etc... It's all depending on what their card specifies.  Don't be alarmed if your device name differs from others.

---

### Post by ned.b on 2006-01-27
I fixed the same problem (ndiswrapped Belkin) on my laptop and posted the fix on another thread...

[http://www.ubuntuforums.org/showthread.php?t=115239&page=3](http://www.ubuntuforums.org/showthread.php?t=115239&page=3)

hope it helps

---

