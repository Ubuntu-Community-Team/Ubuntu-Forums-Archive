---
title: "ubuntu start up takes ages bcause of pppoe"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by Firstlaw on 2011-11-07
Hello,
I have ubuntu 11.10 on LG x140 and an Iburst terminal that connects to the Internet via pppoe connection.
I've managed to get the drivers and install them , I then got rp-pppoe and managed to set it all up
now!
I then realized that network manager doesn't recognize the Internet that i have, the problem would be that software center and the clock , my messenger (empathy), and thunderbird all for some reason don't recognize the Internet...
So ! i followed this thread 
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)

as i'm following the thread above i also used pppoeconf in terminal , which found my connection and asked me if i want to start the connection with computer start! 
and i set all of that up!
now! every thing is BRILLIANT!!! 1 major problem i discovered later!
if i start the computer with out the iburst device plugged in! the computer then takes around 3 ~5 mins to start
because its searching for the iburst to be able to configure network files!
So my 2 questions are

1 . Is there a way for me to ask the computer to skip network configuration if the iburst isn't present
and 2 . do you reckon that i dont need the thread mentioned above, and all i really needed is the pppoeconf?

any help is appreciated , thanks a lot
Cheers

---

### Post by Firstlaw on 2011-11-07
as for question 2 , i have an answer ,I didn't need the thread , i undid everything in the thread 
but heres the trick 
with or without the thread for software center to work I have to restart network manager ....
why is that 
I have to open software center 
then open terminal and type 
sudo /etc/init.d/network-manager restart

then software center is usable...
why!

---

### Post by Firstlaw on 2011-11-07
Update
Okay , basically if i find something i want to install , I can't click on the install button next to it , since its grayed out , i have to restart network manager to get it to work
but then i discovered that if i press on file (top left) I get an install option and that one works ...
so its a glitch in software center that i'll report as a bug or see if some one else reported it and wait for updates
as for question 1 , with not having my iburst terminal pluged and getting a (waiting to configure network) on start up and having to wait for around 3 mins
I fixed that with not having the pppoe connection connect on start up ...
untill i find a solution i'll keep it this way
I would how ever like to have it to set up a connection at start up 
and if it doesn't find the iburst terminal skip and not wait for ages!!!
I'll keep searching untill one day i find an answer!
Cheers!
any help would be great!

---

