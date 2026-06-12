---
title: "auto eth0 not listed under interfaces !! + Network Connection problem"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by ninadpchaudhari on 2012-07-26
Hi, 
New here on the forums, but with Ubuntu from a long time , 

Here you have your :popcorn: for reading the entire thing ;)

the problem is , 


I have to have a static IP for my Ubuntu Desktop , 
For this, i need to edit "/etc/network/interfaces"
And to my surprise , there is no eth0 listed in the file !
I just have to lo interface inside the file !!

now for the same, i tried adding it manually , but then I do not know y but my Desktop behaves like crazy !
it disconnects from the network :D and then When i restart , It simply shuts the Ethernet Port lights and the lights wont light up ( tried "etc/init.d/networking restart" many times) until i manually replug the cable !!

I tried Making a Network alias, as of like, eth0:1
but then i can see the address in "ifconfig -a" but it not actually accessible from my other pcs Arg !!
(via ssh )  

also i faced a similar issue when trying freenas ( the ethernet used to go off !!) 

Puff , tried almost everything ...

when i do it with GUI " network Manager" It does get assigned, the the Damn Funny part is , 
In ifconfig it has a IP over Network but it does not ping my router :D :D :D 
also is not accessible via ssh !!!  
Help

Oh ya, I am ion 12.04LTS & Unity 2D

---

### Post by papibe on 2012-07-26
Hi ninadpchaudhari.

If you are running a Desktop Edition, then Network-Manager is installed. Thus all the network set up is done using the GUI tool.

I would recommend restore /etc/network/interfaces as it was, and set up an static IP using 'Network Connections'.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by ninadpchaudhari on 2012-07-28
tried the same !
But it does not work off ..
It simply gets disconnected ...

I Think i need to do a complete reinstall then ?????

---

