---
title: "DHCP Only Please!"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by leadhead on 2009-09-26
I have a box that is running Ubuntu 9.10. I recently ran a "partial upgrade" and it blew away my IP settings. I had a static IP assigned but now it is DHCP. When I try to change it in the network connections manager I click apply and close and it just goes back to DHCP. This is a wired ethernet connection. 

If the network connections gui is broken, that is fine by me if there is a way I can set it from the terminal. 

I tried to do that in fact...I will back up a smidge. After the updates the network connection manager didnt launch at all. I also had no ip assigned to eth0. I was able to solve this part by discovering that /etc/networking/interfaces.conf commented out my eth0. I then uncommented it and restarted init.d/netwoking. But the interfaces config has dhcp set as default so it grabbed an ip from my router. subsequent later updates seemed to partially fix the network connections manager to where it will launch. But I cannot change my connection to manual.

I know enough about linux to accidentally level Moscow, so there are probably some things in my writeup that dont make sense.

---

### Post by leadhead on 2009-09-26
Ok, I figured out how to configure the interfaces config file to reflect a static ip from a thread further down and it seems to be working. This did not reflect in the network connections manager which is fine by me. I am sure later updates will fix it in time. 

I guess it is automatically grabbing dns from my router which is also fine.

Thanks

---

### Post by Iowan on 2009-09-26
Current version of Network Manager (9.04) ignores interfaces configured in */etc/network/interfaces*... Dunno about 9.10.

---

### Post by leadhead on 2009-09-26
ok so that isnt a big deal...is there another config that the network manager uses? I could comment out the interfaces config file and set the network manager up.

---

