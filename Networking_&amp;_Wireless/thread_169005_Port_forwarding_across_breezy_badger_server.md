---
title: "Port forwarding across breezy badger server"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by czk101 on 2006-05-01
Hi

I want to be able to connected my windows laptop to my cable tv box across my network. My laptop is connected to a router, which in turn is connected to my ubuntu server (i've set up samba and can access this ok). My server is then connected to my cable box. The laptop can connected to the server just fine, and the server can connect to the cable box fine. How can I get my laptop to connect to the cable box as if the server wasn't there? 

           Internet
                                   |
                                router
192.168.62.1
                       |                       
                    server                  
      eth0: 192.168.62.100       
      eth1: 192.168.2.200
                       |
                 cable box
              192.168.2.202


The router is also attached to my laptop, whose ip is 192.168.62.50


I've followed this tut as best I could [http://ubuntuforums.org/showthread.php?t=111972&highlight=port+forwarding](http://ubuntuforums.org/showthread.php?t=111972&highlight=port+forwarding)
but it doesnt really do what I want, as it's an external interface coming in that I want to connect to the internal interface

Any ideas?

Thanks

czk

---

### Post by mips on 2006-05-02
What stops you from swapping external & internal interfaces around ?

To make things a bit simpler install fwbuilder (it's in the repos so can be installed with apt/synaptic), this will give you a GUI interface to config iptables. [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

