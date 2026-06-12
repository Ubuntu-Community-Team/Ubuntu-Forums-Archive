---
title: "Static/DHCP home router with Ubuntu 11.10"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by showe1966 on 2012-01-14
Hi 'yall,

I have just upgraded to Ubuntu 11.10 on my home server and have killed networking.
All sorts of "freaky" things are happening.
It kind of reminds me of setting up networking on "Windows Millenium Edition". That was I laugh a minute I recall...that continued until I installed "RED HAT"....

Here is my setup:-

1. One network card: connects to my internet modem via DHCP.
2. Other network card: static address 192.168.1.1 on internal wired network.
3. I use IPTABLES to masquerade all the other computers on my home network, all at other static addresses, so as they can access the internet.

Here is what I tried:-

1.setting up everything via /etc/network/interfaces.
That file now seems to get overwritten or overridden by the network manager.
Hence, that didn't work.

2. Removed network manager and rebooted.
This had the effect of killing networking.
The network cards did not get assigned device names during boot.

I would prefer to manually administer my network interfaces, so as I can be sure which network interface is assigned which name.
This allows me to set up iptables masquerading correctly and makes sure nothing terrible happens to my firewall.
I don't use wireless and don't need to auto discover interfaces.

Therefore, I would really like to know how to Disable network manager and Set up networking from the command line for 2 network cards and one DHCP and one static network address.

If this is not possible, I'd like to know how to do the above using "network manager", preferrably by directly editing the "network manager" configuration files (where are they ??).

---

### Post by papibe on 2012-01-14
if you remove network-manager, you will need to admin your network by editing files, just as a server.

Could you post the content of your /etc/network/interfaces ?

Regards.

---

### Post by showe1966 on 2012-01-16
Thanks for your input.

I am not sure if I did something wrong, but after I removed network manager, networking did not work at all. The network cards were not detected during bootup, so I had to manually reinstall the packages I had removed , namely 

network-manager-gnome
network-manager

to get the computer to connect to internet again.


Anyway, here is what /etc/network/interfaces looked like:-

```
# The loopback network interface
auto lo
iface lo inet loopback

# My internet modem

auto eth0

iface eth0 inet dhcp

#My internal network

auto eth1
iface eth1 inet static
address 192.168.2.1
broadcast 192.168.2.255
netmask 255.255.255.0
gateway 192.168.2.1
```

I also have a firewall with the following lines in it to set up ip masquerading from my network:-

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Correct me if I am wrong, but after all this, according to me, the routing table should appear as follows:-

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

---

### Post by Iowan on 2012-01-16
It's been awhile since I dealt with */etc/network/interfaces*, but the gateway doesn't look right.

---

### Post by showe1966 on 2012-01-21
any input folks ?
The wife needs to go on the internet so I could be destined for "network-manger hell" if I don't get some help here soon....

---

### Post by shai-tan on 2012-01-21
I have the same problem, couldn't figure out how to resolve it normally either, however I got things back up and running by doing ifdown and ifup on the interfaces. it threw some errors but things were back up

e.g.

ifdown eth0
ifup eth0
ifdown eth1
ifup eth1

seemed to look at the information in /etc/network/interfaces when I did that, before it never took any ip or other info

edit: that said I'm having some severe problems with iptables NAT not loading some web pages even though it's up

---

### Post by showe1966 on 2012-01-22
I am making some slow progress here in the absence of any comprehensive documentation.
I looked at the files that the network manger package installs and got some clues there as to where the configuration files are now.

It seems like the package network manager originally came from red hat.

I tried 
man networkmanager 
which helps a bit and
man networkmanager.conf

BTW the guide

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

no longer works as my network manager is autoconfiguring two new interfaces eth4 and eth5 as it seems to be looking in my existing etc/networking/interfaces file and skipping the ones used in that file... how annoying is that ???
Anyway reading through the documentation it becomes apparent that the solution will be found somewhere associated with the file networkmanager.conf

arrg arrg...why fix something that was working guys ????

---

### Post by showe1966 on 2012-01-22
ok found another clue in the debian documentation.
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

it says here:

As of Debian Squeeze, NetworkManager does not manage any interface defined in /etc/network/interfaces by default.

Unmanaged devices means NetworkManager doesn't handle those network devices. This occurs when two conditions are met:

    The file /etc/network/interfaces contains anything about the interface, even:

    allow-hotplug eth0
    iface eth0 inet dhcp

    And /etc/NetworkManager/NetworkManager.conf contains:

    [main]
    plugins=ifupdown,keyfile

    [ifupdown]
    managed=false

OK that is all clear.
So, if I add the hardware addresses of my interface cards to NetworkManager.conf, NetworkManager will ignore my network cards, hopefully allowing me to revert to configuring them via traditional methods.

So, I edited my /etc/NetworkManager/NetworkManager.conf file to read as follows:


[main]
plugins=ifupdown,keyfile

no-auto-default=00:03:47:df:5e:1f,00:40:f4:1e:29:59

[ifupdown]
managed=false

Annoyingly enough, this did not work.
Instead, network manager configured my network cards using the same ethX numbers it used last time.

Gosh what a pain in the lower back.

---

### Post by drdos2006 on 2012-01-22
Going back to your post of six days previous, your IP address is the same as your gateway. That would create a problem, I am sure.

Due to the fact that you have 2 NIC in your machine you may have to "bond" the cards.

Check these out, did a search on "bridging" and "bonding"

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

### Post by showe1966 on 2012-01-22
i am about to give up with this but here is another reply.
in my first post there is a typo.

it should read as follows:

1. One network card: connects to my internet modem via DHCP.
2. Other network card: static address 192.168.2.1 on internal wired network.
3. I use IPTABLES to masquerade all the other computers on my home network, all at other static addresses, so as they can access the internet.

This is becuase my modem assigns addresses on the 192.168.1.X network, so I have to have my static internat network setup on a different class of network.

anyway, have been trying to use the GUI to share the connection.
It is kind of half working, but there seems to be some kind of double bounce occuring on the internal network in one direction, and nothing occurs in other direction.

I think I will probably go back to 11.04 as this is just a waste of valuable time .

---

### Post by showe1966 on 2012-01-24
i have gone back to 10.04.3 LTS.
Will try again when they fix all the bugs in network manager.
I think what is happening is that on the internal network, it is impossible to set a static network address as the system is always trying to set up the internal network using a DHCP server.

---

### Post by galerie on 2012-01-24
> **showe1966 said:**
> ok found another clue in the debian documentation.
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

it says here:

As of Debian Squeeze, NetworkManager does not manage any interface defined in /etc/network/interfaces by default.

Unmanaged devices means NetworkManager doesn't handle those network devices. This occurs when two conditions are met:

    The file /etc/network/interfaces contains anything about the interface, even:

    allow-hotplug eth0
    iface eth0 inet dhcp

    And /etc/NetworkManager/NetworkManager.conf contains:

    [main]
    plugins=ifupdown,keyfile

    [ifupdown]
    managed=**false**

OK that is all clear.
So, if I add the hardware addresses of my interface cards to NetworkManager.conf, NetworkManager will ignore my network cards, hopefully allowing me to revert to configuring them via traditional methods.

So, I edited my /etc/NetworkManager/NetworkManager.conf file to read as follows:


[main]
plugins=ifupdown,keyfile

no-auto-default=00:03:47:df:5e:1f,00:40:f4:1e:29:59

[ifupdown]
managed=**false**

Annoyingly enough, this did not work.
Instead, network manager configured my network cards using the same ethX numbers it used last time.

Gosh what a pain in the lower back.
I'm not really sure if it should work for you. if you want network-manager manage your connection than you have to change managed=false to managed=true. than you can do everything else in network-manager GUI. I am also a new user of ubuntu but I just experienced similar problem as you.

---

### Post by showe1966 on 2012-02-05
OK.
I tried going back to version 10.04 LTS.
Interestingly, I was still having problems.
Initially, I did not have functionality problems until I upgraded from 11.04 to 11.10. Probably, this is becuase I had got to 11.10 by upgrading since about version 8, which for some reason had kept the configuration files working as they should have done.

Anyway, seeing as it seemed like network manager was doing some kind of dhcp on my internal static network, I eventually decided to try running a dhcp server on the internal network rather than using a static address, as this is what network manager seems to want me to do.

I found a pretty comprehensive guide on the net at the following address:

[http://www.somewhereville.com/?p=1196](http://www.somewhereville.com/?p=1196)

Software version used = 10.04 LTS

vi /etc/sysctl.conf

uncomment the following line to allow packet forwarding:-

net.ipv4.ip_forward=1

add firewall with iptables maquerade on world-connected ethernet interface (eth0):-

sudo touch /etc/init.d/firewall
sudo gedit firewall

#!/bin/sh
#
# Author: Martti Kuparinen <martti.kuparinen@iki.fi>
#
# $Id: firewall,v 1.3 2005/11/25 09:50:43 martti Exp $
#

if [ -r /lib/lsb/init-functions ]; then
    . /lib/lsb/init-functions
fi

firewall_start()
{
#---------------------------------------------------------------
# Initialize all the chains by removing all the rules
# tied to them
#---------------------------------------------------------------
    iptables --flush
# external interface is eth0
# Masquerade out eth0
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from eth0.
iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP
# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

}

firewall_stop()
{
    # Flush all rules
    iptables --flush
}

firewall_status()
{
    iptables -L
}

case "$1" in
    start)
        log_begin_msg "Starting firewall..."
        firewall_start
        log_end_msg 0
        ;;

    stop)
        log_begin_msg "Stopping firewall..."
        firewall_stop
        log_end_msg 0
        ;;

    status)
        log_begin_msg "Firewall Status..."
        firewall_status
        log_end_msg 0
        ;;

    restart)
      log_begin_msg "Restarting firewall..."
        firewall_stop
        firewall_start
        log_end_msg 0
        ;;

    *)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
esac


Once above firewall is written, save it so only root can change it and it is executable.

chmod 700 /etc/init.d/firewall

ls -l /etc/init.d/firewall
-rwx------ 1 root root 1632 2012-02-04 11:55 /etc/init.d/firewall

Add to run level:

sudo update-rc.d firewall defaults

update-rc.d: warning: /etc/init.d/firewall missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/firewall already exist.
stephen@laquila:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID,NEW 
DROP       all  --  anywhere             anywhere            state INVALID,NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID,NEW 
DROP       all  --  anywhere             anywhere            state INVALID,NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

install the dhcp server that will manage the assignment of dhcp addresses on the internal network:

sudo apt-get install dhcp3-server
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dhcp3-server-ldap
The following NEW packages will be installed:
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 377kB of archives.
After this operation, 885kB of additional disk space will be used.
Get:1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates/main dhcp3-server 3.1.3-2ubuntu3.3 [377kB]
Fetched 377kB in 0s (411kB/s)       
Preconfiguring packages ...
Selecting previously deselected package dhcp3-server.
(Reading database ... 152407 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_3.1.3-2ubuntu3.3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dhcp3-server (3.1.3-2ubuntu3.3) ...
Generating /etc/default/dhcp3-server...
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

from
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)
assign a static address to eth1, the internal network interface, via the network manager:-

iface eth1 inet static
        address 10.8.16.1
        netmask 255.255.255.0
        broadcast 10.8.16.0
        network 10.8.16.0

Save a copy of the original dhcp3 config file:
touch /etc/dhcp3/dhcpd.conf.old
cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.old
change /etc/dhcp3/dhcpd.conf so as it reads as follows:

ddns-update-style none;
option domain-name "mynetwork";
option domain-name-servers 151.99.125.1,62.211.64.100;
option routers 10.8.16.1;

default-lease-time 42300;
max-lease-time 84600;
authoritative;

log-facility local7;

subnet 10.8.16.0 netmask 255.255.255.0 {
  range 10.8.16.50 10.8.16.150;
}

the last thing to do before the server can be started is to tell it what interface to listen on. This can be configures in the file /etc/default/dhcp3-server.
open it with 

sudo gedit /etc/default/dhcp3-server

edit following line:

INTERFACES="eth1"

the dhcp-server will be automaticially started upon reboot. to manually start it now use this command
Code:

sudo /etc/init.d/dhcp3-server start

the server would not start.

there were a few messages in syslog:

Feb  4 20:41:35 laquila dnsmasq-dhcp[808]: no address range available for DHCP request via eth1

and

Feb  4 20:37:16 laquila dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Feb  4 20:37:16 laquila dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Feb  4 20:37:16 laquila dhcpd: All rights reserved.
Feb  4 20:37:16 laquila dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb  4 20:37:16 laquila dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Feb  4 20:37:16 laquila dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Feb  4 20:37:16 laquila dhcpd: All rights reserved.
Feb  4 20:37:16 laquila dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb  4 20:37:16 laquila dhcpd: Wrote 0 leases to leases file.
Feb  4 20:37:16 laquila dhcpd: Can't bind to dhcp address: Address already in use
Feb  4 20:37:16 laquila dhcpd: Please make sure there is no other dhcp server
Feb  4 20:37:16 laquila dhcpd: running and that there's no entry for dhcp or
Feb  4 20:37:16 laquila dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Feb  4 20:37:16 laquila dhcpd: are not running HP JetAdmin software, which
Feb  4 20:37:16 laquila dhcpd: includes a bootp server.

So, it looks like the package dnsmasq-base has some kind of dhcp server that is messing up everything.

removed the package 
dnsmasq-base

tried to start the dhcp3 server again

stephen@laquila:~$ sudo /etc/init.d/dhcp3-server start
[sudo] password for xxxxxxx: 
 * Starting DHCP server dhcpd3                                           [ OK ]

Now everything is working OK.

I have a question if anyone can answer it:

1. How do I make sure dhcp3 is starting up when the computer boots up ?
How do i see which programs are automatically started upon startup ?

---

### Post by Iowan on 2012-02-05
> **showe1966 said:**
> 
Now everything is working OK.

I have a question if anyone can answer it:

1. How do I make sure dhcp3 is starting up when the computer boots up ?
How do i see which programs are automatically started upon startup ?

You can try (from a terminal): **ps -ef | grep dhcp**
I run **dnsmasq** as a DHCP/DNS server - I like the ability to **ping** machines by name.
My "static" addresses are actually static leases - so **dnsmasq** knows the name/address.

Depending on which version you run (and whether the machine has a desktop), you might look under System>Preferences>Startup applications.   My server normally runs at runlevel 2 (check with **runlevel**), so I can look in */etc/rc2.d* and see **S15dnsmasq**.

---

### Post by showe1966 on 2012-02-06
I still have one problem.
That is, dhcp3 does not seem to start up automatically.
For packet forwarding to start working, I have to start dhcp3 manually from the command line.
That task exceeds the computing abilities of my wife so currently she can only get on the net whilst I am around !
I think I will have to trawl through the logs to find out what is going on.
Probably another software conflict.

---

### Post by showe1966 on 2012-02-07
I did the command

ps -ef | grep dhcp

NB ps is to show current processes
grep searches for a text string in the output.

I got the following result:-

root       750   710  0 09:35 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-5bf49d44-8b60-4441-a987-3fb6675b5cf6-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
stephen   1644  1591  0 09:39 pts/1    00:00:00 grep --color=auto dhcp

QUESTION
********
what command do i have to type at the command line to see if the dhcp3 server is running after I startup ?

---

### Post by showe1966 on 2012-02-07
I have a GUI installed.
I checked in 

System>Preferences>Startup applications

and dhcp3 is not there.

I am pretty nervous about adding the dhcp3 server via the GUI.
You never know what the GUI is going to do to your configuration files.
***begin rant****IF I WANTED TO USE A COMPUTER WITH A GUI, I WOULD DROP $500 USD AND INSTALL FREEKING WINDOWS 7.***end rant*****

Can't I add it via the command line ?
I have already done the following commands but not sure if they worked:-

sudo update-rc.d dhcp3-server defaults
update-rc.d: warning: dhcp3-server stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 System start/stop links for /etc/init.d/dhcp3-server already exist.

---

### Post by showe1966 on 2012-02-11
any input on this anyone ?

my dhcp3 server is definitely not starting automatically after i switch on the computer.
i have to start it manually..
However, when i restart it seems to stay up...must be something to do with the fact that the dhcp server is remembering the addesses assigned the last time i suppose.

i have an idea...i will add the dhcp3 server startup command to one of the scripts i know executes at startup...maybe that will work.
All i need to do now is identify a suitable script....

anyone know which script i could use ???

---

### Post by Iowan on 2012-02-11
At what **runlevel** does the machine operate (2 or 5 or...)? 
I hadn't seen **update-rc.d** before,but it looks like you *should* be able to use it to start the DHCP server in the desired runlevel. (I gotta wonder if **dnsmasq** disabled **dhcp3**)

Do ANY of the */etc/rc#.d* directories show a S or K entry for **dhcp3-server**? I presume there's an entry in */etc/init.d* or you couldn't start it manually.

---

### Post by showe1966 on 2012-02-12
Dear Iowan,

Thanks for your input.
I will more fully diagnose what is happening shortly...

In any case, how does ubuntu handle the startup of programs these days ?

Can you point me to an explanation of how it is done now ?

Obviously, I'd prefer to configure from the command line (I am a control freak, in case you were wondering ;-) ).

I found this note:

"Any program (or script) can be made to Autostart at bootup by creating a symbolic link to that program (or script) in the ~/.config/autostart folder."

However, this statement is inaccurate.
This is because the command will only be run AFTER the user in question logs in via the GUI, NOT at bootup.

What I need is a command that will start the program in question at bootup and without login of a particular user.

---

### Post by showe1966 on 2012-02-12
zowee i have googled for 3 hours now and it looks like ubuntu now uses this program to start things:

Upstart Startup Manager
see:

[http://www.linuxplanet.com/linuxplanet/tutorials/7033/1](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1)

now all i need to do is find out how to use it ?!

---

### Post by showe1966 on 2012-02-12
I think the dhcp3 not starting could be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/580319](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/580319)

---

### Post by showe1966 on 2012-02-12
In answer to Iowan's earlier post:

1. I don't know which level my computer "operates" at.
What I really need to know, it strikes me, is what level my computer will be after it has booted up (successfully), before anyone has logged in.

2.The file dhcp3-server is in the directory /etc/init.d
I can start my dhcp3 server after I have logged in as my user from the command line with the command:
sudo /etc/init.d/dhcp3-server start
and it comes back with the message "ok".

3. in the directory
/etc/rc2.d
I have  S40dhcp3-server

in the directory
/etc/rc3.d
I have  S40dhcp3-server

In any case, having ploughed through all the c**p about upstart manager and event-lead service startup, it would seem to me like I need to write a script that will start dhcp3 at the right moment rather than using the old "init.d" run-level based method ??

---

### Post by showe1966 on 2012-02-12
I was just totally sold on how wonderful (?) this event-driven service initialization philosophy is so I decided to boot all that old-fashioned run-level stuff into touch and hence I decided to write my own new-fangled launchpad script to start dhcp3 instead, seeing as how the old method is obviously not working in a big way.
.
It would seem to me that the server should start after the interface it configures (eth1) comes up.

So, here goes:

sudo touch /etc/init/dhcp3.conf
sudo gedit /etc/init/dhcp3.conf
added the following to the new file:

start on (net-device-up IFACE=eth1)

script

exec /etc/init.d/dhcp3-server start
end script

I saved it, power-cycled everything, and, amazingly enough, everything seems to work.

BTW I found some vaguely useful and slightly comprehensible stuff here:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Anyway, everything is working now, the nightmare is ended, and the missus can get on the internet in my absence !!
Zehah !!
But surely, shouldn't all this have been a teenie bit easier ?

btw if you want to check what services are running:

sudo service --status-all

---

