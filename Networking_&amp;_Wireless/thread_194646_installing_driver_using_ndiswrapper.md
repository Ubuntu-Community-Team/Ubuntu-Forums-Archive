---
title: "installing driver using ndiswrapper"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by sleburn on 2006-06-11
hi, i could use some help guys..
ok, i downloaded appropriate drivers for my intel wireless card, burned onto a CD, and logged in to my pc under ubuntu (have a dual boot system).

i am trying to take the drivers from the cd by running ndiswrapper:
i type ndiswrapper -i drivername

then it returns; Unable to create directory /etc/ndiswrapper/filename.sys.  Make sure you are running as root

i am running as root!  

any help?  trying to get my wireless card to work in my acer laptop.. what a headache!

thanks for any help all!

---

### Post by ns2048 on 2006-06-12
Just to make sure, are you running 'sudo ndiswrapper -i SOMETHING.INF'? Usually that works. Is this an Intel IPW3945 by any chance?

--ns2048

---

### Post by sleburn on 2006-06-12
yes to both questions..  i know there is a bunch of stuff on ipw3945.  when i try to install using ndiswrapper, it says installing and then quickly tells me that I need to log in as root, even though i am using the user and pswd that i set up as root when I first installed the system

---

### Post by sleburn on 2006-06-12
u know what, i see what you mean.. need to make sure i type 'sudo' first to be recognized as root in ubuntu.... ah.. i think I did, but let me try again making sure i type root

---

### Post by kingsidy on 2006-06-12
if you have the intel 3945, it is supported by default by dapper. I have the same card too and it worked right off.

---

### Post by sleburn on 2006-06-12
really?  great.. i may need your help.. newbie here and trying to get wireless working on my acer laptop has been a headache!

thanks!

---

### Post by kingsidy on 2006-06-12
what model. I have owned 3 acer laptops all ran ubuntu fine. sine dapper my acer travelmate 4202 works fine. I have the intel pro 3945. If you are running the 686 kernel, you need to install the linux 686 smp package in order to get the restricted modules, which include wireless i think. otherwise it should work right away with the 386 kernel.

---

### Post by sleburn on 2006-06-12
thanks, i have an acer aspire 5672.  how do i determine if i am running the 686 kernel?

---

### Post by sleburn on 2006-06-12
i downloaded the drivers (i hope) needed to get 3945 to work when in windows, and burned it to a cd.  Now that i am in ubuntu, do you know how i can extract the data that is on this cd?

its like an 80mb .exe file that ubuntu says it cannot open when i try to open it via double-clicking on the file.

thanks for your help.  If I am making this way to complicated, i would curious to see how you got your wireless card to be detected..

---

### Post by sleburn on 2006-06-12
looking i see i have complete linux 386 kernel

---

### Post by kingsidy on 2006-06-13
the eth1 wireless interface doesn't it come up in the network under administration? You do not need to install the driver or use ndiswrapper because the card is supported by default. Go into system > administration > networking. Look at the screen shot attached.

---

### Post by sleburn on 2006-06-13
i see, thanks.. all 3 are showing as unconfigured (wireless, ethernet, and modem)

---

### Post by kingsidy on 2006-06-13
All you have to do is click on the wireless interface, then on activate. Then go into the properties and fill in the necessary info. you can select the network to connect to from the essid list.

---

### Post by Cyfr on 2006-06-14
[QUOTE=kingsidy]All you have to do is click on the wireless interface, then on activate. Then go into the properties and fill in the necessary info. you can select the network to connect to from the essid list.[/QUOTE]

I can't express how much I love you. I've no idea why, but i never thought about sleecting the access point and just thought my card was unsupported because of maybe something sony had done. I love you :p

(My atheros external card didnt have to have the access point selected, weird!)

---

### Post by thenowherekid on 2006-06-27
I have the same wireless device in my dell xps m1710. when i first installed kubuntu, it worked just fine. now it can not be found. there is no eth1, no wireless under network settings. no wireless devices detected. Do you have any idea why it is acting this way?

---

### Post by Herukazhad on 2006-06-27
I have exactly the same problem, i dont know what to do. When i look to "networking", it doesn appear the "eth1"... for wireless. I tried to install and application... seems to me.. the Wireless lan manager, on the aplication menu->Install or quit programas... But not working, i dont know why...
if someone can help... please...
I tried to with de ipw3945install... but its not working, its show like 4 Fatal errors...

---

