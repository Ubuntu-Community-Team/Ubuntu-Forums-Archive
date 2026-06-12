---
title: "hello and help"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by bumpncarstereo on 2006-04-27
so i installed ubuntu linux on my second desktop computer i had. i was able to access the internet when i had the wep encryption off and mac address filter off. i put the mac address for the linux unit into the router, but i cant figure how to enter the wep encryption. and then it wouldnt access the internet any more.  i tried disableing the wep and mac address and now it wont connect.

it says it is sending and recieving packets thru "connection lo"

what does "up loopback running" mean?
i tried the ifup command and all it did was say ifup: use - help for help. so i entered ifup help and got: Ifup: failed to open statefile /etc/network/run/ifstat: Permission denied

had a random synapse in my brain connect and i went back to re read a few posts.
"/etc/sysconfig/network-scripts/" returned no such file or directory, and so did " cd /etc/sysconfig/net[tab]"

ok so i did some more digging, and found network tools decices, where then i found that it had 2 network devices one was loopback interface (defult?) and the other was ethernet interface (eth0) but it wont let me confingure it, nor do i see anything that says make it default.

found my way to network settings, and it shows ethernet connection :the interface eth0 is acctive.

i am new to the whole linux thing, and kinda new to the whole seting up networks. the router is a dlink di-524, i wanted the linux machiene to be on the router wired so i had uninstalled the wireless card before i started messing around with ubuntu. i got frustrated, and so i let it sit for a while. now i am coming here for help.

also i noticed that the lights on the router arent flashing for the port that the wire for the linux computer is on. but the one for my normal desktop is.

my ultimate goal is to use the linux computer for a server of sorts. being that i have a decent connection i want to host files on it for the web.

---

### Post by duality on 2006-04-27
check "man ifconfig"

And "sudo ifconfig eth0 up" to start the ethernet interface, then "sudo dhclient eth0" to recieve an ip.
see "ifconfig -a" for a list of interfaces , if "eth0" wasnt the right one

---

### Post by bumpncarstereo on 2006-05-07
well i am awaiting furter testing, but my laptop battery is dead right now, so i cant see if the router is transmiting or not,  but i changed ports on the router with this computer and it still worked. the lights on the back of the computer i have setup ubuntu on for the network cable are flashing, along with the the lights on the wireless card i reinstalled.

i also tried what duality sugested.

---

### Post by bumpncarstereo on 2006-05-10
well it looks like the router is working as it should be, there fore the problem lies with the network card on the desktop.

---

