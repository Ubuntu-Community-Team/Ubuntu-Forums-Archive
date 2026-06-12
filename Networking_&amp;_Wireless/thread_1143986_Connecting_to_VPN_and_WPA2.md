---
title: "Connecting to VPN and WPA2"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Nir Friedman on 2009-04-30
Hey,
I'm not even sure how to go about this. My university offers the choice of both of these to get secured access and neither one of them are working for me right now. I am trying to do it through the GUI, I'll mention that to start off. So basically through the network management applet. Ok, so
VPN: I'm totally lost here. My university VPN is PPTP. I go to network management and try to go to VPN. There's two options, open VPN and VPNC. Neither of them have an option to select a PPTP protocol. I have both the linux pptp package and the network manager pptp package. So this is as far as I've gotten.
WPA2: Once again, I open the network management applet. The network type is WPA2-PEAP. So I go to network manager and go to WPA-EAP. I have tried to set it up there, including downloading the CA certificate.

I know I haven't posted much specifics, but I'm not sure if I'm going about this the right way or whether this is even supported in the GUI. I have googled this and looked at a dozen different forum threads, but they either aren't recent (not 9.04) or they discuss how to do it from the command line. I will consider that option next but this really (in my opinion) should be doable from the GUI. So, is it, and if so, how? thanks for help.

---

### Post by version7x on 2009-05-01
I'll give the pptp a stab but I'm using gnome, so YMMV...

I've got the following packages installed....

```
dpkg --get-selections|grep -i pptp
network-manager-pptp				install
pptp-linux					install

```

When I go to NetworkManager and select Configure VPN.  I then click add.  At that point, I get the option for Point to Point Tunneling Protocol.

If you're not seeing that, I'm not sure.  I used the wiki page to configure mine...

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

Also, once I was able to see the pptp option I had to click on the advanced button and select point to point encryption.



As far as your Wireless is concerned, I'm very poor at troubleshooting that.  I've got to play around with mine before it works.  I had to go to our network team and pull up the gui and ask which of the options they'd configured (we've got a weird setup).

Not sure... maybe some details might kickstart my swiss cheese brain.

---

