---
title: "openvpn / vpn --- ubuntu - debian"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by cypher123 on 2011-07-30
hi @all,

i'm new here and i've got a question. 

i've a server with debian lenny.

my client is ubuntu [COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]*Natty Narwhal*[/COLOR][/FONT][/COLOR].

i've made a openvpn connection between them.

server ip: 10.9.8.13
client ip: 10.9.8.14

each other were found by ping.

my wish is, that i can programming live on the server. perhaps with eclipse or komodoedit etc...

on the server i have a samba client installed and said him , only connect with clients openvpn ip.

my question: are there better (secure) ways like samba.

thanks and best regards

cypher

Edit : // After a few hours i found nfs. , i've also find a good tutorial of nfs, but now i become the following error message after i say to debian server: /etc/init.d/nfs-kernel-server start :: FATAL: Could not load /lib/modules/2.6.18-028stab091.2/modules.dep: No such file or directory

can me help someone pls ?

---

### Post by poolet on 2011-07-30
As I said to a previous thread, There is nothing secure on net... If you want a full secure network you need to unplug the cable.... Do not search for secure, I have seen a lot of thing happen even an IPsec can be down a have security issues... 

For your second problem check if your root or not. If you are root(sounds more logical to be ) just exit and try again if your not try to login....

---

### Post by cypher123 on 2011-08-01
hello,

oh man, in the server terminal i always type apt-get update and apt-get upgrade.

thought i ' ve got the newest version of debian.

yesterday, while i search the problem solution, i see it give a newer version as lenny, called squeeze.

now i had done the dist-upgrade. 

thanks for your answer, i will give feedback as soon as possible.

best regards

edit :// can anybody help me pls?


Edit : // Now i've Squeeze, but if i want start the /etc/init.d/nfs-kernel-server ther also come the same error: FATAL: Could not load /lib/modules/2.6.18-028stab091.2/modules.dep: No such file or directory
i looked into this directory and i see i've only /lib/modules/2.6.18-028stab070.2# . where can i update the module? 
i reboot the server, same problem.

uname -a shows: 2.6.18-028stab091.2 #1 SMP Fri Jun 3 00:02:40 MSD 2011 x86_64 GNU/Linux

is this the last stalbe version? if not so, how can i upgrade all of it?

thank you and best regards

---

