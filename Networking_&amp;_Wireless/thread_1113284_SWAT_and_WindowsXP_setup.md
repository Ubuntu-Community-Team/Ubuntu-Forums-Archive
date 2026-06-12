---
title: "SWAT and WindowsXP setup"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Steve R. on 2009-04-01
I have a network consisting of WindowsXP computers and a UBUNTU computer, I would like to see the files on my UBUNTU computer from the XP computer.  I installed SWAT and my UBUNTU computer shows up correctly on my network neighborhood.  However, when clicking on the UBUNTU computer from my XP computer I was asked for a password from the UBUNTU computer. Since I would like an open share system, where I can see the files on the UBUNTU computer, I played around with SWAT some. Now I am only getting an "ACCESS DENIED" message. That implies that I somehow screwed up the "SHARE" options in SWAT.  So:
1. Any thoughts on how SWAT should be configured?
2. Can I access the files on the UBUNTU computer without having to actually login? (ie, the resources are shared (visible and accessible) on the network.)

---

### Post by Steve R. on 2009-04-01
Problem Fixed. I guess getting some sleep and waiting a while allowed me to resolve the issue.  In SWAT under "GLOBAL", I reset the "SECURITY" setting to "SHARE".

Also, in looking at various versions of /etc/xinetd.d/swat, some had the word "groups" and "protocol". Doesn't look like these are necessary, but I added them anyway.  Also, for the version of UBUNTU (8.04) that I have you cannot log in as root as it has root disabled. Of course that line of code could be removed. I simply used my regular user login. 

#default: off
# description: SWAT is the Samba Web Admin Tool.  Use SWAT \
#               to configure your Samba Server. To use SWAT. \
#               connect to port: 901 with your favorite web browser.
service swat
{
        port            = 901
        groups          = yes
        disable         = no
        socket_type     = stream
        protocol        = tcp
        wait            = no
        # Use only_from if you want to restrict access \
        # only_from = localhost
        user            = root
        server = /usr/sbin/swat
        log_on_failure += USERID
}

---

