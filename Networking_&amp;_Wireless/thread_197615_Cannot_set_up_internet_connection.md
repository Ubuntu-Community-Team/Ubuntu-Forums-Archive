---
title: "Cannot set up internet connection"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by necronomicon on 2006-06-16
I have just installed Xubuntu and simply cannot get my internet connection to work. Having set the ethernet card to DHCP and checked that 'pppoeconf' is installed, I ran the 'sudo pppoeconf' command to do the configuring of my account (I have an ADSL connection through a router).

The program does a check on the network cards and fails when 'Searching for PPPoE access concentrator'. I have restarted numerous times with no effect. How do you get this working? Where do I insert the username and password for my service provider so that I can set up the account?

The documentation is no help as I have followed it step-by-step. I really wish for an alternative to Windows but I am getting discouraged.

---

### Post by vuul on 2006-06-16
I think if you have your network like this:
DSL modem>router>xubuntu box
Then the router will be handling the PPPoE dialing.
Your Xubuntu box should be set for DHCP without PPPoE.
The router should give your computer an address something like:
192.168.XXX.XXX
You can check your IP by typing ```
ifconfig
``` at the terminal.
Also log into your router to see if it has a WAN IP address.

---

### Post by necronomicon on 2006-06-16
Sorry, as I wasn't very clear. I have an ADSL modem (Speedtouch) which connects to my network card, which is in the computer (for some reason, my ISP refers to the modem as a broadband router).

I know that it shouldn't be that difficult to set up (I actually do read instructions and originally set up my connect in Windows with no problems), but I have been trying since yesterday.

Do you have any other suggestions? Thanks for your previous reply.

---

### Post by vuul on 2006-06-16
The only other suggestion that I have is if you can't get Xubuntu to do the PPPoE dialing, then call your ISP and have them set your modem from bridge mode to router mode. Some of those Speedtouch modems are routers as well, and they have the option of working as a modem, or as a router.

---

