---
title: "Ubuntu 9.04 wired connection troubles"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by deafpanda on 2010-09-21
Hello there,

I'm having trouble getting onto the internet with ubuntu 9.04.  I have just moved house and have just got the internet set up here (typing this on windows laptop with wireless).  My ubuntu desktop is plugged in to the network, but in the top right hand corner when I click on the network icon I get:

"Wired network
device not managed"

In my old house I had a static IP.  Is this anything to do with it?

Can anyone help me sort this out?

Will

---

### Post by lukeiamyourfather on 2010-09-21
When right clicking the network icon is there an option to edit connections? Select the wired connection and then the IP v4 tab and set it to DHCP, unless you need a specific static IP.

---

### Post by deafpanda on 2010-09-21
Thanks - I can get to edit connections.  However, there are no entries under "Wired".  Should there be?  I tried clicking "add" and adding a new connection with DCHP but I am still not connected

Thanks

---

### Post by michalsiu on 2010-09-21
issue 

> ifconfig

and see if there is an ip assigned to eth0 interface.
if the interface is not there check the contents of /etc/network/interfaces
if the IP should be grabbed with DHCP make sure you have a statement like this:

> auto eth0
iface eth0 inet dhcp


if any changes were made try issuing 

> /etc/init.d/networking restart

---

### Post by deafpanda on 2010-09-21
Thanks.

ifconfig says "inet addr: 192.168.0.7".  This is my static IP from before.

Do I need to change this, if so how?

Thanks

---

### Post by michalsiu on 2010-09-21
as I said above, change the contents of the /etc/network/interfaces file

to do so you have to edit the file with the following command

> sudo gedit /etc/network/interfaces

this will prompt you for root password.
after that find the line starting "auto eth0" and change what's below that so that it looks like:

> auto eth0
iface eth0 inet dhcp

after you did those changes, please issue the following command:

> /etc/init.d/networking restart

I also suggest that you make your interface manageable by network manager, to do so issue the following:

> sudo gedit /etc/NetworkManager/nm-system-settings.conf

find the line 

> [ifupdown]
managed=true

and change the word "true" to "false"
nest time you boot up it should be manageable by network manager

---

### Post by deafpanda on 2010-09-21
Thanks.

When I try /etc/init.d/networking restart I get "> /etc/network/interfaces:5 unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces

---

### Post by michalsiu on 2010-09-21
could you paste the output of the following commands:

> cat /etc/network/interfaces

and

> ls -lah /etc/network/interfaces

---

### Post by Iowan on 2010-09-21
You might try the restart with **sudo**.
You might also comment out everything but the two "lo" lines to see if DHCP might work on the new system. You can also set up a static address via Network Manager.

---

### Post by deafpanda on 2010-09-22
THanks everyone for your help.  In the end I just installed 10.4 from cd and internet worked right out of the box.

THanks anyway

---

