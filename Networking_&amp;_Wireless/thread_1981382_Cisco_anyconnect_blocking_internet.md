---
title: "Cisco anyconnect blocking internet"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by neelsonwheels on 2012-05-16
I'm stumped and want to see if someone can guide me...

The short is I'm 99% sure after installing the Anyconnect client (to connect to campus resources) I can now only connect to the internet with Anyconnect running. That is, if I disconnect from the client no internet whatsoever within Ubuntu 12.04 x64.

Has anyone heard of this? Google has failed me (or I'm not searching for the right thing). I can provide more info as needed...

thanks,
jason

---

### Post by neelsonwheels on 2012-05-18
Bump... anyone?

---

### Post by neelsonwheels on 2012-05-19
For anyone that is interested...

[LIST]
[*]I had gone this convoluted way to get the JRE installed to get the anyconnect client installed (didn't know about openconnect at the time)
[*]Got it up and running, and then noticed a few days later couldn't connect without going through anyconnect first
[*]Hulked out, tried some things which in the end resulted in completely removing JRE
[*]I could still get internet access through Anyconnect... WTH!!??
[*]In the midst of trying things I installed openconnect, uninstalled anyconnect, and got things running.
[*]Now I can only get internet through openconnect... will probably just reinstall at some point
[/LIST]

---

### Post by Group on 2012-05-19
[http://www.umtekoil.ru/forum/memberlist.php?mode=viewprofile&u=39908](http://www.umtekoil.ru/forum/memberlist.php?mode=viewprofile&u=39908)

---

### Post by Dreadslayer on 2012-09-30
Here's a link to the solution: [http://www.kubuntuforums.net/showthread.php?60287-Cisco-AnyConnect-blocks-internet-access](http://www.kubuntuforums.net/showthread.php?60287-Cisco-AnyConnect-blocks-internet-access)

I had the exact same issue and wasn't able to google it. So maybe from now on people don't have to create new topics regarding this issue.

---

### Post by galfly on 2013-03-12
Hi,

It depends where you're connecting to. If the  secure gateway is configured for "Always on" in trusted network detection settings, then your access will be restricted entirely when you're on some network that is not within the trusted list.

---

