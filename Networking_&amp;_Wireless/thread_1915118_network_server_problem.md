---
title: "network server problem"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by dazman19 on 2012-01-25
Hi, our internal router forwards web traffic through to a machine on our local network. 

the problem is, occasionally our router cannot connect to the web server machine. But i can connect to it on the local network. 

I dont think its a problem with the router because when i log into the web server and run 

```

daryl@eziserver:~$ sudo /etc/init.d/networking restart
[sudo] password for daryl: 
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces ... (warning).
Reconfiguring network interfaces...if-up.d/mountnfs[eth0]: lock /var/run/network/mountnfs exist, not mounting ... failed!
done.

```

it fixes the problem for about 2-3 days, then it manages to bung out again. Does anyone know what i should check?

---

### Post by jonobr on 2012-01-25
Hello there


on your webserver machine when you dont see web traffic hitting it,
I would recommend that on the terminal window open a capture for port 80 traffic (Assuming your using 80)

```
sudo tcpdump -i any port 80
```

Leave that window open if you do web stuff and see packets in the output of the above window, then packets are being recieved and could point to a application layer (apache) issue.
If no packets are shown it would most likely be a routing issue or an issue with blocked packets.

It could be iptables or ufw but given its running opk and then stops, chances of that are slim

If you get some info on tcpdump. maybe you could post here and we could have a look

---

### Post by SeijiSensei on 2012-01-26
What happens if you set up a continuous ping job on some machine behind the router to see if you can keep the server alive?

```
ping -i 60 -n 9999999 ip.addr.of.server
```

This pings the server once per minute up to 9999999 times.

It may just be a bad NIC; have you tried replacing the adapter?

---

