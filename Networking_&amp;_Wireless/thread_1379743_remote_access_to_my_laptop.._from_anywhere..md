---
title: "remote access to my laptop.. from anywhere."
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by ja660k on 2010-01-12
hey guys,
as the title suggests im trying to enable ssh in a way that i can be on the other side of the world and ssh into this laptop (given the laptop is on).

it worked for HTTP for a while yesterday, but i managed to break it.
now when i type my WAN ip address into browser my router resets :confused:

so any help would be great.

- Yes i do have ssh, apache.. etc. installed and working.
- I have a motorola SBG900 router.

a picture tells 1000 words so ill add some screenshots of the routers admin page.

the address of my laptop is 192.168.0.100 and hostname ja660k

I have added DHCP lease for my laptop, bypassing the routers firewall (to accept inbound connections)

Picture1.png

I have added a DMZ host to my laptop

Picture3.png

and i have enabled port forwarding to my laptop

Picture2.png



any help would be great :-)
thanks in advance

---

### Post by shredder12 on 2010-01-13
What did you actually do that you are now unable to open any website using ur browser?
Are you able to ping websites or IP addresses?

Your firewall config seems to be right. You have allowed incoming connections to 192.168.0.100, forwarded the 22 port. I am just not sure about your internet connectivity and browser trouble.

---

### Post by ja660k on 2010-01-13
yeah its working.. im on the laptop right now.

---

### Post by shredder12 on 2010-01-13
In order to connect to your system remotely which is behind a firewall or NAT you will need to tunnel through the firewall/router. 
This can probably be achieved by ssh-tunneling or virtual private networks..
You may try openvpn for virtual private networks.
and this article might help you for ssh tunneling [http://serverfault.com/questions/66483/ssh-remote-access-vpn-tunnel](http://serverfault.com/questions/66483/ssh-remote-access-vpn-tunnel)

---

### Post by ja660k on 2010-01-13
yeah, i just realized my router doesnt loopback. 

so you are completely correct... it works...
testing it from within my network caused my router-fail.

thanks for your help.

---

