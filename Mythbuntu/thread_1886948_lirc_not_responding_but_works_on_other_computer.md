---
title: "lirc not responding but works on other computer"
date: 2011-11-25
forum: Mythbuntu
---

### Post by zeltak on 2011-11-25
hi guys

i have a weird issue

i installed mythubuntu and all works well exept the streamzap remote...sometimes it works after a reboot and sometimes in doesnt..

when i issue irw i get no response (the light on the reciver does light up). im an arch user and if i move the reciever over to arch it works like a charm everytime

the thing is that onve every 3-4 reboots it suddenly comes to life..

where can i check whats going on? 

thx 

Zeltak

---

### Post by klc5555 on 2011-11-26
Sounds like either the hardware is not being properly initialized before the lirc daemon is starting up, or the lirc daemon itself is not starting. On distros with an unhealthy emphasis on booting quickly, startup timing becomes a problem.

Can you (from a prompt) bring lirc to life with sudo killall lircd followed by sudo lircd ? (Or sudo lircd -n  which will keep lirc in the foreground of the terminal, so you can see any errors).

If this simple test doesn't do it, you need to check the logs under /var/log: syslog (after a boot), and/or lircd (if your lirc installation includes this log) for clues as to what's going wrong.

---

