---
title: "Realtek RTL8187b wireless problem finally solved or not?"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by gumbygum on 2009-02-16
Has the problem with the Realtek RTL8187b wireless card not working in Linux been definitively solved? I am about to buy a Toshiba L300, which has that card, and I've spent days searching the net about this. The most recent info I saw was that the new Linux kernel fixes the problem. But then I saw posts saying, no, it still doesn't work. 

Can anyone tell me whether this problem has been solved, or will be solved in the very near future? This laptop is the clear choice for my needs IF I can use the wireless. I am a total Linux newbie planning to move to Linux with this laptop so I want to be confident that it will be able to run wireless and run it to its full capabilities, at least in the very near future. Thanks for any help. Sorry I don't have time to read every post about this issue.

---

### Post by Aarookie on 2009-02-16
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up
I'm on 32 bit computer, not sure if this will work in 64 bit environment, my bro's computer wouldn't accept 32 bit driver with this method, and his card doesn't have 64 bit windows' drivers

---

