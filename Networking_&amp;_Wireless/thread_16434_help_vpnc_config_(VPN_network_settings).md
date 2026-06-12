---
title: "help vpnc config (VPN network settings)"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by dott.malcom on 2005-02-21
Sombody can help me to configure this program?

- I get internet acces only trough windows because in the place where i am there is only the VPN, and i'm not able to configure this program

- I've just installed vpnc with synaptic

I don't know where to start, please, this is the only reason i can't use Linux here, help me solve it!

Thanks in advance

---

### Post by themindlessmatt on 2005-02-27
Currently using VPNC to connect to university network, which uses Cisco equiptment.

There is an example config file at /etc/vpnc/example.conf...

So...

Make a copy for you to modify...

Go to terminal and type...

sudo cp /etc/vpnc/example.conf /etc/vpnc/university.conf

sudo gedit /etc/vpnc/university.conf

Then, alter the first 4 lines to match the connection details...

IPSec gateway the.address.or.ip.of.server
IPSec ID group.name.given.to.you.by.administrator
IPSec secret group.password.given.to.you.by.administrator
Xauth username your.username.given.to.you.by.administrator

Save...

Then, to connect... (university is the name of the conf file you just created, without the .conf on the end).

---------
sudo modprobe tun
sudo vpnc-connect university
---------

To disconnect
----------
sudo vpnc-disconnect
-----------

Hope that helps,

Matt

---

### Post by lee_connell on 2005-07-27
hey guys,

i got vpnc installed i setup my config and i am asked for username and password and it says it connected and puts the process in memory.

i check ifconfig and there is an ip assigned to me from the pix using tun0 interface.

however i cannot ping any ip or connect to any ip on the network im connecting to which is 192.168.0.0.

I am not allowed to ping any host names like [www.google.com](www.google.com) as i can see there was a route added to my table which throws all traffic to tun0 which would be the answer to this.

my concern and main question here is why can't i ping any 192.168.0.0 network?  the error it gives me is this:  

/etc/vpnc$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

---

