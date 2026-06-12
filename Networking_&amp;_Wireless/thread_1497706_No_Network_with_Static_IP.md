---
title: "No Network with Static IP"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by The_Oblivium on 2010-05-30
Hi! I've been "experiencing" Ubuntu for about 4 months and all went well with Ubuntu 9 but now all of a sudden i formatted my pc installed windows 7 and run a live cd of ubuntu 10.4. When i configured, using the network manager, my lan connection (static ip, address 192.168.1.3; netmask 255.255.255.0; gateway 192.168.1.1) worked well but after a reboot of the live cd my network wont work at all in ubuntu. I tried ubuntu 9 again, linux mint 9 ubuntu 10, xubuntu10, and kubuntu10... none worked ... i input the static ip date onto the network manager and connect to that ... and nothing ... my internet connection wont work ... please help me !!! I am using a normal ethernet cable and on windows 7 my connection works fine with the same ip ...

---

### Post by puppywhacker on 2010-05-31
It's easier if you have a ubuntu installed on a harddisk, since now you will have to configure the network after each start. Except for the ip-addresses you also have to configure DNS and it is not completely clear to me if you can ping the gateway

"ping 192.168.1.1"

---

### Post by lisati on 2010-05-31
My preference is to set static IPs in my router. That way there's less chance of an IP address conflict and other such problems.

---

### Post by Iowan on 2010-05-31
I presume you've checked **ifconfig -a** to verify the IP address?

---

### Post by The_Oblivium on 2010-05-31
> **Iowan said:**
> I presume you've checked **ifconfig -a** to verify the IP address?

yes i have done that and it is as i wanted and as i have on windows 7 but still no network ... tried to install to hardrive and it still has the same issue ... when i do ping 192.168.1.1 i returns me the host unreachable text .... any ideas?

EDIT: i've removed the network manager and configured eth0 with the terminal by sudo gedit/etc/network/interfaces

---

### Post by Iowan on 2010-05-31
What are the results of **route -n**? I suspect it'll show the gateway as 192.168.1.1 - but worth checking...

---

### Post by The_Oblivium on 2010-06-01
> **Iowan said:**
> What are the results of **route -n**? I suspect it'll show the gateway as 192.168.1.1 - but worth checking...

new info : if i unplug my internal hdd and boot any linux distro from a live usb i then can configure my static ip address and connect to the network and internet... if i ever enter windows 7 i have to redo the same process again in order for me to have linux with internet over a static ip.. any ideas what can it be?

---

### Post by dineshs on 2010-06-02
I am not an expert but hope chili555s posts like these may help
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)
> If Network Manager is running, it is unlikely you will get manual configuration working. I have tried and failed many times. If you want to connect manually, I suggest you remove Network Manager

---

### Post by The_Oblivium on 2010-06-02
> **dineshs said:**
> I am not an expert but hope chili555s posts like these may help
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

sorry but that was a try i did 
i uninstalled network manager and created mannualy thenetwork but still nothing

---

### Post by Iowan on 2010-06-02
Not intended as sarcasm - what kind of "nothing" do you get? 
After manual network configuration, I presume you restarted/rebooted. Did **ifconfig -a** show an IP address? did **route -n** show router as gateway?

---

### Post by The_Oblivium on 2010-06-06
yes both gave me the correct values i gave them ... its weird cause if i unplug internal drives and then run a ubuntu live cd, network configured exactly the same as with internal drives plugged in, i can connect ... :S

---

