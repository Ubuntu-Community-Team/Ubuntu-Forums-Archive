---
title: "dynamic Firewall"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Seddy on 2010-01-13
Currently I've installed Ubuntu 9.10 Desktop Edition and my PC is connected to the internet with every port forwarded to it.
This is what I want to do with a Firewall:
-block every incoming traffic from every IP except on one port where every IP is allowed
-execute a console-command to temporarily allow incoming traffic for an specific IP for all ports(or a list of ports)
-block the allowed IP after some idle-time

Is it possible to set something like this up?
Currently I have installed firestarter, but it seems to have just very little console-command interaction. 

Thanks for your help!

---

### Post by Lars Noodén on 2010-01-13
Yes, see IP Tables.  You will need to be, or become, at least a little comfortable with very simple shell scripting.  

To have different filter rules, one way is to set up different scripts.  

To run the iptables scripts as a regular user and still have them take effect, you will need to set that up in [sudoers](http://manpages.ubuntu.com/manpages/karmic/en/man5/sudoers.5.html)

```

# for example the lines below in /etc/sudoers
# allows anyone in the group "filter" do run these scripts:

%filter ALL = (ALL) PASSWD: /usr/local/sbin/filterscript1.sh "", \
                            /usr/local/sbin/filterscript2.sh ""

```

To have the settings change, use [at](http://manpages.ubuntu.com/manpages/karmic/en/man1/at.1.html) or [cron](http://manpages.ubuntu.com/manpages/karmic/en/man8/cron.8.html).

---

### Post by Lars Noodén on 2010-01-13
Here is what I used for a while.  It may not be the best intro to either shell scripting or iptables, but pieces of it might be useful.  

Please note that if your services cannot safely operate without the crutch of a firewall or filter, then it shouldn't be connected to the net in the first place.  

```

#/bin/sh
# basic IP Tables-based IPv4 filter
# Lars Nooden, lars.curator@gmail.com
# 25 Jan 2009

# update-rc.d firewall start 20 2 3 4 5 . stop 20 1 6 S .

# See: 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/initscrcomconv.html 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/facilname.html

# For a non-init.d option, See Also:
# https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup

### BEGIN INIT INFO
# Provides:          firewall
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start packet filter at boot time
# Description:       Enable packet filter provided by IP Tables.
### END INIT INFO

# load script logging functions
. /lib/lsb/init-functions

start_4filter()
{
   ## 
   ## set default policies
   iptables --policy INPUT   DROP;		# has to be DROP, 
   iptables --policy OUTPUT  DROP;		# default policy 
   iptables --policy FORWARD DROP;		# won't use REJECT

   ##
   ## start fresh
   iptables -Z;	# zero counters
   iptables -F;	# flush (delete) rules
   iptables -X;	# delete all extra chains

   ##
   ##
   iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
   iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT
   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   iptables -A INPUT   -j REJECT;	# hack for changing default policy
   iptables -A OUTPUT  -j REJECT;	# from DROP to REJECT
   iptables -A FORWARD -j REJECT;	# 


}

stop_4filter()
{
   ## 
   ## set default policies to let everything in
   iptables --policy INPUT   ACCEPT;
   iptables --policy OUTPUT  ACCEPT;
   iptables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   iptables -Z;	# zero counters
   iptables -F;	# flush (delete) rules
   iptables -X;	# delete all extra chains

}

##
###
##

start_6filter()
{
   ##
   ## set default policies
   ip6tables --policy INPUT   DROP;	# has to be DROP,
   ip6tables --policy OUTPUT  DROP;	# default policy
   ip6tables --policy FORWARD DROP;	# won't use REJECT

   ##
   ## start fresh
   ip6tables -Z;	# zero counters
   ip6tables -F;	# flush (delete) rules
   ip6tables -X;	# delete all extra chains

   ##
   ##
   ip6tables -A INPUT -i lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   ip6tables -A OUTPUT -o lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   ip6tables -A INPUT   -j REJECT;	# hack for changing default policy
   ip6tables -A OUTPUT  -j REJECT;	# from DROP to REJECT
   ip6tables -A FORWARD -j REJECT;	#

}

stop_6filter()
{
   ##
   ## set default policies to let everything in
   ip6tables --policy INPUT   ACCEPT;
   ip6tables --policy OUTPUT  ACCEPT;
   ip6tables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   ip6tables -Z; # zero counters
   ip6tables -F; # flush (delete) rules
   ip6tables -X; # delete all extra chains

}

start_ssh()
{
   ip6tables -N SSH;	# create chain
   iptables  -N SSH;	# create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;

   # accept incoming connections, in moderation
   ip6tables -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 
   iptables  -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 

   # allow finite new connections per timelimit
   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT

   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
}

start_squid()
{
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 3128 -j ACCEPT
   iptables  -I INPUT -i eth0 -p tcp --destination-port 3128 -j ACCEPT
}

##
###
##

main()
{
   case "$1" in
      start)
           log_daemon_msg "Loading packet filter rules" "iptables"
           start_4filter;
           start_6filter;
           log_end_msg $?
       ;;
      addssh)
           log_daemon_msg "Adding packet filter rules + ssh" "iptables"
           # start_4filter;
           # start_6filter;
	   start_ssh;
           log_end_msg $?
       ;;
      addsquid)
           log_daemon_msg "Adding packet filter rules + squid" "iptables"
           # start_4filter;
           # start_6filter;
	   start_squid;
           log_end_msg $?
       ;;
     stop)
           log_daemon_msg "Clearing packet filter rules" "iptables"
           stop_4filter;
           stop_6filter;
           log_end_msg $?
       ;;
     force-reload|restart)
       $0 stop
       $0 start
       ;;
     *)
       echo "Usage: $0 {start|addssh|addsquid|stop|restart|force-reload}"
       exit 1
       ;;
   esac
}

# allow several parameters to be used, in sequence
while test -n "$1";  do
  main $1;
  shift;
done;


exit 0

```

---

