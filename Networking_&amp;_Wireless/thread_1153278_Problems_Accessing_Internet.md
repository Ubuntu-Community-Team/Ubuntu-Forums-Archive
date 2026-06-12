---
title: "Problems Accessing Internet"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Generic Bond on 2009-05-08
Hi. I downloaded Ubuntu for my mother's HP laptop. I was confident and stupid enough to delete Windows from her hard drive, because I had done this same process on my boyfriend's Toshiba laptop and everything worked just fine, so I didn't have any worries. 

When I installed Ubuntu, everything was fine. It absolutely WILL NOT access any sort of wireless internet, whatsoever. It keeps telling me to download updates and restricted hardware, but I don't have internet to download anything!

Any ideas?

---

### Post by Generic Bond on 2009-05-08
Okay. Now it's giving me a wireless driver to download but I don't have any internet to download the driver.

---

### Post by evolutionaryit on 2009-05-08
Generic Bond,

In order to get your wireless card working you are going to have to get connected to the Internet.  I'm willing to bet that your wireless card needs to have a restricted driver to work at all.    The easiest way to do this is to connect your machine via its wired Ethernet interface to the Internet and download the restricted driver, (and any other updates) then you can connect wirelessly thereafter.  For more info see the docs below or ask for further clarification here.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Best of luck & enjoy the weekend!

---

### Post by netwarriorwy on 2009-05-08
If I were you I'd try to check if my wireless interface is up.

Go to a terminal and type

> ifconfig -a. You should see something like wlan0. If not just type > sudo ifconfig wlan0 up and it should fix it. 

If that's not the problem I agree with evolutionaryit and try connecting your laptop to the wired network.

Dont forget to check if you have a DHCP or static ip connection, if you have static ips then right click on the network-applet and click on > Edit Connections...->Wired tab->choose your wired network->click on the Edit button

Now you need to enter the parameters. IP,subnet mask,gateway,dns.

If you are just DHCP, coonect yourself to the wired network and check the following command:

> lspci -v and check for Network Controller, you'll see the one you're using for wireless as well as the driver.

Check if its supported by Ubuntu. You can check this page:
[http://linuxwireless.org/en/users]("http://linuxwireless.org/en/users")

I have an HP Pavilion dv6000 with Ubuntu 9.04 fresh new instalation and the wireless rocks! Btw my processor is Intel. If you're Intel check this site. [http://intellinuxwireless.org/]("http://intellinuxwireless.org/")

You can also download the packages your system is telling to and see what happens, thats the fun of this :popcorn:

I hope it helps!

---

### Post by superprash2003 on 2009-05-09
if you could hook your machine via LAN ( wired ) to a router and then get the updates..

---

### Post by Generic Bond on 2009-05-09
Thanks for all of your input. I figured it out.

---

