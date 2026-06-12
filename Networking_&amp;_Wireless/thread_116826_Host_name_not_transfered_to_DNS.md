---
title: "Host name not transfered to DNS"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by linuxfroggy on 2006-01-13
I have a small issue and may be someone can help to let me understand. I use my Ubuntu box behind a linux based firewall (Ipcop) which also plays the role of DNS server. I can reach internet, that is to say external network, using firefox, evolution, ping... using hosts names but I can not use names for the internal network (I have another laptop running also Ubuntu). Looking at the Ipcop setup, the DHCP server is handling properly the IP address business but does not receive the name of the Ubuntu boxes. Plugging an XP box on the internal net, I found that the name was recieved by Ipcop. In another words, it seems that the Ubuntu boxes do not handle their names to the Ipcop router... Can someone light a candle on that ?

Best regards,

Linuxfroggy

[B]*******************************************
Problem solved
[/B]

Hello,

I have found the solution to this problem. It was quite simple in fact. Looking at DHCP client configuration file, it appears that Ubuntu is set up to not send any hostname information (security I suppose). Uncommenting the line 'send host-name "hostname" ' is necessary to let the client informing the DNS server of the hostname.

Thanks again for the advices.

Regards,

**************************************

---

### Post by Mr_Grieves on 2006-01-13
What do you mean with "but I can not use names for the internal network"?
You can't use the hostnames of you're computers on the Internal network?

If that's what you mean, you need to define them in a hostfile locally on each computer, if thier not in DNS.

In Ubuntu:
```

/etc/hosts

```

In XP:
```

x:\windows\system32\drivers\etc\hosts

```

Syntax for both should be

```

123.4.5.6 computername

```

---

### Post by linuxfroggy on 2006-01-14
Hello Mr Grieves,

Thanks for the reply.

Regarding your question, I mean that I can not use hostnames to ping the two Ubuntu boxes on the internal network. I agree I can use the /etc/hosts but it would mean static IP rather tha dynamic ones attributes by the DNS server which in my case is the IPCop firewall/router (it is a specialized Linux release based on SmoothWall).

What surprises me is that when I plug on the internal network a XP box, the hostname of that box is correctly transferred to the IPCop DNS server (the hosts and dynamic IP adresses list can be retrieved easily in IPCop). If I am not mistaken, this indicated that the IPCop DNS server is working correctly.

In return, it seems that Ubuntu DHCP client is not transferring properly its hostname to the DNS Server.

Would you have an idea ?

Regards,

LinuxFroggy

---

### Post by linuxfroggy on 2006-01-14
Hello,

I have found the solution to this problem. It was quite simple in fact. Looking at DHCP client configuration file, it appears that Ubuntu is set up to not send any hostname information (security I suppose). Uncommenting the line 'send host-name "hostname" ' is necessary to let the client informing the DNS server of the hostname.

Thanks again for the advices.

Regards,

LinuxFroggy

---

### Post by adamonduty on 2006-01-14
Thank you, I have been having the same problem with the hostname not being passed to local dns. By the way, the exact file I edited was /etc/dhcp3/dhclient.conf and uncommented the line that you spoke of and put my own hostname in instead.

---

