---
title: "How to connect internet ?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by annim on 2010-02-19
**hello, **
**i am a begginer for linux based OS, i want to connect to internet. i got my wi-fi modem. i got ubuntu 9.10 installed and it eastablish connectong automatically with modem atleast but after that, what i have to do to get connect to internet. **
 
**i want to go slow now , so please anybody help me and expalin me how to configure my modem to get connect to internet. **
 
**i got basic information about bash, the cmd prompt in linux. so anybody can use that term to explain me.**
 
**thanx!:p**

---

### Post by mionescu on 2010-02-19
Can you give a few more details. Are you trying to connect to a wireless router? Do you need a password for that? I understand from your post that Ubuntu recognized yout wireless card. Is it right?

---

### Post by Iowan on 2010-02-19
It'd be helpful to see results of **route -n** (from a terminal). Help getting that information is available by request...

---

### Post by annim on 2010-02-20
thankyou for giving time to my problem,
 
well, in network manager i got all buttons as dead under VPN tab.!!!
 
whta i come to know after searching in net that in ubuntu 9.10, the openvpn package is not been provided!!! :(....
 
nextly, when my ubuntu connects to my wireless modem, its gets automatically connected.... no passwords demand.
 
after this, configuring router! i dont know how to configure it.!!!!
 
i have executed some commands to install open-vpn as root/admin user by typing 'sudo' with the command. by after that , resutl is the package is missing or can't found.!!!!!
 
i am an average level of programmer but in windows platform, now i want to switch myself to LINUX to get myslef at same level in linux platform in programming terms. :D
 
i can understand technical terms  so you can use any terms u want to.
 
 
in network manager, i got DSL and wired connection, the same one which gets connected automatically . the VPN tab is totally dead.
 
now problem is, i am not so use-to to how to install programs and how to create installers of any apps created by me.! 
 
wating for help! thans!

---

### Post by thebigob on 2010-02-20
> **annim said:**
> thankyou for giving time to my problem,
 
well, in network manager i got all buttons as dead under VPN tab.!!!
 
whta i come to know after searching in net that in ubuntu 9.10, the openvpn package is not been provided!!! :(....
 
nextly, when my ubuntu connects to my wireless modem, its gets automatically connected.... no passwords demand.
 
after this, configuring router! i dont know how to configure it.!!!!
 
i have executed some commands to install open-vpn as root/admin user by typing 'sudo' with the command. by after that , resutl is the package is missing or can't found.!!!!!
 
i am an average level of programmer but in windows platform, now i want to switch myself to LINUX to get myslef at same level in linux platform in programming terms. :D
 
i can understand technical terms  so you can use any terms u want to.
 
 
in network manager, i got DSL and wired connection, the same one which gets connected automatically . the VPN tab is totally dead.
 
now problem is, i am not so use-to to how to install programs and how to create installers of any apps created by me.! 
 
wating for help! thans!

Just for clarification VPN is Virtual Private Network. This should only be used to connect to a VPN. If you are just wanting to connect through your default gateway (your router or modem) you do not need to worry about vpn at all.

Can you type in a terminal "ifconfig" and paste the comments into a reply.

---

### Post by mionescu on 2010-02-20
What exactly do you want to configure? Do you need to enter passwords for the dsl provider? Then you don't need the vpn. Can you make it clear what are you trying to do?

---

### Post by Iowan on 2010-02-20
> **annim said:**
> 
i have executed some commands to install open-vpn as root/admin user by typing 'sudo' with the command. by after that , resutl is the package is missing or can't found.!!!!!First, I'll agree with the others that VPN shouldn't be necessary to connect to your ISP. Second, what commands did you use to install the package? Ubuntu has several package managers - Synaptic, aptitude, and apt-get for example. Did you use something like **sudo apt-get install <packagename>**?

---

