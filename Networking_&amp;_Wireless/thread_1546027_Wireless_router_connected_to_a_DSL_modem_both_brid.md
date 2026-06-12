---
title: "Wireless router connected to a DSL modem both bridged to a secure university network"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by jbartl on 2010-08-04
I have a very unique problem.  I am a college student living in campus housing.  I have a wireless router connected to a DSL modem which is connected to a secure university network via a phone line (very strange way of allowing students to connect to the internet).  The wireless router and DSL modem are both setup as bridges.   Once connected to the network, students are required to log in to SafeConnect.
  I am running windows and Ubuntu on a dell inspiron, and UNR on a Dell netbook.  I have had no trouble with the windows machine, and no problems logging in with the netbook elsewhere on campus, but when I try to connect to the network over the wireless DSL combo, the network manager says I am connected, but firefox loads the page forever (no page displayed, and no page load error).  I can’t even load the safeconnect page.
  I have tried various things that I have found online, but I have had no success .  I have also tried editing network manager, but I don’t fully understand what I am doing.  I have also tried attaching the computer directly to the DSL modem, and the same thing happens (also same thing happens with the dell inspiron).
  Network services on campus says that it sounds like ubuntu is blocking a certain package being sent to it (which is what I hypothesized as well), but that doesn’t explain how I am able to connect elsewhere on campus.  Also even if ubuntu is blocking a certain package, I have no knowledge about what that package is, or how to allow it.  I am not trying to go through a proxy server nor do I have any firewalls.
 
 
  I have almost exhausted all sources of help.    The university’s view on linux is if you are using it you probably know what you are doing (real big help they are)
Any help you can provide is greatly appreciated.

---

### Post by jbartl on 2010-08-22
Does anyone have any ideas? ](*,)

---

### Post by jbartl on 2010-08-23
Let me simplify since the paragraph above is so long

UNR+Wireless Router+DSL Modem+Bridged Network+Campus Security= ](*,)

I've narrowed down the problem to ubuntu since (1) Windows can connect to the network and work with the router (2) I've tried using wine to use a windows version of firefox.

Is there anything special that needs to be done with ubuntu for bridged networks?  I will continue trying on my own.

---

### Post by jbartl on 2010-10-06
Found a possible problem.  The modem is a zoom X5 router which only works with certain operating systems.  Here is the manual:

[http://www.zoom.com/documentation/adsl/5554_UsersManual_EngRevB.pdf](http://www.zoom.com/documentation/adsl/5554_UsersManual_EngRevB.pdf)

In appendix D (page 49) it talks about how to set up unix and linux network managers to work with the modem.  However, the only linux distributions listed are Debian, Suse, and Red Hat.  I am going to see if the network manager in Ubuntu can be edited to meet the same requirements.

---

