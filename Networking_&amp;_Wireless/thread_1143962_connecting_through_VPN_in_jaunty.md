---
title: "connecting through VPN in jaunty"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by jacobian64 on 2009-04-30
Hello all
I am having problem connecting through VPN in ubuntu jaunty, I am using ifup-pptp to connect to vpn in my campus and I've got this error. 

```
kamsis@kamsis-desktop:~$ sudo ifup-pptp
[sudo] password for kamsis: 
/usr/sbin/ifup-pptp: 93: vpn: pppd started for pptp0 to 10.14.203.5: not found
Terminated
/usr/sbin/ifup-pptp: 96: ipparam: not found
/usr/sbin/ifup-pptp: 104: pptp: pppd failed to start: not found
/usr/sbin/ifup-pptp: 93: vpn: pppd started for pptp0 to 10.14.203.5: not found
```

also if you want to check my script for /usr/sbin/ifup-pptp then here it is
```
kamsis@kamsis-desktop:~$ sudo cat /usr/sbin/ifup-pptp
#!/bin/sh 
# Based on Red Hat's ppp scripts 
# MSG - yinyang@eburg.com 
# 06/28/2000 

# Changes: 
# 06/28/2000 - modified scripts from original ssh vpn scripts. 

PATH=/sbin:/usr/sbin:/bin:/usr/bin 


if [ "$1" = watch ] ; then 
shift 
DEVICE=$1 
shift 

PID=`grep -v ppp /var/run/ppp-${DEVICE}.pid` 

while ( test -e "/var/run/ppp-${DEVICE}.pid" && \ 
test -d "/proc/${PID}" ) ; do 
sleep 5s 
done 

[ -e /var/run/${DEVICE}-up ] || exit 0 
fi 


# Get the configuration for this connection 
#cd /etc/sysconfig/network-scripts 
#. network-functions 
. /etc/conf.d/ifcfg-pptp0 
CONFIG=$1 
[ -f "$CONFIG" ] || CONFIG=ifcfg-$1 
#source_config 


if [ "$2" = "boot" -a "${ONBOOT}" = "no" ]; then 
exit 
fi 


[ -x /usr/sbin/pppd ] || { 
echo "/usr/sbin/pppd does not exist or is not executable" 
echo "ifup-pptp for $DEVICE exiting" 
logger -p daemon.info -t ifup-vpn \ 
"/usr/sbin/pppd does not exist or is not executable for $DEVICE" 
exit 1 
} 

opts="lock lcp-echo-interval 30 lcp-echo-failure 4 noipdefault noauth" 
if [ "${DEFROUTE}" = yes ] ; then 
# pppd will no longer delete an existing default route 
# so we have to help it out a little here. 
route del default >/dev/null 2>&1 
opts="$opts defaultroute" 
fi 
if [ "${PEERDNS}" != no ] ; then 
opts="$opts usepeerdns" 
fi 
if [ -n "${MRU}" ] ; then 
opts="$opts mru ${MRU}" 
fi 
if [ -n "${MTU}" ] ; then 
opts="$opts mtu ${MTU}" 
fi 
if [ -n "${IDLETIMEOUT}" ] ; then 
opts="$opts idle ${IDLETIMEOUT}" 
fi 
if [ -n "${IPADDR}${REMIP}" ] ; then 
# if either IP address is set, the following will work. 
opts="$opts ${IPADDR}:${REMIP}" 
fi 
if [ "${DEBUG}" = yes ] ; then 
opts="$opts debug" 
fi 

if [ -z "${VPN_USER}" ] ; then 
(logger -p daemon.info -t ifup-pptp \ 
"vpn: VPN_USER is not defined, authentication credentials required." &)& 
exit 1 
else 
opts="$opts user ${VPN_USER}" 
fi 
if [ -z "${VPN_HOST}" ] ; then 
(logger -p daemon.info -t ifup-pptp \ 
"vpn: VPN_HOST is not defined, to whom do I connect?" &)& 
exit 1 
else 
opts="$opts remotename ${VPN_HOST}" 
fi 

(logger -p daemon.info -t ifup-pptp \ 
"vpn: pppd started for ${DEVICE} to ${VPN_HOST}" &)& 

/usr/sbin/pptp "${VPN_HOST}" updetach $opts ${PPPOPTIONS} \ 
ipparam $DEVICE linkname $DEVICE 
LINKUP=$? 

if [ "${LINKUP}" -ne "0" ]; then 
(logger -p daemon.info -t ifup-pptp \ 
"pptp: pppd failed to start" &)& 
# exit 1  
ifup-pptp 
fi 

REALDEVICE=`grep ppp /var/run/ppp-${DEVICE}.pid` 
for net in ${ROUTES}; do 
unset NETWORK NETMASK 
eval `echo $net | sed -e 's:\(.*\)/\(.*\):NETWORK=\1;NETMASK=\2:'` 
route add -net ${NETWORK} netmask ${NETMASK} dev ${REALDEVICE} 
done 

if [ "${PERSIST}" = yes ] ; then 
touch /var/run/${DEVICE}-up 
"$0" watch "${DEVICE}" "$@" & 
fi

```
can you tell me what I have done wrong? or is there any other way for me for connecting through VPN in jaunty.

actually I didn't get the above error if I use hardy and intrepid. I guest some bug must resides in jaunty that prevent me from connecting through vpn so that I can't access internet. Well any help would be appreciated. thanks

---

