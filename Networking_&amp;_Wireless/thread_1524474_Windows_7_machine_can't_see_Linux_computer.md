---
title: "Windows 7 machine can't see Linux computer"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by normh on 2010-07-05
Windows 7 computer can't see ubuntu 10.04 computer. Ubuntu machine can see and access rest of windows network including a linux enabled PVR. Tried various things to no avail.When setting up for shared folders I got a message that I needed to install shared services.  I did this but I only have one share through option: Unix networks (NFS).  The samba option, which I should be using is not available.  I tried to allow "Share files over the network" but had to install some extra service.  While "share files over the network" can and has been enabled, accessing the windows network has become painfully slow and my windows 7 machine still can't see the linux box

---

### Post by dmizer on 2010-07-05
Take a look at the "Windows 7 configuration" section in the 6th link in my sig.

While the post is geared to allowing Ubuntu to see Windows shares, the notes on Windows 7 will help things work in both directions.

---

### Post by amethyst igor on 2012-11-01
> **dmizer said:**
> Take a look at the "Windows 7 configuration" section in the 6th link in my sig.

While the post is geared to allowing Ubuntu to see Windows shares, the notes on Windows 7 will help things work in both directions.

I've read a lot of tutorials and messages while trying to get my Linux share to be accessible from Windows on the network, and yours (link #6) is the most helpful by far. The key was disabling the Firewall via the GUI--simple as that--and also removing references to WINS in /etc/sama/smb.conf because my Windows networks does not appear to use WINS but instead uses the DHCP settings on my router. I followed many of your instructions up to the one about the Linux firewall [UFW] and after disabling the firewall, that was that, I was able to access many shares. 

It is not apparent that the Firewall is active, because clicking on it, it appears to be off, but I realized it was active by looking at the file you mention in your link. It was stopping all attempts by the Windows PC to access the Linux computer. 

Thanks again, now I can finally get things done. :guitar:

---

