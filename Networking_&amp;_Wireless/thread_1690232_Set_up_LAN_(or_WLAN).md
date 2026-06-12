---
title: "Set up LAN (or WLAN)"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by sid.mallya on 2011-02-18
Hey guys, I am an absolute retard when it comes to networking, so please be nice ! :P
 
I have an ADSL connection at home. I am using ethernet to access the ADSL connection on the desktop which runs Ubuntu. The IP address of the desktop is 192.168.2.2
 
Using a Wi-Fi, I am sharing this ADSL with my laptop, which runs Windows. The IP address of laptop is 192.168.2.3/4 (depends)
 
I cannot ping the laptop or desktop using these IP addresses. I have used ipconfig and ifconfig to get the local IP addresses. 
 
How do I set up a LAN between these computers and how do I share files ? I may not need to set up Samba as I am planning to install Mint on a small partition of the laptop.

---

### Post by Jahid65 on 2011-02-18
[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

 to change windows workgroup see [this link]("http://www.liberiangeek.net/2010/05/how-to-enable-file-sharing-in-windows-vista-7-and-allow-linux-systems/")
to install & configure samba in ubuntu see [this link]("http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/")

for ubuntu-mint (linux-linux) file sharing you need openssh or ssh (not sure) It is Places > Connect to server (SSH)

---

### Post by rvchari on 2011-02-18
> **sid.mallya said:**
> Hey guys, I am an absolute retard when it comes to networking, so please be nice ! :P
 
I have an ADSL connection at home. I am using ethernet to access the ADSL connection on the desktop which runs Ubuntu. The IP address of the desktop is 192.168.2.2
 
Using a Wi-Fi, I am sharing this ADSL with my laptop, which runs Windows. The IP address of laptop is 192.168.2.3/4 (depends)
 
I cannot ping the laptop or desktop using these IP addresses. I have used ipconfig and ifconfig to get the local IP addresses. 
 
How do I set up a LAN between these computers and how do I share files ? I may not need to set up Samba as I am planning to install Mint on a small partition of the laptop.

when you are using the router to access the internet, i doubt if that router can be used to make a lan between your computers.

you may need a seperate switch to interconnect between the computers. (one to one direct cabling may not work)

allocate the main computer IP 192.168.1.50 and let the default gateway be 192.168.1.1 / 3 / 5 however u configure. all other computers that are linked through switch will be 192.168.1.51 / 52 etc....

to do this, you will need 2 lan cards on your main computer that will act as your server. (one for lan to switch and other for internet connection cable to switch. you can connect the adsl modem to the switch) this way you can configure which user can have access to net and who cannot....

i am not a hardware guy but this is how i have done it at my side.... hope my info will be of some help to you

---

