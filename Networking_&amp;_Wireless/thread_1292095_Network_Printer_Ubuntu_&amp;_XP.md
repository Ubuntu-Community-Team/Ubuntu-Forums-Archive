---
title: "Network Printer Ubuntu &amp; XP"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2009-10-15
I am the tech support person for our local library and recently installed Ubuntu Jaunty on our 6 public PCs. One has a HP LaserJet 2100M installed and connected to it. That machine and the other Ubuntus print OK but the XP and Apple I can't get to print. I have tried several procedures with no luck.We also are having print delays of several minutes from the Ubuntu that has the printer attached when we try to print anything except text. I am not a professional tech person but am fairly proficient at XP. It was my idea to install Ubuntu on the public machines, but if I am to be allowed to keep the Ubuntus I have to get the 3 librarians XP machines to print also. I am at the library today from now 1pm EST USA to 7pm if anyone could call and help me get this working. I can call you right back so you don't pay for a long distance call. Thank you hopefully someone. The number here is 1-231-882-4037.

---

### Post by chili555 on 2009-10-15
Please check here: [http://ubuntuforums.org/showpost.php?p=2124612&postcount=2](http://ubuntuforums.org/showpost.php?p=2124612&postcount=2)

It has been a while since I allowed XP to run here, so I can't swear this works, still, but it should.

---

### Post by cmcanulty on 2009-10-15
PS we have a dynamic IP address as a static one costs too much extra.

---

### Post by cmcanulty on 2009-10-15
I am afraid I don't know how to assign a static ip address as we have a dynamic one here at the library. A static one costs a lot more.

---

### Post by chili555 on 2009-10-15
> **cmcanulty said:**
> I am afraid I don't know how to assign a static ip address as we have a dynamic one here at the library. A static one costs a lot more.You have a dynamic address from your internet service provider. That's fine. However, behind your router or other access point, every computer has it's own IP address. The easiest way (not the only way, nor, perhaps the most elegant way) to accomplish this is for the computer with the printer attached to have a static address on the router, so that all the other computers can find it, or more precisely, the printer.

Please check PMs.

---

### Post by chili555 on 2009-10-16
To create a static IP address on the machine with the printer, determine the DHCP range of the switch and assign an address outside it, for example, 192.168.2.170. Do:```
sudo gedit /etc/network/interfaces
```Amend it to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.170
netmask 255.255.255.0
gateway 192.168.2.1
```Proofread carefully, save and close gedit. Now restart networking:```
sudo /etc/init.d/networking restart
ifconfig
```Is your address now x.170? Let's test it:```
ping -c3 www.google.com
```If you got ping returns, you are all set!

---

### Post by cmcanulty on 2009-10-16
Thanks much chili 555. Today I got called by library and Ubuntu printer keeps uninstalling and have to reboot or no machine prints, after reboot all OK,  and the mice and trackpads are stopping working. Guess I just lost microsoft headaches forUbuntu ones and I have no clue what could be causing these problems.

---

### Post by chili555 on 2009-10-17
> **cmcanulty said:**
> Thanks much chili 555. Today I got called by library and Ubuntu printer keeps uninstalling and have to reboot or no machine prints, after reboot all OK,  and the mice and trackpads are stopping working. Guess I just lost microsoft headaches forUbuntu ones and I have no clue what could be causing these problems.Not necessarily. It's always a possibility that the cause of the error is overheating or some other hardware issue. You can sometimes isolate problems by looking at *syslog* or *messages*, thus:```
sudo less /var/log/syslog
sudo less /var/log/messages
```The *less* command will allow you to scroll back and forth with the arrow keys. You can look for errors or warnings with:```
sudo cat /var/log/syslog | grep -i warn
sudo cat /var/log/messages | grep -i warn
```and then the same for *error*. You might have to post over in Greneral Help to get help for those problems.

---

