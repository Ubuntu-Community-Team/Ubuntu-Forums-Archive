---
title: "Hardy, IBEX etc. Wired LAN problems."
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by pgmer6809 on 2009-04-02
When I tried the live CD of Hardy and IBEX on my computers I could not get the wired LAN to work. Since that time, I have been doing some investigation.
Here is a summary of the results so far.
-----------------------------------------
From what I can see they did a major re-write of some of the ifconfig code around kernel 2.26 or so. The results for many wired LAN chips are that assigning an IP address to the ethernet interface is no longer possible.

]I have several computers with different flavors of wired LAN cards/chips.
With kernel 2.22 (Ubuntu Gutsy) I did not have any problems.
With kernels 2.26 and 2.27 I have verified the following problem.

On some of the LAN cards/chips the link will come up, but an IP address cannot be assigned.
This is true whether the assignment is via DHCP or via a manual ifconfig cmd from a terminal session.

For example
ifconfig eth0 add 192.168.2.112
reports: SIOCSIFADDR no buffer space available.

ifconfig eth0 192.168.2.112 netmask 255.255.255.0
reports one or both of the following error messages:
SIOCSIFADDR no buffer space available.
SIOCSIFNETMASK cannot assign requested address

dhclient eth0 reports:  send_packet message too long.
as well as the SIOCSIFADDR error message.

I have verified this behaviour with various distros, Ubuntu Ibex, Fedora 10, Felicia Mint, and Mandriva 2008.

From my limited bug tracing ability it looks like the module devinet.c is the one printing the error messages, but I do not have the expertise to figure out why.

Here are the various LAN chips that I tested, the driver they use with the 2.26 and later kernels and the results:

MFG    LAN-CHIP    Driver      VERS        Result.
VIA    RHine-II    via-rhine    1.4.3      OK
SMC    AMTEK-NC100 tulip        1.1.15     OK
3Com   3c905       3c59x                   OK
Intel  3945ABG     ipw3845      1.2.2mp    OK (wireless)
Intel  Pro/100VE   e100       3.5.17-k4-NAPI ERRORs/FAIL
Marvel  Yukon      skge       1.11         ERRORS / FAIL
Realtek RTL811/81688 r8169    2.2LK        ERRORS / FAIL
Realtek RTL8139    8139too   0.9.28        OK

It looks like the more recent chips have the problem, but the older ones do not.
I wonder if a work around would be to use NDISWRAPER and the windows driver for the chips that don't work?
pgmer6809

---

### Post by bgerlich on 2009-04-02
There seems to be a bug either in the kernel (patched versions[here](http://tjworld.net/ubuntu/bugs/lp284377/)) or in the Network Manager that causes this. Try either installing the patched kernel or better yet disable NM and try ifconfig before installing the new kernel -maybe you can avoid it.

---

### Post by pgmer6809 on 2009-04-03
> **bgerlich said:**
> There seems to be a bug either in the kernel (patched versions[here](http://tjworld.net/ubuntu/bugs/lp284377/)) or in the Network Manager that causes this. Try either installing the patched kernel or better yet disable NM and try ifconfig before installing the new kernel -maybe you can avoid it.

The problem is definitely NOT in Network Manager. Network Manager works fine.
It even detects that the (non-working) link is up (which it is). The problem is definitely in ifconfig.c cmd (who is responsible for getting an IP address assigned), which calls devinet.c which calls ??? gets some sort of return and then reports the error.

I am not sure how to patch a kernel or to install a patched kernel. 
I don't know what portion of a kernel would work with some LAN drivers (older ones) and not others (newer ones).
pgmer6809

---

### Post by pgmer6809 on 2009-04-03
> **pgmer6809 said:**
> The problem is definitely NOT in Network Manager. Network Manager works fine.
It even detects that the (non-working) link is up (which it is). The problem is definitely in ifconfig.c cmd (who is responsible for getting an IP address assigned), which calls devinet.c which calls ??? gets some sort of return and then reports the error.

I am not sure how to patch a kernel or to install a patched kernel. 
I don't know what portion of a kernel would work with some LAN drivers (older ones) and not others (newer ones).
pgmer6809

Thanks very much for the link.
Just from scanning the text of the patches it looks like that would address the problem.
I note that the patched kernel provided at your links is a 2.28 version.

Question 1. Will Ubuntu be providing updated kernel images for Ibex and Hardy?
Question 2.
If the answer to 1 is "Not soon" then I presume I need to DL the text of the patch, apply it to the devinet.c module (and also figure out how to patch the kernel headers file?) and recompile the whole kernel?
Any hints on how to do that? (I have obviously DL'ed the kernel source already.
Thanks,
pgmer6809

---

