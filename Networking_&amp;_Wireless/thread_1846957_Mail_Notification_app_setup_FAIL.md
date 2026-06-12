---
title: "Mail Notification app setup FAIL"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by Osmodivs on 2011-09-19
Hello.
I am trying to set up an account in the **Mail Notification** app from Ubuntu    [http://www.nongnu.org/mailnotify/ ]("http://www.nongnu.org/mailnotify/")
I found in several web sites tha say there is a way to check your_** Hotmail**_ mail via **POP3**, but when I try to configure the connection type, there is no way to change the settings there. I need to input this settings according to this site [http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/](http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/) :
```
Incoming Server: pop3.live.com
 Incoming Port: 995
 SSL Encryption: yes
 Outgoing Server: smtp.live.com
 Outgoing port: 25 (use port 587 if the default port is not working)
 Authentication: yes
 TLS Or SSL: yes
```All I get is a message: *unhandeled POP3 mailbox (unable to connect to pop3.live.com)*
I do not even know if I am filling the right text boxes with the right especifications.
This is what I have:
**General**
Mailbox type: POP3
Account:Server: pop3.live.com
Username: [EMAIL="mymail@hotmail.com"]mymail@hotmail.com[/EMAIL]
Password: &#9702;&#9702;&#9702;&#9702;&#9702;&#9702;&#9702;&#9702;&#9702;&#9702;
**Connection Type:** (here I do not have a way to change the connection type, standard is deffault)
&#9679; Standard      Port: 110
&#9675; In-band SSL/TLS   Port: 110
&#9675; SSL/TLS on separate port  Port: 995
**Mailbox Name**
&#9675;Default
&#9679;Other: smtp.live.com

Can someone _please _help me setup this app?

---

