---
title: "IP_ADD_MEMBERSHIP Error"
date: 2009-11-01
forum: Mythbuntu
---

### Post by iitywygms on 2009-11-01
Hi

I am running ubuntu 9.04 with .22-fixes 22653
Lately I have noticed that the backend fails to start after a reboot. Not sure when this started happening.
The IP_Add_Membership error has me stumped.
I tried to do this with no results.

sudo route add -net 239.0.0.0/8 eth0

Any other suggestions?
Not really a big deal unless I get a power failure and am not at home. If I manually start the backend all is good.
Here is the relevant part of the backend log.

2009-10-30 18:46:35.987 Testing network connectivity to '192.168.2.4'
2009-10-30 18:46:36.121 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-10-30 18:46:36.211 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
2009-10-30 18:46:36.321 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
................................................................................
2009-10-30 18:46:38.444 UPnPautoconf() - No UPnP backends found
2009-10-30 18:46:38.789 No UPnP backends found
No UPnP backends found
Would you like to configure the database connection now? [no]
[console is not interactive, using default 'no']
2009-10-30 18:46:39.015 Deleting UPnP client...
2009-10-30 18:46:39.016 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-10-30 18:46:39.243 Failed to init MythContext, exiting.

Thanks for the help.

---

### Post by iitywygms on 2009-11-02
Anyone seen this before?

---

### Post by ian dobson on 2009-11-02
Hi,

Looks as if mythbakend is starting up before you network interface has an IP address. Does your mythbackend system have a fixed IP address or does it get the address by DHCP?

Maybe try starting mythbackend abit later in the boot process by changing the mythbackend startup script to include a delay or changing the number of the startup script (S55mythbackend -> S99mythbackend).

Regards
Ian Dobson

---

### Post by iitywygms on 2009-11-03
Hi Ian

My backend uses a static ip.

I would like to try the changes you suggested, but I am semi linux illiterate, can you please be a little more descriptive as to how to do this?

---

### Post by ian dobson on 2009-11-04
Hi,

When linux boots it looks in the /etc/rcX.d directory for all files starting with K or S and executes them based on the 2 digit number following the K or S. If the program starts with K then the program is called with the option stop. If the program starts with S then it is called with the option start. 

Note the X in the rcX.d is the runlevel that the system is running at (2-multiuser, no X).

So what you need to do is find where mythbackend is starting and increasing the number. On my main server mythtv starts at runlevel 2 as /etc/rc2.d/S24mythtv-backend. So in my case if I changed the 24 to 60 mythtv would start later in the boot process.

Another question, are you running X on your box (Graphical frontend) and how is your IP address configured? Are you using network-manager or is the IP address hardwired in /etc/network/interfaces?

Regards
Ian Dobson

---

### Post by iitywygms on 2009-11-04
Yes, I am running x. xfce
I configured the network using network-manager.  I right clicked on it and edited connections that way.

I will try to start mythbackend later and report the results.

---

### Post by iitywygms on 2009-11-04
I changed the startup as you suggested.
The backend started normally upon reboot.
THANK YOU!

Why are you asking if I am running x and about the network configuration?

---

### Post by ian dobson on 2009-11-04
> **iitywygms said:**
> I changed the startup as you suggested.
The backend started normally upon reboot.
THANK YOU!

Why are you asking if I am running x and about the network configuration?

Network manager is evil (if your running a server). The X window application network-manager can only set the IP address of your ethernet _**after**_ X is started. As mythtv-backend starts before X is running (if you have a low startup number) it cannot attach to the IP address defined and gives the error "IP_ADD_MEMBERSHIP".

For a normal desktop system Network manager is a "nice fluffy, warm, cosy" solution for network configuration but it can cause more problems than it's worth.

Regards
Ian Dobson

---

