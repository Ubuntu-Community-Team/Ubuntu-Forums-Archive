---
title: "Can't solve Broadcom BCM4313 wireless problem on Ubuntu 12.04"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by bblanchon on 2012-10-06
Hello,

I've just installed Ubuntu 12.04 32bit on my HP dm1, and the wireless doesn't work. The wireless card is the Broadcom BCM4313. I tried many solutions from many forums, but nothing works. Can someone help me to solve this problem ?

Thanks a lot !

bblanchon

---

### Post by bblanchon on 2012-10-07
Nobody can help me, please ?

Thank you !

---

### Post by Sef on 2012-10-07
Not knowing what you have tried, have you followed [these instructions]("http://ubuntuforums.org/showthread.php?t=1604868")?

---

### Post by bblanchon on 2012-10-07
Thank you for your answer Sef !
I've just tried the three solutions on your link, but it still doesn't work.
Tell me if you need more information about my computer to help me !

Thanks again !

---

### Post by chili555 on 2012-10-07
Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by bblanchon on 2012-10-08
> **chili555 said:**
> Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

The first rfkill list is done without pushing the wifi button and the second one, after pushing it.

Thank you !

---

### Post by chili555 on 2012-10-08
Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? If so, we'll write a file and make it persistent.

---

### Post by bblanchon on 2012-10-08
> **chili555 said:**
> Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? If so, we'll write a file and make it persistent.

```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo modprobe -r hp-wmi
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo rfkill unblock all
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

Thank you chili555 :), but there is not any improvement...

---

### Post by chili555 on 2012-10-08
Now please try an additional step:```
sudo modprobe -r wl
sudo modprobe brcmsmac
sudo rfkill unblock all
rfkill list all
```

---

### Post by bblanchon on 2012-10-08
> **chili555 said:**
> Now please try an additional step:```
sudo modprobe -r wl
sudo modprobe brcmsmac
sudo rfkill unblock all
rfkill list all
```

```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo modprobe -r wl
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo modprobe brcmsmac
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo rfkill unblock all
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Thanks a lot ! Pushing the button, it works !
However, even if I'm closed to the wifi router, the signal is very low. Do you know how I can solve this problem ?

---

### Post by bblanchon on 2012-10-08
And, as you suggest before, it doesn't work when I restart the computer.

---

### Post by chili555 on 2012-10-08
Let's get the driver fixed first:```
sudo su
apt-get remove --purge brcmwl-kernel-source
echo brcmsmac >> /etc/modules
exit
```Now reboot and let me have a report.

---

### Post by bblanchon on 2012-10-08
I've done commands that you told me to reactivate wifi after doing last commands and reboot, but the signal is still quite low. In "Connection informations", the speed indicated is 28Mb/s at 40cm of the router.

---

### Post by chili555 on 2012-10-09
> **bblanchon said:**
> I've done commands that you told me to reactivate wifi after doing last commands and reboot, but the signal is still quite low. In "Connection informations", the speed indicated is 28Mb/s at 40cm of the router.I am not aware of any method in the driver to affect signal strength. You might look around in the router's configuration pages. Make sure if there is a transmit power setting, that it's at the maximum. Experiment with channels. Most routers are set, by default, at channel 6. I have the best luck with channel 11. Finally, many routers have a selection for antennae; left, right, both or automatic. Experiment with each.

---

### Post by bblanchon on 2012-10-09
Thank you chili555, but nothing changes. On other forums, it seems that installing the driver from the Broadcom website ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) it works. I tried, following the Readme instructions, but I have a problem when I try to do the make function. This is what happens :
```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~/drivers/hybrid_wl$ sudo make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-31-generic-pae »
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CC [M]  /home/baptiste/drivers/hybrid_wl/src/wl/sys/wl_linux.o
/home/baptiste/drivers/hybrid_wl/src/wl/sys/wl_linux.c:388:2: erreur: unknown field ‘ndo_set_multicast_list’ specified in initializer
/home/baptiste/drivers/hybrid_wl/src/wl/sys/wl_linux.c:388:2: attention : initialization from incompatible pointer type [enabled by default]
/home/baptiste/drivers/hybrid_wl/src/wl/sys/wl_linux.c:388:2: attention : (near initialization for ‘wl_netdev_ops.ndo_validate_addr’) [enabled by default]
make[2]: *** [/home/baptiste/drivers/hybrid_wl/src/wl/sys/wl_linux.o] Erreur 1
make[1]: *** [_module_/home/baptiste/drivers/hybrid_wl] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-31-generic-pae »
make: *** [all] Erreur 2

```

Do you know how I can solve this problem ?

Thank you !

---

### Post by chili555 on 2012-10-09
Please see here: [http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/](http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/)

Please post back if you need assistance applying the patch.

---

### Post by bblanchon on 2012-10-09
> **chili555 said:**
> Please see here: [http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/](http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/)

Please post back if you need assistance applying the patch.

Thank you for the link, it works now, with the full signal !!
However, I have to do that in the terminal at each boot :
```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo modprobe lib80211
[sudo] password for baptiste: 
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo modprobe cfg80211
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo rfkill unblock all
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ sudo rmmod brcmsmac
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ cd drivers/hybrid_wl/
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~/drivers/hybrid_wl$ sudo insmod wl.ko

```

Do you know what I can do ?

Thank you again !!

---

### Post by chili555 on 2012-10-09
Please try just this and tell me the result. We'll fix it easily:```
sudo modprobe -r brcmsmac
sudo modprobe wl
```

---

### Post by bblanchon on 2012-10-10
> **chili555 said:**
> Please try just this and tell me the result. We'll fix it easily:```
sudo modprobe -r brcmsmac
sudo modprobe wl
```

I've just tried this after rebooting, but nothing happens. It just shows me "Network disconnected"

---

### Post by chili555 on 2012-10-10
Please do:```
sudo gedit /etc/modules
```Where brcmsmac appears, remove it and replace it with wl. Proofread, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Is there any mention of wl in there? If so, remove it. Add:```
blacklist brcmsmac
```Proofread, save and close gedit.

Reboot. Now check to see which module is and isn't loaded:```
lsmod | grep -e brcmsmac -e wl
```Hopefully wl and its dependent lib80211 only are loaded. Check rfkill:```
rfkill list all
```Any improvement?

---

### Post by bblanchon on 2012-10-10
Thank you again for your help, but nothing changed.

```
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ lsmod | grep -e brcmsmac -e wl
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
baptiste@baptiste-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

---

### Post by chili555 on 2012-10-10
We're close! Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
```Is it working?

---

### Post by bblanchon on 2012-10-10
> **chili555 said:**
> We're close! Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
```Is it working?

I've tried this, but nothing changes...

---

### Post by bblanchon on 2012-10-14
Does anyone know what I can try now ?

Thank you !

---

### Post by bblanchon on 2012-10-23
Nobody can help me please ?

---

### Post by chili555 on 2012-10-23
> **bblanchon said:**
> Nobody can help me please ?Please try:```
sudo modprobe -r wl
sudo modprobe -r lib80211
sudo rfkill unblock all
sudo modprobe wl
rfkill list all
```If this doesn't work, I suggest you file a bug report against *hp-wmi*: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

*hp-wmi* is supposed to recognize key presses and translate them to action, such as Fn+F2,or similar, means 'please turn on the wireless.'

If it does work, we can write a few lines in rc.local to do so on boot.

---

### Post by bblanchon on 2012-10-23
I'm really sorry, but when I tried to reboot my computer to use Ubuntu, the WiFi was working. So, I will notice the topic as Solved !

Thank you chili555 for your help !

---

### Post by rodolphoarruda on 2013-06-20
Hi all,

I have managed to solve the issue on my Lenovo laptop with BCM4313 runing on Ubuntu 12.04

See it here: [http://ubuntuforums.org/showthread.php?t=2111181&p=12699508#post12699508](http://ubuntuforums.org/showthread.php?t=2111181&p=12699508#post12699508)

RA

---

### Post by Gneykan_ on 2014-02-01
Hi,
 I experienced the same problem and I tried the instructions you gave and it worked for me but when i restart the computer the problem comes back and I have to fix again.Is there any solution to fix that problem?

---

### Post by chili555 on 2014-02-01
> **Gneykan_ said:**
> Hi,
 I experienced the same problem and I tried the instructions you gave and it worked for me but when i restart the computer the problem comes back and I have to fix again.Is there any solution to fix that problem?
There was a lot of ground covered in this long, old thread. Which instructions did you use, exactly?

---

### Post by Gneykan_ on 2014-02-03
lspci -nn | grep 0280
rfkill list all
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
sudo modprobe -r wl
sudo modprobe brcmsmac
sudo rfkill unblock all
rfkill list all

---

### Post by Gneykan_ on 2014-02-03
i am new to ubuntu and i tried all the codes mentioned before in order.

---

### Post by chili555 on 2014-02-03
> **Gneykan_ said:**
> i am new to ubuntu and i tried all the codes mentioned before in order.We need to start with the *results* of these commands:```

lspci -nn | grep 0280
rfkill list all
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
sudo modprobe -r wl
sudo modprobe brcmsmac
sudo rfkill unblock all
rfkill list all 

```Some will have no result and some will tell us valuable information. Please tell us.

---

### Post by Gneykan_ on 2014-02-03
guney@guney-AOD270:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
guney@guney-AOD270:~$ rfkill list-all
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-2ubuntu1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
guney@guney-AOD270:~$ sudo modprobe -r hp-wmi
[sudo] password for guney: 
guney@guney-AOD270:~$ sudo rfkill unblock all
guney@guney-AOD270:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
guney@guney-AOD270:~$ sudo modprobe -r wl 
FATAL: Module wl not found.
guney@guney-AOD270:~$ sudo modprobe brcmsmac
guney@guney-AOD270:~$ sudo rfkill unblock all
guney@guney-AOD270:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
guney@guney-AOD270:~$

---

### Post by chili555 on 2014-02-03
Did your wireless come to life? ```
iwconfig
```Are there any clues here?```
dmesg | grep -e wlan -e brcm
```

---

