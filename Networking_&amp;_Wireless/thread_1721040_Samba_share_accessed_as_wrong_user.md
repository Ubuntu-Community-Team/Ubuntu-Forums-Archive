---
title: "Samba share accessed as wrong user"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by tbridges42 on 2011-04-04
I've had a Samba share set up for awhile now on my Ubuntu 10.04 server. Now I'm trying to create separate shares for separate users. When I started, I was logging in from my Windows box where I was Tony, and the only user on my 'nix box was htpc. I had the majority of my file permissions as open.

Now, I've created new users on the server, including Tony. But when I open a Samba share from my Windows computer, it does so as htpc. This is not a setting I ever put anywhere. I don't care about specific user names, but I want to have a folder that only I can access from my Windows box, and for someone else to have a folder only they can access from their Windows box.

Any ideas?

---

### Post by tbridges42 on 2011-04-05
It turned out to be a Windows certificate issue. I solved that, but now all my shares are read-only and I can't figure out why.

---

### Post by pricetech on 2011-04-05
How did you set up your shares ??  The easiest way I've found is using:

System - Administration - Samba

If it's not there, install system-config-samba using Synaptic.

---

