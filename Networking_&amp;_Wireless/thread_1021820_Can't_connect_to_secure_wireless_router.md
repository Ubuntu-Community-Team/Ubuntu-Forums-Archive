---
title: "Can't connect to secure wireless router"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by patman0623 on 2008-12-26
Could you possibly point me to the answer for the following problem I have: 

I cannot seem to connect to a wireless network when there is security on the network. 

Here is all my info:
1) I am running Ubuntu 8.04 Hardy
2) I have a third party software driver installed for wireless (I am running Wireless-N, which is fairly new). I'm 95% sure it's a security issue, because I am able to see all routers in the vicinity, so the driver appears to work.
3) The router is a linksys WRT54G.
4) When I dualboot back into Windows, it can connect just fine.
5) The security is 64 bit WEP (10 hex keys), and I have a passphrase. When I try to connect, whether by the key or passphrase, it rejects me and can't connect. 
6) I tried wifi-radar, and it only comes back with "invalid argument" when I type in all the data.

To clarify:
[IMG]http://i49.photobucket.com/albums/f268/patman0623/Screenshot-WirelessSecurity-Mozilla.png[/IMG]
[IMG]http://i49.photobucket.com/albums/f268/patman0623/Screenshot-WirelessNetworkKeyRequir.png[/IMG]

Help guys. I want to be able to access a secure wireless router on Linux!

---

### Post by AlexBellisBrown on 2008-12-26
Why dont you just change the WEP encryption on your router to 128bit ASCII, and then log into it on Ubuntu and Windows, it should be easier, just as secure and give no problems.

---

### Post by jpmelos on 2008-12-26
Coincidently, I bought a new router wireless today, and faced the very same problem. I just changed the security mode to WPA-PSK/WPA2-PSK, and my Ubuntu connected successfuly upon password entry.

I set security option and encryption to automatic.

Try the WPA-PSK stuff, pretty sure it will help...

---

### Post by patman0623 on 2008-12-27
Thank you so much for the help guys. Quite the help, for sure.

Now, I might not be able to get my mother to agree to me changing the settings on the router, but at least it's worth a try.

Thanks again.

---

