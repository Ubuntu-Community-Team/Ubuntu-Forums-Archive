---
title: "Odd wireless problem with Ubuntu 10"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by fidgaf on 2010-09-18
I have just installed a squeaky-clean new version of Ubuntu 10.04.1 on a fresh, empty hard drive. No adjustments have been done.

I have a Livebox-1808 for my sins and the wireless adapter (Instantly detected) found the signal. Ubuntu would not connect directly (defaults to WAP I think) so I had to do a manual install (Activate pairing, enter WEP key). Very quick and no problems.

It shows the connection at 100% and all seems to be functioning correctly but nothing else will use the connection.

Firefox and Update seem unaware that there is a valid, working Internet connection (or is there?).

This is the only changes I've made to an otherwise virgin install.

Any suggestions?


.

---

### Post by John Petley on 2010-11-20
Hi

I seem to have the same problem with 10.4. did you get anywhere with this?

John

---

### Post by uncaspi on 2010-11-20
Can you ping your router and google.com

---

### Post by fidgaf on 2010-11-21
> **John Petley said:**
> Hi

I seem to have the same problem with 10.4. did you get anywhere with this?

John

I got nowhere and haven't used Ubuntu since the post above (September).

@uncaspi, Ping returns nothing - so it's saying it's connected but obviously isn't. 

Naughty Ubuntu. :D

---

### Post by uncaspi on 2010-11-21
Do you have route to your router?
sudu /sbin/route -n

---

### Post by fidgaf on 2010-12-24
> **uncaspi said:**
> Do you have route to your router?
sudu /sbin/route -n

I have no idea what this means. I get a response when I type that in but it means nothing.

There are two IP addresses under "Destination" if that helps.

---

### Post by grahammechanical on 2010-12-24
If Network Manager is showing available wireless networks then, your wireless adapter is recognized and working. You are connected to something, the router/modem, but is the router/modem connected to an ISP? Check the LEDs on the modem.

regards.

---

### Post by fidgaf on 2010-12-24
> **grahammechanical said:**
> If Network Manager is showing available wireless networks then, your wireless adapter is recognized and working. You are connected to something, the router/modem, but is the router/modem connected to an ISP? Check the LEDs on the modem.

regards.

Yes it is connected - Other PCs are using it (like this one I'm typing on).

---

### Post by grahammechanical on 2010-12-24
Perhaps we should start at the beginning because I am confused about what is going wrong. Left click the network icon. Select your wireless connection from the list of available wireless connections and tell us what happens. How about trying that? Please.

Regards.

---

