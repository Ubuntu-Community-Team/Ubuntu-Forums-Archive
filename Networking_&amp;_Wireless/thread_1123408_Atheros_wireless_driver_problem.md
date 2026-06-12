---
title: "Atheros wireless driver problem"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Omri16 on 2009-04-12
Hi all,

I have an HP Pavilion dv6000 laptop with an Atheros wireless driver. lspci -v gives the following:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: fast devsel, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

```
I tried to get wireless connection using the instructions given by reasoner here:
[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6]("http://ubuntuforums.org/showpost.php?p=5711824&postcount=6")
But it doesn't seem to work well. After I did the svn thing and tried the make and make install commands I got this:
```
omri@omri-laptop:~/madwifi/madwifi-hal-0.10.5.6$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/home/omri/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.o
cc1: warnings being treated as errors
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c: In function 'ath_hw_reset':
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c:1634: warning: unused variable 'lclass'
make[3]: *** [/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.o] Error 1
make[2]: *** [/home/omri/madwifi/madwifi-hal-0.10.5.6/ath] Error 2
make[1]: *** [_module_/home/omri/madwifi/madwifi-hal-0.10.5.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [modules] Error 2
omri@omri-laptop:~/madwifi/madwifi-hal-0.10.5.6$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/home/omri/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.o
cc1: warnings being treated as errors
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c: In function 'ath_hw_reset':
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c:1634: warning: unused variable 'lclass'
make[3]: *** [/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.o] Error 1
make[2]: *** [/home/omri/madwifi/madwifi-hal-0.10.5.6/ath] Error 2
make[1]: *** [_module_/home/omri/madwifi/madwifi-hal-0.10.5.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [modules] Error 2

```
I don't know why it shows an error, and I have no idea if it worked or how to connect to a wireless network (I don't know where to find the list of available networks). Can anyone please guide me?

Thanks a lot!! :)

---

### Post by moore.bryan on 2009-04-12
couple of quick questions: what ubuntu flavor are you using (gnome, kde, xfce, other)? what kernel are you using? the following lines in a terminal will give that info:
```

lsb_release -a
uname -r

```

---

### Post by tfc on 2009-04-12
This points to the problem:
```
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c: In function 'ath_hw_reset':
/home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c:1634: warning: unused variable 'lclass'
```

Someone set the make-script make the compiler cry "ERROR!!!" if there's a warning.

Open the file /home/omri/madwifi/madwifi-hal-0.10.5.6/ath/if_ath.c 
And edit:
```
int i, lclass = 0;
```
To
```
int i;
```

It should compile now.

---

### Post by Omri16 on 2009-04-12
Thanks, now it really compiles! But where do I see the list of wireless networks, and how do I connect to one?

EDIT:
lsb_release -a gives:
```
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```
uname -r gives:
```
2.6.24-22-generic

```

---

### Post by tfc on 2009-04-12
After having typed "make" and "sudo make install" you have the module compiled and installed, but not loaded.

"sudo modprobe ath_pci" loads it. Some seconds later you should be able to list wireless networks.

---

### Post by Omri16 on 2009-04-12
I did the "sudo modprobe ath_pci" but I don't know what to do now...

---

### Post by por100pre1 on 2009-04-12
Try *testing* an Intrepid Live CD. Intrepid uses the Atheros ath9k driver. If wireless works on the Intrepid Live CD, you should consider upgrading your Ubuntu release.

---

### Post by tfc on 2009-04-12
> **por100pre1 said:**
> Try *testing* an Intrepid Live CD. Intrepid uses the Atheros ath9k driver. If wireless works on the Intrepid Live CD, you should consider upgrading your Ubuntu release.

Yeah, it's a better solution instead of messing around with an old ubuntu version.
But if ath9k makes problems (on my machine it does), use madwifi.

---

### Post by Omri16 on 2009-04-12
I don't really understand - I think my ubuntu is the latest one. I managed to compile it and (I think) loading it - what do I do now?

---

### Post by Omri16 on 2009-04-12
I'm sorry to jump the thread up, but it got to the second page already... I managed to install the madwifi, can someone tell me how to list the available wireless networks?

Thanks!

---

### Post by t0mppa on 2009-04-12
To see the list of available wireless networks, run ```
iwlist scan
``` in a terminal window or open up the Network Manager which should be found from the Notification Area, right side of the top panel.

And ath9k is a driver designed for 802.11n chips, no point using it with a 802.11abg type of chip. The MadWifi driver should work just fine for this chip.

Oh and you're on Ubuntu 8.04, which is a long term support version (meaning it's supported until 2011), no explicit need to upgrade yet. There's 8.10 out, but judging from this forum, it certainly doesn't make things any easier when it comes to wireless issues. Version 9.04 is also coming out in a week or so, so if you're set on updating your system, better get the beta version of that (can be updated to full later) or wait until the final version is launched.

---

### Post by Omri16 on 2009-04-12
I tried the command iwlist scan and got:
[CODE]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
[\CODE]
In the notification area I don't see anything... what's going on? :P

Thanks

---

### Post by t0mppa on 2009-04-13
Then your driver isn't working. Are you sure you got it installed properly? Run ```
sudo lshw -C network
``` to give some idea of what's going on.

---

