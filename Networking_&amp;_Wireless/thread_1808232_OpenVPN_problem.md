---
title: "OpenVPN problem"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by shahverdy on 2011-07-20
I have installed OpenVPN for network-manager using "sudo apt-get install network-manager-openvpn". Now I have it in my network-manager, but I dont know how to configure a connection, I have a configuration script, when I import that script in network-manager it automatically creates a connection, but still problems exists ...
How can I solve this ?

my scripts is this : [http://goo.gl/prKCi](http://goo.gl/prKCi)

---

### Post by shahverdy on 2011-07-20
still nothing ... 
:(

---

### Post by neen2k on 2011-07-20
hi,

im new in linux but I was able to get openvpn work however i did not  user the network manager for openvpn.

I did install openvpn

"sudo apt-get install openvpn"

after install I get the ca.crt file and configuration.conf copied it to /root i think then run the command like this.

Open terminal then type this:

"openvpn configuration.conf"

i got connection and it said Initialized Complete.  However it will not inform you that you are connected.  Just try to browser the internet or  try to check your IP address if it already change.

If you have problem with tap32/tun, try install KVpnc.

"sudo apt-get install kvpnc"

---

### Post by shahverdy on 2011-07-20
Thanks for your instruction, I able to connect to any other servers but mine :( 

what about L2tp? Do you have any solutions ?

---

