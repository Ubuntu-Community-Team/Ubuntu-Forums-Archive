---
title: "VMware Workstation -7 &amp; Ubutu 9.10"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Josh1216 on 2010-01-15
Hi,

I have  a IBM T61 notebook where-in I have installed Ubuntu on VMware workstation7. The host operating system is Win XP SP3. My problem is that I cannot connect to  wireless network independently from Ubuntu 

So if I disconnect wireless  connection from host OS ( Win XP) and try to connect from Ubuntu I cannot. Infact I see no network manager icon on the panel apart from wired network connection icon.

Attached is the screenshot of the panel for reference. 

I'm able to connect to internet from Ubuntu when I connect back to my access point from host OS. I have also noticed that Ubuntu gets an unique ip address  from my router (as I have installed Ubuntu  in Bridged mode  on vmware). 

What I would like,  is to see the available WIFI  around  and able to connect to my access point directly from Ubuntu.

Any help would be appreciated.

Thanks

---

### Post by changingstate on 2010-01-15
A copy of ubuntu in vmware can't control hardware windows is using. If you want to connect ubuntu separately, I recommend attaching a USB NIC and using the options in vmware to pass control of the device straight into the virtual machine.

---

