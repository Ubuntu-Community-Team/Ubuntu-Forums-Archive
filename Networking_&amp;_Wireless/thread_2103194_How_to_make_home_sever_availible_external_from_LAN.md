---
title: "How to make home sever availible external from LAN"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by BStrizzy on 2013-01-09
Hey guys, 

Quick question, I currently have a home server with a static I.P address that I set and I am ready to make my server available externally so I can access it where ever I am at. I am trying to connect to my sever where ever I am at via SSH. I know I have to go to my router settings and make it external some how. I currently have a linkysys router.

advice and guidance?

---

### Post by haqking on 2013-01-09
> **BStrizzy said:**
> Hey guys, 

Quick question, I currently have a home server with a static I.P address that I set and I am ready to make my server available externally so I can access it where ever I am at. I am trying to connect to my sever where ever I am at via SSH. I know I have to go to my router settings and make it external some how. I currently have a linkysys router.

advice and guidance?

depending on your router you need to forward the ports to the IP of that machine.

If you want to ssh for example then forward port 22 (though best to change it for outside world connectivity)

if its for web then forward port 80

etc
etc

However your external IP is likely to change unless its static also so you will need some type of DynDNS service or a static IP

---

### Post by dpurgert on 2013-01-09
step 1. know your external IP address (192.168.x.xxx is not routable to the world).  i use [www.whatismyip.com](www.whatismyip.com) for this check 
step 2. set up your router to port forward anything on port 22 to your server (though as noted above, you may want some random high port on the external side pointing to the internal port 22)
step 3. go somewhere "not home" (university, coffee shop, etc) and try to ssh into your home server.
step 4. (optional) get a service like dyndns so you don't have to keep checking your home public IP.  This involves some additional router setup, and/or may require flashing a better system onto it (ddwrt, tomato, etc).

---

### Post by ahallubuntu on 2013-01-09
In addition to the above suggestions, consider setting up a VPN server at home.  That puts you on your home network from anywhere, and you can get to any device on your local network. If you setup an OpenVPN server with certificates, that is more secure than opening port 22 to the world (which means hackers can try to access your server by cracking the password).

I have a router with DD-WRT (yes, also does DynDNS) that also has an OpenVPN server built into it.  Only larger images of DD-WRT contain the OpenVPN server - your router has to have enough RAM and NVRAM for it to work.  If OpenVPN is built into the router, then you can leave the home server in standby and use Wake-On Lan to wake it up remotely whenever you need it.

Not all routers can run a firmware like DD-WRT at all. Consider getting a cheap old Linksys WRT54G router as a gateway using DD-WRT.  There are different versions of the WRT54G.  Get version 4 or older (or WRT54GL) to be able to run the full version of DD-WRT with OpenVPN.

---

### Post by BStrizzy on 2013-01-09
> **haqking said:**
> depending on your router you need to forward the ports to the IP of that machine.

If you want to ssh for example then forward port 22 (though best to change it for outside world connectivity)

if its for web then forward port 80

etc
etc

However your external IP is likely to change unless its static also so you will need some type of DynDNS service or a static IP

awesome advice, trying this first thing int he morning

---

### Post by BStrizzy on 2013-01-09
> **ahallubuntu said:**
> In addition to the above suggestions, consider setting up a VPN server at home.  That puts you on your home network from anywhere, and you can get to any device on your local network. If you setup an OpenVPN server with certificates, that is more secure than opening port 22 to the world (which means hackers can try to access your server by cracking the password).

I have a router with DD-WRT (yes, also does DynDNS) that also has an OpenVPN server built into it.  Only larger images of DD-WRT contain the OpenVPN server - your router has to have enough RAM and NVRAM for it to work.  If OpenVPN is built into the router, then you can leave the home server in standby and use Wake-On Lan to wake it up remotely whenever you need it.

Not all routers can run a firmware like DD-WRT at all. Consider getting a cheap old Linksys WRT54G router as a gateway using DD-WRT.  There are different versions of the WRT54G.  Get version 4 or older (or WRT54GL) to be able to run the full version of DD-WRT with OpenVPN.

yeah i was considering using a vpn. would I still need to open up the ports on my router configs for this or is this going a completely different route? I would really only like for me to access the server, so im guessing vpn would be the best way?

---

### Post by ahallubuntu on 2013-01-09
> **BStrizzy said:**
> yeah i was considering using a vpn. would I still need to open up the ports on my router configs for this or is this going a completely different route? I would really only like for me to access the server, so im guessing vpn would be the best way?

No, you don't need to open port 22 for ssh if you connect using a VPN.

You'll still have to open *a *port (probably 1194, the OpenVPN standard port), but because you can use certificates with OpenVPN not just a simple password as you would with ssh, it should be much more secure.  You don't have to worry about brute force challenges against your SSH password.

---

### Post by BStrizzy on 2013-01-09
> **ahallubuntu said:**
> No, you don't need to open port 22 for ssh if you connect using a VPN.

You'll still have to open *a *port (probably 1194, the OpenVPN standard port), but because you can use certificates with OpenVPN not just a simple password as you would with ssh, it should be much more secure.  You don't have to worry about brute force challenges against your SSH password.

ok gotchya, i tried to find some how to's on how to install openVPN on my ubuntu server. everywhere i look it is saying how to install it on ubuntu desktop

---

### Post by ivicks on 2013-01-09
> depending on your router you need to forward the ports to the IP of that machine.

If you want to ssh for example then forward port 22 (though best to change it for outside world connectivity)

if its for web then forward port 80

etc
etc

However your external IP is likely to change unless its static also so you will need some type of DynDNS service or a static IP

I just wanted to mention the last time I looked DynDNS didnt offer their free service anymore, but that was probably about a year ago. Just wanted to toss that out there :)

---

### Post by ahallubuntu on 2013-01-09
> **BStrizzy said:**
> ok gotchya, i tried to find some how to's on how to install openVPN on my ubuntu server. everywhere i look it is saying how to install it on ubuntu desktop

Have you tried this one?

[https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)

Basically, there are two steps on the server side:
- create your keys and certificates
- create the server config file

The tricky part is figuring out which certificates are used for what.  A TUN configuration is simpler than a TAP (bridged) configuration.

Then, setup the client side.

If you have a Ubuntu Desktop client (laptop etc. you will use to connect back your VPN from the internet outside), install the OpenVPN plug-in for network manager so you can connect to your VPN via network manager under the VPN menu instead of doing it via terminal commands.

---

### Post by BStrizzy on 2013-01-10
> **ahallubuntu said:**
> Have you tried this one?

[https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)

Basically, there are two steps on the server side:
- create your keys and certificates
- create the server config file

The tricky part is figuring out which certificates are used for what.  A TUN configuration is simpler than a TAP (bridged) configuration.

Then, setup the client side.

If you have a Ubuntu Desktop client (laptop etc. you will use to connect back your VPN from the internet outside), install the OpenVPN plug-in for network manager so you can connect to your VPN via network manager under the VPN menu instead of doing it via terminal commands.

ok sounds good, i am indeed using ubuntu desktop but i am also duel booted with windows 7. I am creating smb files shares, would I need anything else to connect via my windows side? also with my mobile (root accessible) android phone

---

### Post by BStrizzy on 2013-01-10
> **dpurgert said:**
> step 1. know your external IP address (192.168.x.xxx is not routable to the world).  i use [www.whatismyip.com]("http://www.whatismyip.com") for this check 
step 2. set up your router to port forward anything on port 22 to your server (though as noted above, you may want some random high port on the external side pointing to the internal port 22)
step 3. go somewhere "not home" (university, coffee shop, etc) and try to ssh into your home server.
step 4. (optional) get a service like dyndns so you don't have to keep checking your home public IP.  This involves some additional router setup, and/or may require flashing a better system onto it (ddwrt, tomato, etc).

hey so I just opened up port 22 on my router directed to my server ip, how ever the ip i put it to go to is a local I.P. I am having trouble  finding the EXTERNAL i.p address of the router. reading thru forums such as 

[http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal](http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal)

i am confused of how to find this out. also in my router settings do i direct the ssh traffic to the i.p address that i have locally? or will it be my external i.p?

---

### Post by BStrizzy on 2013-01-10
hey so I just opened up port 22 on my router directed to my server ip,  how ever the ip i put it to go to is a local I.P. I am having trouble   finding the EXTERNAL i.p address of the router. reading thru forums such  as 

[http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal](http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal)

i  am confused of how to find this out. also in my router settings do i  direct the ssh traffic to the i.p address that i have locally? or will  it be my external i.p?

---

### Post by haqking on 2013-01-10
> **BStrizzy said:**
> hey so I just opened up port 22 on my router directed to my server ip, how ever the ip i put it to go to is a local I.P. I am having trouble  finding the EXTERNAL i.p address of the router. reading thru forums such as 

[http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal](http://askubuntu.com/questions/145012/how-can-i-find-my-public-ip-using-the-terminal)

i am confused of how to find this out. also in my router settings do i direct the ssh traffic to the i.p address that i have locally? or will it be my external i.p?

your external (WAN) ip should be shown on your router interface.

If not then go to [www.whatismyip.com](www.whatismyip.com)

However as already said it will likely change often, hence the need for a dynamic DNS service.

You forward on the router the port to the IP of the machine running the service (internal)

---

### Post by BStrizzy on 2013-01-11
> **haqking said:**
> your external (WAN) ip should be shown on your router interface.

If not then go to [www.whatismyip.com]("http://www.whatismyip.com")

However as already said it will likely change often, hence the need for a dynamic DNS service.

You forward on the router the port to the IP of the machine running the service (internal)


awesome, exactly what a university network ubuntu user told me. thanks! Will be marking this thread as solved!

---

