---
title: "Unable to connect to internet via proxy server with apt-get"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by megreid on 2010-05-14
I am unable to connect to the Internet in lucid via a proxy server using apt-get or synaptic. Opera & firefox connects to the internet fine with the proxy setting. I have tried the following solutions
1) set proxy setting using systems|preferences|network proxy
2) editing ~/.bashrc & /etc/.bashrc
3) creating a /etc/apt/apt.conf file.
4) putting the proxy setting in synaptic

For the proxy setting I have used the both the verbose name as well as the ip address. There is no logon requirements for the proxy server. Either formats work in the browsers

---

### Post by davemarker on 2010-05-14
What kind of proxy server is it, do you know?  I know there are some special issues you have to look into regarding Microsoft's ISA Server. Maybe look into ntlmaps [http://ntlmaps.sourceforge.net/or](http://ntlmaps.sourceforge.net/or) cntlm [http://cntlm.sourceforge.net/](http://cntlm.sourceforge.net/)

I've had luck in the past with ntlmaps using the tutorial found here: [http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Web-Browsing-Behind-ISA-Server-HOWTO/](http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Web-Browsing-Behind-ISA-Server-HOWTO/) , but recently had issues getting it to work with a LiveCD environment.  Just today in fact I went over to cntlm and loaded up the win32 version on my Windows 7 laptop  and use that as a proxy to get out to the internet.

---

### Post by megreid on 2010-05-15
Thanks for suggestion. Unfortunately this did not work for me as my proxy server does not require a priori authentication. In fact using cntlm software generated errors such as bad url or insane proxy server. The solution to my problem was as follows. using opera i directed the browser to the proxy server ([http://proxy.universitydomain:proxyport](http://proxy.universitydomain:proxyport)) and got a .pac file. I then searched in the pac file and found the name of actual proxy server following instructions from 

[http://www.linuxquestions.org/questions/debian-26/using-apt-behing-a-pac-http-proxy-592148/](http://www.linuxquestions.org/questions/debian-26/using-apt-behing-a-pac-http-proxy-592148/)

I then used this proxy server  in synaptic & system|preferences|Network proxy. 

Note I had to use the IP address and not the verbose name for it work.

---

