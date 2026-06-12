---
title: "Network bonding problem, I'm losing packets."
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-02-25
This is kind of a complicated topic, I'm just hoping anyone can help me but I'll give it a shot. So basically guys what I'm trying to do here is bond 2 NICs by running the following:
```
ifenslave bond0 eth2 eth3
```The big issue is when I ping a website, for example I'll run:
```
ping google.com
```
I notice a lot of packet loss. I'd say around 35% packet loss, which is pretty high. The way I setup the network bond could have had something to do with it, I did use ethtool for the interfaces by running the following:
```
ethtool eth0 && ethtool eth1 && ethtool eth3
```
If you're interested, this is my modprobe configuration for the network bond:
```
alias eth0 tg3
alias eth1 tg3
alias bond0 bonding
options bond0 mode=1 miimon=100
```
I also tried changing the "options" line to the following:
```
options bond0 mode=0 miimon=100
```
Still losing packets like crazy, so I'm not really sure what's going on here. I'd also like to give you my ifcfg-bond0 configuration file, it's default, but I guess it wouldn't hurt to look at:
```
DEVICE=bond0
IPADDR=192.168.1.1
NETMASK=255.255.255.0
NETWORK=192.168.1.0
BROADCAST=192.168.1.255
ONBOOT=yes
BOOTPROTO=none
USERCTL=no
```
I also have the bonding module loaded as well, I ran the following to make sure:
```
sudo modprobe bonding mode=0 miimon=100
```
So I've done everything right I think on my part for the network bond to work, but I'm kind of lost.

---

### Post by Crafty Kisses on 2009-02-27
So I have solved this problem strangely enough, I did some research and I noticed some people were having a lot of the same issues as me, but their fixes were not working for me. So what I did was edit this line in my bonding configuration file:
```
options bond0 mode=0 miimon=100
```
To the following:
```
options bond0 mode=1 miimon=100
```
Then I was still having issues, but the thing was I realized by default I'm pretty sure the mode was always 1. So what I did was got the configuration file for the following:
```
/proc/net/bonding/bond
```
Then I noticed it was still "0" in that configuration file, I changed it to 1, then I restarted by running the following:
```
sudo shutdown -r now
```
Then what I did after that was re-bonded the NICs by running the following command:
```
ifenslave bond0 eth2 eth3
```
I noticed I was still receiving packet loss, but not nearly as much, so I wanted it to be perfect, so then what I did was made sure the bonding module was present, which the weird thing it wasn't I ran the following command:
```
lsmod | grep bond
```
Nothing showed up, but when I ran the following:
```
sudo modprobe bonding
```
The module did actually showed up when I grepped again. So I re-pinged a website and there was little to no packet loss, so I obviously was happy. Then I rebooted, but then I noticed my NICs weren't bonded any more, so I didn't want to run the same command every time I booted up, so what I did was opened the following configuration file:
```
/etc/sysconfig/network-scripts/ifcfg-bond0
```
Then this is how my configuration file looked:
```
DEVICE=bond0
IPADDR=192.168. 1.12
NETMASK=255. 255.255.0
GATEWAY=192. 168.1.1
USERCTL=no
BOOTPROTO=none
ONBOOT=no
```
So I figured out, if you change ONBOOT to yes, it will start on boot up, so all you have to do is the following:
```
ONBOOT=yes
```
Then reboot once again by running the following:
```
sudo shutdown -r now
```
Then the NICs should be bonded still and you should have little to no packet loss and everything should be working. If you are still having problems with packet loss, after all this, you want to open this configuration file: 
```
/etc/sysconfig/network-scripts/ifcfg-eth1
```
Then it should look a little something like this when you first see it:
```
DEVICE=eth1
BOOTPROTO=none
#NETMASK=255.255.255.0
ONBOOT=yes
#TYPE=Ethernet
USERCTL=no
#IPV6INIT=no
#PEERDNS=yes
#Settings for bonding
MASTER=bond0
SLAVE=yes

```
What you can do is change the line that says MASTER=bond0 to the following:
```
MASTER=bond1
```
Then that will also fix any issues you maybe having after you following my steps. That should solve the packet loss issue, well it did for me anyway.

---

### Post by Crafty Kisses on 2009-02-27
As it turns out, I actually didn't solve my problem, but as stated in the posts above by myself the packet loss has decreased a lot but it's still pretty high, I'd say around 25% which again for me anyway is way too high, I think a lot of people would agree, I'm a little frustrated as of right now but I finally tried to manually configure my network bond, So I brought my network bond down by running the following:
```
ifconfig bond0 down
```
Then I tried re-bonding the NICs by running the following:
```
ifenslave bond0 eth2 eth3
```
Which obviously re-bonded them, but I'm still losing packets. So I decide to start from scratch by removing the device driver modules by running the following:
```
rmmod bonding
```
So to make sure the module is completely gone I run the following:
```
lsmod | grep bonding
```
It's gone, I don't get any results from that, which is good for now. So then I edit the following configuration file:
```
etc/rc.d/rc.local
```
There also seems to be a problem with when I reboot the NICs unbond for some reason, so this is the current configuration I'm using that seems to keep the network bonded upon reboot:
```
modprobe bonding mode=balance-alb miimon=100
modprobe e100
ifconfig bond0 192.168.1.1 netmask 255.255.255.0 up
ifenslave bond0 eth2
ifenslave bond0 eth3
```
So to test this I rebooted by running the following command:
```
sudo shutdown -r now
```
Then to my surprise the networks are still bonded, which is a start! Then I need to configure each bond, so I edit my module configuration, and this is how it's looking right about now:
```
alias bond0 bonding
options bond0 -o bond0 mode=balance-rr miimon=100
alias bond2 bonding
options bond1 -o bond3 mode=balance-alb miimon=50
```
Also I'd like to post my list of network bonds:
```
alias bond0 bonding
options bond0 mode=some-mode miimon=50
alias eth2 e1000
alias eth3 e1000
```
I then realized I don't have a slave for bond0 so I run the following command:
```
add above bonding e1000
```
I also make sure my installation supports network bonding by running the following:
```
sudo cat ifenslave /sbin/ifup
```
Which it obviously does and I've already named the ethernet bond with iftab but I wanted to make sure. So most of my network bonding configuration has been done, so I restart the network by running the following command:
```
/etc/init.d/network restart
```
So now it's time to edit that actual module configuration the way I want it, so this is  how it looks right now:
```
alias bond0 bonding
options bond1 mode=balance-alb miimon=100
```
So now I restart the network again by running the following command:
```
/etc/rc.d/init.d/network restar
```
So now I now it's time to actually configure the actual network bond, so I open up the ifaces configuration file by running the following:
```
cat /etc/net/ifaces/failover/options
```
So I finally fully configure it, it looks something like this:
```
TYPE=bond
BONDMODE=1
HOST='primary backup'
BONDOPTIONS='use_carrier=1 miimon=100 primary=primary'
```
I removed the bonding module yet once again as stated above, so I load it once again by running the following:
```
sudo modprobe bonding
```
I want to make sure my network bond is up and running, so I run the following command:
```
ifenslave bond0 eth2 eth3
```
Then I need to make sure failover is up and running, so I bring that right up:
```
ifup failover
```
Make sure my configuration looks good, which it does. This is actually what it looks like for the eth1 bond, looks pretty solid:
```
DEVICE=bond0
IPADDR=192.168.1.12
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
USERCTL=no
BOOTPROTO=none
ONBOOT=yes
```
So the moment of truth comes, I ping a website. To my surprise the packet loss is down yet again, but not fully gone to my disappointment. It would only appear 15% of packets are being loss in this moment in time, which I'll live with for now, I can live with it. I'll work on this very complicated network bond later and see if I can't get this up and running correctly.

---

