---
title: "default route removed after suspending"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by jal on 2011-08-02
Hi all, I have an annoying little problem with my network routing table,

the default gateway route is removed whenever the computer suspends.
This is for the wireless nic, I never noticed the problem with wired.
When I fire up the machine I have to  
```
sudo route add default gw router
```
(router is in hosts)

I've added this to interfaces
```
up route add 0.0.0.0 gw 192.168.0.1 dev wlan0
```
to no avail.

No routing is specified in the network manager dialogue for either nic; in fact I've tried to enter it but it doesn't seem to keep the 0.0.0.0 specification (which is what 'default' seems to be).

10.10(maverik)

tia

---

### Post by jal on 2011-08-16
just for information, I can duplicate the fault simply by 

```
sudo /etc/init.d/network-manager stop
sudo /etc/init.d/network-manager start
```

drops the default gateway (my nat router)

---

### Post by jal on 2011-08-24
this is from the kern.log, seems to only check for IPv6 routers; of which I have none:

```
Aug 24 17:31:32 sig kernel: [25413.941059] wlan0: authenticate with xx:xx:11:f4:xx:xx (try 1)
Aug 24 17:31:32 sig kernel: [25413.942847] wlan0: authenticated
Aug 24 17:31:32 sig kernel: [25413.942872] wlan0: associate with xx:xx:11:f4:xx:xx (try 1)
Aug 24 17:31:32 sig kernel: [25413.945151] wlan0: RX AssocResp from xx:xx:11:f4:xx:xx (capab=0x431 status=0 aid=1)
Aug 24 17:31:32 sig kernel: [25413.945154] wlan0: associated
Aug 24 17:31:32 sig kernel: [25413.972394] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 24 17:31:43 sig kernel: [25424.544066] wlan0: no IPv6 routers present
```

---

### Post by sbraz on 2011-08-24
does **route add default gw router** fix the problem?
if so, you can put a script like this in /etc/pm/sleep.d/
```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)
**	route add default gw router**
        ;;
    *)
        ;;
esac
exit $?

```

---

### Post by jal on 2011-08-26
tried this is sleep.d

```
	route >> /tmp/fixit.log
        echo $(date) fixed >> /tmp/fixit.log
	route add default gw router
	route >> /tmp/fixit.log
```

but, here's the disappointing result

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
Fri Aug 26 16:39:17 NZST 2011 fixed
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

so network config is happending later in the piece.

---

### Post by sbraz on 2011-08-26
this is a script i used some time ago i copied you.
```
root@sbraz-netbook:/etc/pm/sleep.d# cat 99_resume-wireless.OLD 
#!/bin/bash
case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)
        restart network-manager
	sleep 1
	ifconfig eth1 up
	sleep 1
	rfkill unblock wifi
	sleep 1
	nmcli nm wifi on
        ;;
    *)
        ;;
esac
exit $?
```
maybe calling **restart network-manager** will fix your problem? :(

---

### Post by jal on 2011-08-27
sbraz, thank you for the script. 

Although it wasn't a fix (actually, it did work as designed, but the routing issue remained) the rfkill and nmcli were good tools to know about.

With the script I was able to do some experiments to narrow the problem, and I now believe that the problem lies with my lan setup and not the laptop network configuration.

I am running two routers, a wired one connected to the ISP's modem for WAN, and another wireless router connected to the LAN only.

While playing around, instead of my normal fix: 
route add default gw router
I tried this: 
sudo dhclient

which did set up the routing, however the default route was through the wireless router instead of the wired router.

So I'm going to have another look at the routers' setup now.

Thanks for your help.

---

### Post by sbraz on 2011-08-27
try setting the ip manually on your wireless connection, without specifying the default gateway.

[[IMG]http://img97.imageshack.us/img97/5830/screenshoteditingwiredc.th.png[/IMG]](http://imageshack.us/photo/my-images/97/screenshoteditingwiredc.png/)

---

### Post by jal on 2011-08-29
> **sbraz said:**
> try setting the ip manually on your wireless connection, without specifying the default gateway.

[[IMG]http://img97.imageshack.us/img97/5830/screenshoteditingwiredc.th.png[/IMG]](http://imageshack.us/photo/my-images/97/screenshoteditingwiredc.png/)

That was how it was set up, but I thought that I should double check. 

It was... so going on the premise that if nothing is ventured, nothing can be gained, I went ahead and set the default gateway.

It worked! 

sbraz, thank you very much for your help. 
This issue is now solved PEBKAC

---

