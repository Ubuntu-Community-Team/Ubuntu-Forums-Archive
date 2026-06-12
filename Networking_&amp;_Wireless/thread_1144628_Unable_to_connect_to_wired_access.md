---
title: "Unable to connect to wired access"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by ArchieBunker on 2009-04-30
I'm new to Ubuntu and Linux in general, but I like learning new things and I'm not going to give up on this. I switched over from Windows, because I really like MythTV. So I built a new machine and installed Mythbuntu 8.10 (I assume it's the same Ubuntu version). At any rate, I'm at a dead end trying to get network connection. When I had Windows installed, I just plugged in the ethernet cable and it worked, but I haven't had the same luck with Ubuntu.

I've been through the message boards and tried a few different things. I found the jamesonwilliams script fix, but that didn't work...or I didn't execute it properly. At any rate, here's some of my info:

Lan Chipset: Realtek 8111C

lspci | grep Ethernet
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev 02)

uname -mro
2.6.27-7-generic i686 GNU/Linux

I would be glad to provide any other information that would help. Thanks!

---

### Post by mousestalker on 2009-05-01
Have you tried disabling "Wake on LAN" in your computer's bios?

---

### Post by Butthead on 2009-05-01
Try running the "Recovery" option in the Grub menu and have it fix any broken packages.

Seems to have worked in my case.

---

### Post by Butthead on 2009-05-01
Disregard.  Mine is not working again either. :(

---

### Post by eworthy on 2009-05-01
Yep same here.  Wired network was working fine in this inspiron 2200 but died upon doing a "distribution upgrade" 9.04.  Wireless is working.
I can't believe with the testing and maturity of Ubuntu that this has happened.

---

### Post by eworthy on 2009-05-01
my bad.  wired only said it wasn't working.  In fact there was a DHCP error which I caused :( which was the problem.  It still says "not managed" but it is working fine.

---

### Post by ArchieBunker on 2009-05-02
Thanks for the suggestions. I can't find the WoL option in my BIOS, but I also can't find an energy setting either. Anyone know where this is on Asrock BIOS?

---

### Post by mousestalker on 2009-05-02
> **ArchieBunker said:**
> Thanks for the suggestions. I can't find the WoL option in my BIOS, but I also can't find an energy setting either. Anyone know where this is on Asrock BIOS?


What motherboard?

---

### Post by ArchieBunker on 2009-05-02
Asrock A780FullHD

---

### Post by H.K.Murmu on 2009-05-02
I have the same problem and always use pppoeconf to connect internet. But now I am able to connect through network manager applet no need to open a terminal.

To connect through[COLOR=Blue] ADSL modem[/COLOR] you have to configure your modem device by self or take it to your service provider. Once configured then follow the steps
1[COLOR=Red]:-system[/COLOR]----[COLOR=Blue]adminstration[/COLOR]------[COLOR=Purple]user and groups[/COLOR]
2:-In user setting select [COLOR=Purple]use[/COLOR]r-----[COLOR=Purple]propertie[/COLOR]s---check the box "[COLOR=Blue]connect to internet using modem[/COLOR]" and "[COLOR=Blue]connect to wireless and ethernet networks[/COLOR]" then close
3:- open [COLOR=Blue]network manager apple[/COLOR]t from panel under DSL --[COLOR=Blue]-ADD[/COLOR]---Edit DSL connection-----in tab[COLOR=Blue] DSL[/COLOR] provide internet [COLOR=Navy]userid and password[/COLOR] and under tab[COLOR=Red] IPv4 setting[/COLOR] select "[COLOR=Red]automatic pppoe[/COLOR]" and then close(perhaps require restart system not sure)
4:-In pannel left click network manager applet and click the radio button 
5-now you are connected to internet through [COLOR=Red]Network manager Applet[/COLOR]

---

### Post by ArchieBunker on 2009-05-03
> H.K.Murmu 	 		**Re: Unable to connect to wired access**
 I have the same problem and always use pppoeconf to connect internet. But now I am able to connect through network manager applet no need to open a terminal.

To connect through[COLOR=Blue] ADSL modem[/COLOR] you have to configure your modem device by self or take it to your service provider. Once configured then follow the steps
1[COLOR=Red]:-system[/COLOR]----[COLOR=Blue]adminstration[/COLOR]------[COLOR=Purple]user and groups[/COLOR]
2:-In user setting select [COLOR=Purple]use[/COLOR]r-----[COLOR=Purple]propertie[/COLOR]s---check the box "[COLOR=Blue]connect to internet using modem[/COLOR]" and "[COLOR=Blue]connect to wireless and ethernet networks[/COLOR]" then close
3:- open [COLOR=Blue]network manager apple[/COLOR]t from panel under DSL --[COLOR=Blue]-ADD[/COLOR]---Edit DSL connection-----in tab[COLOR=Blue] DSL[/COLOR] provide internet [COLOR=Navy]userid and password[/COLOR] and under tab[COLOR=Red] IPv4 setting[/COLOR] select "[COLOR=Red]automatic pppoe[/COLOR]" and then close(perhaps require restart system not sure)
4:-In pannel left click network manager applet and click the radio button 
5-now you are connected to internet through [COLOR=Red]Network manager Applet[/COLOR]

Thanks for the suggestion. This isn't practical for me, because I connect to a router and not the modem directly(without going into a big explanation, it is a necessity to do it this way). That being said, I did connect directly to my modem with the machine I'm having issues with, then went through your steps. Much to my displeasure, still no connection.

---

### Post by H.K.Murmu on 2009-05-03
I have the same problem and always use pppoeconf to connect internet. But now I am able to connect through network manager applet no need to open a terminal.

To connect through ADSL modem you have to configure your modem device by self or take it to your service provider. Once configured then follow the steps
1:-system----adminstration------user and groups

2:-In user setting select user-----properties---check the box "connect to internet using modem" and "connect to wireless and ethernet networks" then close

3:- open network manager applet from panel under DSL ---ADD---Edit DSL connection-----in tab DSL provide internet userid and password and under tab IPv4 setting select "automatic pppoe" and then close(perhaps require restart system, not sure)

4:-In panel left click network manager applet and click the radio button

5-now you are connected to internet through Network manager Applet

Best of luck

---

### Post by ArchieBunker on 2009-05-03
Did you mean to post that again?

---

### Post by mousestalker on 2009-05-03
All [Asrock mobos have 'wake on lan']("http://www.asrock.com/support/faq.asp?c=General"), apparently. The only way I see to disable it in your bios is to navigate to the ACPI configuration screen and make sure 'PCI Devices Power On' is set to 'disabled'. If it already is and you still have this problem, then we can rule this one out.

---

### Post by ArchieBunker on 2009-05-04
> mousestalker 	 		**Re: Unable to connect to wired access**
 		All [Asrock mobos have 'wake on lan']("http://www.asrock.com/support/faq.asp?c=General"), apparently. The only way I see to disable it in your bios is to navigate to the ACPI configuration screen and make sure 'PCI Devices Power On' is set to 'disabled'. If it already is and you still have this problem, then we can rule this one out. 

It was already set to disable.

---

### Post by drjackal on 2009-05-21
please! how does one unlock his user? all my settings seem to have been frozen!!

---

