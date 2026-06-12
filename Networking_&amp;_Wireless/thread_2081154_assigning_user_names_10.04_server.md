---
title: "assigning user names 10.04 server"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-11-06
I have a new server at a school. We have a staff list, currently with 32 entries. There will also be a requirement to create student accounts which could number under 500. This process is complicated by the fact that local language is Thai, which I don't speak or read. I have created a samba file sharing system and need to pass out unique usernames and passwords, as well as set permissions for the various groups these users will be assigned to. I came up with the following: convert all group id's to 3 digit numbers which would be converted from default guid's (50 becomes 050, etc.), then since the staff list is already numbered and totals less than 1000, convert the numbers already on the staff list also to 3 digit numbers (1 becomes 001,etc.). Then a username would be generated combining the guid and uid (I would be 112031, for example), then a typical randomly generated 6 digit password is assigned to each user. Simple enough? OK, but when I attempted to use adduser to start the process, it rejected the username as not meeting name_regex standards. For my own sanity, I need to stick with the all numeric username format. Am I overthinking it? Should I just change the range of UID's? It appears that maybe I don't want a dynamic assignment(?). Suggestions appreciated.

---

