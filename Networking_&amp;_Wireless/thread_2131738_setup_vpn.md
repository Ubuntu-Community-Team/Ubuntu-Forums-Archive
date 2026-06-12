---
title: "setup vpn"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by vincentk222 on 2013-04-02
hi 
I have setup a vpn connection which works succesfully.
I connect my computer home (Ip : 192.168.1.0) to my work network (172.16.254.0)
I have a web server at work
How can I browse this remote web [http://172.16.254.123](http://172.16.254.123) from my local computer 192.168.1.50
even if vpn connection is etablish I can not ping 172.16.254.123

regards

---

### Post by LeDieu on 2013-04-03
I assume that with "vpn connection which works successfully" you mean that the connection to the VPN service goes fine. But from there on you are experiencing some issues (so its not working fine :P).
Also, am I understanding correctly that you want to use your VPN as a proxy to the 'internet'?
If so, I think you might have some IP table configurations that are in your way, or you haven't configured your VPN service and/or network interfaces correctly. Before I continue, can you please give us some more info on what VPN software you are using (e.g OpenVPN), your current configuration and what you have done so far. Configuring a VPN is a pain in the *** so the more info the better. Cheers.

---

