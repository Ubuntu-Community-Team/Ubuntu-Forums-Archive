---
title: "Help in Setting up wireless network."
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by samaybhavsar on 2009-01-09
Hi!

Myself Samay and this is my first post in this forum. I just installed Ubuntu 8.04 in my laptop but dont know how to setup the internet connection. I have ADSL internet connetion with a wi-fi router. I have Windows Vista where the wi-fi internet is working fine. But I dont know how to set up in Ubuntu.

My laptop is HP Pavilion DV4 1131tx. Can anyone help me out with this ??? I am also facing some resolution problem. But will do it later.

Thanks
Samay

---

### Post by samaybhavsar on 2009-01-09
so many views and no reply ?

---

### Post by aeronotix on 2009-01-09
First of all make sure all the drivers for your wireless card are there, you should be able to find this in System->Administration->Hardware Drivers. 

If none are installed google your adapter/pmcia-card etc and find the drivers.

Go from there and post back.

---

### Post by adamitj on 2009-01-09
> **aeronotix said:**
> First of all make sure all the drivers for your wireless card are there, you should be able to find this in System->Administration->Hardware Drivers. 

If none are installed google your adapter/pmcia-card etc and find the drivers.

Go from there and post back.

Indeed. First of all you need to check out if your wireless card drivers are installed and fully functional before try to setup your network. If not, you might got help here for this.

---

### Post by superprash2003 on 2009-01-09
if you still face problems.. post output of
1)lshw -C network
2)iwconfig
3)iwlist scanning
4)ifconfig

 from the ubuntu terminal(Applications->Accessories->Terminal)

---

### Post by samaybhavsar on 2009-01-12
I updated my version of Ubunutu from 8.04 to 8.10 and things are working now. Thanks for all your help.

---

