---
title: "Network-Manager doesn't work with original madwifi-driver"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by forquato on 2006-06-13
Hello!

i deleted restricted modules because I installed the original driver from the nvidia site... But it make the madwifi-drivers deleted too. So I installed newest madwifi-atheros driver. 

Now, the Network Manager doesn't work.  
It worked with contained madwifi drivers in ubuntu 6.06, but after deleting restricted modules and installing original-madwifi drivers, network-manager doesnt work. 
Is that a Bug or is there a way to make network-manager work?

forquato

---

### Post by dyssident on 2006-06-13
if madwifi + NetworkManager worked for you out of the box youve already had more luck than i have.

if it worked before you may simply want to do `sudo apt-get install --reinstall linux-restricted-modules` then build the nvidia drivers and overwrite whatever  apt installed. im not sure how good of an idea just overwriting is tho; you may need to remove the driver with modprobe or something mysterious like that.

if you removed linux-restricted-modules then built the current code from madwifi.org, you have installed a completely different version of madwifi. dapper uses madwifi-old and madwifi.org is currently working with madwifi-ng. 

you might want to try [this howto]("http://www.ubuntuforums.org/showthread.php?p=703020#post703020")  and set up the latest wares. so far i havent been able to get madwifi-old or madwifi-ng to work, but i will soon be trying this tutorial in hopes that it works.

---

### Post by Eversmann on 2006-06-25
I'm in the same situation. Can't use network manager with original madwifi driver, and i am only able to use it because if not, wifi radio doesn't start :-(

---

