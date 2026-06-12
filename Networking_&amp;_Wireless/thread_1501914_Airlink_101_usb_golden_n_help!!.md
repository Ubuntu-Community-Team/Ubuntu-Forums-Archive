---
title: "Airlink 101 usb golden n help!!"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by KegHead on 2010-06-04
Hi!

I just picked up an el cheapo airlink 101 golden n mini usb adaptor.

It isn't recognized in 10.04.

Does anyone know what driver or deb file I should download?

Thanks!

KegHead

---

### Post by chili555 on 2010-06-04
Please plug in the device and open a terminal and post:```
lsusb
dmesg | grep 819
```Thanks.

---

### Post by KegHead on 2010-06-04
jim@jim-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jim@jim-laptop:~$ dmesg | grep 819

---

### Post by chili555 on 2010-06-04
It is supposed to work with the driver r8192s_usb, but there is sometimes a firmware problem. Please do:```
sudo modprobe r8192s_usb
iwconfig
dmesg | grep -i firmware
```

---

### Post by chili555 on 2010-06-04
Just in case we need it, here is a firmware file. dmesg will tell us if that's the problem or not.

---

### Post by KegHead on 2010-06-05
jim@jim-laptop:~$ sudo modprobe r8192s_usb
[sudo] password for jim: 
jim@jim-laptop:~$ sudo modprobe r8192s_usb
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:236  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

jim@jim-laptop:~$ dmesg | grep -i firmware
jim@jim-laptop:~$

---

### Post by chili555 on 2010-06-05
It looks like a wireless interface was created, although I am mystified that it's eth1. Now, let's again look at:```
dmesg | grep -e eth -e 819
```Thanks.

---

### Post by KegHead on 2010-06-07
jim@jim-laptop:~$ dmesg | grep -e eth -e 819
[    0.408199] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.288306] eth0: RTL8102e at 0xf8056000, 00:21:70:d4:48:74, XID 04a00000 IRQ 27
[   13.988307] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   14.728384] r8169: eth0: link up
[   14.728436] r8169: eth0: link up
[   25.392035] eth0: no IPv6 routers present
[   25.672042] eth1: no IPv6 routers present
jim@jim-laptop:~$

---

### Post by chili555 on 2010-06-07
Please insert the device and do:```
sudo su
echo r8192s_usb >> /etc/modules
reboot
```When the computer comes back up, please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file dmesg.zip in your home directory. Please post it as an attachment to your reply.

Thanks.

---

### Post by KegHead on 2010-06-08
Hi!

Here you go!

KegHead

---

### Post by chili555 on 2010-06-08
> usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
rtl819xU:request firmware fail!Please go back to the firmware I attached in a previous post. Download it to your desktop. Right click and select 'Extract Here.' Now let's move it to the correct place.```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Now let's reload the module and see if we have better behavior:```
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
iwconfig
```

---

### Post by KegHead on 2010-06-08
Hi!


jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan1     802.11b/g  link  ESSID:"wicklund"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:E9:1B:DC:3C   
          Bit Rate=54 Mb/s   

Looks like it's working!

Thanks!

KegHead

          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-53 dBm  Noise level=-112 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by KegHead on 2010-06-08
Hi!

Do you know if there are any problems using g and n wifi next to each other. I'm going to use two wifi connections.

KegHead

BTW-Thanks again!

---

### Post by chili555 on 2010-06-08
I am not aware of any issues. Using two wireless connections will be tricky. I have never done it, but it sounds challenging!

---

### Post by ebohatch on 2010-06-25
> **chili555 said:**
> Please go back to the firmware I attached in a previous post. Download it to your desktop. Right click and select 'Extract Here.' Now let's move it to the correct place.```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Now let's reload the module and see if we have better behavior:```
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
iwconfig
```

I am having the same problem, followed all of your directions. When I did dmesg, I did not get firmware missing message.
 I ran rmmod -f r8192s_usb  and it said "No such file or directory". Then I did modprobe r8192s_sub  and it states "FATAL: Module r8192s_sub not found."   ???

Also now if I have the wireless USB plugged in I cannot get to the internet, as soon as I unplug it I get access again. ???

---

### Post by KegHead on 2010-06-25
Hi!

Chili555 can help you!

KegHead

---

### Post by KegHead on 2010-11-26
Hi!

Since fixing my problem, I've added a trendnet n.

I'm able to use the drivers on the trendnet and d link (b&g).

I just select the router I want and wail away!

The difference in connection between the two is 50 vs 144.

I use the trendnet almost all of the time.

Thanks again chili555.

KegHead

---

### Post by pigbuntu on 2011-04-28
Thank you! I registered because I had similar issues and this worked for me. Thanks!

---

### Post by janetra on 2011-06-16
Thank you! Worked perfectly.

---

### Post by deadset22 on 2011-07-28
I just want to say thanks. I have been working on the doing the same thing and the info here really helped. Thanks again

---

