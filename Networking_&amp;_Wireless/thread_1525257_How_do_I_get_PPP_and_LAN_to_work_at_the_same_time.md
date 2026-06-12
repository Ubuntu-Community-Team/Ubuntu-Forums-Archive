---
title: "How do I get PPP and LAN to work at the same time?"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by skew on 2010-07-06
Is their a way to get ppp (56k dialup) and my wired home LAN (eth0) to work at the same time with Lucid?  

     Currently in order to connect to the Internet I must disconnect from the LAN first, likewise to connect to my LAN I have to disconnect the PPP connection to the Internet before it will function. I had read a similar post from another who also had this problem but received no replies...  [http://ubuntuforums.org/showthread.php?t=1228649](http://ubuntuforums.org/showthread.php?t=1228649) so I thought I'd try again.

     I'd like to eventually implement ICS (Internet connection sharing) but for the time being I would be content just being able to use the LAN at the same time as I am connected to the Internet. I didn't have this problem in the past using Hardy but it now has become and issue with Lucid. The real head scratcher for me is why this and other things used to work with Hardy and earlier versions of Ubuntu yet now no longer function. It may be just my experience but I have noticed a fair amount of problems with my Lucid, from garbled screen characters to my internal win-modem which used to work (slmodem) but doesn't anymore. I now have to use an external modem to connect to the Internet. A real pain for a laptop user.  Granted, these are mostly small glitchy things (internal modem exempted) which I can shrug off grumbling, for the time being, so I won't berate these issues here any longer. 

     FWIW: I'm using Wicd for my network manager, Lucids packaged network-manger was problematic.. I've also connected my two computers directly with one Ethernet cable as well as through a linksys router, both methods work wonderfully as far as just a simple LAN without PPP is concerned.

Would any one have any thoughts on how to proceed with my PPP LAN issue?

Thanks all!

---

### Post by skew on 2010-07-07
The football (Soccer for our American friends ;-) ) match is over now so i'll BUMP this post.

---

### Post by skew on 2010-08-05
BUMP  Come on guys! You mean to tell me in this huge forum there isn't anybody that can help me out with this?  

  FWIW I use Guarddog as my firewall and after an 56k online session I have to reconnect to the LAN through Wicd. Then I restart my firewall (Guarddog), I then press the apply button after which I then I can use the home LAN again. I need to do the reverse to go back online with ppp0 through my 56k modem. 

This is a real hassle and I am seriously thinking (with much prodding from my kids) of going to a MAC or GOD FORBID Windows 7 OS since this and many other things which had once worked with Ubuntu in previous releases don't seem to function anymore. If I have to change OS's it will end my primarily happy relationship with this OS since Dapper. Damn Pity if you ask me!

PLEASE ANYONE!!!:(

---

### Post by gvoima on 2010-08-14
If you are using network-manager, that cannot atm. handle multiple connections.

But it can be done manually, has been there for ages. It's just that the applet can't with the current version handle it. I think it is on feature list for the 0.8.2 release, not sure.

---

### Post by skew on 2010-09-20
> **gvoima said:**
> If you are using network-manager, that cannot atm. handle multiple connections.

But it can be done manually, has been there for ages. It's just that the applet can't with the current version handle it. I think it is on feature list for the 0.8.2 release, not sure.

I'm impressed somebody actually replied...

I'm using wicd. What's ATM? How can it be done manually?

---

