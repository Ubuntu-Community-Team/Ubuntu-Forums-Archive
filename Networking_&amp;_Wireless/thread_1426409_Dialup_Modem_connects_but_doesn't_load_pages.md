---
title: "Dialup Modem connects but doesn't load pages"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-03-10
I had started another thread about this but had a terrible subject line. Others may have this issue.


Found the answer deep in the bowels of documentation. My question now is  " did version 20 mess this up for everyone with dialup"?

 	Code:
 	gksudo gedit /etc/ppp/options 
Add this line and save:

replacedefaultroute

---

### Post by alexfish on 2010-03-11
> **Silvertones said:**
> I had started another thread about this but had a terrible subject line. Others may have this issue.


Found the answer deep in the bowels of documentation. My question now is  " did version 20 mess this up for everyone with dialup"?

     Code:
     gksudo gedit /etc/ppp/options 
Add this line and save:

replacedefaultroute


Hi

interesting one this , I have looked up two threads about this replacedefaultroute
[http://ubuntuforums.org/showthread.php?t=576332](http://ubuntuforums.org/showthread.php?t=576332)
[http://fixunix.com/ppp/62413-unrecognizecd-option-replacedefaultroute.html](http://fixunix.com/ppp/62413-unrecognizecd-option-replacedefaultroute.html)

But I will try this 

thanks 

alexfish

---

### Post by Silvertones on 2010-03-11
Alexfish,
You had the same problem?
My first wubi install worked fine without this. I uninstalled wubi and did a side by side then did all of the updates. My wubi was v 19 of the Kernel. When 20 came out I decided to do the side by side. Once complete I configured wvdial & Gnome -PPP as before. I could connect but pages would not load. I added this line and it worked. What do you think is going on here?

---

### Post by alexfish on 2010-03-11
Hi

Have done more searches This one goes back to 2001 with a ref to SuSEs

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=93936](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=93936)

I have changed the options to include this "replacedefaultroute" and it appears to be working with the network manager {Ubuntu 9.10 kernel - 17 } , but will monitor  the next few weeks, maybe a good day when connections work fine ,also I don't know if it will impact on other setting, IE wireless and wireless connections

One other setting I had previously changed in the options file was setting the IPCP configure-NAKs returned before starting to "ipcp-max-failure 30" this also appears to work

The one thing I don't understand is Gnome PPP always connected and had no problems with the browser , yet at times NM had problems with the browser , this was mainly due to the network manager failing to return the resolved address to the reslovconf.

This was solved by setting the IPv4 to Automatic (PPP) address only,this defeated the object of using named servers, this led me to hacking around with the options file.thus found changing the ipcp-max-failure {default 10 } to 30 worked on my system

according to the howto ppp there is no entry of the mentioned [I][SIZE=1][I]replacedefaultroute option

[http://tldp.org/HOWTO/PPP-HOWTO/options.html](http://tldp.org/HOWTO/PPP-HOWTO/options.html)

[/I][/SIZE][/I][SIZE=1]As to what is really happening " this bug seems to have been around a lot longer than Ubuntu 9.10 " . So I now think all the bad press about 9.10 is Unjustified in this respect . It will be interesting to find a official patch to this problem or bug .
[/SIZE]*[SIZE=1][/SIZE]*[SIZE=1]regards

alexfish
[/SIZE]*[SIZE=1][/SIZE]* **[SIZE=1][/SIZE]**

---

### Post by Silvertones on 2010-03-12
I have two lappies that sit side by side. One is a Dell and is my Internet machine & one is a Toshiba & is my music machine.

The Dell has  a USR USB Dial up modem to access the Internet & a Belkin card that is used to network the Dell & Toshiba. It also serves as the WiFi card when I take the Dell out on the road. Eveything is working perfectly. I do not have to reconfigure anything.
Still can't figure why the first install didn't need this and the second did. Could be some weird thing with the Wubi vs real install.

---

