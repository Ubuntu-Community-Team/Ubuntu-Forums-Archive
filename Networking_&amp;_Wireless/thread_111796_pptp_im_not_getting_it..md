---
title: "pptp im not getting it."
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by Bone Down on 2006-01-02
Hello all, it has been about 4.5 yrs since I played with linux (use to work for Linux Networx when I started), well I decided I have had about enough of all the XP updates, and would like to migrate my laptop to a win free environment.

I have just about made it fully happen, I am taking it one step at a time and furthering the move with each step.

My next largest hurdle is to connnect to my employers network via pptp vpn, I am not able to access intranet and/or email without it.

So here is the situation, I have followed the steps as best as I can, and I was able to connect to the network, but that is the furthest that I can go.

Indicates that I have successfully connected, but I am unable to access my intranet, download email, and or surf any internet at all period.

Could any of you assist me with this?

Oh and I really like Ubuntu, linux has made leaps and bounds in the last 4.5 yrs.
I think I may be back to stay.

---

### Post by mips on 2006-01-03
What have you done so far. What guides did you follow ? Provide links so we can see what you did ? Copy your config files here.

---

### Post by alamba on 2006-01-03
That's typically a VPN problem and not a ubuntu issue per se. I just installed a pptpd server (on ubuntu) at office and was able to connect and download without a glitch. While u've indicated that u're using pptp, can you specify the VPN server side you're using, is it a cisco concentrator by any chance?

Akshay

---

### Post by Bone Down on 2006-01-03
[QUOTE=mips]What have you done so far. What guides did you follow ? Provide links so we can see what you did ? Copy your config files here.[/QUOTE]

These are the two guides I referenced after a week of researching the subject.
I first went with VPNC only to find out that my work no longer utilizes cisco vpn and is now using windows pptp or mppe (ithink it is called).

As I mentioned earlier pptp indicates that I am actually logged in, but I am unable to surf the net or hit my intranet, not able to retrieve email either.

[http://www.ubuntuforums.org/showthread.php?t=91249&highlight=pptp-linux]("http://www.ubuntuforums.org/showthread.php?t=91249&highlight=pptp-linux")
[http://pptpclient.sourceforge.net/howto-debian.phtml#install]("http://pptpclient.sourceforge.net/howto-debian.phtml#install")

let me know how to post the conf file and I will do so.
I set this up thru the pptpconfig gui.

Thanks for your support on this.

---

### Post by Bone Down on 2006-01-03
[QUOTE=alamba]That's typically a VPN problem and not a ubuntu issue per se. I just installed a pptpd server (on ubuntu) at office and was able to connect and download without a glitch. While u've indicated that u're using pptp, can you specify the VPN server side you're using, is it a cisco concentrator by any chance?

Akshay[/QUOTE]

I was not saying that it is an ubuntu problem, I am very sure it is a setting that I am not familiar with.
The company that I work for has since switched from cisco vpn and most users are now using winxp vpn to log in to the network.
The network guys are not very familiar with linux and did confirm that I am connnecting (in win mode) via pptp so I dropped vpnc and went with pptp-linux.

I hope that this helps you to help me.
Thanks in advance for any support.

I have done many a search on this, but I will be very honest at this point I am lost and I am not very sure what to do next.

Research has arrived me to where I am now, and I am only doing this one step at a time so that I am not jumping all over the place on different subjects.

---

### Post by Bone Down on 2006-01-03
any ideas ??

---

### Post by Bone Down on 2006-01-03
did I post this in the wrong forum? if so please let me know what is a better forum to post this in as I would really like to resolve this situation and move on.

I have been messing with this now for about a week now and I have only been able to get to this point here now.

I am sure it is a simple thing that I have over looked and just need some guidence.

Any help is appreciated.

thanks in advance.

---

### Post by mips on 2006-01-04
Under the **Miscellaneous** tab tick **Enable Connection Debugging facilities [Debug]**

When you start a new tunnel a debug window will pop up. Paste the output here but XXX out sensitive confidential info.

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)
[http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html](http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html)
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

You might want to submit your problem to the mailing list or visit the IRC channel [http://pptpclient.sourceforge.net/contact.phtml#list](http://pptpclient.sourceforge.net/contact.phtml#list)

Also maybe do a search on the Debian forums.

---

### Post by Bone Down on 2006-01-04
[QUOTE=mips]Under the **Miscellaneous** tab tick **Enable Connection Debugging facilities [Debug]**

When you start a new tunnel a debug window will pop up. Paste the output here but XXX out sensitive confidential info.

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)
[http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html](http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html)
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

You might want to submit your problem to the mailing list or visit the IRC channel [http://pptpclient.sourceforge.net/contact.phtml#list](http://pptpclient.sourceforge.net/contact.phtml#list)

Also maybe do a search on the Debian forums.[/QUOTE]

Thanks a bunch I will do this as soon as I have some time tonight.
I have dons many searches on google and yahoo, as well as within the ubuntu forums.

again thanks for offering me some more options.

---

### Post by mishranurag on 2006-01-07
Hi!
 When I try to connect VPN from my home, it says connected and sends a lot of bytes and packets but recieve none :(
Can anybody guide me here?
Anurag
Following is the log of message I got when I connected with the VPN

Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/0
CHAP authentication succeeded
MPPE 128-bit stateless transmit compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 128.173.35.xxx
remote IP address 128.173.32.xx
primary   DNS address 198.82.247.34
secondary DNS address 198.82.247.98
pptpconfig: pppd process exit status 0 (started)
ip route add 128.173.32.xx via 192.168.1.1 dev eth0  src 192.168.1.2
RTNETLINK answers: File exists

pptpconfig: command failed, exit code 2
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected

---

### Post by Bone Down on 2006-01-08
ok here is my log.
fresh install on new HDD and no windows at this time so I am hoping to get this dealt with before the end of the weekend so that I can access at the bare minimum email via evolution (for business).

Following is a log from pptpconfig:
```
pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.2 2004/06/19 08:57:15
# pppd --version
pppd version 2.4.3
# uname -a
Linux DC-Comics 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686 GNU/Linux
# grep mppe /proc/modules
# modinfo ppp_mppe
Array
(
    [name] => kwevpn
    [server] => kwevpn.am.kxx.xxx
    [domain] => 
    [username] => login
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1
pptpconfig: debug information dump ends,
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 202.19.126.xxx>]
sent [IPCP ConfAck id=0x1 <addr 202.19.126.xxx>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 10.0.15.130> <ms-dns1 10.0.1.21> <ms-dns3 10.0.1.44>]
sent [IPCP ConfReq id=0x3 <addr 10.0.15.130> <ms-dns1 10.0.1.21> <ms-dns3 10.0.1.44>]
rcvd [IPCP ConfAck id=0x3 <addr 10.0.15.130> <ms-dns1 10.0.1.21> <ms-dns3 10.0.1.44>] 
Cannot determine ethernet address for proxy ARP
local  IP address 10.0.15.130
remote IP address 202.19.126.xxx
primary   DNS address 10.0.1.21
secondary DNS address 10.0.1.44
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.19.126.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1
pptpconfig: pppd process exit status 0 (started)
ip route add 202.19.126.xxx via 192.168.99.99 dev eth1  src 192.168.99.105
RTNETLINK answers: File exists

pptpconfig: command failed, exit code 2
pptpconfig: routes added to remote networks
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.19.126.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1

```

Thanks in advance for your support on this matter.

BD

---

### Post by Bone Down on 2006-01-08
btt - this is a pain in the butt.
I have tried the many different configurations within pptpconfig and the only one that appears to connect is the one listed above.
I can't figure out how to stop this thing once it is started, without rebooting, in order to do more research on the subject.

I work for a large global company, and the network admins do not have time to assist with this as they are swamped with other issues and have basically told me that it is not support software and they reccomend that I stay with the windows setup.

Dual boot is a hassle, if I can not get this pptp to work then I fear I will have to bag ubuntu (linux) for a while.

I have spent on this stupid pptp problem now a total of 63 hours (21 hours alone out of the last 28 hours)(19 straight yesterday).

Here is the kick in the pants, this is the only thing keeping me from dropping windows, it is like the switch to cut power to windows is just one foot out of reach and no matter what angle I try I can not reach it.

---

### Post by mips on 2006-01-08
This might be nothing but something just caught my eye.

Can you ping IP addresses on your companies Intranet ???
Your DNS entries are pointing to 10.0.1.xxx addresses, is this correct, are they the same in windows.

Something else,
```
Destination Gateway Genmask Flags Metric Ref Use Iface
[COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR] 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.99.0 0.0.0.0 255.255.255.128 U 0 0 0 eth1
0.0.0.0 192.168.99.99 0.0.0.0 UG 0 0 0 eth1
```

Is the xxx address a 10. or 202. network ? I'm trying to establish what network/subnet your company is using in order to determine if the route via ppp0 is correct. The mask looks weird to me.

If you think some information is to sensitive to post you can also mail me if you want. 
192.168. & 10. are private addresses uses by most companies and are not accessable/routable over the internet unless you run a vpn/tunnel.

---

### Post by mips on 2006-01-08
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)

> 4. the PPTP Server may have given its own IP address for the new interface (compare "remote IP address" in the debug logs with the IP address you give to pptp). 	try one of the following:

   1. change the point-to-point IP address of the newly created ppp interface, using an ip-up or ip-pre-up script, for example;

      #!/bin/sh
      # $1: interface-name
      # $4: local-IP-address
      # delete the assigned address from the network device
      ip addr del $4 dev $1
      # add back the assigned address along with a replacement peer address
      ip addr add $4 peer 10.0.0.1/32 dev $1
      # add a default route, remove if not wanted
      route add default $1

   2. change the point-to-point IP address of the newly created ppp interface, using ifconfig, for example;

      ifconfig ppp0 pointopoint 10.0.1.1

      where 10.0.1.1 is the address to be adopted, see internal address for how to determine this.

   3. add a static route to the PPTP Server via your usual default gateway, for example;

      route add -host x.x.x.x/32 gw y.y.y.y dev nnn0

      where x.x.x.x is the IP address of the PPTP Server, y.y.y.y is the IP address of your usual default gateway, and nnn0 is the name of the network interface through which the gateway is contacted.

   4. request a more appropriate address by adding an option such as :10.0.1.1, where 10.0.1.1 is the address to be adopted, (the PPTP server may be configured to refuse the request, or may not be capable of it)

   5. use the iptables and ip commands to direct the tunnel packets away from the tunnel interface, see our Routing HOWTO for more detail,

   6. ask the PPTP Server administrator to change the configuration to use another remote address.


**[COLOR="Red"]Can you also follow the Fault Tree on this page and see how far you get please.[/COLOR]**

---

### Post by Bone Down on 2006-01-08
[QUOTE=mips]This might be nothing but something just caught my eye.

Can you ping IP addresses on your companies Intranet ???
Your DNS entries are pointing to 10.0.1.xxx addresses, is this correct, are they the same in windows.[/QUOTE] = I have never tried, as I am a remote access user and only way for me to access the network is via vpn, so to be real honest I have never tried.

[QUOTE=mips]Something else,
```
Destination Gateway Genmask Flags Metric Ref Use Iface
[COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR] 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.99.0 0.0.0.0 255.255.255.128 U 0 0 0 eth1
0.0.0.0 192.168.99.99 0.0.0.0 UG 0 0 0 eth1
```

Is the xxx address a 10. or 202. network ? I'm trying to establish what network/subnet your company is using in order to determine if the route via ppp0 is correct. The mask looks weird to me.

If you think some information is to sensitive to post you can also mail me if you want. 
192.168. & 10. are private addresses uses by most companies and are not accessable/routable over the internet unless you run a vpn/tunnel.[/QUOTE]


```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.19.126.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1 
```

---

### Post by mips on 2006-01-08
[http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html](http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html)
> 
Other Settings

    * Make sure you add the following alias to your /etc/modules.conf file to be able to load the ppp-compress-18 module : 'alias ppp-compress-18 ppp_mppe'
    * Routing can be configured as described below:

      e.g. To connect to all devices on the 142.103.0.0 net over the VPN, configure routing as follows:
          o route add -net 142.103.0.0 netmask 255.255.0.0 dev ppp0

      e.g. To connect to an individual device 142.103.10.10 over the VPN, configure routing as follows:
          o Determine the end point of your VPN tunnel using "ifconfig ppp0" command. The address of the end-point/gateway will be listed as "P-t-P: 142.103.x.x" where 142.103.x.x is the IP address of the end-point/gateway.
          o Setup a route to the device 142.103.10.10 through the gateway 142.103.x.x.
          o route add 142.103.10.10 gw 142.103.x.x

You are now ready to connect to UBC VPN.

This is kinda what I'm getting at. This one is a biatch to sort out as it's hard when you are not the one behind the keyboard and secondly you have no clue as to how the network is setup logically & physically.

I'ts probably something stupid/trivial.

We could also chat via AIM, MSN, ICQ or Skype if you want, that way things could go a bit faster.

But for now I'm going to bed, way to late here... 
G'night John-Boy, Jason, Mary Ellen, Ben, Erin, Jim-Bob, Elizabeth!

---

### Post by Bone Down on 2006-01-08
MIPS  thanks a ton, I use msn I will set it up in my user cp so that you can contact me.

you have given me even more things to attempt so I will give it another go round and see how it turns out.

---

### Post by mips on 2006-01-08
[QUOTE=Bone Down]= I have never tried, as I am a remote access user and only way for me to access the network is via vpn, so to be real honest I have never tried.

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.19.126.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1 
```[/QUOTE]

I see no way/route to get to the DNS servers listed in the previous post. The mask 255.255.255.255 basically indicates a single device, try changing it to 255.255.255.0 or what ever the correct mask is.

Could I ask you to capture all possible information from when you are running a tunnel in Windows and compare them to your Linux settings.

---

### Post by Bone Down on 2006-01-08
im not sure what ip's need to be used I have updated the output file. I think I will have to await a moment that I can chat with you via IM to see if together we can figure this out.

In the meantime, I will attempt to find out the windows tunnel information.

All I have to go on is server address kwevpn.am.kxx.xxx with user name and login.

I will attempt to work with one of the other network admins that have been very helpful in the past see if he is willing to share additional settings that I might not have figured out.

BD

---

### Post by mishranurag on 2006-01-08
Hey mips!
If you could help me for this pptp thtough skype or msn or yahoo, that would be really great. My id mishranurag in all of these.
Thanks
Anurag

---

### Post by mips on 2006-01-09
[QUOTE=mishranurag]Hey mips!
If you could help me for this pptp thtough skype or msn or yahoo, that would be really great. My id mishranurag in all of these.
Thanks
Anurag[/QUOTE]

mishranurag,

I will try to help you as soon as I've finished helping Bone Down. I don't multitask to well ;)

In the meantime I would like you to do the following. If you have it working on a windows machine please copy and paste all the setup info to a single file with detailed descriptions, screenshots of the setup in Network control panel & copies of config files would also help. Collect all possible infor on the connection and network.

I will contact you with my email address then you can send all this info to me, hash out username & password references.

---

### Post by mishranurag on 2006-01-11
Thanks mips, I don't know what configuration files I might have for VPN, but I followed the following instructions to connect  to VPN from windows machine.  

[http://answers.vt.edu/ask4help/connection/vtkb2304.htm](http://answers.vt.edu/ask4help/connection/vtkb2304.htm)  

These instructions are provided by the computing services at VT. 
Thanks in advance.
Anurag  :)


[quote=mips]mishranurag,

I will try to help you as soon as I've finished helping Bone Down. I don't multitask to well ;)

In the meantime I would like you to do the following. If you have it working on a windows machine please copy and paste all the setup info to a single file with detailed descriptions, screenshots of the setup in Network control panel & copies of config files would also help. Collect all possible infor on the connection and network.

I will contact you with my email address then you can send all this info to me, hash out username & password references.[/quote]

---

### Post by Bone Down on 2006-01-12
first off I want to say thanks a ton to MIPS, although I am still not up and running at 100% MIPS has been huge in his efforts to aide a complete stranger.

Here is what I was able to accomplish so far (with MIPS and some others help not on this board): 
I appear to make a successful connection to the vpn server, dhcp assigns new local ip, and adds dns ip's to the resolv file.

ppp0 is now showing up in the ifconfig output (was not showing up in the past).

However I keep getting the following  error in the terminal that I use to start pptpconfig ```
Module ppp_mppe not found 
``` does anyone have an idea on this one?

I found a few things about the newer kernel utilizing an mppc version and to check the alias file to make sure that there is an alias entry for it, and there is.

it seems that once the error comes up I lose my ppp0 connection.

---

### Post by Bone Down on 2006-01-16
okay one more possible problem elininated?
Tonight I connected directly to the inet bypassing all of the routers, connected as usual, many packets going out, but nothing coming in, can not ping anything, cannot connect to any www's and still cannot connect to the work intranet.

---

### Post by Bone Down on 2006-01-17
btt 241 views and only MIPS has an idea?

---

### Post by Bone Down on 2006-01-19
MIPS - I was able to get this working via irc, I want to thank you big time for your help and support on this matter.

pptpconfig still has bugs in it (this from the writer of via irc) so some manual configuration was done, as well as a small script that was placed within the ip-up.d file.

I will go back thru all the logs and see if I can make heads or tails of what was done so that I can post them up here.

I will say this though Anurag everything that was utilized is in the troubleshooting section of the pptpconfig on sourceforge.

[pptpclient on sourceforge]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml")

---

### Post by mips on 2006-01-19
Cool ! Glad it got sorted out. Chat to you a bit later.

---

### Post by larytet on 2007-11-27
Re Error "Cannot determine ethernet address for proxy ARP"

run 
sudo pptpconfig

Create a new entry, let;s say MyOffice. There is some minor bug in the pptpconfig GUI. Make sure to select the entry to edit and click update. Pay attention, that after you click Update you should select the entry again.

Configure IP address of the server, login, etc,
user routing option "Interface only"
add in the "edit Network rules" entry like 192.168.2.0/25 named "my office"
Here i assume that home network (local) is 192.168.1.0 and office network (remote) 192.168.2.0. 

Select main entry and make sure that everything is configured alright.
Try to start. You will get something like this 

using channel 52
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3fff8786> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3fff8786> <pcomp> <accomp>]
......................................................................
rcvd [IPCP ConfAck id=0x3 <addr 192.168.0.30> <ms-dns1 192.168.2.2> <ms-dns3 69.81.156.1>]
rcvd [IPCP ConfReq id=0x7 <addr 192.168.2.61>]
sent [IPCP ConfAck id=0x7 <addr 192.168.2.61>]
Cannot determine ethernet address for proxy ARP

To get full debug information edit file /etc/ppp/options  - uncomment line 
#debug
or just add line 
debug

Next step create script like this

```

#!/bin/bash

echo 'restart pptp'
/etc/init.d/pptpd restart


echo 'VPN down'
poff
sleep 5

echo 'Open VPN'
pon MyOffice
sleep 20

echo 'Add routes' 
ip route add 192.168.2.0/24 dev ppp0


```

chmod +x scriptname
sudo ./scriptname

---

