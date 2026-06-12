---
title: "Router acting up?"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by bluevoodoo1 on 2006-02-23
All of the sudden I lost my internet connection last night. No worries, I figured it was due to the internet company. Woke up today, STILL not on. Lights on the modem were on, router lights on too. After a shutdown and unplug, then plug in modem/router it got back online. I'm very curious to know... with the internet working perfectly last night, then stopping, what would be a reason for this "router reboot?"

---

### Post by dbott67 on 2006-02-23
A couple of questions:

1. Are you on cable or DSL?
2. Is it a D-Link or Linksys router (or similar)?

If you have a DSL connection, it's possible that your PPPoE connection is 'disconnected'.   Try logging in to your router and going to the status/connection page to see if your router has established a PPPoE connection to your ISP.  If not, the status will say "disconnected" and there should be a "connect" button.

If you have cable, the connection to your isp should be automatic (DHCP) in most cases.  Make sure that the status indicates that your router obtained an IP address from the cable provider.

-Dave

---

### Post by bluevoodoo1 on 2006-02-23
Thanks for your quick reply!!! 

1. Cable
2. Netgear router

It's set to obtain IP from ISP. I'm on the computer now, and it's working fine (after all the unplugging and plugging). Do you have any ideas what would cause that sort of interruption I had last night that would require the unplugging/plugging, or am I just being paranoid????

---

### Post by dbott67 on 2006-02-23
Routers are just little dedicated computer appliances running some sort of *nix variant.  Like all computers & operating systems, they can occasionally freeze or lock-up.  A reboot will generally cure the problem.

Sometimes the problem is not related to your router; it may be the cable modem, the ISP or some other problem.  I generally recommend  the following:

1. Ping other 'known working devices' on your network (i.e. another computer, printer, etc.)
2. Ping the router (normally something like 192.168.1.1)
3. Ping a known popular website (google.com, msn.com, etc.)

Using the above techniques, you can determine where the problem lies (or at least where to start looking for problems).  Not being able to ping the router or another known working device might indicate a problem with the cable or NIC in the computer, etc.

After isolating where the problem might be, and assuming that you can ping local resources but not internet resources, try the following:

1. Try logging into the router & verify connection status
2. Reset or re-boot the router (cycle power, etc.)
3. Reset cable/DSL modem (again, just cycling the power may do the trick)
4. Call your ISP to verify if they are experiencing any outages.

If they are not having any problems, then you may want to take the next step.  Before beginning, I would recommend that you always keep a hard copy of your ISP settings handy so that you can re-enter them into the router:

1. Update the router's firmware.  Sometimes the ISP ipdates their hardware and it creates issues downstream to their clients.  Many router manufacturers regularly update the firmware to fix bugs and other issues that arise.
2. If your firmware is already up-to-date, just try re-entering your settings into the router.  I have personnally experienced a corruption of my PPPoE user account settings in an older Linksys router that I used to have.  Re-entering the settings cured it.

Hope this helps.

-Dave

---

### Post by bluevoodoo1 on 2006-02-23
Wow, thank you very much!! I will keep all of that in mind for any future problems!

---

### Post by dbott67 on 2006-02-23
You're welcome.  btw, nice BB guide.

---

### Post by bluevoodoo1 on 2006-02-23
[QUOTE=dbott67]You're welcome.  btw, nice BB guide.[/QUOTE]

Thank you! :D

---

