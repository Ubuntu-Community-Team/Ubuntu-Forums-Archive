---
title: "Need to have Multiple IP's for faster download speed"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by 3rag0n on 2009-03-22
I live in my university's hostel and all computers must connect to the internet via a central server(it seems). As a result, the average download speed for everyone is around 6 to 7 kbps (with minor fluctuations). The ip's are assigned by dhcp. Now, my friend once tried this :

he ran two operating systems in vmware with ubuntu as the host. (3 simultanoues os'es).  He downloaded the same file from a website parallely in each os , and the speed was the same (7 kbps in each). This was because there was a different IP address for each VM. 

Now, each virtual machine must create a virtual IP in the host os to have its own different IP (i think). I'm a n00b when it comes to networking, but i have this idea :
-> I can create , say, instead of 20 VM's, 20 virtual IP's (aliases or whatever) 
-> Now I write a python or shell script that downloads a section of, say, a huge package in the ubuntu repos.
 That is, suppose the file is 20 mb's.
 I run 20 scripts.
One script will download the First MB, the Second will download the 2nd MB, and so on. Note that this what some of those download accelerators available out there do, except in this case, each script downloads through a different IP. Thus, the effective speed i get is:
 <average speed>*<number of virtual IP's>
In the example, it would be like 7 *20 = 140 kbps approximately.

So i need help on how to obtain new multiple IP addresses via dhcp, on the same computer(without VM's) , and how to tell the script to channel it's data through a particular IP.

Please help... anything would be greatly apperciated.
(Sorry fr  my poor english)

---

### Post by 3rag0n on 2009-03-22
bump.:popcorn:

---

### Post by 3rag0n on 2009-03-22
Bump

---

### Post by 3rag0n on 2009-04-08
Up
.

---

### Post by coutts99 on 2009-04-08
That doesn't sound possible.

It's easy enough to get multiple IP's on your interface, but a script that downloads specific chunks of file? Give up and get used to 7k downloads :)

---

### Post by 3rag0n on 2009-04-08
booomp

---

### Post by 3rag0n on 2009-04-08
> **coutts99 said:**
> That doesn't sound possible.

It's easy enough to get multiple IP's on your interface, but a script that downloads specific chunks of file? Give up and get used to 7k downloads :)

Most download accelerators download segments of a file... for example ... the FF addon DownThemAll... so its possible...!!

Any ideas on how to channell a connection thru a particular virtual interface

---

### Post by 3rag0n on 2009-04-08
I learned how to create virtual network interfaces ( eth0:*) via ifconfig... so any help on how to use 'em ?... to channel connections thru one of them....???

---

### Post by 3rag0n on 2009-04-08
any help?? :)):P):P

---

### Post by 3rag0n on 2009-04-08
up

---

### Post by 3rag0n on 2009-04-08
:s

---

### Post by Joeb454 on 2009-04-08
Try not to bump more than once every 24 hours, I know it can be frustrating :) but it's considered rude on many internet forums :)

---

