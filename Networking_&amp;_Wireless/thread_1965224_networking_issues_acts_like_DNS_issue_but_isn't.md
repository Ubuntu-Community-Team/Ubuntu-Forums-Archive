---
title: "networking issues acts like DNS issue but isn't"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by donavan on 2012-04-25
I have got a weird problem I can't figure out, here are the basics.  I have ubuntu 11.10 w/xfce (win7 dual boot) on my laptop.  I have other machines running Windows on the same network.  I am getting what acts like a DNS issue some of the time. However it cannot be a DNS issue unless it is local to the laptop.  Other machines on the network function fine (all windows machines) and this machine when booted into windows works fine. I know its not specifically a hardware issue because I can use this same machine at other locations with no issues.  I have tried this in both chrome and Firefox, symptoms appear in both browsers often with issues for different sites sometimes the same sites.  I have manually set my DNS to pull from OpenDNS's, Google's, and my ISP's server instead of letting my router handle it.  I can ping and even use lynx with no issue.  I have tried setting my MTU to 1492, 1500 and auto. The wlan0 uses the Ath9k driver.  The router is a Belkin N150.  Can someone please tell me how to fix this issue.

---

### Post by SeijiSensei on 2012-04-25
It could be a firewalling issue if the reply packets from the remote DNS servers aren't passed back to you.

Try this:

```
host www.google.com 8.8.8.8
```

If the request times out, something is blocking you from querying remote DNS servers.  If the router is configured to provide DNS, does that not work for you?

---

### Post by donavan on 2012-04-25
thanks for the reply but unfortunately I have already tried that.  Anything I do in the command line works just fine, ping, host, mrt, lynx but it seems any web browser just craps out. There are no firewalls between me and the internet, unless ubuntu has one built in to works sometimes but not others.

---

### Post by Ms. Daisy on 2012-04-25
Just to address your firewall comment: Your router surely has a firewall, and ubuntu comes with UFW (Uncomplicated FireWall) installed. But if you don't know then clearly you're running the default which would not cause this behavior (I don't think). You can do a quick check of your rules with ```
 sudo ufw status
```

---

### Post by donavan on 2012-04-25
In an effort to make sure that I wasn't my ubuntu install I went ahead and reinstalled with the beta version of 12.04 and still the same issues have popped up. I am going to disable IPv6 and see if that helps, but im kinda doubting it being that I disabled it on the last version I had.

---

### Post by jonobr on 2012-04-25
could you try 

```
nslookup google.com
```

what do you get?
Post the results back here.

---

