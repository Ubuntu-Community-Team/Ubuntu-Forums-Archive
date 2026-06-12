---
title: "Cannot completely load web pages on any web browsers"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by Xtian_1028 on 2010-06-22
Hello! I am a newbie when it comes to the Ubuntu 10.04.

I seem to have stumbled on a problem regarding internet connectivity. My web browser (Firefox or any other web browsers) can't completely load the desired webpages like yahoo.com or even google.com.

But as I read different blogs in this forum, I have convinced myself that there is an internet connection.

= when I ping different websites, Iseem to get good responses from those sites. Only when I need to browse the webpage do Iget no results.

= ifconfig seems to respond well enough.

= even "route" shows the IP address of my router/gateway correctly. 

The problem , I think, lies on the proxy settings or the DSN.

Any help is greatly appreciated. Thank You! 
Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by Linuxforall on 2010-06-22
Have you checked your MTU settings, some ISP's stipulate lower than standard settings.

---

### Post by Xtian_1028 on 2010-06-22
From Right Clicking Networks Manager > Edit Connections > Highlighting eth0 >edit > and observing the MTU bar

I can see that it is in "automatic" bytes. Should I change that?

thanks!
Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by Xtian_1028 on 2010-06-22
Thanks man! It is done!

It seems I just have to write this down in the terminal:

sudo ifconfig eth0 mtu 1500

Thanks to you and a bright friend of mine.

Thanks!!

---

