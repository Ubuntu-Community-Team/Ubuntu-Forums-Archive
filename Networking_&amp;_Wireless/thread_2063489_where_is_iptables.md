---
title: "where is iptables?"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by h66m9d on 2012-09-27
Hi
I cant find iptables configuration file?
in redhat base linux is in /etc/sysconfig/iptables
anyone can help me?

---

### Post by kc1di on 2012-09-27
> **h66m9d said:**
> Hi
I cant find iptables configuration file?
in redhat base linux is in /etc/sysconfig/iptables
anyone can help me?

Though I'm no firewall expert here I believe Ubuntu uses a tool called ufw to configure the firewall you can find more info at these pages. good luck,

[https://help.ubuntu.com/10.04/serverguide/firewall.html]("https://help.ubuntu.com/10.04/serverguide/firewall.html")

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-building-a-firewall/]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-building-a-firewall/")

---

### Post by Lars Noodén on 2012-09-27
The official way in Ubuntu is to use the [UFW front end](https://help.ubuntu.com/community/UFW) for iptables.  It will put the rules in /etc/ufw/ with some configuration in /etc/default/ufw

See the bottom of the wiki page for more information on UFW:
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

They are a bit simplistic though.  So if you work with iptables directly then you can choose where in /etc/ you want to put the rules and how you want to activate them.

---

### Post by tangozopo on 2012-09-27
> **h66m9d said:**
> Hi
I cant find iptables configuration file?
in redhat base linux is in /etc/sysconfig/iptables
anyone can help me?

Hi, l am new to this forum. Can someone assist me as l have tried navigating but with no success.
1.How do you guys create new posts that we end up bennefitting from.
2.I want to setup a mail server on ubuntu 12.04 with the following. 
   -Dovecot+Postfix+Spamassassin+Clamav+Amavis+Horde 
3.The server should use mbox instead of maildir but all docs l have found so far use maildir
4.If l have to stick to maildir, will that not affect horde
5.The server should scan outgoing mail for spam and bounce it back to local user if it has spam otherwise we end up being black listed.
Can any one assist with easy step by step comprehensive set-up or refer me to easy guides

---

### Post by kc1di on 2012-09-27
> **tangozopo said:**
> Hi, l am new to this forum. Can someone assist me as l have tried navigating but with no success.
1.How do you guys create new posts that we end up bennefitting from.
2.I want to setup a mail server on ubuntu 12.04 with the following. 
   -Dovecot+Postfix+Spamassassin+Clamav+Amavis+Horde 
3.The server should use mbox instead of maildir but all docs l have found so far use maildir
4.If l have to stick to maildir, will that not affect horde
5.The server should scan outgoing mail for spam and bounce it back to local user if it has spam otherwise we end up being black listed.
Can any one assist with easy step by step comprehensive set-up or refer me to easy guides

Hi tangozopo and welcome to Ubuntu forums,

in order to start a new thread you go to the appropriate section 
in this case I would say Server platforms here :[http://ubuntuforums.org/forumdisplay.php?f=339]("http://ubuntuforums.org/forumdisplay.php?f=339")

Then look in then upper left the will be a botton that says [HTML]new thread[/HTML] click on that to start you new topic.

here are a couple pages that may be of help to you :
[http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/]("http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/")

[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/]("http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/")

---

### Post by tangozopo on 2012-09-27
> **kc1di said:**
> Hi tangozopo and welcome to Ubuntu forums,

in order to start a new thread you go to the appropriate section 
in this case I would say Server platforms here :[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Then look in then upper left the will be a botton that says [HTML]new thread[/HTML] click on that to start you new topic.

here are a couple pages that may be of help to you :
[http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/)

[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

Thanks so much

---

### Post by kc1di on 2012-09-28
Your Welcome tangozopo and enjoy :)

---

### Post by h66m9d on 2012-09-28
Thanks to all :KS

---

