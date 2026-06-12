---
title: "Terminal Server Client issue - help!"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by juny20 on 2010-12-03
I am at a loss. I can not access my work remote desktop via the terminal server client on my wired box running Ubuntu 10.10. My wireless laptop is able to connect right away once I established the VPN connection. The VPN connection is established on both boxes with no problems. 

When I tried the Terminal Server Client on my wired boxed, it says it can not establish a connection. Yet my wireless box gets connected immediately!

I check the /etc/dhcp3/dhclient.conf and the /etc/resolv.conf to see if there were any differences, but they are essentially the same. When I have the vpnc connection, they both recognize it and I am able to ping the IP address shown when I do a "ifconfig" on the terminal.

What can be the problem? Anything I need to configure on a wired computer versus a wireless one? What else can I check?

---

### Post by juny20 on 2010-12-04
Just following up on my problem to see if anyone has any solution.
What about ports? Do I need to configure any ports? But then again, I can connect with no issues on my wireless laptop, but no on my wired desktop. So I am guessing ports are fine?

To me, it seems the issue is with the Terminal Server Client, but I can not determine what...Anyone experienced this issue?

---

### Post by Wicca on 2010-12-04
Hi there,

> **juny20 said:**
> When I have the vpnc connection, they both recognize it and I am able to ping the IP address shown when I do a "ifconfig" on the terminal.

That's OK, but that's just your local IP address you got from the VPN server. It doesn't proove that the tunnel is correctly working.
What about pinging the machine you want to connect to?

I don't think Terminal Server Client is the problem, but the way the VPN connection is set up. To me it seems that the vpn connection on your wired box has not a valid route.

---

### Post by juny20 on 2010-12-04
Thank you Wicca!You are 100% correct!
I just tried doing a ping to the computer and on my wired desktop, I received a "Operation not permitted" message.

However, on my wireless laptop, I was able to ping the computer, sent 11 packets, 11 received, and nothing loss!

So, you are right, it is the VPN setting.
How can I check to see what the differences are?
Any other test I can run to isolate the root cause?

Thanks for your input!!!

---

### Post by juny20 on 2010-12-04
Ok, I think this is solved now.

The issue was Firestarter. I do not know how to configure it to work with VPN, but I disabled it and I connected right away!

I read this articles:
[http://ubuntuforums.org/showthread.php?t=131249]("http://ubuntuforums.org/showthread.php?t=131249")

[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")

After reading this, I opted to disable the Firestarter at least when I am using VPN to connect to my work. At this point, it works and until I learn how to configure Firestarter to allow my connection, this is my solution.

Hope it helps anyone who is having a similar issue.

Thanks.

---

### Post by Wicca on 2010-12-04
Hmmm... "Operation not permitted" might indicate something else.

But first, check the route settings of the VPN connection on both machines.

In Network Manager, go to VPN connections --> Configure VPN, select the connection, go to Edit -> IPv4 Settings. Make sure all settings are equal on both machines, as set on your wireless box. Then click Routes... and again: all you see here should be equal on both boxes.

Let me know if that's the case.

EDIT: I see you already solved it. The firewall is something I would have mentioned in case your tunnel settings were OK.... Good you sorted it out!

---

### Post by juny20 on 2010-12-04
Thanks for your help Wicca!

---

### Post by Wicca on 2010-12-04
You are welcome ;)

---

