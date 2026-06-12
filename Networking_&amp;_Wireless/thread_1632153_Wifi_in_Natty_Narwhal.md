---
title: "Wifi in Natty Narwhal?"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by flibs69 on 2010-11-27
Anyone know if the 10.10 sucky wifi is being addressed in 11.04 Natty Narwhal?

I am in the process of downloading the daily build of it to see if it's improved at all, but it's taking its time (doesn't help that it's oversized...)

---

### Post by kerry_s on 2010-11-27
:lolflag:

as far as i know, wifi is fine in 10.10 for most people, i have no problems.

maybe you should define "sucky", file a bug report, you can do something. just saying it sucks & hoping someone will fix it is going to leave you waiting for nothing.

---

### Post by chili555 on 2010-11-27
> **kerry_s said:**
> :lolflag:

as far as i know, wifi is fine in 10.10 for most people, i have no problems.

maybe you should define "sucky", file a bug report, you can do something. just saying it sucks & hoping someone will fix it is going to leave you waiting for nothing.+1000

It's fine for me on two laptops.

---

### Post by flibs69 on 2010-11-27
Well, I have had major problems on a netbook (RTL8187SE) and with a desktop with Netgear WN111v2 USB (same problem with both), and the "sucky" was just quoting someone else from the thread where I was trying to get to the bottom of those problems where they said that wifi was broken in 10.10 and to drop back to 10.04.  (Both have been almost cured by using NDIS drivers, though not completely).  Original thread was [http://ubuntuforums.org/showthread.php?t=1618500](http://ubuntuforums.org/showthread.php?t=1618500)

---

### Post by flibs69 on 2010-11-28
I just tried installing Natty using update-manager -d and it failed miserably.  The update happened ok, but then I had (to begin with) no wifi at all, and then after removing the ndis drivers and using the ubuntu ones, no X windows at all.  So I still don't know if natty will work better than maverick with my wifi...

---

### Post by charles-wolfman on 2011-04-30
i had wifi in 10.10, and now 11.04 has screwed it up.

yay

---

### Post by peskadot on 2011-05-17
I have same problem as Wolfman.  Connectivity was good with 10.10 but extremely slow with 11.04.  Worse than with VISTA, and Ubuntu should consider that an insult.  Any suggested solutions??

---

### Post by HellesAngel on 2011-07-16
> **chili555 said:**
> +1000
It's fine for me on two laptops.
That's not a very high benchmark for software testing, nor useful information for those with no connection.  Credit where it's due- this is the first & only Linux release I've seen that supports WPA2 on this old Orinoco hardware, but 11.04 Natty Narwhal's NetworkMangler still seems to be buggy as hell for wireless connections.

On this laptop it takes some 20 minutes and repeated attempts to make a connection, but once the connection is made it is pretty reliable.  I suspect this is a symptom of the DHCP problems others have mentioned on other threads, but I have also frequently observed iwconfig reporting the NetworkMangler trying to connect to the wrong WLAN.  There is absolutely no good reason for it to do this, it must be a bug which I'll continue to research.

Assigning a static IP address should help the first problem but trying to establish a wireless connection to the wrong ESSID is just a waste of time.

---

