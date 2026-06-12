---
title: "Could not connect to server: localhost : 7200 (Dynamips/Dynagen)"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by shan316 on 2008-12-24
Hi,

I have installed Ubuntu 8.01.. I am trying to run dynagen.. I have successfully installed dynamips, but whenever I try to run my net file, I get the error  Error: Could not connect to server: localhost : 7200
Press ENTER to continue.

My dynamips is running correctly.. Please see the output below: -

root@ubuntu:~/Desktop/cisco-labs# dynamips -H 7200 &
[1] 10303
root@ubuntu:~/Desktop/cisco-labs# Cisco Router Simulation Platform (version 0.2.8-RC2-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: Oct  2 2008 01:17:18

ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
Hypervisor TCP control server started (port 7200).

And, my net file contents are: -

autostart = False
 
[localhost : 7200]
workingdir = /home/shan/Desktop/cisco-labs

[[3640]] 
       image = /home/shan/Desktop/c3640-js-mz.124-17.ex.bin 
       ram = 128 
       disk0 = 0 
       disk1 = 0 
       mmap = True 
       ghostios = True 
       idlepc = 0x604fbc60         
       
[[ROUTER R1]]
model = 3640
console = 2001
slot0 = NM-4E
s1/0 = R2 s1/0

#

[[router R2]]
model = 3640
console = 2002
slot0 = NM-4E

The loopback is up, and I can ping it..

shan@ubuntu:~/Desktop/cisco-labs$ netstat -antu | grep 7200
tcp6       0      0 :::7200                 :::*                    LISTEN     

what could be the problem and how to solve it? I am tired of trying.. so, please someone help me out..

Best regards,

---

