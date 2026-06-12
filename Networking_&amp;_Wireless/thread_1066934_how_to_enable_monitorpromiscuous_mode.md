---
title: "how to enable monitor/promiscuous mode"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by inaka98 on 2009-02-11
Hi there, I have a Cisco Aironet wireless Atheros AR5001X+ installed on an HP laptop running Ubuntu 8.10.  The card is working because I can logon to the wireless network at work and ping other IPs on the network.  I would like to know how to enable monitor and/or promiscuous mode on this card because I am trying to run wireshark to capture traffic communication using this card.  I am new to Linux and any help would be appreciated, thanks.

---

### Post by SunSpyda on 2009-02-11
To put a NIC into promiscuous mode, open the terminal and enter this -
*sudo ifconfig xxx promisc*
Once this command is run, you will need to enter the root password. Replace the xxx with the device name of your NIC, usually this is eth0 or rausb0.

---

### Post by inaka98 on 2009-02-11
I tried the command, but when I typed iwconfig, it still displays the "Mode:Managed".  How do I check if the mode has been changed to promiscuous?  I tried typing in "sudo ifconfig xxx monitor" to change it to monitor mode, but I get a message saying "monitor: Unknown host".  How do I change the mode to monitor?  Thanks.

---

### Post by Leetbumble on 2009-12-31
When you type 

 #sudo ifconfig xxx prmisc

the xxx is the name of your wireless card.



To find this type 

 #ifconfig -a

which will output all of your devices. The one you are looking for is
    WLAN[number]
Where number will likely be a 0 (zero) because it is your first wireless card.

The final command would look like 

  #sudo ifconfig wlan0 promisc


Hope this helps.

---

