---
title: "weird issue with wireless authentication"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by filfish on 2009-04-23
We have a wireless network in work that is 

SSID = Work
Wireless Security = Dynamic Wep (802.1x)
Authentication  = Protected EAP
Anonymous Identity = 
CA certificate - work.cer
PEAP Fersion = Version 1
Inner Authentication = MSCHAPv2
Username = [email]filfish@anydomain.com[/email]
Password = mysecret

on my ubuntu 8.10 laptop my username is phil

When I click for it to connect it interrogates the servers, on our cisco box it shows that it is associated (certificate works) but for Authentication it shows No, I look at the radius box for login info and see a user denied for filfish@phil
It should show up as [email]filfish@anydomain.com[/email] but it seems to be passing the username entered along with the username of the local machine rather than the username @ domain name entered

Any suggestions?

The details above work correctly on a windows XP and Vista boxes but we can't get our Ubuntu boxes to authenticate.

Cheers

---

### Post by filfish on 2009-04-23
Ok, so we're getting somewhere, we've reinstalled network manager now it won't send any info to the authentication server using PEAP version 1, but it does send the correct username using PEAP version 0, I can see on the authentication server that the user name is recognised and resolves against the users common name with their OU etc so it recognises the user.

But it keeps failing with

Reason-Code = 16
Reason Authentication was not successful because an unknown user name or incorrect password was used.

Well, we know the username is correct as the authentication server resolves it to an OU and a user, so it's down to the password, we changed it to something really simple "passw0rd" and it still failed, we even waited for our servers to replicate.

I think it is sending the username ok but having issues sending the password in a format that is accepted.

Any ideas?

cheers

---

