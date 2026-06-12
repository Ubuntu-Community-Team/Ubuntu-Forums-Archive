---
title: "Can't share printer from Ubuntu 8.04 to Windows XP"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by kol-tai on 2009-03-09
Just a warning up front, I'm a complete newbie at Ubuntu so please respond with that in mind.  Thanks!

In consulting the community document "https://help.ubuntu.com/community/NetworkPrintingFromWinXP"and after typing the printer URL in the printer wizard in Windows XP I get the message that Windows cannot find the printer.  This is where I'm stuck.

I've also looked at several threads but think I'm just getting more confused.

Would someone be kind enough to walk me through it?

Much appreciated!

Kol-Tai

---

### Post by Paul41 on 2009-03-09
Are you connecting with the ip address? Is your computer's ip assigned through DHCP from your router. If that is the case it could by that you now have a different ip address on the Ubuntu computer.

---

### Post by kol-tai on 2009-03-09
Yes, I'm connected through a router with DHCP so both the Ubuntu machine and Windows machine both should have separate IP's.

I don't know where to find the IP address on the Ubuntu machine though or how to check connectivity.

---

### Post by kol-tai on 2009-03-09
Oh, and I used the host name not IP address in my URL.

---

### Post by Paul41 on 2009-03-09
To get your ip address in Ubuntu type the following in the terminal:

```
ifconfig
```

Once you get the ip address try to ping it from Windows to make sure it is seeing the computer.  From the command prompt in windows type the following (where ipaddress is the ip of your Ubuntu machine):

```
ping ipaddress
```

Did you set up a hostname?  I don't think using your user name will work (but I could be wrong).

---

### Post by kol-tai on 2009-03-09
Got it!  I used the IP address instead of the host name and I'm in business.

Thanks for your help!

---

### Post by Paul41 on 2009-03-09
Glad you got going. Keep in mind that with your ip being set by DHCP when your Ubuntu computer gets a new ip you will have to re-point your connection.  You may want to looking into giving the Ubuntu computer a static ip so it stays the same all the time.

---

### Post by grummpy on 2009-03-14
Hi,I hope I`m doing this right! I have a question reguarding finding ifconfig in linux 804 since I`m new at this,you mentioned typing in terminal,code:ifconfig.Since I have never used terminal how would I go about this? Like I said I`m new with linux so please bear with me. Thank you.

---

### Post by Paul41 on 2009-03-15
To get to the terminal, in the menus to go Applications->Accessories->Terminal. you will get a screen that is like the command prompt in Windows. From there type ifconfig and press Enter and it will give you a bunch of information back.  In there you will have some information that looks something like this: inet addr:192.168.1.102 . That is you ip address.

---

### Post by navigatoru on 2009-04-21
hi there, 

I have a similar problem with printer sharing on ubuntu. 
I installed Ubuntu Desktop edition on a virtual machine with the IP (192.168.233.132). I installed a printer (10.11.5.31) on Ubuntu. Till now everything is wonderful. 
Now, I want to share this printer on Ubuntu, because I want to print from the host machine (Windows XP - 10.238.24.99). The connectivity between all machines is ensured. 
From Ubuntu I can print on printer, from Windows I can print on printer, but when I want to print on printer (shared on Ubuntu), I can't. 
I shared the printer in server from System>Administration>Printing without succes.

Any ideea ?

Thanks.

---

### Post by CyberMick on 2009-04-26
Similar issue here.
Separate ubuntu 9.04(Desktop) machine separate windows xp machine.
I can print to printer fine if I plug USB cable in directly from printer from either machine.
I cannot network print to cups "shared"(Shared from ubuntu) printer from windows xp machine on same network.
I have used the administration gui (System -> Administration -> Printing) I right click on the printer I have installed and Properties. Policies State is Enabled Accepting Jobs is enabled and Shared is enabled.

This should work right?

---

### Post by CyberMick on 2009-05-01
Anyone?

---

### Post by Gerard08 on 2009-05-04
Koi-tai's link to > [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) worked for my connection which is a laptop running XP connected to a NetGear Router.  I did have to replace the desktop name with the IP address listed in Wicd manager into the add printer wizard. It went smoothly from there. My printer is a HP 1018 that is partially supported and uses HP drivers found here: > [https://launchpad.net/hplip](https://launchpad.net/hplip) . I turned to Wicd as I was having trouble creating a static IP in 8.10.

---

