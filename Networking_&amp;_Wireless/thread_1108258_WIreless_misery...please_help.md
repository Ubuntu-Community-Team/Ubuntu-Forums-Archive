---
title: "WIreless misery...please help"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by comradejanus on 2009-03-27
OK im relatively new to ubuntu and the world of linux, so please give me a hand here...

I tried installing ubuntu on my samsung nc10, everything works fine, except the wireless! The wireless card has the driver installed...I think.

I typed:

 sudo apt-get install linux-backports-modules-intrepid

into the terminal and it installed something, but I have no idea how to check its activated or what. Nothing is showing up under "Network" in my places and i tried using the network configuration utility but that doesnt seem to find any networks.

I did post this morning but no-one replied.

Please help someone!

---

### Post by comradejanus on 2009-03-27
argh is no one going to help me?

---

### Post by coffeecat on 2009-03-27
[There you go]("https://help.ubuntu.com/community/NC10")! :wink:

There's a bit more to do after the 'sudo apt-get install linux-backports-modules-intrepid' bit.

---

### Post by comradejanus on 2009-03-27
yea I have done all that stuff but I have no idea what to do now or if its worked. When I go to network configuration there is nothing under wireless.

Also when I type iwconfig I get the following:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


What does that mean?

---

### Post by coffeecat on 2009-03-27
OK, you've done the blacklists and rebooted. After rebooting, you should see the Network Manager applet icon near the top right. Click on that and if the network card is working properly, a little menu should drop down showing any wireless networks in range. Click on the one you want and it should prompt you for the WEP/WPA passphrase. And that should be it.

And that's what I did when I installed Ubuntu on my Eee which has the same/similar Atheros wireless chipset.

---

### Post by comradejanus on 2009-03-27
Nah I dun see it :( Nothing comes up. When the drop down menu appears. I must have not installed it properly.

---

### Post by superprash2003 on 2009-03-28
post output of the following commands
1)iwconfig
2)iwlist scanning

---

### Post by comradejanus on 2009-03-31
Hi

Sorry for the extreme lateness of my reply.

When I run 

Sudo iwlist scanning 

I get the mac and SSID of all the connections that I normally recieve on my windows set up, including my home one that I want to connect to.

So it sees it but how do I connect to it.

I tried the manual connection utility but the OK button is continually grayed out, even when ive filled all the details on the 'wireless' and 'Security' tabs, but I dont really know what to put under IPv4. I've just left DCHP as automatic.

---

