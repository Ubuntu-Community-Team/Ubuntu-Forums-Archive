---
title: "Help with Bridged connection"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by thieaux on 2009-07-23
I'v created a bridge between eth0 and eth1 both wired connections, it works fine, perfect, but i cannot access the internet in the box that is bridged, i've used a script found around here, i am guessing it has to do with the dns, but i have a concern why is that one of the connnections gets an address instrad of the 0.0.0.0 that its suppose to ... heres the script ive use:

#!/bin/bash  
# Create global variables   
# Define Bridge Interface 
br="br0" 
# Define list of TAP interfaces to be bridged, 
# for example tap="tap0 tap1 tap2". 
#tap="tap 0" 
# Define physical ethernet interface to be bridged 
# with TAP interface(s) above. 
eth0="eth0" 
eth1="eth1"
eth_ip="10.0.0.40" 
eth_netmask="255.255.255.0" 
gw="10.0.0.1"   

start_bridge () {   
#################################   
# Set up Ethernet bridge on Linux   
# Requires: bridge-utils   
#################################    


brctl addbr $br 
brctl addif $br $eth0
brctl addif $br $eth1  
ifconfig $eth0 0.0.0.0
ifconfig $eth1 0.0.0.0  
ifconfig $br $eth_ip netmask $eth_netmask up   
#route add default gw $gw $br
} 

stop_bridge () {   
####################################   
# Tear Down Ethernet bridge on Linux   
####################################    
ifconfig $br down
brctl delbr $br    

}  
case "$1" in 
start)   
echo -n "Starting Bridge"   
start_bridge   
;; 
stop)   
echo -n "Stopping Bridge"   
stop_bridge   
;; 
restart)   
stop_bridge   
sleep 2   
start_bridge   
;; 
*)   
echo "Usage: $0 {start|stop|restart}" >&2   
exit 1   
;; 
esac

---

