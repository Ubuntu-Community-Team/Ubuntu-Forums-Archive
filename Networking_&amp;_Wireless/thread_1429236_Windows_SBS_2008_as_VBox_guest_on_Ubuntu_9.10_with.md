---
title: "Windows SBS 2008 as VBox guest on Ubuntu 9.10 with LikewiseOpen and ntpd"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by LinxPatrick on 2010-03-13
I would like to put my Ubuntu 9.10 host machine onto my Windows SBS 2008 domain but use the Ubuntu 9.10 host as a time server. The Windows SBS 2008 server is a VirtualBox guest machine and its system time is unstable (runs slow).
 
The setup is this:
Host: Ubuntu 9.10
- LikewiseOpen to join to the Windows domain
- ntpd to sync the host's time to four different time servers (but not the SBS box)
- VirtualBox 3.14
 
Guest: Windows SBS 2008
- VirtualBox 3.14 guest
- Domain Controller
- w32time server enabled (client is disabled)
- The only server for w32time is the Ubuntu 9.10 host
 
 
The problem with the setup is that using LikewiseOpen to join the host to the domain, the ntpd service automatically attempts to synchronize it's time from the domain controller. On the other hand, the domain controller is a VirtualBox guest and its time is unstable so it attempts to synchronize from the host machine. This creates a time loop and causes the host's time to be all over the place but consistently behind the actual time.
 
If the Ubuntu 9.10 host is not joined to the domain, the host clock stays in sync with the external time servers and the VirtualBox time service keeps the Windows SBS 2008 time in sync with the host.
 
The ntp.conf file on the Ubuntu 9.10 host is configured as follows:
 
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help
tinker panic 0
driftfile /var/lib/ntp/ntp.drift
 
# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable
 
# You do need to talk to an NTP server or two (or three).
server time-a.timefreq.bldrdoc.gov #iburst
server wwv.nist.gov #iburst
server utcnist2.colorado.edu #iburst
server time.nist.gov #iburst
 
# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details. The web page <[http://support.ntp.org/bin/view/Support/AccessRestrictions](http://support.ntp.org/bin/view/Support/AccessRestrictions)>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.
restrict time-a.timefreq.bldrdoc.gov mask 255.255.255.255 nomodify notrap noquery
restrict [www.nist.gov]("http://www.nist.gov") mask 255.255.255.255 nomodify notrap noquery
restrict utcnist2.colorado.edu 255.255.255.255 nomodify notrap noquery
restrict time.nist.gov mask 255.255.255.255 nomodify notrap noquery
 
# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1
fudge 127.0.0.1 stratum 10
# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust
restrict 192.168.11.0 mask 255.255.255.0 nomodify notrap
 
# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255
#broadcast 192.168.11.255
# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines. Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient
keys /etc/net/keys
 
 
I suspect a modification needs to be made to the ntp.conf file to prevent (restrict) ntpd from trying to sync to the domain controller when the host is joined to the domain but I will ask my question in a more generic manner. What do I need to do to prevent the Ubuntu 9.10 host from attempting to sync with the Windows 2008 server while still joining the host to the domain using LikewiseOpen?

---

