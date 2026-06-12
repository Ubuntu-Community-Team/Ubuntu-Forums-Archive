---
title: "configuring openvpn slowly driving me crazy help"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by tuxulin on 2012-10-18
i have googled and seen only a hand full of
vpn setup and configuration guides plus even
few autoscripts to get the job done for you.
but in all is some sort of errors that leads
to either certificates not been written or
missing vpn files or files pointing to other
files that do not exist.
this also includes the openvpn tutorial on
ubuntu website LOL.

i have a VPS running ubuntu 12.04 64bit no desktop
im looking for a vpn guide that actually that works. 

have you got vpn running ?
please if you have can you point in the right
direction as to where i can follow a step by step guide.

by the look of things centos have no problem with openvpn
but i choose to stay with ubuntu.

---

### Post by ahallubuntu on 2012-10-18
Yes, I have installed OpenVPN server in several scenarios with Ubuntu but not on 12.04 LTS, only on 10.04 LTS.

I did have some issues getting it to work.  The setup with a DD-WRT router that has OpenVPN built in was far, far easier, but I also used TAP not TUN for that, and I think TAP is simpler.  In one scenario I needed TUN.  The average user is probably OK with TAP (fewer routing options).

Basically, there are three things you have to deal with:

- openvpn server setup file
- certificates
- networking interfaces file (if using TUN, I needed to add a bridge; maybe not required for TAP).

If you are using Ubuntu 11.10 or newer, have you tried this how-to guide?

[https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)

For the client portion, if you are trying to connect with an Ubuntu client, you can use the network manager add-on and set up the OpenVPN connection entire with the Gui.  For the server side, though, you need to edit config files and generate certificates, etc.

If you are having specific issues, what are they?

---

### Post by tuxulin on 2012-10-18
thanks for the reply ahallubuntu
after getting back from work ill go througth 
the link you provided thanks

on my vps i think i have "tap" confirmed by 
cat /dev/net/tun with a bad state reply

i hope this tut will be good... either way ill be
back to let you know

Thanks again
Tux

---

### Post by tuxulin on 2012-10-20
just wanted to say thanks again i managed to sort it all out now just to find another new problem waiting for me. LOL

cheers buddy
Tux

---

