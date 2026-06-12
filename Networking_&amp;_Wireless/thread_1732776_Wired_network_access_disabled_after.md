---
title: "Wired network access disabled after"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by agentsmith.android on 2011-04-18
I am working on ubuntu 10.10 in a VM. I went ahead and did updated the system when prompted. That has disabled my wired network connection. I am not sure what is the reason. If it is a device driver or any network service. I guess device driver is not an issue as I can detect my network card from ubuntu. 
Does any one know the solution?

---

### Post by klr on 2011-04-18
I've had the same problem over the last couple of days (I cannot remember any specific update but there was one around that time):

[http://ubuntuforums.org/showthread.php?t=1732570](http://ubuntuforums.org/showthread.php?t=1732570)

klr.

---

### Post by agentsmith.android on 2011-04-18
mii-tool does not work for me. Without any connection, I can't get ethtool:(
Is there any other way to revert to prev settings. (I am not sure if mii-tool can revert to settings before updates.)

---

### Post by klr on 2011-04-18
Afraid that's the cutting edge of my linux networking knowledge. Note you absolutely must sudo the command and that it's -R and not -r.

klr.

---

### Post by agentsmith.android on 2011-04-18
I had used sudo with -R. I guess I need to do reinstallation. :(

---

### Post by agentsmith.android on 2011-04-18
I found a solution. Check this port: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

I don't know why any network update configures interface in a loopback mode. Please,enlighten me why something like this is done :(. Why setting for interface can be kept constant.

---

