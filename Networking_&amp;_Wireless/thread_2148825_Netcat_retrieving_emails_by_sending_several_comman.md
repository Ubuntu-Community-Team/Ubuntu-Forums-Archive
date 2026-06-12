---
title: "Netcat: retrieving emails by sending several commands to a pop3 server."
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by jotterand on 2013-05-26
Hi,

I'm trying to retrieve mails from a pop server with the netcat command (I need to analyse the header of these e-mails so that I can create better spam filters):

so starting a connection with netcat (nc) and then sending the commands one after the other is working well: 

```

nc pop.server.com 110 

+OK POP3 perditon ready on mail.infomaniak.ch 0002bdce

USER username
+OK USER username set, mate

PASS xxxxx
+OK You are so in

LIST
+OK 2 messages:
1 2694
2 24364
.

```

But when I try to send all these commands in one bash line, the connection seem to stop after the PASS command and the LIST command isn't achieve:

```
echo -ne "USER username\r\nPASS password\r\nLIST\r\n" | nc -i 5 pop.server.com 110

+OK POP3 perditon ready on mail.infomaniak.ch 0002bdff
+OK USER test@cttyverdon.com set, mate
+OK You are so in


```

the -ne argument of the echo command is useful to send the CRLF endline sequence. And the -i 5 argument make the nc command wait 5 second between the sending of each command. 

So my question is how can I send a batch of commands all at once to the pop server and retrieve the emails content? I would be glad if you have any suggestions to give me.

Bye Bye and thank you in advance for your help! 

I'm working with Linux Ubuntu 12.04

---

