---
title: "Wifi connection depending on power plug / battery."
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by marco furio ferrario on 2011-05-11
I have a asus eeepc 1000h, ubuntu 11.04 just upgrated and working fine (almost).

The point is that apparently randomly wireless connection results impossible to be established. I have noticed that this happen ony if the laptop is running on battery, although it is not strictly related to it, in fact most of the time it works just fine. It is neither related to a low level of battery charge, as I have experienced it many times with full battery. 
 CURIOUS THING: I have experienced the same also with other laptop (macbook pro) and os (windows) and also with my Kindle!!!!, and i could ALWAYS solve the problem BY PLUGING the device (mac, asus, kindle) to a power source: once connected the wifi works fine. 
 Notice that I have experienced it with different internet connections in different places, so issue is not related to the net or the local power supply. 

IS THERE ANYBODY ABLE TO GIVE SOME LOGICAL EXPLANATION TO IT?

---

### Post by Blastwizard on 2011-05-29
Have the same problem with my EeePC 1000 under  11.04 (it worked fine under 10.04), wireless connections work fine when the netbook is on AC supply, but disconnects when on battery, I tested it on different wireless networks, including a 3G network on USB dongle. I suspect an problem with the ACPI, not giving enough power to the network devices when power is supplied by the battery. It would be good to have a fix to that problem.

---

### Post by marco furio ferrario on 2011-06-03
Somebody told me that is a system problem, saying that the program controlling the wifi is "volatile" ie it sometimes cancels wifi settings to free memory when pc is on battery power. But this guy obviously only told me why happen but not how to fix... why you linux geek have this tendency to be so lame?

---

### Post by DrDank on 2011-06-22
I'm having the same problem, someone help

---

### Post by JRCavileer on 2011-07-24
Same issue!! Someone please help!

---

### Post by Jamesi on 2011-07-24
when my windows become ' unstable' i could not be bothered waiting for 5 hours for it to return to normal status ( my CD was not back up, it was ACER ) anyway, i downloaded, burned the iso on a disc. on my other old laptop which runs ubuntu 10.04.  Anyway, when i stuck the LIVE CD in my acer laptop. the connection to my internet ( i am from the uk so i use BT ) would not connect. I restarted my hub, but it still did not work. so i had to do a bit of research. with whatever you are with, EG, virgin media. and you cant connect then you are going to have to go into ' Edit settings' when you clicked on your wireless icon.

Depending on your connection you want to make ( wireless) in my case, then you neeed to click on ' Wireless' in the ' Network connections ' window. Then click on the Name of your internet. Mine is called ' AUTO BTHOMEHUB483-W' I am too lazy to change it :p anyway. Once the name is highlighted. click on ' edit' then i went on IPv4 settings. and that is as far as i can help you. for my BT connection ' error' i had to go on the BT forums. and a guy gave me the settings. i think you should go to the internet provider's forum and ask around. or google it. Sorry for not helping :p

---

### Post by balmar on 2011-08-24
Found a solution that seems to work: [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67). See also the bug report [https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445](https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445).

I had the same issue on my Eee 901 after upgrading to 11.04.

---

