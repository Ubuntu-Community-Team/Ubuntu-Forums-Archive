---
title: "Mobile broadband connects but Firefox and Evolution don't"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by stefcep on 2009-11-20
Hi All,

I have been using my broadband mobile ( from "3" in Australia with Huaweii E220 USB modem) for 8 months with 9.04 without problem.  Today, I can connect-according to Ubuntu anyway-, but Firefox and evolution tell me there is no network.  I'd appreciate any advice.

---

### Post by t0mppa on 2009-11-20
The most likely culprits are:[LIST=1]
[*]**DNS malfunction**, this is true if you can ping 74.125.79.99, but not [www.google.com](www.google.com)
[*]**default gateway missing**, this is true if you run **ip route list** from terminal and don't see a line beginning with *default*
[/LIST]

If you can't ping outside your local network even by IP, but can still ping your default gateway (the ip address after the *default via* bit), then things get a bit more complicated and a trace route might be an idea to find out at which step the packets stop reaching the destination.

---

### Post by stefcep on 2009-11-20
> **t0mppa said:**
> The most likely culprits are:[LIST=1]
[*]**DNS malfunction**, this is true if you can ping 74.125.79.99, but not [www.google.com](www.google.com)
[*]**default gateway missing**, this is true if you run **ip route list** from terminal and don't see a line beginning with *default*
[/LIST]

If you can't ping outside your local network even by IP, but can still ping your default gateway (the ip address after the *default via* bit), then things get a bit more complicated and a trace route might be an idea to find out at which step the packets stop reaching the destination.

I was able to ping with 74.124.79.99, but not [www.google.com](www.google.com).

So its a DNS malfunction i guess

Can anyhting be done to fix this?

---

### Post by t0mppa on 2009-11-21
Edit */etc/dhcp3/dhclient.conf*, find the line with *prepend domain-name-servers*, uncomment it (remove the # in front of it, so it's read), if it it's commented, and change it to the following:```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

Said two servers are those of [OpenDNS]("http://www.opendns.com/"), you can later comment (add the # in front of it) this line again, to have it ignored, if you want to swap back to your ISP's DNS servers.

---

### Post by stefcep on 2009-11-21
> **t0mppa said:**
> Edit */etc/dhcp3/dhclient.conf*, find the line with *prepend domain-name-servers*, uncomment it (remove the # in front of it, so it's read), if it it's commented, and change it to the following:```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

Said two servers are those of [OpenDNS]("http://www.opendns.com/"), you can later comment (add the # in front of it) this line again, to have it ignored, if you want to swap back to your ISP's DNS servers.


Your suggestion didn't work, but it pointed me in the right direction,

I had to RT click on the network applet in the title bar->Edit connections->Mobile broadband->three->edit->ipv 4 settings->DNS Server.  Here I deleted the existing numbers in there and replaced them with 208.267.222.222, 208.67.220.220.

I have no idea what any of above does, but it works.
Is this sudden problem due to a change at my ISP or an Ubuntu thing?  BTW Vista has continued to work fine in the mean time.

---

### Post by t0mppa on 2009-11-21
> **stefcep said:**
> Your suggestion didn't work, but it pointed me in the right direction,

I had to RT click on the network applet in the title bar->Edit connections->Mobile broadband->three->edit->ipv 4 settings->DNS Server.  Here I deleted the existing numbers in there and replaced them with 208.267.222.222, 208.67.220.220.

Ah yes, I forgot you could do that on GUI. It probably is better that they're over there, so you can find them more easily. Glad you got it working though.

> **stefcep said:**
> I have no idea what any of above does, but it works.
Is this sudden problem due to a change at my ISP or an Ubuntu thing?  BTW Vista has continued to work fine in the mean time.

It got rid of the earlier values for DNS servers and replaced them with those of OpenDNS, which is a free service providing DNS to anyone that needs it. Unless you personally edited the configuration on Ubuntu, I'd say it was an ISP thing, but if everything works just fine on Vista, then maybe they just changed something at the ISP's end and the update didn't reflect properly to your settings on Ubuntu.

---

### Post by stefcep on 2009-11-22
> **t0mppa said:**
> Ah yes, I forgot you could do that on GUI. It probably is better that they're over there, so you can find them more easily. Glad you got it working though.



It got rid of the earlier values for DNS servers and replaced them with those of OpenDNS, which is a free service providing DNS to anyone that needs it. Unless you personally edited the configuration on Ubuntu, I'd say it was an ISP thing, but if everything works just fine on Vista, then maybe they just changed something at the ISP's end and the update didn't reflect properly to your settings on Ubuntu.

Thanks.  Would never have got it working on my own.  This what i like about Linux: community spirit.

---

### Post by roderickf on 2010-04-25
Hi stefcep,
I was having exactly the same issue as you did before just now. Also aussie 3 mobile broadband but i'm using Karmic Koala 9.10. I did an update last night.
I think this DNS issue is somehow due to system update. I was trying to do what you guys discussed but no luck. However, I directly delete my three mobile broadband profile and add it manually. And guess what? ha, everything works!
Cheers, -Roderick

---

