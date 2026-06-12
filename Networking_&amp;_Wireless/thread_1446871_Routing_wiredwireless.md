---
title: "Routing wired/wireless"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by RyanRahl on 2010-04-04
Hi, I've got a wireless network in my home and I have a PC downstairs with a wireless interface and a wired. The wireless works with the internet and the rest of the LAN and the wired is connected to a network printer via crossover cable. I can see the wireless from everywhere on the network but i can't see the printer IP or the wired IP. I can see the printer IP only from the local machine. this is my network setup on the machine in question:

# The primary network interface
iface wlan0 inet static
	address 192.168.0.50
	netmask 255.255.255.0
	broadcast 192.168.0.255
	network 192.168.0.0
	gateway 192.168.0.1

# The secondary network interface
iface eth0 inet static
	address 192.168.200.31
	netmask 255.255.255.0
	broadcast 192.168.200.255
	network 192.168.200.0
	gateway 192.168.0.50

and the printer IP is:

192.168.200.30

I want this PC to route traffic to the printer from other PCs on the network because it's an LPD printer and I don't want to share it. I also don't want to have to run an ethernet cable all the way down my stairs to the printer.

This command should return '1' right?:

me@localhost:~$ cat /proc/sys/net/ipv4/ip_forward

but it returns a zero. I'm not sure but i think that means im not routing. Anyone know what im doing wrong?
0

---

### Post by gzarkadas on 2010-04-04
I wish I had done it and seeing it work before but I didn't, be warned. Anyway, in the machine that connects to the printer:

1. add the following line to `/etc/sysctl.conf':

net.ipv4.ip_forward=1

You may have to restart the network or reboot; I don't remember right now. Also review your firewall rules to avoid any surprises.

2. Add entries to the routing table with the `route' command (after you verify they work make them a startup script):

route add 192.168.0.0
route add 192.168.200.30

If thins don't work as expected, have a look at [http://tldp.org/LDP/nag2/x-087-2-iface.interface.html](http://tldp.org/LDP/nag2/x-087-2-iface.interface.html); it may be of help. Your syslog may also give hints of what is not working.

---

### Post by RyanRahl on 2010-04-06
OK so i had a bunch of issues but now im connected again. I had to disable NetworkManager and reconfigure my interfaces with the help of this page:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

file as follows:

# The loopback network interface
auto lo wlan0 eth0
iface lo inet loopback

#wireless network interface
iface wlan0 inet static
wireless-essid 	wraith
wireless-	channel 6
#wireless-mode 	managed
address 	192.168.0.50
netmask 	255.255.255.0
broadcast 	192.168.0.255
network 	192.168.0.0
gateway 	192.168.0.1

#wired network interface
iface eth0 inet static
address 	192.168.200.31
netmask 	255.255.255.0
broadcast 	192.168.200.255
network 	192.168.200.0

> 1. add the following line to `/etc/sysctl.conf':

net.ipv4.ip_forward=1

You may have to restart the network or reboot; I don't remember right now. Also review your firewall rules to avoid any surprises.


I changed this and the command still returned 0, but then I ran this command: 

sysctl -w net.ipv4.ip_forward=1

and checked again and the output changed to 1. weird right?

now when i try to use the route add command it returns:

root@giger:/# route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1 dev eth0
SIOCADDRT: No such process

I also tried to add the route into the interfaces file as described here: 

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

this also did not work unfortunately and sure it has something to do with "SIOCADDRT: No such process." Im having a hard time finding a lot of info on my particular situation with this error. any ideas?

Also when I restart my network interface i get this:

root@giger:/# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         
RTNETLINK answers: No such process

but all of the network functions just fine (aside of course from the routing)

> [http://tldp.org/LDP/nag2/x-087-2-iface.interface.html](http://tldp.org/LDP/nag2/x-087-2-iface.interface.html)<===very informative btw

---

### Post by gzarkadas on 2010-04-06
I picked the following from searching in linux forums for `SIOCADDRT: No such process' (the bold inside the quote are mine):

> ...have the same problem -- basically, starting network during boot works fine but trying to restart network daemon (/etc/rc.d/network restart) results in an error like in the previous post. My **workaround is to stop the network daemon, unload/reload the network card module and the start the network daemon again**...The thread is [=&sev[0]=&pri[0]=&due[0]=&reported[0]=&cat[0]=&status[0]=open&percent[0]=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto="]here]("http://bugs.archlinux.org/task/9960?string=network+restart&project=1&type[0). There are also other opinions inside, that relate this issue with the code used inside the ifup / ifdown scripts. Since it is not an Ubuntu system, there may be differences, but it may worth to try tweaking their code (remember to make a backup of those, to recover easily if something really breaks).

[This thread]("http://ubuntuforums.org/showthread.php?t=753480") also describes another tool to use. It may worth to try.

---

### Post by gzarkadas on 2010-04-06
btw, the simple route commands I have posted did not worked?

---

### Post by RyanRahl on 2010-04-06
> btw, the simple route commands I have posted did not worked?
root@giger:/# route add 192.168.0.0
SIOCADDRT: No such device
root@giger:/# route add 192.168.200.30
SIOCADDRT: No such device

I'll check those threads thanks. :)

---

### Post by RyanRahl on 2010-04-06
I fixed this:

> **RyanRahl said:**
> 
root@giger:/# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         
RTNETLINK answers: No such process


temporarily by setting the wireless to dhcp and configuring my dhcp server to static assign 192.168.0.50 to wlan0 via MAC address. The part that gets me about this is that the ifconfig output stays the exact same whether i use static or dhcp addresses (aside of course from the RX/TX packets/bytes counters). 

Still trying to figure out why this is still happening: 

> **RyanRahl said:**
> 
root@giger:/# route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1 dev eth0
SIOCADDRT: No such process


---

### Post by gzarkadas on 2010-04-06
I though a bit about it and I believe that the routing commands in your gateway should be the following: 

# make one route to printer, 
# one for the wlan network and 
# one (default) for everything else through the wlan's gateway.
 
[COLOR=Red]route add -host 192.168.200.30 dev eth0
route add -net 192.168.0.0 netmask 255.255.255.0 dev wlan0
route add default gw 192.168.0.1 dev wlan0

[/COLOR]

---

### Post by Iowan on 2010-04-06
> **RyanRahl said:**
> Still trying to figure out why this is still happening:Wonder if it's because the default route is already defined? [This]("http://ubuntuforums.org/showthread.php?t=1050689") is the same error...

---

### Post by RyanRahl on 2010-04-21
Ok, so i kinda made some progress. I hooked up a laptop to the eth0 side of the network with a crossover and made it route out through the wireless by:

adding these lines to /etc/iptables.up.rules

```
-A PREROUTING -i eth0 -j ACCEPT
-A PREROUTING -j ACCEPT
-A PREROUTING -m state -i wlan0 --state ESTABLISHED,RELATED -j ACCEPT
```

and using eth0 as the gateway. Worked great really.
So i basically tried the same thing but in the opposite direction:

```
-A PREROUTING -i wlan0 -j ACCEPT
-A PREROUTING -j ACCEPT
-A PREROUTING -m state -i eth0 --state ESTABLISHED,RELATED -j ACCEPT
```

and used the wlan0 ip for the gateway on a wireless pc on the network and I cannot ping 192.168.200.30 pr 192.168.200.31

I must be missing something

---

### Post by gzarkadas on 2010-04-21
You instructed your firewall to accept routing packets, but you didn't supplied the routes to your ip stack. This is the part that is missing: the appropriate route commands. 

I can't add something more to this; I 'll setup a network with a configuration similar to yours and post my results when I have it working. It will take some time though, so please be patient :).

---

### Post by gzarkadas on 2010-06-07
Hi, I finally managed to get some time and experiment with my network. I made it to use my network printer with the setup that you want, with the only change that I used a switch because I didn't have a crossover cable handy.

I describe the steps that guided me to a working configuration (I actually printed a test page from another pc in my wireless network). You will have to tweak the solution to enter your specific ip and subnet values.

**Step 1**

You will first have to make the computer that connects to the ethernet subnet into a DHCP server for this subnet. The steps are described on this [guide]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html"); follow them. My configuration settings for the working example are:

[U]file: /etc/default/dhcp3-server
[/U]```
INTERFACES="eth0"
```[U]file: /etc/dhcp3/dhcpd.conf
[/U](first section described in guide just comments out lines, so is not included here; but don't forget to do it)
```

subnet 192.168.200.0 netmask 255.255.255.0 {
  range 192.168.200.100 192.168.200.254;
  option domain-name-servers 192.168.1.254;
  option domain-name "lan";
  option routers 192.168.200.1;
  option broadcast-address 192.168.200.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```**Step 2**

You must prepare the computer  that connects to the ethernet subnet to properly forward packets between the two networks. This includes:
-- Changing values to /etc/sysctl.conf to allow forwarding
-- adding network addresses for the interfaces where needed
-- adding routes to the routing table
-- adding allow rules to your firewall

Because I was just testing the concept, I made all these changes dynamically and added them to a start-up script to run at one of the available runlevels (5 in my case). I suggest to use the same way, because it will be easier in the future to disable them if you change your configuration, but instead activate this script in runlevel 2, which is the default runlevel entered during computer boot.

[U]file: /etc/init.d/routify (the init script)
[/U]Create a file in this path and paste the contents of  the code box below inside it. Then make it executable. 

The commands below will open a gedit window to paste the text. Save and close gedit after pasting and proceed to the next (chmod) command.
```

sudo touch /etc/init.d/routify
gksudo gedit /etc/init.d/routify
sudo chmod 755 /etc/init.d/routify 

```If you use other settings you will have to tweak the variables at the start. Do this while the gedit window is open, after pasting the text.

The script uses two functions to make and unmake the changes and a lock file to avoid repetitive execution should anyone use `telinit <runlevel>' consequtively or is installed in more than one runlevel.

In order to be used without having to know the exact firewall configuration, the script inserts some allow rules in front of each affected chain. It may need tweaking if you want stricter security or have a policy of deny at outbound packets; just add allow rules or modify where the rules are inserted. `man iptables' has all the necessary information. You can view your existing rules by executing `sudo iptables --list-rules | less' in a terminal window.
```

#!/bin/bash
#License GPLv3+: GNU GPL version 3 or later <[http://gnu.org/licenses/gpl.html](http://gnu.org/licenses/gpl.html)>.

# Description:
# Convert machine to a router that routes traffic from wlan0 to eth0.
# wlan0 settings: net 192.168.1.0/24   | gw 192.168.1.254 | route to eth0 
# \ but only if source is wlan0-net
# eth0  settings: net 192.168.200.0/24 | gw 192.168.200.1 | route to wlan0 and *

SUBNET="192.168.200"
GATE="${SUBNET}.1"

ETHNET="${SUBNET}.0/24"
WLANET="192.168.1.0/24"

LOCK="/var/log/routify.lock"

make_router()
{
    # configure /etc/sysctl related settings

    pushd /proc/sys/net 2>/dev/null

    echo 1 > ipv4/ip_forward
    echo 1 > ipv6/conf/all/forwarding
    echo 1 > ipv6/conf/default/forwarding

    echo 1 > ipv4/conf/all/send_redirects
    echo 1 > ipv4/conf/default/send_redirects

    echo 1 > ipv4/conf/all/accept_source_route
    echo 1 > ipv4/conf/default/accept_source_route
    echo 1 > ipv6/conf/all/accept_source_route
    echo 1 > ipv6/conf/default/accept_source_route

    popd

    # configure ip / routes / dns

    local eth_address=$(ifconfig eth0 \
        | grep "inet addr" | awk '{print $2}' | awk -F: '{print $2}')
    eth_address+='/24'    # mask

    ip addr del ${eth_address} dev eth0
    ip addr add ${GATE}/24 broadcast ${SUBNET}.255 dev eth0
    ifconfig eth0 ${GATE} broadcast ${SUBNET}.255 netmask 255.255.255.0

    route add -net ${ETHNET} eth0

    # configure firewall

    iptables -I INPUT -i eth0 -s ${ETHNET} -p udp -m udp --sport 68 --dport 67 -j ACCEPT
    iptables -I FORWARD -i eth0  -s ${ETHNET} -j ACCEPT
    iptables -I FORWARD -i wlan0 -s ${WLANET} -d ${ETHNET} -j ACCEPT
}

unmake_router()
{
    # de-configure firewall

    # If the -D commands do not work you may try to clean-restart your firewall
    iptables -D FORWARD -i wlan0 -s ${WLANET} -d ${ETHNET} -j ACCEPT
    iptables -D FORWARD -i eth0  -s ${ETHNET} -j ACCEPT
    iptables -D INPUT -i eth0 -s ${ETHNET} -p udp -m udp --sport 68 --dport 67 -j ACCEPT

    # de-configure ip / route / dns

    route del -net ${ETHNET} eth0

    local eth_address=$(ifconfig wlan0 \
        | grep "inet addr" | awk '{print $2}' | awk -F: '{print $2}')
    eth_address+='/24'    # mask

    ip addr del ${GATE}/24 dev eth0
    ip addr add ${eth_address} broadcast ${SUBNET}.255 dev eth0
    ifconfig eth0 ${eth_address} broadcast ${SUBNET}.255 netmask 255.255.255.0

    # de-configure /etc/sysctl related settings

    pushd /proc/sys/net 2>/dev/null

    echo 0 > ipv6/conf/default/accept_source_route
    echo 0 > ipv6/conf/all/accept_source_route
    echo 0 > ipv4/conf/default/accept_source_route
    echo 0 > ipv4/conf/all/accept_source_route

    echo 0 > ipv4/conf/default/send_redirects
    echo 0 > ipv4/conf/all/send_redirects

    echo 0 > ipv6/conf/default/forwarding
    echo 0 > ipv6/conf/all/forwarding
    echo 0 > ipv4/ip_forward

    popd
}

case $1 in
start)
    echo "$0: Subneting eth0 interface..."
    touch ${LOCK}
    make_router
    echo "Done."
    ;;
stop)
    echo "$0: Restoring eth0 interface to default config..."
    if [ -f ${LOCK} ] ; then
        rm -f ${LOCK}
        unmake_router
    fi
    echo "Done."
    ;;
status)
    if [ -f ${LOCK} ] ; then
        echo ""
    else
        echo
    fi
    ;;
restart|reload)
    echo "$0: Re-subneting eth0 interface..."
    if [ ! -f ${LOCK} ] ; then
        touch ${LOCK}
        make_router
    fi
    echo "Done."
    ;;
*)
    echo "Usage: $0 {start|stop|restart|reload|status}"
    exit 1
    ;;
esac

```Now update your init scripts, using the `update-rc.d' command in a terminal window. Use `man update-rc.d' to learn about the needed options; make sure you read the `EXAMPLES' section because it makes the usage rather clear. For my working example this was:
```

sudo update-rc.d routify start 99 5 stop 99 0 1 2 3 4 6 S

```Activate the changes either by rebooting or by issuing (the <...> should be the appropriate numbers):
```

sudo telinit <another runlevel>
sudo telinit <your selected runlevel>

```[B]Step 3
[/B]
You will have to add a route in all other computers on the network. For my setup this is:

```
sudo ip route add 192.168.200.100 via 192.168.1.66
```In order to execute this in every boot, you will have to make it a start-up script, or modify an existing one to add this command.

[B]Step 4

[/B]Now in each computer on the network that you want to print to this printer, select the `System|Administration|Printers' menu. Then at the window that opens press the `New' button. A dialog box shows up. 

Select `Network Printer|Find Network Printer' from the list at the left and enter the ip address of the printer at the `System Name' text box. Mine had a `print network configuration option'; if yours has not try to ping it to locate the address . Then press the `Search' button. 

When the printer is found you will have to select the proper vendor and model. Print a test page to confirm that the printer works.

[B]Step 5

[/B]Enjoy your printer(or come backif it does not work)** :). **

---

### Post by RyanRahl on 2010-09-27
Sorry it took so long to get back but your setup worked very nicely, thank you.

---

### Post by gzarkadas on 2010-09-27
Nice to hear it worked for you :smile:; it was a good exercise for me also.

---

