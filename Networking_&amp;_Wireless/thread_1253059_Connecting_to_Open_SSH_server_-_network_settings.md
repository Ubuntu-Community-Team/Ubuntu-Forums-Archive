---
title: "Connecting to Open SSH server - network settings?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by blackandwhitepandabear on 2009-08-29
Hi, I am using Ubuntu Hardy Heron. I had my desktop ssh server on a wireless network and I used to be able to connect to it via ssh (I think roaming mode was enabled then?). I switched to a wired network about a month ago (DHCP), and it also could connect to it via ssh. Now, when I go back to the wireless connection I can no longer connect to it by ssh. My wireless device is ath0 so I have changed my network settings through Firestarter (turning it off the firewall does not solve the problem) and the Network Settings tool. Some observations when using the wireless card:
- I can view webpages on the internet.
- 'ssh user@localhost' and 'ssh user@ipaddress' both work on my Ubuntu machine but (the latter) does not work from a remote machine. 
- I can still connect to the machine via ssh if I use the wired network connection.
- After switching to wireless I tried 'sudo /etc/init.d/networking restart', but to no avail.
I wonder if there is something obvious I am missing, or something else I can try?
Thanks much...!

---

