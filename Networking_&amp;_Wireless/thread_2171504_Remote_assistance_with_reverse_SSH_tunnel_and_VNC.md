---
title: "Remote assistance with reverse SSH tunnel and VNC"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by vmalep on 2013-08-31
Hi everybody,

I would like to figure out how to establish a VNC connection through reverse SSH tunnel AND via a public server (and with host and guest behind firewall without NAT).

The network diagram would look like this:

Step 1 (working):
    [guest] --- SSH --- [firewall] ---> [public server] <--- [firewall] --- reverse SSH tunnel ---> [host]

Step 2 (not working):
    [guest] --- SSH[VNC viewer] ---> [public computer] <--- [VNC server]reverse SSH tunnel ---> [guest]

I found the very good tuto explaining how to setup the reverse SSH tunnel and it works fine (I can connect with SSH from the guest to the host).

I also found tuto explaining how to setup VNC through reverse SSH tunnel, but assuming that the guest had public IP address (or assuming the VNC viewer be on the public computer).

Also, I tried connecting from the guest to the public server with ssh -X, but to no avail.

This would be useful not only to assist running computer, but also to assist friends during their Ubuntu installation (or to do it remotely for them), once the Ubuntu Live is running.

Waiting for suggestions!!!

And thanks in advance!
Pierre

---

### Post by prodigy_ on 2013-08-31
Reverse SSH is based on port forwarding. To enable VNC you'll need to forward the VNC port as well.

But to be perfectly honest your scheme looks too complicated. Are you sure it cannot be simplified? OpenVPN with client-to-client option may be something to look into.

---

### Post by vmalep on 2013-08-31
Hi Prodigy,

Thanks for your reply. Your are probably right and I am also considering [VPN with PPTPD]("http://globalcynic.wordpress.com/2013/04/26/pptpd-ubuntu-12-04-vps-fail2ban/").

Still, I am am actually trying to replicate is the solution implemented by software like TeamViewer and now that we can rent dedicated server for 5$/month it would be a great added value for Ubuntu to offer an easy and powerful remote assistance and/or VPN solution (OpenVPN is good, but complicate to install and configure) with the distribution.

Best regards,
Pierre

---

### Post by prodigy_ on 2013-08-31
Actually OpenVPN is very easy and straightforward to configure (compared to L2TP for example). See HOWTO here: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

But for remote assistance I'd suggest using one of the already existing products. What's wrong with TeamViewer and why are you trying to reinvent it?

---

### Post by vmalep on 2013-08-31
Well, not very font of proprietary software. And I just gave a try to teamviewer, as you suggested. After having dealt with the 64 vs 32 arch, All what I got was the obligation to create an account...

I found this interesting discussion: [http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out](http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out)

But seems also complex... ;-)

---

### Post by vmalep on 2013-08-31
Another interesting link explaining how to use the public server as ssh relay:
[http://toic.org/blog/2009/reverse-ssh-port-forwarding/](http://toic.org/blog/2009/reverse-ssh-port-forwarding/)

---

### Post by vmalep on 2013-09-07
Hi,

Eventually, the easiest solution I found is the n2n software:
[http://www.ntop.org/products/n2n/](http://www.ntop.org/products/n2n/)

It is very easy to setup  a VPN (no actual configuration, just one a command line with a few arguments) and to ssh into the remote computer, but the share desktop (VNC) did not work well: I could connect, the the screen remained black and the mouse cursor was not functioning. Maybe a problem of speed...

BR
Pierre

---

