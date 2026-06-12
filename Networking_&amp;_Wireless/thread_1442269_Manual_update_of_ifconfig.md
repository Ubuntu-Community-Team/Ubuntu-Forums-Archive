---
title: "Manual update of ifconfig"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by babelproofreader on 2010-03-29
To get internet access on my second computer I have to follow the manual routine detailed below:

 sudo ifconfig eth0 down
 sudo ifconfig eth0 hw ether ..........
 sudo ifconfig eth0 up
 sudo ifconfig eth0 ....... netmask ........ broadcast ........
 sudo route add default gw .........

where the various ........ represent the relevant addresses. This is necessary because my ISP only recognizes one computer - my first one. The above works fine, I simply copy and paste the above from a text document, but I would like to know which files I can alter/create so that all the above is achieved automatically when I boot my second computer.

---

### Post by chili555 on 2010-03-29
Without sudo, add each separate line to /etc/rc.local right above 'exit 0.'

---

### Post by diesch on 2010-03-30
Add an entry to /etc/network/interfaces, see the [interfaces man page](http://manpages.ubuntu.com/manpages/karmic/en/man5/interfaces.5.html) and /usr/share/doc/ifupdown/examples/network-interfaces.gz for some examples.

---

### Post by babelproofreader on 2010-03-30
Neither of the above suggestions have worked. My /etc/network/interfaces on my second computer is currently:

auto lo
iface lo inet loopback

iface eth0 inet dhcp
hwaddress .............

auto eth0
iface eth0 inet static
address ............
netmask .............
broadcast .......
gateway ...........

where all the ........... are the relevant addresses taken from ifconfig and route run on my working computer.

Running ifconfig on the second computer after the manual procedure detailed above gives 

eth0      Link encap:Ethernet  HWaddr .........  
          inet addr:............  Bcast:..........  Mask:..........
          inet6 addr: ................ Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:994737 (994.7 KB)  TX bytes:148754 (148.7 KB)
          Interrupt:11 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

which is the same as that on the working computer.

---

### Post by chili555 on 2010-03-30
May I see your /etc/rc.local as amended and not working?

---

### Post by babelproofreader on 2010-03-30
> **chili555 said:**
> May I see your /etc/rc.local as amended and not working?

#!/bin/sh -e
#
#rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifconfig eth0 down
ifconfig eth0 hw ether ..............
ifconfig eth0 up
ifconfig eth0 ......... netmask ....... broadcast ...........
route add default gw .........
exit 0

I have also tried with the lines #!/bin/sh -e & #rc.local uncommented, both individually uncommented and uncommented together, but to no avail.

---

