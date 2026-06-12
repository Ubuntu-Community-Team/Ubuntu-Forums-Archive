---
title: "Router not working..."
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by glad. on 2010-07-06
Hey all,
For starters, I am pretty inexperienced with linux/command line/etc. Learning, but pretty slowly.

As for my problem--my new router isn't working at all.
Right now this computer is connected directly to the modem, so the modem is definitely working (it's also quite new). When I try to hook things up to the router, however, nothing works.
What I do is connect this computer to the router via wire, and all the other computers connect to the router by wireless. 
What's odd is that the other computers *can* get the wireless signal. I.e. if I named my connection JohnSmith, they can all connect to JohnSmith 100%. It's just, they don't get any internet, and neither does this computer (connected by wire to the router).

I have no idea why that would be. 
All I've done is plug in the router and go to 192.168.1.1 and change the username/password etc.

One oddity is that, going to 192.168.1.1, and going to Administration--Management--trying to change the router password that appears there: I can't. I can erase it, type in my desired password, and then hit save, but then the screen reappears after having been "saved" with the old password. But I can change the password to connect to the wireless.

My router is a Linksys E1000

Thanks for your help.

---

### Post by pedro_orange on 2010-07-06
Are you sure your modem is actually connecting to the Internet? I presume you have an ADSL / ADSL+ connection? You usually need to give the modem a username / password combo and a DNS server so that you can dial up and establish a broadband connection. 

You usually set this up in the configuration pages (The web page you login into)

The router itself should be fine. From the PCs (Wired or wireless) you should be able to ping it's IP address. (Hopefully all the clients are DHCP)
They should also be able to ping each other.

The wireless password (i.e the WPA/WEP key) will presumably be under the Wireless/WAN settings.

NB: I do not own an E1000, I am just saying how most router/modems are set up from my experience.

---

### Post by glad. on 2010-07-06
> **pedro_orange said:**
> Are you sure your modem is actually connecting to the Internet? I presume you have an ADSL / ADSL+ connection? You usually need to give the modem a username / password combo and a DNS server so that you can dial up and establish a broadband connection. 

You usually set this up in the configuration pages (The web page you login into)

The router itself should be fine. From the PCs (Wired or wireless) you should be able to ping it's IP address. (Hopefully all the clients are DHCP)
They should also be able to ping each other.

The wireless password (i.e the WPA/WEP key) will presumably be under the Wireless/WAN settings.

NB: I do not own an E1000, I am just saying how most router/modems are set up from my experience.
Sorry, I should have said that it's a cable modem.

And I haven't been given any kind of page to log into to set up a username or password or anything (is that just an ADSL thing?) 

It does seem like the router is fine, and the problem lies with the modem somehow.

---

### Post by pricetech on 2010-07-06
Reboot your modem.

Cable modems "marry" themselves to a specific MAC address until rebooted.  Everything is functioning, it's just that the modem won't talk to the new MAC address.

Leave the router on while the modem is rebooted.  Once all the lights on the modem come on normally, you might have to reboot the router for it to pick up an IP.

---

