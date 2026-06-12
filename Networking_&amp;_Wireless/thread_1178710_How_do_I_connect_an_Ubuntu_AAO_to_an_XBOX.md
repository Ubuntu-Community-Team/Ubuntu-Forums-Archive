---
title: "How do I connect an Ubuntu AAO to an XBOX?"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2009-06-04
Ok. I have an XBOX softmodded and have XDSL on it. It's far from my router, so I can't just connect it to an ethernet cord. I've read somewhere on here that you can connect two Ubuntu computers directly with an ethernet cord to share the wireless of one of them. How exactly do I do this? Thanks in advance for the help.

---

### Post by slammed87d21 on 2009-06-04
Anyone?

---

### Post by Boondoklife on 2009-06-04
First you will need to get a cross over cable, you can buy them or try to make one just take a google search.

Then you will need to setup NAT to get the internet sharing working. This will be the more intresting part. You can try out firestarter, which is a gui for the iptables service. If that does not work then you will need to look into creating your own iptables rules and getting NAT working manualy.

You will most likely need to setup the nic on the xbox and the computer with static ip's also, I don't have an xbox but would assume this is possible. If it is not then you would also have to setup a DHCP server on the computer too.

as you can see fun fun, can I as why you just dont get ethernet to wifi adapter, would prolly save you a huge headache.

---

### Post by slammed87d21 on 2009-06-06
Is it possible to just set up my ethernet port on my Aspire One similar to a router? I know I can have the Xbox have a static IP, so I don't see why I couldn't do this. Any and all help is appreciated.

---

### Post by slammed87d21 on 2009-06-06
So is this possible? I believe that I've read somewhere here how to do it, but I can't find it searching.

---

### Post by slammed87d21 on 2009-06-07
Bump

---

### Post by Boondoklife on 2009-06-07
> **slammed87d21 said:**
> Is it possible to just set up my ethernet port on my Aspire One similar to a router? I know I can have the Xbox have a static IP, so I don't see why I couldn't do this. Any and all help is appreciated.

I think I answered this in my post when I said> Then you will need to setup NAT to get the internet sharing working. This will be the more intresting part. You can try out firestarter, which is a gui for the iptables service. If that does not work then you will need to look into creating your own iptables rules and getting NAT working manualy.

That all means YES and to try and lookup the information on firestarter and iptables, especially the sections having to do with NAT (Network Address Translation).

---

### Post by slammed87d21 on 2009-06-09
Ok. Sorry about the noob response, had a brain fart from working on vacuum tube radios all day. Anyway, after installing firestarter, it kept saying there wasn't an eth0 connection. Well, I went to edit connections, and edited eth0 to a link-local connection. That was the only way it would connect. Ok. on my dashboard (xbox) it shows an I.P. When the Xbox is booting to it's dashboard, Network Manager is showing its connecting/connected to eth0 as well as eth1 (wifi). When I boot xDSL, it does not show an internet connectionor I.P. It does automatically if I connet the Xbox to the router. Any suggestions on what I'm doing wrong?

---

### Post by slammed87d21 on 2009-06-09
Anyone?

---

### Post by slammed87d21 on 2009-06-09
Bump

---

### Post by slammed87d21 on 2009-06-10
I made a crossover cable, but still no go. I've tried several different setups in Network Manager with no luck also. I honestly seemed to have better luck with a standard ethernet cable. Anyone?

---

### Post by slammed87d21 on 2009-06-10
Anyone?

---

### Post by slammed87d21 on 2009-06-11
~Bump~

---

