---
title: "Need to be notified of IP change"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by darkenvy6 on 2011-01-11
Hey, I'm looking for a script that could somehow notify me by email or something when my extenal IP address changes. I host a game server on my ubuntubox and my dynalias doesnt change automaticly (no software to auto-change :\ )

If my IP changes again my server will be down for days untill I travel 70 miles to its location to check manually.
Help!!!

---

### Post by PatchesTheCaveman on 2011-01-12
You can use *ddclient* to automatically update your Dynamic DNS address.

Otherwise, install *sendmail*, point it to your SMTP server, and add something like this to your /etc/cron.hourly/ directory:
```
#!/bin/bash

#Set your e-mail settings
TO=me@example.com
SUBJECT=IP Change

FILE=/var/local/myip.txt

CIP=`ip address show | awk -F '[ /]+' '/inet / && $3 != "127.0.0.1" {print $3}'`
SIP=$(cat $FILE)

if [[ $SIP != $CIP ]]; then
    echo -e Subject: $SUBJECT"\r\n\r\n"$CIP | sendmail $TO
    echo $CIP > $FILE
fi
```

---

### Post by ripat on 2011-01-12
You should indeed use a dynamic DNS client and use a proper dynamic DNS service that works like DynDNS or no-IP (clients ddclient and noip2).

As for the script above, it will only give the local IP address not the external one. There is also a typo in that script:

- CIP=`ifconfig  | grep 'inet ad[COLOR="Red"]d[/COLOR]r:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`
+ CIP=`ifconfig  | grep 'inet adr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`

Finally, I count 4 pipes and external programs on that line. It might be much faster (and elegant) to use only *awk* to extract the local IP. I personally use the *ip* command that I find much faster than ifconfig:
```
ip address show | awk -F '[ /]+' '/inet / && $3 != "127.0.0.1" {print $3}'
```

---

### Post by PatchesTheCaveman on 2011-01-12
My version was correct.  The output of ifconfig does say "inet addr".  I know it works because I tested it.  :-)

Your solution is more elegant though.  I'll update my post to use that instead.

---

### Post by sj1410 on 2011-01-12
You can also use Dynamic DNS (ddns). You dont need to bother about you ip change, or check email, just point to the domain and ddclient on you ubuntu will take care about it.


[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by darkenvy6 on 2011-01-12
Wow! Installing ddclient was way easy. How do I know its running though? I mean I was able to see the list of my dyndns's so I know it can log in and all. 
Check to see if its running?

Now I'm a little short on time right now but I would like to implant the email option, its only like a once a month change but it would be a good email to recieve.

---

### Post by PatchesTheCaveman on 2011-01-12
It logs to /var/log/daemon.log so you can look in there to see if it's working properly.

Since your IP doesn't change that often, and the e-mail will be more informational than necessary, you can put it in /etc/cron.daily/ instead so it doesn't run as often.

The first time it runs it will e-mail you your IP because it doesn't have a baseline one stored to check for a change.  So you can test it that way.  If you want to force it to have to e-mail you again, just delete the /var/local/myip.txt file.

Also, instead of installing sendmail, install the *nullmailer* package instead.  It's a much easier program to configure to accomplish the same task (sending an e-mail from the command line to your SMTP server).  Apparently sendmail or nullmailer are required by ddclient so if you didn't install that yet you really want to.

---

### Post by darkenvy6 on 2011-01-12
This may be a problem. I am usually located behind a firewall that I do not have access to. I cant port forward or anything. Thus having my gaming server send me mail wouldnt be possible.

I was actually referring to email (POPS I think it is called) but I do like the idea of this mailing system.

---

### Post by PatchesTheCaveman on 2011-01-13
That won't be a problem.  You can configure *nullmailer* to use any SMTP server to send the outgoing mail.  You can use the one provided by your ISP or any free e-mail service that offers one (like Gmail).

---

