---
title: "How to set up multiple IP addresses in Ubuntu"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by killthebabysitter on 2011-05-27
After some searching I finally got my NetworkManager applet behaving the way I want! So I figured I'd share with others interested.

I'm a developer by day and deal with mostly ethernet appliances, so I wanted an all inclusive ethernet set up so I could have DHCP when availalbe as well as a variety of other static IP addresses when I'm in the field. (It's a pain to have to switch manually with Network Manager IMO)

So how I did it was to go to: 
System->Preferences->Network Connections

I have only one profile called Auto eth0
It is set up to have a Manual IP address of 127.0.0.2 netmask 255.0.0.0 (Really doesn't matter what IP it is as it will be overwritten by our script later)

So now when you plug in an ethernet cable NetworkManager will automatically connect you with an IP of 127.0.0.2.

Now we need to create a script that contains all of the static IP addresses we want, and to request a dhcp lease. NetworkManager is pretty clever and contains a dispatcher that calls all the scripts within /etc/NetworkManager/dispatcher.d/ when a connection goes up or down.

The script (I named mine MultipleIP.sh):

(You can just change the line "eth0" to whatever interface you would like, or you could get even more advanced and do this for multiple interfaces as well.)
```

#!/bin/bash
# Place this script in /etc/NetworkManager/dispatcher.d to have it run everytime eth0 goes up
# Create a NetworkManager profile with a static IP, as the static IP will 
# be overwritten with a dhcp IP so you always have static IP's regardless of
# whether or not you got a dhcp lease
IF=$1
STATUS=$2

function SetMultipleIPs()
{
    ifconfig $IF:0 192.168.0.109 netmask 255.255.255.0
    ifconfig $IF:1 192.168.1.109 netmask 255.255.255.0
    ifconfig $IF:25 192.168.25.109 netmask 255.255.255.0
    ifconfig $IF:169 169.254.1.109 netmask 255.255.255.0
    
    dhclient3 $IF &
}
 
if [ "$IF" == "eth0" ]
then
    case "$2" in
        up)
        logger -s "Multiple IP Script up triggered"

        # Set IPs since our link is up    
        SetMultipleIPs
        ;;
        down)
        logger -s "Multiple IP Script down triggered"

        ;;
        pre-up)
        logger -s "Multiple IP Script pre-up triggered"

        ;;
        post-down)
        logger -s "Multiple IP Script post-down triggered"

        ;;
        *)
        ;;
    esac
fi

```
(If you don't want logging, just remove the logger lines)

Save the script and make it executable:
sudo chmod +x MultipleIP.sh

Now copy the script into /etc/NetworkManager/dispatcher.d/
sudo cp MultipleIP.sh /etc/NetworkManager/dispatcher.d/

Now try it out, disconnect and reconnect your network and you should have all of your static IPs and a dhcp lease if available. 

The best part about this script for me is NetworkManger always crapped out if it couldn't get a dhcp lease, where this script allows me to always have my static IPs and if I get a dhcp lease great, if not at least I have my static IPs.

Enjoy

---

