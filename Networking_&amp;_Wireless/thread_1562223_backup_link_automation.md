---
title: "backup link automation"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by roskiy on 2010-08-27
Hello,
I am in the hope to setup automated backup connectivity for my small office. Already spent one week googling for solution that really works for my situation but still no good solution

Currently i have 2 Internet uplinks
a= Wired ADSL 1.5 Mibs async
b= Wireless ISP with 5 Mibs sync /248 network
i use $b as my primary connection to network and in cases when it fails going for the second

All office computers connect to internet using Ubuntu Server with 2 eth interfaces (eth1 facing internet IP x.x.x.x, eth0 to LAN) as a gateway which masquerade LAN IP's IP 172.16.0.1

and connection $b is provided by router with 2 interfaces 
1st (some sort of ADSL) facing internet
and eth interface facing lan. router is providing masquerading too

when provider a line goes down i have to issue on ubuntu gateway commands to change it's default gateway

```
route del default gw
route add default gw 172.16.0.4

```
which i confine into script isp2.sh

and when conection reestablished i issue

```
route del default gw
route add default gw x.x.x.y

```(where x.x.x.y is ip of ISP gateway)
that form script isp1.sh

i have tried to automate check for connection failure and came up with something that resulted not to work.

```
test "$(whoami)" != 'root' && (echo you are using a non-privileged account; exit 1)
# space separated hosts to ping
# this is pigable ISP host
HOSTS="10.0.8.1" 
# location where logs and status files will be saved
WORKDIR=~/
# how many pings to send
COUNT=4

for myHost in $HOSTS
do
  count=$(ping -I eth1 -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  STATE=$(cat $WORKDIR'link_state')
  if [ $count -eq 0 ]
        then
        if [ "$STATE" != "Backup" ]
        then
                echo $(date)' Main Uplink Failed '
                echo $(date)' Main Uplink Failed ' >> $WORKDIR'pinglog.log'
                sh $WORKDIR'isp2.sh'
                echo 'Backup'>$WORKDIR'link_state'
        else
                echo 'Still on backup'>>null
        fi
  else
        if [ "$STATE" != "Normal" ]
        then
                echo $(date)' Main Uplink Reestablished '
                echo $(date)' MainUplink Reestablished ' >> $WORKDIR'pinglog.log'
                sh $WORKDIR'isp1.sh'
                echo 'Normal'>$WORKDIR'link_state'
        else
                echo 'Normal Operation'>>null
        fi
  fi
done

```

now the problem:
for some reason when automated scripts goes for backup it never return to normal operation. Ping stops to work. 

I feel like there should be a simple way but i am new to linux and unaware of it.

Any suggestions?

---

