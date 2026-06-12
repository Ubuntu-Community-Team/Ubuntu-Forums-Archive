---
title: "Losing/refusing ssh/network connections after inactivity period"
date: 2005-01-11
forum: Networking &amp; Wireless
---

### Post by praveen on 2005-01-11
I installed warty and upgraded to hoary 1-2 days back. 

After 3-5 minutes of inactivity, any ssh connection gets closed and I cannot open a new connection. I get a connection refused from ssh. I saw this while running warty too. I cannot open connections to any other port either. But pinging the IP works... 

This machine was previously running sid and it was using the same network driver (e1000). Is there an option that I am missing? 

I tried fiddling with my BIOS settings... powersave settings were an S1 and S3 on this Dell Optiplex 270. I am not sure what these settings are, but the original was S1 and I changed it to S3 to no effect (only those two were available.)

Not sure what else I must tweak. Any suggestions?

---

### Post by praveen on 2005-01-14
[QUOTE=praveen]I installed warty and upgraded to hoary 1-2 days back. 

After 3-5 minutes of inactivity, any ssh connection gets closed and I cannot open a new connection. I get a connection refused from ssh. I saw this while running warty too. I cannot open connections to any other port either. But pinging the IP works... 

This machine was previously running sid and it was using the same network driver (e1000). Is there an option that I am missing? 

I tried fiddling with my BIOS settings... powersave settings were an S1 and S3 on this Dell Optiplex 270. I am not sure what these settings are, but the original was S1 and I changed it to S3 to no effect (only those two were available.)

Not sure what else I must tweak. Any suggestions?[/QUOTE]

I would really appreciate if someone gave me a suggestion as to what may be wrong here. 

- I am thinking it is not ACPI because I can connect to the machine after hours of inactivity, but get disconnected within a minute. After that I cannot connect (connection refused). 

- I fiddled with the BIOS power settings trying both powersave combinations (S1 and S3) with similar results. 

- sshd config has keepalive explicitly set to "yes"


What else could be causing this? Nothing apparent in /var/log/syslog /var/log/messages.

---

