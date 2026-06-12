---
title: "Force ufw firewall to log only to a specific log file?"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by kimchi on 2010-10-28
How can I make ufw log only to a specific log file, such as "/var/log/ufw.log"?

The ufw man page says "Logged packets use the LOG_KERN syslog facility." This seems to redundantly fill up "/var/log/ufw.log", /var/log/kern.log and /var/log/messages with identical ufw log entries. I have ufw logging set to low. There doesn't seem to be any more log configuration options, either via the ufw command line or the handful of ufw configuration files I found.

---

### Post by wojox on 2010-10-28
Try and run

```
cat /var/log/messages | grep UFW
```

You turned it on right?

```
sudo ufw logging on
```

---

### Post by kimchi on 2010-10-28
> **wojox said:**
> You turned it on right?

Yes... logging is definitely working. Like I said, currently it's logging to multiple files, filling up messages and kern.log with identical entries as ufw.log. 

I want to only log to ufw.log.

---

### Post by kimchi on 2010-11-01
*bump*

I've been Googling and I haven't really found anything helpful other than a couple others complaining about the same thing.

---

### Post by zang3tsu on 2010-11-24
This might be helpful:

[http://vincom2.wordpress.com/2010/04/07/logging-ufw-to-a-seperate-logfile/]("http://vincom2.wordpress.com/2010/04/07/logging-ufw-to-a-seperate-logfile/")

I tested it and it works.

---

