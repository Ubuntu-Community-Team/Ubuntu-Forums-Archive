---
title: "how do i share my wlan0 internet connection to ethernet?"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by sxcmandan on 2009-02-08
Hi,
   - I connect to the internet through wlan0 on my laptop.
   - My aim is to share this internet connection to my ps3 via ethernet.
   - on windows this was as easy as checking the 'share internet    connection' box.
   -This ethernet connection is to my ps3, however this should not matter as it did not in windows xp.
   -My question is...How do i achieve this in ubuntu (intrepid)?

---

### Post by issih on 2009-02-08
This thread will hopefully help you out :)

[http://ubuntuforums.org/showthread.php?t=1000942](http://ubuntuforums.org/showthread.php?t=1000942)

---

### Post by sxcmandan on 2009-02-12
thanx for the thread but it dosent work for me :(

---

### Post by issih on 2009-02-13
Rats..another alternative is to use firestarter, after that things get a bit mired in terminal commands.

Give firestarter a whirl, see if that does what you want.

---

### Post by Iowan on 2009-02-13
[This]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") one help?

---

### Post by priegog on 2009-04-05
Hey, I don't know if you got it to work, but I'll give it a shot:

1) run in the command ```
sudo apt-get install dnsmasque-base
```
2) Right click on the network-manager icon and select "edit connections"
3) On the "wired" tab, click the "add" button
4) Click on the "IPv4 Settings" tab and on "method" select "shared to other computers. Click on "OK" and then "close"
5) restart your computer. When it's on, and so is the ps3 (with the network cable connecting them both) you should click on the network manager icon and select this new connection you just created. Now it should work. 

Note: depending on your ethernet card and your ps3's you may or may not need a crossover ethernet cable, which is a special one created by putting the cable terminals in reverse order. You can google this to find out more. 
Hope it helps, and let me know if it does.

---

### Post by MarineMan215 on 2009-06-17
I have a laptop that has a wifi card (wlan0) and i want to share the wifi internet with my desktop through an ethernet cable (eth0). The laptop runs ubuntu 9.04, the desktop runs either windows xp home edition or ubuntu 9.04. 

The laptop gets a signal and the connection works. When i try to connect them together the notification says "connected to wired", or something like that, and then says "disconnected to wired" almost as soon as it connects

Please help,
~MarineMan215

---

### Post by priegog on 2009-06-17
Has it ever worked in windows for you? Because if not, the simplest explanation is that you'd need a crossover cable for it to work. Most ethernet cards don't support autodetection of when you're connected to another computer, and so you need to use a crossover cable.

---

### Post by MarineMan215 on 2009-06-17
It has worked fine when i had windows xp pro on my laptop (before i accidently formatted it when i wanted to first install and try out ubuntu). The desktop immediately tries to connect to the laptop when i plug in the cable. Then i hit the button to use the network with the "shared to other computers" option. It connects and then for some reason it immediately after connecting, goes and disconnects.
I have a ([http://www.staples.com/office/supplies/p4_Staples-10-Crossover-Cable-Yellow_166723_Business_Supplies_1_10051_SC3:CG58:DP1804:CL140456](http://www.staples.com/office/supplies/p4_Staples-10-Crossover-Cable-Yellow_166723_Business_Supplies_1_10051_SC3:CG58:DP1804:CL140456)) connecting the computers.

~MarineMan215

---

### Post by priegog on 2009-06-17
If you've done all the right steps, then I honestly have no idea :S HOpefully someone else will be able to help you out

---

