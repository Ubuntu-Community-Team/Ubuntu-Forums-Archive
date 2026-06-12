---
title: "Problems with VPN on virtual guest computer. Please check code"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by BudworthTDog on 2012-04-23
I use hidemyass.com VPN service for downloading torrents. I use the following script to connect. If the VPN service drops then my entire connection drops so my IP doesn't leak. Everything works fine with it but I have recently been trying to use it in a virtual box guest computer. The VPN service works fine on the guest computer when I use the default script, the only thing about that is if the service is to drop it just switches over to my normal connecting and my IP will leak. Using this special code it will connect to the VPN service but I can't surf, download, or even ping anything.

Ultimately what I want to do is use my normal real IP on the host computer and the VPN service on my guest computer. I am using my ethernet connection. I'm guessing there is just something that needs tweaked with the code but I'm not sure what it is.   

#!/bin/bash

cd `dirname $0`
if [[ $1 == '-l' ]]
then
  curl -s "http://vpn.hidemyass.com/vpnconfig/countries.php"
else
  sudo iptables -F

     COUNTRY=`echo $1 | sed 's/ /+/g'`
   curl -s "http://vpn.hidemyass.com/vpnconfig/client_config.php?win=1&loc=$COUNTRY" > client.cfg

 # Allow traffic to any HMA server.
  for remote in `cat client.cfg | awk '/remote [0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/ { print $2; }'`;
  do
    REMOTE_IP=`echo $remote | cut -d ':' -f 1`
    sudo iptables -A INPUT -s $REMOTE_IP -j ACCEPT
  done

  # Allow local traffic.
  sudo iptables -A INPUT -s 10.0.0.0/8 -j ACCEPT
  sudo iptables -A INPUT -s 172.16.0.0/12 -j ACCEPT
  sudo iptables -A INPUT -s 192.168.0.0/16 -j ACCEPT

  # Disallow everything else.
  sudo iptables -A INPUT ! -i tun+ -j DROP

# Allow traffic from any HMA server.
  for remote in `cat client.cfg | awk '/remote [0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/ { print $2; }'`;
  do
    REMOTE_IP=`echo $remote | cut -d ':' -f 1`
    sudo iptables -A OUTPUT -d $REMOTE_IP -j ACCEPT
  done

  # Allow local traffic.
  sudo iptables -A OUTPUT -d 10.0.0.0/8 -j ACCEPT
  sudo iptables -A OUTPUT -d 172.16.0.0/12 -j ACCEPT
  sudo iptables -A OUTPUT -d 192.168.0.0/16 -j ACCEPT

  # Disallow everything else.
  sudo iptables -A OUTPUT ! -o tun+ -j DROP

  sudo openvpn --config client.cfg
fi

---

