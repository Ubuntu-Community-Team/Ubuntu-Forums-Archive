---
title: "getting my ethernet to be recognized by ubuntu."
date: 2005-01-14
forum: Networking &amp; Wireless
---

### Post by Mr. Mystofaleeeese on 2005-01-14
I've Booted with the Live CD of ubuntu on my laptop....its awesome. i cant say enought good things about it.  but the one thing I'm having a problem with is connecting to Internet.  i cant get ubuntu to recognize my ethernet card.  I also can't get my internal WIFI card to recognize my router either.  I'd love to upate ubuntu but i cant cause i cant connect to the internet. 

Thanks,  

Mr. Mystofaleeeese

P.S.

If you need to know what type of laptop it is ...its a toshiba P-25.

---

### Post by hardcandy on 2005-01-14
[http://www.do-linux.net/P30.html](http://www.do-linux.net/P30.html) is a list off how things work with Mandrake 10.1 with a P30. Gives some idea of the modules needed for the hardware. The network card if it is the same as yours would need the 8139too module. "sudo lsmod" will show you the modules loaded already. You may need to turn off WEP if enabled to configure the wireless (you can turn it back on later). And you may need to install the mad-wifi module.
"sudo ifconfig eth0 up" then "ifconfig" will show if the NIC interface is up.  "sudo iwlist" will show what access points the wireless is seeing.

---

### Post by Mr. Mystofaleeeese on 2005-01-15
So I configured my ethernet, its now working.  but the WIFI is still not picking up anything.  I have open wirless (no WEP).  I have the little wireless icon in my panel it just says that i have no wireless to receive.  "Mad-wifi" where can i find the download for it?  and where would i install it to?

Mr.Mystofaleeeese

---

### Post by hardcandy on 2005-01-15
[http://www.mattfoster.clara.co.uk/madwifi-faq.htm](http://www.mattfoster.clara.co.uk/madwifi-faq.htm)

[http://debian.isg.ee.ethz.ch/public/](http://debian.isg.ee.ethz.ch/public/)

---

### Post by Mr. Mystofaleeeese on 2005-01-18
It was a long process but.....i finally got it recognized ...i had to download the mad-wifi like you said.  I also had to download the patch.  Which i then had to install them...but after like 6 hours of troubleshooting i finally got it to work. It was a bit slow at first but after a while i just turned sudo ifup ath0 and sudo ifdown eth0 and everything was golden ....i appreciate your help. thanks again hardcandy

Mr. Mystofaleeeese

---

