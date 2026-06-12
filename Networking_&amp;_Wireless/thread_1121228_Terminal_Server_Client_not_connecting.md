---
title: "Terminal Server Client not connecting"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by nixIT on 2009-04-09
Hello all,

I have Ubuntu 8.10 installed on my laptop at work.   When I first installed it, I could connect to our Win 2000/2003 servers with Terminal Server Client.  However now when I connect, or should say *try* to connect with TSC, I get a message "Connection dropped (or refused can't remember which) by host".

I can connect to the same server with a windows box though.

Any ideas?

---

### Post by Cybie257 on 2009-04-09
Are you using RDP or VNC? Is there any delay before it crashes out with the connection error? 

Could be MTU settings. Let's start with the above first and I will go from there. I had similar issues in the past. It was related to MTU settings, which you can change via the Network Connections under the System->Preferences menu

-Cybie

---

### Post by nixIT on 2009-04-13
> **Cybie257 said:**
> Are you using RDP or VNC? Is there any delay before it crashes out with the connection error? 

Could be MTU settings. Let's start with the above first and I will go from there. I had similar issues in the past. It was related to MTU settings, which you can change via the Network Connections under the System->Preferences menu

-Cybie

Am using RDP.

MTU is currently set to automatic.

When I click Connect, the window goes away, and the windows that *should* be the server I want to admin flashes for a split second before it goes away and the error window comes up.

--nixIT

---

### Post by nixIT on 2009-04-16
> **Cybie257 said:**
> Are you using RDP or VNC? Is there any delay before it crashes out with the connection error? 

Could be MTU settings. Let's start with the above first and I will go from there. I had similar issues in the past. It was related to MTU settings, which you can change via the Network Connections under the System->Preferences menu

-Cybie

What did you change your MTU settings to?  Mine are currently set to automatic.

--nixIT

---

