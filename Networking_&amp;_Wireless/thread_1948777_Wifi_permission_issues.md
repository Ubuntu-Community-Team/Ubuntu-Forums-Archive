---
title: "Wifi permission issues"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by Speedwagon on 2012-03-28
My System76 netbook has been having an issue with wifi permissions.  The computer is being loaned to my sister, and I created an account for her.  The account is a standard user account, that does not have change permissions.  Without any discernable reason, the wifi won't connect to the network at random times. Ubuntu 11.10 running, it gives the following error:

[IMG]https://lh5.googleusercontent.com/-Npwq8vSXA1E/T3O3YFLJgKI/AAAAAAAAAqQ/EpK2Ed7TMLc/s640/Screenshot%2520at%25202012-03-13%252018%253A04%253A57.png[/IMG]

---

### Post by Paddy Landau on 2012-03-29
By default, a new user does not have permission to connect to wireless and Ethernet networks.

Also by default, new wireless connections are not made available to all users on the computer.

I suggest:

[LIST=1]
[*]In the Users and Groups application, set your sister's account's permissions to allow to connect to wireless and Ethernet networks.
[*]In your own (Administrator) account, edit the settings for the wireless network in question and tick the box, "Available to all users". This will automatically make it available to your sister, who should no longer be bothered with authentication requests.
[/LIST]

---

### Post by Speedwagon on 2012-03-29
Well that's the thing, the permissions are set to allow all users.  Most of the time, she can connect just fine.  It's only on occasion that this happens.

However, I will go in and do as you say, unselecting and reselecting as needed.

---

### Post by Paddy Landau on 2012-03-29
> **Speedwagon said:**
> Well that's the thing, the permissions are set to allow all users.  Most of the time, she can connect just fine.  It's only on occasion that this happens.

However, I will go in and do as you say, unselecting and reselecting as needed.
Let us know if it makes any difference.

I wonder if the computer is perhaps disconnecting occasionally (poor reception?) and attempting to connect to a different wireless point?

---

### Post by Speedwagon on 2012-03-29
> **Paddy Landau said:**
> Let us know if it makes any difference.

I wonder if the computer is perhaps disconnecting occasionally (poor reception?) and attempting to connect to a different wireless point?

Hard to say, as it hasn't done it in my presence.  That's why I had her get a screen shot.  She is not command line inclined, so remote diagnosis is difficult.  But, it **shouldn't** be doing that, since the wireless is in the same apartment as the computer.

---

### Post by Speedwagon on 2012-04-01
Talked to my sister today, and it is still having the issue.  Any more ideas?  If I can get it do it for me, are there any commands I can run to isolate the issue at hand?

---

### Post by Paddy Landau on 2012-04-01
I'm sorry, at this point I am stumped.

Next time you visit your sister, see if she can tell you exactly where she is and what she is doing when it happens. Watch the wireless receptivity quality at that time. With luck, some pattern will emerge.

---

