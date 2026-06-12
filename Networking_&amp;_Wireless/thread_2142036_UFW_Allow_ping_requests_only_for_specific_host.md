---
title: "UFW: Allow ping requests only for specific host"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by kamishi on 2013-05-04
I am setuping my server and I must disable the ping requests for everyone except me and a list of hosts (aaa.bbb.ccc.ddd).
  I am using the tool ufw, on ubuntu server, I read that I have to comment those lines:
  **[SIZE=2]ok icmp codes[/SIZE]**

  -A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT 
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT 
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT 
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT 
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT,

  

However, by doing that It will disallow everyone to ping, which is a  problem because I need "aaa.bbb.ccc.ddd" to have a response to its ping  requests.

  Can you help me to write the correct command? 
  Thank you a lot in advance.

---

### Post by Hadaka on 2013-05-04
Hi, read over this link for some info.
[https://smartertrack.webcontrolcenter.com/KB/a1570/cloud-vps-ubuntu-manage-firewall-rules-with-ufw.aspx](https://smartertrack.webcontrolcenter.com/KB/a1570/cloud-vps-ubuntu-manage-firewall-rules-with-ufw.aspx)
you should be able to allow by your aaa,bbb,ccc,ddd ip address's and deny the rest.

[FONT=courier new][FONT=tahoma][FONT=courier new][FONT=tahoma][FONT=courier new]-A ufw-before-input -s 111.222.3.44   <- ip address[/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by kamishi on 2013-05-11
Thank you ! I will try that :)

---

