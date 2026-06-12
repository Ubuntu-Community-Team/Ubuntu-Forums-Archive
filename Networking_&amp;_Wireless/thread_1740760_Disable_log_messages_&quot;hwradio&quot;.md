---
title: "Disable log messages &quot;hwradio&quot;"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by Dave_L on 2011-04-27
[Ubuntu 10.04]

Every 60 seconds, 24 hours a day, a line like the following is logged to /var/log/messages and some of the other system logs:

```
Apr 27 11:37:48 HOSTNAME kernel: [DDDDDD.DDDDDD] ================>r8192_wx_set_scan(): hwradio off
```

That's with the wireless card disabled (since I'm using a wired network). If the wireless card is enabled, the message changes to "hwradio on".

How can I disable these messages?

---

### Post by Dave_L on 2011-04-28
I haven't found out how to turn off the messages, but I've used a workaround to divert them to their own log file. In case anyone's interested, here are the details:

Created file /etc/rsyslog.d/40-hwradio.conf with following contents:

```
# Log kernel generated hwradio log messages to file
:msg,contains,"r8192_wx_set_scan(): hwradio" /var/log/hwradio.log

# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated hwradio log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
& ~
```

Restarted rsyslog service:
```
sudo service rsyslog restart
```

Created file /etc/logrotate.d/hwradio with contents:
```
/var/log/hwradio.log {
        rotate 4
        weekly
        compress
        missingok
}
```

---

