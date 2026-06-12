---
title: "Server in internal network needs gateway"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by Netzt on 2011-10-20
Hi.

I'm trying to solve the following config problem.

I Ubuntu-Server is running and provides services (website, downloads) for an internal network. This server need access to the internet to send emails and get updates.

To the internet it goes by static ip and gateway, without any login-process, on eth0.
In the internal network the server has an static ip on eth1.
So fare no problem.

But internal network is divided in different VLANs which are routed, so that I need to have a "second gateway".

I solved the problem half a year ago by some simple lines in the /etc/network/interface, but I can't remember what I did or where I found the solution.

Is the problem understandable described? (Sorry for my English)
How to change my config?

Thanks a lot!

---

### Post by waltsullivan on 2011-10-20
Read "man ifconfig". It says, in part:
[INDENT]If your kernel supports alias interfaces, you can specify them with eth0:0 for the first alias of eth0. You can use them to assign a second address.
[/INDENT]

---

### Post by Netzt on 2011-10-20
> **waltsullivan said:**
> Read "man ifconfig". It says, in part:[INDENT]If your kernel supports alias interfaces, you can specify them with eth0:0 for the first alias of eth0. You can use them to assign a second address.
[/INDENT]
Thanks, but I got two NICs, so its no problem to have two addresses, the gateway is the problem or do I just don't I get your hint?

---

### Post by Netzt on 2011-10-21
I read a lot, the tip didn't work at all.

---

### Post by Netzt on 2011-11-22
I found the solution, but another problem came on.

The solution following this manual [http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)
I 

Now there is "1 admin" in /etc/iproute2/rt_tables/rt_tabels

and the ist a file called /etc/iproute2/rt_tables/rt_tabels.save where some of the routes are saved.

Why are not alle routes saved the and where are they saved. I'd like to be able to save the routes somewhere where they will still exist after a reboot.

Thanks for help.

---

