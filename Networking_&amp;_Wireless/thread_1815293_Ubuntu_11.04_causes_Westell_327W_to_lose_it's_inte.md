---
title: "Ubuntu 11.04 causes Westell 327W to lose it's internet connection"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by mx597turbo on 2011-07-31
I use a Westell 327W dsl modem/router to connect to the internet. I installed Ubuntu 11.04 on two computers. My desktop is connected with ethernet and works perfectly. However, when I connect my laptop with wifi, it causes the router to lose it's internet connection. All connected devices are affected. The only way to fix the problem is to shut off and turn on the router again. This problem only happens with with the laptop and Ubuntu. I use the same laptop with Win7, and it connects fine. I also have no problems connecting my Android phone or PS3 to the router. The wifi in the laptop is an Atheros model.

I have tried no security, WEP, and WAP. The result is the same with all three settings. I can still access the router config from any device 192.168.1.1 after the internet goes out. The DSL led on the router stays on, and the config says the DSL connection is active.

Thanks in advance for any help.

---

### Post by mx597turbo on 2011-07-31
I solved the problem by buying a Tenda wireless router from Microcenter. The laptop connected and worked perfectly.

On a side note, I tired connecting the laptop to the 327W via ethernet, and that also killed the internet connection. So there must have been some conflict between the laptop while running 11.04 and the 327W. The router was only $25, so no big deal.

Considering all the problems that show up in searches for the 327W, it seems to me that it's best to just use it as a modem, and buy a dedicated router for your network.

---

### Post by MrAnon on 2011-09-19
I currently have same issue.  Have a fresh install on a laptop, and  every time ubuntu connects I have to flick the power switch on the  Westell 327w router to get the internet connection to work again.  Every  10 seconds or so the router's security log reports:  
[COLOR=Black]
[/COLOR]  [COLOR=Black]1[/COLOR]                 [COLOR=Black]09/19/2011[/COLOR]                 [COLOR=Black]   06:55:43   [/COLOR]                 [COLOR=Black]Inbound                                                  [/COLOR]                 [COLOR=Black]RulesDropWANTCP [/COLOR][COLOR=Black][/COLOR][COLOR=Black]Alert[/COLOR]
TCP Flags:                 14 (  ack  rst   )

Alert: TCP WAN Traffic to WAN IP

I'm really new to Ubuntu, and hoping someone more experienced could help me out with this.  :)

---

