---
title: "can see wireless network, but can't connect"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by super newbie on 2011-11-24
Hi Everyone,

i purchased a Netgear 300N wireless network adaptor and i think its set-up correctly because the LED on the adapter itself is flashing and when i  look at my network connections i see my wireless network.  the problem i'm having is getting my pc to connect to the wireless network.  i'm currently connected via ethernet cable, but when i unplug the cable and reboot, i can see my wireless network but it won't connect.  using ubuntu 11.10 and the "connect automatically" option is checked
thanks in advance

---

### Post by chili555 on 2011-11-28
Isn't 300N the model of your wireless router? What is the wireless device in your computer? Please open a terminal and run and post:```
lsusb
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Rosignol on 2011-11-28
just a quick thought, many computers have a physical switch to enable the wireless connection have you checked this?
hope it's not too obvious

---

### Post by Bucky Ball on 2011-11-28
> **Rosignol said:**
> just a quick thought, many computers have a physical switch to enable the wireless connection have you checked this?
hope it's not too obvious

+1. Wise to start at the beginning ... ;)

Post as chilli says. Have you gotten all updates while online with the cable and perhaps checked System>Additional Drivers (or whatever it's now called in more current releases)?

---

### Post by super newbie on 2011-11-28
@chili555
here is the output of lsusb
mike@mike-MS-7592:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 004 Device 002: ID 1bcf:05ce Sunplus Innovation Technology Inc. 
mike@mike-MS-7592:~$ lspci -nn | grep 0280
mike@mike-MS-7592:~$ rfkill list all
mike@mike-MS-7592:~$ 

let me provide all the info i can....we have 2 desktops and were sharing a monitor and keyboard.  my internet runs from my cable modem into a D-Link Dir-615 wireless router. i would like to take one of the desktop PC's and move it into the basement and use my TV as a monitor.  i purchased a Netgear N300 wireless usb adaptor and it's the usb adaptor that i am having trouble configuring.  at one point the LED on the netgear adaptor was flashing like it should and when i clicked on the network icon on the top right of my screen it listed both my wired and wireless networks.  i unplugged the wired connection, rebooted to see if i could connect to the wireless, but now the wireless network is no longer listed.  now when i click on the network icon, i only see "wired connection 1".  if i scroll down to "edit connections", i see "wired connection 1" in the wired tab and when i click on the wireless tab i see "defaultm" which is the name of my wireless network.  hope that helps, and i really appreciate everyone's help with this.

---

### Post by Bucky Ball on 2011-11-28
> **Bucky Ball said:**
> Have you gotten all updates while online with the cable and perhaps checked System>Additional Drivers (or whatever it's now called in more current releases)?

?

Also, static IP or your router is serving you one via DHCP?

---

### Post by super newbie on 2011-11-29
@ Bucky

my system is up to date.  when i click on Applications - Additional drivers it says no proprietary drivers are installed, and yes my router is using DHCP. i installed "windows wireless drivers" and when i click that it tells me that its using a driver called "bcmn43xx32".  i removed that driver and re-installed it and as soon as i re-installed it, it automatically connected to my wireless network.  as a test i unplugged my ethernet cable and was "surfing" via wi-fi.  i rebooted and it would not connect to my wireless network.....so i un-installed and re-installed "bcmn43xx32" again, and it finds and connects to my WiFi.  so we now know that i can use my WiFi, but now the question is....why do i have to un-install and re-install "bcmn43xx32" after rebooting?  any ideas?  thanks again to everyone who is helping me

---

### Post by Bucky Ball on 2011-11-30
Ah, well if you can get online ...

Uninstall the wireless driver, get online with a cable and go to System>Administration>Synaptic Package Manager, look for and install 'b43-fwcutter' and 'firmware-b43-installer'. Reboot. Now look for additional drivers. It might just connect 'automagically' after a reboot.

---

### Post by sidzen on 2011-11-30
Suggest unplugging the D-linkand using only the Netgear.  Start over,rebootin modem,then router,then PC.

---

### Post by super newbie on 2011-12-04
thanks everyone, i'll stick with what works for now, that being, removing and reinstallng bcmn43xx32 after every reboot.  thats good enough for me right now

---

