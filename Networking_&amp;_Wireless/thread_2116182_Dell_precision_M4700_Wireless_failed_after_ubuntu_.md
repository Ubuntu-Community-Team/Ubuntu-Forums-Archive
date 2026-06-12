---
title: "Dell precision M4700: Wireless failed after ubuntu 12.04 updating"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by rbaena on 2013-02-15
Hello everybody,

 hope somebody can help.
 I am working on a Dell precision M4700 laptop with Ubuntu 12.04 and KDE desktop.
 After a "suggested" system updating, my wireless connection stops working. KNetWorkManager sees the wireless and tries to connect to it but, after a while, a small windows pops up and asks for a password. If I introduce the wireless one I have it tries again but nothing happens. That window appears again and again asking for a password. 
 Such windows has a key as a symbol on the top left corner, the same key appears over the KNetWorkManager symbol which is on the bottom panel. The window has the title "Secretas de [wireless name] - Service for KDE-" (in Spanish sorry :-)).

 I guess some security measurement has been activated after the updating but I do not know how to deactivate it.

 I am sure the password is correct and the router is working fine, indeed, I am using another laptop to publish this thread using the same wireless connection.

 I also post some useful information:

kernel: 3.2.0-37-generic
desktop KDE
ubuntu 12.04.2 LTS

iwconfig:

   lo: no wireless extension
   eth1: IEEE 802.11abg ESSID off/any
             Mode: managed access point: not-associated
             Retry long limit:7 RTS thr off Fragment thr off
             power management: off
   eth0: no wireless extension

Thanks for your support!

---

### Post by chili555 on 2013-02-15
Please see your question at askubuntu.com.

---

### Post by Merrattic on 2013-02-15
Which is here: [http://askubuntu.com/questions/256373/wireless-failed-after-ubuntu-12-04-updating](http://askubuntu.com/questions/256373/wireless-failed-after-ubuntu-12-04-updating)

Try turning the hardware wireless switch off if you have one? On my Dell Precision M6500 I have to have it _on_ for W7 but _off_ for Xubuntu 12.04.2.

---

### Post by rbaena on 2013-02-15
Thanks for your answer. 
I do not see any hardware switch to set off the wireless device. Where is it?

---

### Post by chili555 on 2013-02-15
Please see #13 attached.

---

### Post by rbaena on 2013-02-15
Thanks, I tried switching off the button  #13 but it does not work either.

---

### Post by chili555 on 2013-02-15
Please move the switch to ON and open a terminal and run and post:```
rfkill list all
```Move the switch the other way and run and post again:```
rfkill list all
```

---

### Post by rbaena on 2013-02-16
Hi,  I tried the following: 

hardware switch on
rfkill list all

0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

Then, hardware switch off
rfkill list all
0: dell-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

Finally I set the switch on again.
The wireless is still not working. It sees the home LAN and tries to connect again and again but it does not.

---

### Post by chili555 on 2013-02-16
> hardware switch on
rfkill list all

0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
At this point, we know the switch is not stopping your wireless. Let's troubleshoot the wireless device itself. Please run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by rbaena on 2013-02-16
Here you are ip a and lpsci -nn | grep 0280

rbaena@fajnmp2:~/DataPart2/Otros$ lspci -nn | grep 0280

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

rbaena@fajnmp2:~/DataPart2/Otros$ ip a

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether d4:be:d9:82:0a:99 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether a4:17:31:4b:52:6e brd ff:ff:ff:ff:ff:ff                                                                                                                                                                                                                         
    inet6 fe80::a617:31ff:fe4b:526e/64 scope link                                                                                                                                                                                                                              
       valid_lft forever preferred_lft forever

---

### Post by chili555 on 2013-02-17
May we see:```
sudo dpkg -s bcmwl-kernel-source | head -n5
lsmod | grep -e b43 -e brcm -e wl
dmesg | grep -e b43 -e wl
```

---

### Post by rbaena on 2013-02-17
Hi, here you are:

sudo dpkg -s bcmwl-kernel-source | head -n5
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4174

lsmod | grep -e b43 -e brcm -e wl
wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

dmesg | grep -e b43 -e wl | more
[170049.077022] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170049.077026] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170049.077174] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170049.077179] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170051.073213] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170051.073216] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170053.068357] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170053.068365] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170055.063480] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170055.063483] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170055.063531] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170055.063533] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170057.058588] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170057.058595] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170059.053488] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170059.053491] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170061.050182] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170061.050190] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170061.050307] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170061.050311] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170063.043156] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170063.043159] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170065.037855] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170065.037858] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170067.034091] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170067.034094] ERROR @wl_cfg80211_get_station : Could not get rssi (-1) 
etc etc until 2 or 3 pages more

---

### Post by chili555 on 2013-02-17
> I also post some useful information:

kernel: 3.2.0-37-generic
desktop KDE
ubuntu 12.04.2 LTS
Conratulations! You are the proud owner of an official bug! You lucky guy/gal/cyborg! [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281)> Since update to 3.2.0-37 wireless is broken.A patch is referred to and, frankly, I am not at all sure how to apply it.

We could try building bcmwl-kernel-source from Broadcom's own package and amend it slightly here: [http://forums.fedoraforum.org/archive/index.php/t-280821.html](http://forums.fedoraforum.org/archive/index.php/t-280821.html)

You could also boot into a previous version, 3.2.0-3[COLOR="Red"]6[/COLOR]-generic, for example, remove the linux-image for -37 and wait until a fix is implemented. 

I will be glad to assist you in any way I can. What do you prefer?

---

### Post by rbaena on 2013-02-17
Aaaah! Yes, I feel happy and proud of myself!! :confused:](*,)

I would be even more happy if I had not updated the kernel. Anyway, yes, I think the best option for me now is to come back to version 3.2.0-3[COLOR=Red]6[/COLOR]-generic and wait until this is fix.

Can you tell me how to go on now? I hope it is enough an apt-get remove.

Should I need to be connected to internet? In that case I will have to wait until tomorrow to have a cable at work.

Thanks for your help =D>

---

### Post by chili555 on 2013-02-17
> Can you tell me how to go on now?Yes. Reboot and in the first few moments of the boot process, press and hold Shift. The GRUB menu will appear. It may take a quick hand and a couple of tries. Please see attached.

Select the -36 version, or any version older than the faulty -37, with the arrow keys. Boot into it. Then open Synaptic Package Manager and look for linux-image-3.2.0-37-generic. Right-click it and select 'Mark for Complete Removal.' Do the same for linux-image-generic. Click 'Apply' and you should be all set.

When Update Manager pops up a few days from now and wants to install updates, no linux-image should be offered and won't until you re-install linux-image-generic, the 'always update' package. However, I'd check carefully and decline the updates if linux-image is included. If so, post back and we'll sort it out.

You might bookmark the bug I linked and check back to see when a fix is released.

---

### Post by rbaena on 2013-02-17
OK thanks. 

Just to be sure I am not going to do anything wrong. Once I boot with -36 version I have to remove the following two packages:

linux-image-3.2.0-37-generic
linux-image-generic

In future, can I still do apt-get update/upgrade on my own? 

Cheers

---

### Post by chili555 on 2013-02-17
> **rbaena said:**
> OK thanks. 

Just to be sure I am not going to do anything wrong. Once I boot with -36 version I have to remove the following two packages:

linux-image-3.2.0-37-generic
linux-image-generic

In future, can I still do apt-get update/upgrade on my own? 

CheersYes, exactly. Watch carefully for updates to linux-image and decline if there should be any, although the removal of linux-image-generic should prevent it.

---

### Post by rbaena on 2013-02-18
Hi, before proceeding with the removal of these two packages I have two more doubts.

 A) I have booted with the previous linux version, i.e. 3.2.0-35. The wireless connection is not working either. I had expected to be able to make the connection with this kernel.

B) If I try to mark any of these two packages, Synaptic also asks for the removal of the package linux-generic. Is this really safe? I mean, will the system go back to the previous version automatically?

Best

---

### Post by chili555 on 2013-02-18
I thought the trouble started on upgrade and that the wireless was working as expected prior to 3.2.0-37. No? Before we proceed, let's get the wireless working reliably. Is bcmwl-kernel-source installed?```
sudo dpkg -s bcmwl-kernel-source | head -n5
```Is the message the same as here?```
dmesg | grep wl
```> [170049.077022] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170049.077026] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[170049.077174] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[170049.077179] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)> Synaptic also asks for the removal of the package linux-generic. Is this really safe?I am sure it is. linux-generic is not installed on my system at all. Is that ***all*** that is proposed to remove?

---

### Post by rbaena on 2013-02-19
>I thought the trouble started on upgrade and that the wireless was working as >expected prior to 3.2.0-37. No?

Indeed it was!

From the previous version I get

rbaena@fajnmp2:~$ uname -a
Linux fajnmp2 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

rbaena@fajnmp2:~$ sudo dpkg -s bcmwl-kernel-source | head -n5
[sudo] password for rbaena: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4174

rbaena@fajnmp2:~$ dmesg | grep wl
[    8.980341] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.004502] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.004517] wl 0000:03:00.0: setting latency timer to 64
[    9.035433] INFO @wl_cfg80211_attach : Registered CFG80211 phy

Now I try to connect to the wireless and...

rbaena@fajnmp2:~$ dmesg | grep wl
[    8.980341] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.004502] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.004517] wl 0000:03:00.0: setting latency timer to 64
[    9.035433] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  249.043394] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  249.043397] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  280.996639] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  280.996647] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  280.996779] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  280.996784] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  282.989797] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  282.989805] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  284.986043] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  284.986051] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  286.981931] ERROR @wl_cfg80211_get_station : Could not get rate (-1)

etc, etc...

The same window as I mentioned at the beginning of this thread (the one with a "key" as a symbol) has appeared asking for a password.

Cheers

---

### Post by chili555 on 2013-02-19
Would you please get me a full diagnostic workup? Reboot so we start with a clean slate. With a working wired ethernet connection, do:```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time. The Mac address, WPA key and WEP keys are removed for your security. Reply back, click on the paper clip and attach the netinfo.txt file.

Thanks.

---

### Post by rbaena on 2013-02-19
Ok, I will do it on Thursday from work. At home I do not have the possibility to do a wire connection.

---

### Post by rbaena on 2013-02-21
Hi, here you are (attach) the output for wireless_script. Just in case I executed for both -35 and -37 kernels.

---

### Post by chemistrydiva on 2013-02-21
I'm having similar problems but with the 3.2.0.38 kernel, which I just updated last night. However, when I try to load a previous kernel there are no other options (and so far I can't find the equivalent of menu.lst in grub2 to be able to add more boot options - I am looking in /etc/default but so far no luck). I've tried quite a few fixes after looking through quite a few threads on here but I think this one might be beyond me. Is it okay to ask for help in here or should I be posting in a different thread?

---

### Post by chili555 on 2013-02-21
> **chemistrydiva said:**
> I'm having similar problems but with the 3.2.0.38 kernel, which I just updated last night. However, when I try to load a previous kernel there are no other options (and so far I can't find the equivalent of menu.lst in grub2 to be able to add more boot options - I am looking in /etc/default but so far no luck). I've tried quite a few fixes after looking through quite a few threads on here but I think this one might be beyond me. Is it okay to ask for help in here or should I be posting in a different thread?I suggest your own new thread since your card and driver details, etc. are likely not the same.

---

### Post by rbaena on 2013-02-25
Hi, I attached the txt file reports last Thursday as you asked. I am not sure if you got them. Cheers.

---

### Post by chili555 on 2013-02-26
> **rbaena said:**
> Hi, I attached the txt file reports last Thursday as you asked. I am not sure if you got them. Cheers.What explains this? How do you have two IP addresses when wireless is disconnected?????> - Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  [COLOR="Red"]IPv4 Settings:
    Address:         192.168.112.175[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.112.1

    [COLOR="Red"]Address:         161.116.78.36[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         161.116.78.254

    DNS:             153.96.19.83Have you entered any settings in Network Manager manually?

---

### Post by rbaena on 2013-02-26
No idea. Maybe it was an internet security measure at work. An external IP to give access to an internal LAN. Just guessing...  In any case I was connected with a cable. 

I only touched the password of the wireless in KnetWorkManager. Of course, I removed it several times to let KnetWorkManager to detect it again.

---

### Post by marioman619 on 2013-06-10
Hi, I had the same issue before but once I installed the latest version the problem seemed to have gone away. Otherwise I think you can fix it by downgrading the kernel to the one with an Ubuntu version that worked.

---

