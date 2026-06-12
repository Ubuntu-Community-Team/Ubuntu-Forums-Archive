---
title: "Laptop conecting problems"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-08-20
OK so I have a an Acer Aspire 5313 running Ubuntu 10:04, it was working fine connecting to my home network. But now for no apparent reason won't connect properly. It connects to the but network but its like it can't get past the router. I cant get it to communicate with my PC if I try ping my PC (192.168.1.64) it comes back "192.168.1.1 Host is Unreachable."
 
The connection status shows its connected though. It can't get out to the internet either. I was thinking that it was perhaps my router, untill just now when I tried to connect it to my friends router and got the same deal.
 
However when I take to my poloytech it is connects to their student Wifi with no troubles. This is all the same for both ethernet and wireless.
 
Short of trying a clean install, is there a way that I can some how reset all the networking detail so that it is just like it was in a fresh install? unless someone knows something??

---

### Post by Nach_ on 2010-08-20
did you have some firewall on ? check if its blocking your network trafic on your ethernet intreface

---

### Post by Jonny87 on 2010-08-20
Yep I've checked that, the ufw is inactive. I now currently writting this from my laptop on a Live Ubunt CD so I'm pretty sure that its something in my Ubuntu install and not the laptop or router. The wiered thing is though is that it connects fine at my poloytech to their student hot spot. just doesn't to connect to any other. Well when I say that, it show that its connected to the likes of my home router but it cant go any furthe than that (i.e access the web).

I'd do a clean install if it weren't for the fact that I've got slow internet, and it would take forever to re-download the packages. And that I've just got things set the way that I want them. But I'm very close to doing it anyway.

---

### Post by Jonny87 on 2010-08-23
I'm not 100% sure what caused the problem but I fixed it. I just did a clean install of / and kept the /home partition as it was. I got around the download issue by making copies of the DEB's in /var/cache/appt/archives and then manually installing them, tedious but works. All in all the laptop is connecting fine now.

If any one works out what actually caused the problem, I'd still like to know.

---

### Post by ramakrishna_cse on 2010-12-09
My Internet service provider redirects to login page.
I am able to see the redirect page(from firefox) in windows
and it works,but in Ubuntu I am unable to redirect, it says 'page cannot be displayed'
 
wireless card is Up and running and I see statics many packets are sent and received.
The Firefox is unable to Redirect to ISP login page ..pls help me

---

### Post by kiriakos321 on 2010-12-09
Try this : open terminal and write ping 192.0.0.1

---

