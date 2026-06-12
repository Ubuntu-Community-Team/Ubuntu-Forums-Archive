---
title: "iptables, ubuntu 10.04"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by demosthenesk on 2011-05-07
Hello,

i have some problems with iptables on ubuntu 10.04.
my default policy is DROP and i want to open "holes" on firewall according
1) to services i want as a client, example, http, ssh client etc
2) to services i want to serve as a server, example Apache, MySQL, Sendmail etc.

i made a script to start/stop the firewall but i think any rules i set they do not work.
iptables -L shows that rules exist in chains but they do not work!

my script is the next one

```

#!/bin/sh
#
# Initscript for firewall.
#
# description: Starts and stops firewall
# 
### BEGIN INIT INFO
# Provides: firewall script
# Short-Description: Starts and stops firewall
### END INIT INFO

# Check if root is running this script

if [ $(id -u) -ne 0 ] ; then
    echo "ERROR: Try to run this as root."
    # LSB specification errorcode
    exit 4
fi

#########################################
#Enable broadcast echo protection
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#Disable Source Routed Packets
for f in /proc/sys/net/ipv4/conf/*/accept_source_route; do
    echo 0 > $f
done

#Enable TCP SYN Cookie Protection
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

#Disable ICMP Redirect Acceptance
for f in /proc/sys/net/ipv4/conf/*/accept_redirects; do
    echo 0 > $f
done

#Dont send redirect messages
for f in /proc/sys/net/ipv4/conf/*/send_redirects; do
    echo 0 > $f
done

#Drop Spoofed Packets
for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
    echo 1 > $f
done

#Log packets with impossible addresses
for f in /proc/sys/net/ipv4/conf/*/log_martians; do
    echo 1 > $f
done
#########################################

flush()
{
    #Remove any existing rules from all chains
    iptables --flush
    iptables -t nat --flush
    iptables -t mangle --flush
}


accept_policy()
{
    #set default policy to accept
    iptables --policy INPUT ACCEPT
    iptables --policy OUTPUT ACCEPT
    iptables --policy FORWARD ACCEPT

    iptables -t nat --policy PREROUTING ACCEPT
    iptables -t nat --policy OUTPUT ACCEPT
    iptables -t nat --policy POSTROUTING ACCEPT

    iptables -t mangle --policy PREROUTING ACCEPT
    iptables -t mangle --policy OUTPUT ACCEPT

}


drop_policy()
{
    #set default policy to drop
    iptables --policy INPUT DROP
    iptables --policy OUTPUT DROP
    iptables --policy FORWARD DROP

    iptables -t mangle --policy PREROUTING DROP
    iptables -t mangle --policy OUTPUT DROP
}

remove_user_chains()
{
    iptables -X
    iptables -t nat -X
    iptables -t mangle -X
}


rules()
{
  ####### Allow any ssh client to any remote ssh server
  iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT
  iptables -A INPUT -p tcp --sport 22 -j ACCEPT 

  ##########################################################

}


start() 
{
    flush
    remove_user_chains
    
    #Log everything for debuging
    iptables -A OUTPUT -j LOG
    iptables -A INPUT -j LOG
    iptables -A FORWARD -j LOG

    #unlimited traffic on loopback interface
    iptables -A INPUT -i lo -j ACCEPT
    iptables -A OUTPUT -o lo -j ACCEPT
        
    drop_policy
    rules
}
  

stop() 
{   
    flush
    remove_user_chains
    accept_policy
}



restart() 
{
    stop
    start
}


case "$1" in
    start)
    start
    ;;
    stop)
    stop
    ;;
    restart)
    restart
    ;;
    *)
    echo "Usage: $0 {start|stop|restart}"
    exit 1
esac

exit 0

```even the rules for loopback interface do not applied!
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

what am i doing wrong?

i think the script is correct.
(note this script is a test one in order to understand what is wrong with the firewall)
:confused:

---

### Post by demosthenesk on 2011-05-07
to add something,

when i run the script the default policy is applied to DROP for all chains.
But the rules seems not to be applied.

So when i try to login with ssh from the firewalled pc to a ssh server everything is DROPed.
Or when i use loopback example, a browser with htp://localhost again everything is DROPed.

So i conclude that the rules do not applied!

---

### Post by jramshu on 2011-05-07
You could have used ufw to open and close ports with ease. I'm no scripter, still learning, so I can't help much with that.

---

### Post by demosthenesk on 2011-05-07
> **jramshu said:**
> You could have used ufw to open and close ports with ease. I'm no scripter, still learning, so I can't help much with that.

thanks for your interest.

i intend to make a more flexible script with iptables with features that ufw does not have.
That's why i use bash script and iptables.

i know much more for iptables than this simple script but here i wanted to ask if iptables have any bug or ubuntu in order to use iptables have a setting that i dont know.

if anyone knows about that and can read the bash script please let help me.

---

