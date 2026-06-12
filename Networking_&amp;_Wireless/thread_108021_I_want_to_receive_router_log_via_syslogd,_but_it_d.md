---
title: "I want to receive router log via syslogd, but it doesn't work."
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2005-12-24
[EDIT]
I found a workaround. Look [here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=607798").
[/EDIT]

Hi. I am using a wlan router/dsl modem (GoldLine wireless adsl router, I think it's from CompuShack) and have it set up to send its log to my laptop's IP. On the laptop, I changed /etc/init.d/sysklogd  to start syslogd with the -r parameter. But I still don't receive any log messages from my router. Is there anything more I need to change?

---

### Post by ubuntuuser on 2005-12-25
Ok, I played a little bit with it. Now I know that my router IS sending the messages to my laptop (I captured some auth.info pakets with ethereal) and they ARE logged. I simply could not see the messages on my terminal window (where I have tail -f /var/log/messages running) because the messages are stored in a different file. Well, actually are they split onto two or three files, depending on the kind of syslog message that is received. Is there any way I could filter all syslog messages coming from my router to a seperate file?

---

