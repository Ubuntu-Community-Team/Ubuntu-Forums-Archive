---
title: "VNC over SSH"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by irishetalon007 on 2012-06-20
Greetings!

I'm new(er) to SSH. I've got a working set of client and server. However, if I do a "sudo reboot" on the remote pc, then when i log back in, I'm unable to connect to the VNC server. 

In other words, is there any way to force a specific user to logon as if they're on the remote machine so that the VNC server will start?

Many thanks!

---

### Post by irishetalon007 on 2012-06-27
Bump?

---

### Post by steeldriver on 2012-06-27
Hi I'm not quite sure what you're asking - how are you configuring / running the VNC server? are you SSH-tunneling the VNC connection?

AFAIK there are several ways of doing this kind of thing, please bear in mind the security aspects especially if the remote machine is exposed to a public network:

1. you can connect via SSH and then start VNC on a per-session basis and then start your VNC client and connect back

2. you can leave the VNC server running in 'forever' mode as a regular user - this is the setup used in Mythbuntu where the primary Mythbuntu user is pretty much always logged in

3. you can start the VNC server in forever mode as root on session-startup as described here:

 [http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

which allows you to log in remotely at the regular greeter screen - I use this for a headless box on my home LAN

Hope this points you in the right direction

---

### Post by asmoore82 on 2012-06-27
You might want to check out the VNC setup in my signature.

---

### Post by irishetalon007 on 2012-06-27
Thanks guys!
One question: what does "headless" mean?

---

### Post by mwclark4453 on 2012-06-27
Your computer doesn't have a screen (or keyboard and mouse usually as well).  You have to access it from a remote computer via SSH or VNC (or both).

---

### Post by irishetalon007 on 2012-06-27
Great! THanks to both of you. 

Steeldriver - all options that you gave are appealing to me. Do you have access to tutorials for each?

---

