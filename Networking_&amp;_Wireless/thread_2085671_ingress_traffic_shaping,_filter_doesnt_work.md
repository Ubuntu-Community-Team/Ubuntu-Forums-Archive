---
title: "ingress traffic shaping, filter doesnt work"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2012-11-18
hi,


playing around with traffic shaping, somehow my ingress class 1:40 never gets any traffic.

iptables -t mangle -L -v 

shows that iptables marks packages but tc never puts them into 1:40, why?
this should put the marked (iptables mark) traffic into 1:40
```

tc filter add dev $indev parent 1: protocol ip handle 1 fw flowid 1:40

```but somehow it doesnt....any ideas?

traffic shaping script is for a openwrt AA box, hence the pppoe-wan.
```

#!/bin/bash

dev=pppoe-wan #outgoing traffic
indev=ifb0 #incoming traffic ( really eth0, but with this "workaround" you can use egress for inbound traffic )



for module in ifb sch_sfq sch_htb sch_ingress act_mirred ipt_mark cls_u32 cls_fw;
do
if lsmod|grep $module 2>&1 >/dev/null; then
    echo "already loaded"; 
    else insmod $module; 
fi
 
done


#in kbit
downlink=1720  #~210kbyte/s   (mehr machbar, aber zum testen extra niedrig gewählt)
uplink=245 #~30kbyte/s   recht hoch gewählt, funktioniert?







upload() {
    echo "setting up upload..."
                                                                                  
        # install root HTB, point default traffic to 1:20:                     
        tc qdisc add dev $dev root handle 1: htb default 20                        
                             
        # shape everything at $uplink speed - this prevents huge queues in your 
        # DSL modem which destroy latency:                                        
        tc class add dev $dev parent 1: classid 1:1 htb rate ${uplink}kbit burst 6k
                                           
        # high prio class 1:10:                                                    
        #20kb/s                                                                    
        tc class add dev $dev parent 1:1 classid 1:10 htb rate $(($uplink*2/3))kbit \
        burst 6k prio 1 ceil ${uplink}kbit
                                                                                       
        # bulk & default class 1:20 - 10kb/s                                       
        tc class add dev $dev parent 1:1 classid 1:20 htb rate $(($uplink*1/3))kbit \
           prio 2
      
                                                                                   
        # Stochastic Fairness for bulk:                                  
        tc qdisc add dev $dev parent 1:20 handle 20: sfq perturb 10
                                                                       
    #gaming traffic into "high prio" class
    tc filter add dev $dev parent 1: protocol ip handle 2 fw flowid 1:10
}


upload_filter() {
        #get outgoing gaming traffic
        #192.168.11.11 is the pc used for games
        #most shhooters like bf2/bf3/bc2/css use UDP on a range of high ports
        #this assumes that you only use TS3 for voice communication - which also uses UDP
        #9987 is the TS3 servers port, so everything else thats udp is assumed to be gaming traffic
        #this also captures DNS but there should be no request while gaming
        
        iptables -t mangle $1 POSTROUTING -p udp ! --dport 9987 -s 192.168.11.11 -j MARK --set-mark 2
}



download() {
    ip link set dev ifb0 up
    tc qdisc add dev $dev handle ffff: ingress
    tc filter add dev $dev parent ffff: protocol ip u32 match u32 0 0 action mirred egress redirect dev ifb0

    tc qdisc add dev $indev root handle 1: htb default 50

    tc class add dev $indev parent 1: classid 1:1 htb rate ${downlink}kbit burst 1k

    # high prio class 1:40:
    tc class add dev $indev parent 1:1 classid 1:40 htb rate $(($downlink/2))kbit \
           burst 1k prio 1 ceil ${downlink}kbit

    # bulk & default class 1:50 - gets A LOT less speed
    tc class add dev $indev parent 1:1 classid 1:50 htb rate $(($downlink/2))kbit \
           burst 1k prio 2

    # Stochastic Fairness for bulk
    tc qdisc add dev $indev parent 1:50 handle 50: sfq perturb 10

    # gaming traffic (none of the filters below work)
    #tc filter add dev $indev parent 1: protocol ip handle 1 fw flowid 1:40
    tc filter add dev $indev parent ffff: protocol ip handle 1 fw flowid 1:40
}


download_filter() {
    # get incoming gaming traffic
    # see explanation in upload_filter
    iptables -t mangle $1 POSTROUTING -p udp ! --sport 9987 -d 192.168.11.11 -j MARK --set-mark 1
}



start() {
        stop
    upload
        download
          download_filter -I
          upload_filter -I
}

stop() {
    # clean existing down- and uplink qdiscs, hide errors
    tc qdisc del dev $dev root    2> /dev/null > /dev/null
    tc qdisc del dev $dev ingress 2> /dev/null > /dev/null
    tc qdisc del dev $indev root    2> /dev/null > /dev/null
    tc qdisc del dev $indev ingress 2> /dev/null > /dev/null
    download_filter -D
    upload_filter -D
}


restart() {
    stop
    sleep 1
    start

}

show() {
    
    # Display status of traffic control status.
    echo "qdisc"
    echo "out:"
    tc -s qdisc ls dev $dev
    echo "in:"
    tc -s qdisc ls dev $indev
    echo ""
    echo ""
    echo "classes:"
    echo "out":
    tc -s class show dev $dev
    echo "in:"
    tc -s class show dev $indev
    echo ""
    echo ""
    echo "filters:"
    echo "out:"
    tc filter list parent ffff: dev $dev
    echo "in:"
    tc filter list parent ffff: dev $indev
}



case "$1" in

    start)

        echo -n "Starting bandwidth shaping: "
        start
        echo "done"
        ;;

    stop)

        echo -n "Stopping bandwidth shaping: "
        stop
        echo "done"
        ;;

    restart)

        echo -n "Restarting bandwidth shaping: "
        restart
        echo "done"
        ;;

    show)

        echo "Bandwidth shaping status::"
        show
        echo ""
        ;;

    *)

        pwd=$(pwd)
        echo "Usage: test-ts.sh {start|stop|restart|show}"
        ;;

esac

exit 0

```

---

### Post by KisteBecks on 2012-11-19
As written here:
[http://www.mail-archive.com/lartc@mailman.ds9a.nl/msg15545.html](http://www.mail-archive.com/lartc@mailman.ds9a.nl/msg15545.html)

this wont work because if ifb.
at least mark doesnt work and thats probably also the reason classify wont

---

