---
title: "home server not accessible from internet"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by heylookltsme on 2012-08-04
I'm having trouble accessing my home server from the internet and I'm at my wit's end trying to figure it out - any help is much appreciated!

I'm running ubuntu server 11.10.  I've got a few services set up that I'd like to access from the WAN - including apache and subsonic. (Everything works beautifully from within my LAN - no problems.) 

Apache is listening on port 13370 because my ISP (optimum online) blocks 80. Subsonic is on 4040 - I can't imagine any problems with that port. My router is forwarding both. 

From the WAN, I cannot access [http://my-external-ip:13370](http://my-external-ip:13370) in a web browser. Connection times out. However, I **can** access it via both lynx and wget. Same is true for port 4040. 

So... what the hell.  I don't even know where continue troubleshooting at this point. I was convinced optimum online was cleverly blocking the traffic until I discovered I could hit the services with lynx and wget. Is it possible for an ISP to block connections from a traditional web browser but leave loop holes open for more obscure things like lynx?  I don't know nearly enough about the components involved to even know if that's a sensible question! Please be kind. :)

Please let me know if there's additional information needed to help solve this problem. Any help is greatly appreciated! TIA.

---

### Post by spjackson on 2012-08-05
This sounds odd. If lynx works over the internet, you'd think that the browser would too. Have you tried more than one browser? Is the browser using a proxy? If it's not a proxy issue, I can't think of anything else.

---

### Post by heylookltsme on 2012-08-05
Oh good call! I feel stupid now. I had a friend try and it worked for her.  I had been testing with a remote desktop connection to my work computer and they must be using a proxy.  Oh silly me. At least now I know there's nothing wrong my side. 

Now to figure out how to get around the proxy issue at work! :)  

Thanks for your help!

---

