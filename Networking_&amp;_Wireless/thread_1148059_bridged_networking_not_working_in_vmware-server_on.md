---
title: "bridged networking not working in vmware-server on jaunty"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by ittayd on 2009-05-04
Hi,

I downloaded the latest (1.0.9) vmware-server from vmware, installed, then downloaded a patching bundle from [http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627) and installed, configuring bridged network over my wireless card (vmnet2 over wlan0). 

When I start my (only) guest (Windows XP), the network interfaces don't get an IP from DHCP (I have a wireless router. I turned mac filtering off).

Do you have suggestions as to how to debug / fix this?

Thank you,
Ittay

---

### Post by ittayd on 2009-05-04
bump

---

### Post by dog.breath on 2009-05-05
I'm seeing the same behavior after upgrading my host from Intrepid to Jaunty.  I'm running VMWare Server 2.0.1 with a WinXP guest.

---

### Post by dabl on 2009-05-17
Has anyone found a fix for VMWare bridged networking on 9.04?

I thought possibly my issue could have been attributable to the old Win XP VM, which I've been dragging around for several years. However, today I set up a new Win 7 RC VM, first in sidux, where it works flawlessly (except sound ...) and then opened it from Kubuntu 9.04 and I got the same "bridged network is down" error as I get from the Win XP VM.  So, the issue is definitely in *buntu 9.04, not the VM or VMWare Player.

---

### Post by superprash2003 on 2009-05-18
have you tried static ip , or using the repair option in windows or the dhclient command in ubuntu

---

### Post by dabl on 2009-05-18
SOLVED. 

Well, maybe "WORKED AROUND A BUG" is more to the point.

On 9.04, but not any earlier version that I know of, you have to do this before you start your virtual machine;
```

sudo /etc/init.d/vmware stop
```

```
sudo /etc/init.d/vmware start
```


Then the VM will open with bridged networking available.  Go figure ...

---

### Post by RealG187 on 2009-06-07
I did that and it still isn't working for me
[http://ubuntuforums.org/showthread.php?t=1167432](http://ubuntuforums.org/showthread.php?t=1167432)

---

