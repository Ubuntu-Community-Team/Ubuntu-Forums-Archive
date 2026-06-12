---
title: "dhclient3 option flags"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by oliver341 on 2012-05-07
I would like to edit the option flags which dhclient3 is started with. Could someone tell me where dhclient3 is called from so I can edit the option flags it is called with? Thanks.

---

### Post by chili555 on 2012-05-07
I'm not exactly sure what you're trying to do here, but I'd start in /etc/dhcp/dhclient.conf.> # Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#

<snip>


---

### Post by oliver341 on 2012-05-07
Hi chili555, thanks for your reply.

I'm trying to enable verbose logging by using the -v option flag. Can this also be done via dhclient.conf?

---

### Post by chili555 on 2012-05-07
Sorry, I'm on the way out the door. I'll check in later.

---

### Post by chili555 on 2012-05-07
You might have a look at /etc/dhcp/dhclient-enter-hooks.d/debug. It looks like you can change the variable to YES and see a debug file in /tmp/dhclient-script.debug. Will that do?

---

### Post by oliver341 on 2012-05-07
I could try that, but ideally I'd like to launch dhclient3 with the -v flag, and for that I'd have to work out where it is called from. I could rename dhclient3 to dhclient3-real, and create a script called dhclient3 which calls the dhclient3-real binary and adds the -v flag, but that's an ugly solution and surely it's possible to add the -v flag somewhere?

---

### Post by chili555 on 2012-05-07
Sorry, I'm fresh out of ideas. Aren't the logs in /var/log/syslog pretty verbose?

---

### Post by oliver341 on 2012-05-07
The dhclient logs are showing occasional DHCPNAK, i.e. the router refused to renew the lease. I was hoping adding the -v flag to dhclient might give me some clues. I'll probably try the kludge I talked about earlier.

Is it possible that dhclient3 is called via a binary with the option flags hard coded? That doesn't seem too flexible if true.

---

### Post by chili555 on 2012-05-07
I'm pretty certain it's called at /etc/init.d/networking and Network Manager.

---

### Post by oliver341 on 2012-05-07
Yeah, me too. I've hunted around though and can't find any of the existing flags, like -pf or -lf, in any of the scripts. I'm hoping someone can shed light on this.

---

