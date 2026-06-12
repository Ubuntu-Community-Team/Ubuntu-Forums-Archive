---
title: "help with syslog messages from dd-wrt router"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by wriggary on 2009-03-20
Hi all, i'm back again.  Its hard to believe that I've been using Ubuntu for 6 months straight now.  I'm getting better, but I apparently have a lot more to learn.

So, I've managed to flash my linksys router with dd-wrt firmware, which now works wonderfully, instead of going down when too many tcp connections are happening. :P 

I've been playing around with the syslogd service on my router, and I'm not having any trouble receiving the syslog messages, they appear just fine in /var/log/messages, the catch-all log.  I also tried to set a custom rule in my syslog.conf file, so it would write the router's logs to a seperate file for later perusing, and not having to dig though days of /var/log/messages.  But I'm not sure of the syntax.  I've read the man pages, and google'd  my butt off on this one, but I can't figure out how to get log entries to go to /var/log/router.

```
#  /etc/syslog.conf	Configuration file for syslogd.
#
#			For more information see syslog.conf(5)
#			manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log

# Logging for router at 192.168.XXX.1
*192.168.XXX.1*			-/var/log/router

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files...
```

So, I added the rule *192.168.XXX.1* (replace XXX with my actual router address) on the advice from some google search.  But it seems that when i use the line :*192.168.XXX.1*, everything gets dumped to /var/log/router . not just entries from that hostname.  Could have something to do with the double asterisks.  I've also tried to enter just the ip, no asterisks, and also the router's hostname, both with and without the asterisks, and only *HOSTNAME* (again, replace with actual router hostname) would create any output.  And it was identical to /var/log/messages.

So, how exactly does one sort logs recieved from another box into their own folder without changing to another syslog util?

Many thanks!

Gary

---

