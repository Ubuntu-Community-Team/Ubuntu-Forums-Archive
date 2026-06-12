---
title: "Compaq 110 cannot 'see' any wireless access points?"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by gobbledigook on 2010-12-11
Hi there!

Installed 10.10 maverick on my compaq mini 110, activated the restricted STA driver... But under the networking drop down it shows wireless as enabled but I cannot actually see any networks, there should be about a half a dozen to see. Works fine under windows. Before the restricted drivers are activated ifconfig shows eth0 and after eth0 and eth1 but when I do iwscan eth0 or eth1 it tells me this action is not supported! 

I have tried reinstalling from cli but no difference? Any ideas? 

Thanx!

Ps sorry for poor post I am posting via mob

---

### Post by bkratz on 2010-12-11
When you say iwscan were you referring to 

sudo iwlist scan

?

---

### Post by gobbledigook on 2010-12-14
yes! my apologies i have been off looking at modding the bios to take a more widely supported card.... but for that i need a windows environment which i no longer have!!! very frustrating :( 

seems everytime i decide to go wholly ubuntu on a system the wireless screws up or i don't have the right driver... i even looked before i purchased the laptop, saw that it worked with the 3rd party drivers adn though that was it! lets go! (i really am only frustrated at myself here!!!)

I was posting from my mob at the time as that was the only way possible to me to post. I have tried following steps in the myhpmini forum:

install
reboot
enable drivers
enable wireless
reboot

no avail

and i have tried the steps in the wireless wiki which includes manually installing from the CLI, and blacklisting previous drivers. same effect

I was using iwlist eth0/eth1 scan

but after iwconfig i see that that it should be: iwlist wlan0 scan

will post agan when i can get home and type up the exact steps and  output :)

---

### Post by gobbledigook on 2010-12-14
for some reason now it works... spent ages writing up my steps as well :)

---

