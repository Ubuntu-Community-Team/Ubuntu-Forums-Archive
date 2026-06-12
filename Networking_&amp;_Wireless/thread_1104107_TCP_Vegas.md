---
title: "TCP Vegas"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by MountainDeux on 2009-03-23
I just started using Ubuntu server recently and am getting the hang of things. My first project here at work was to make a firewall. I have already installed ShoreWall but was really interested in using TCP Vegas. I read in a few places that it was included in many Kernels but I was unable to find anything in this latest release of server that has it.

So my question is, do I have to recompile the Kernel myself to include TCP Vegas or is there a Kernel available through apt-get that I can dowload that includes it?

Thanks!

---

### Post by jnihil on 2009-04-26
Try this:

# modprobe tcp_vegas

then see if it worked:

# cat /proc/sys/net/ipv4/tcp_available_congestion_control
cubic reno vegas

Now to change the algorithm:

# echo vegas > /proc/sys/net/ipv4/tcp_congestion_control

Check it via:

# cat /proc/sys/net/ipv4/tcp_congestion_control
vegas

---

### Post by WitchCraft on 2010-08-23
> **jnihil said:**
> Try this:

# modprobe tcp_vegas

then see if it worked:

# cat /proc/sys/net/ipv4/tcp_available_congestion_control
cubic reno vegas

Now to change the algorithm:

# echo vegas > /proc/sys/net/ipv4/tcp_congestion_control

Check it via:

# cat /proc/sys/net/ipv4/tcp_congestion_control
vegas

I've been looking for this, too.
Thank you!

---

