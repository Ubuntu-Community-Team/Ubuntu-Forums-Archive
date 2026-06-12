---
title: "Iptables/Masquerading....say what??"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by viperce on 2010-11-17
Hi im fairly new to Ubuntu/Linux and i have somehow managed to get a server up and running.
For the past few months i have been trying to get masquerading working but the more posts i read the more confused i am getting.

Could someone please help me or point me in the right direction. something idiot proof would be nice :D

I have 2 network cards 

eth0=Internal Lan      IP address 192.168.0.254
eth1=router External  IP address 10.0.0.1

would help if i let you know what i am trying to do....i want all my internal lan traffic to go through my linux box & only have port 80 & 3128 go through squid.
so for all pop3/smtp action i want the linux machine to act like a router & for port 80 & 3128 i want it to go through squid.

---

### Post by jpl888 on 2010-11-17
The setup you have at the moment will be what's known as "double-nat" which isn't good.

You should either bridge the 2 ethernet interfaces (my preferred setup) or use the RFC1483 functionality of your router and run a PPPOE/A client directly from your linux box so that eth1 actually gets an external IP. As opposed to the private IP it currently has.

The former has an advantage in that it's a transparent firewall, but connection tracking won't work.

The latter connection tracking will work, but if the Linux box goes down so will the internet.

For instance I try to get customers to use servers with built in Baseband Management Controller's so I can get access to the server over the internet even if it won't boot. You can't do that with the latter setup.

Tell me which you want to do and I will tell you how to do it :)

---

### Post by puppywhacker on 2010-11-17
I principle you don't need to NAT (MASQ) twice, you can just setup a route to the real external internet. In practice that would depend on how your adsl-modem or whatever you have will react to multiple ip-ranges.

The transparent proxy you asked about is explained here
[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

The trick is to redirect traffic in and out of your squid.
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

---

### Post by viperce on 2010-11-19
> **jpl888 said:**
> 
You should either bridge the 2 ethernet interfaces (my preferred setup) or use the RFC1483 functionality of your router and run a PPPOE/A client directly from your linux box so that eth1 actually gets an external IP. As opposed to the private IP it currently has.

The former has an advantage in that it's a transparent firewall, but connection tracking won't work.


I have my clients authorizing with squid3 will that still work if we go this route?

---

### Post by viperce on 2010-11-19
will this bypass my iptables & rules completely or would i be able to forward traffic on 80 & 3128 to squid?

echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by jpl888 on 2010-11-19
In answer to your first question, proxying, either with Squid or other proxy will still work regardless of which route you take.

Enabling ip forwarding is necessary for the firewall to work anyway.

May I suggest you also use HAVP in front of Squid as it will scan web traffic for viruses.

I just use HAVP on it's own these days but I used to chain it with Squid back in the day. I used to have HAVP on port 8080 tell it to forward traffic to port 3128 and have a redirect rule as the other poster mentioned earlier to redirect port 80 to 8080 transparently.

At one point I even had Dansguardian in the mix to content filter too but OpenDNS seems to be as good and less hassle to setup.

---

### Post by viperce on 2010-11-19
sounds good then how do i go about getting that going??

---

### Post by jpl888 on 2010-11-19
So you want it bridged, with HAVP and Squid chained in a transparent proxy?

---

### Post by viperce on 2010-11-19
if i can still have auth running on that then yes please :D

---

### Post by jpl888 on 2010-11-19
Urm no sorry auth won't work in transparent proxy.

You can either configure clients manually or use a proxy auto discovery script in that case (can't remember exactly what it's called but I have used it before) or of course stop using auth?

---

### Post by viperce on 2010-11-19
i dont mind configuring the clients manually to connect to the proxy server as long as the auth still works, which i thought would not be possible with transparent proxy server :P.

So does this mean you can no longer help :(

---

### Post by viperce on 2010-11-19
i need auth :( 

We have way to many staff members that i need to keep an eye on :(

---

### Post by jpl888 on 2010-11-19
Don't worry I can help whatever way you want it.

First we need to setup the bridge, then iptables, and then we'll do the proxy config.

Bridge - /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.x.x
        netmask 255.255.255.0
        gateway 192.168.x.x
        bridge_ports eth0 eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

Replacing IP addresses with your own.

Iptables - /etc/rules-save

```
 Generated by iptables-save v1.4.4 on Fri Aug  6 20:53:42 2010
*filter
:INPUT ACCEPT [33394:2816896]
:FORWARD ACCEPT [73745:4845726]
:OUTPUT ACCEPT [18134:2282560]
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 20:23,25,43,80:81,443,465,587,843,873,995,1935,3389,5222 -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 5900,8008,8080,9002,11371,18990,20913 -j ACCEPT
-A FORWARD -p udp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 123,623,1194,5060 -j ACCEPT
-A FORWARD -p icmp -m physdev --physdev-in wlan1 --physdev-out eth0 -j ACCEPT
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j DROP
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j DROP
COMMIT
# Completed on Fri Aug  6 20:53:42 2010

```

If you aren't sure or can't find out what each port is ask me. 

When you have those in place you will need to restart networking and apply iptables:-

```
/etc/init.d/networking restart
```

```
iptables-apply /etc/rules-save
```

We'll look at the proxy once you have those sorted. :)

---

### Post by viperce on 2010-11-22
Thank you so much for this dude :D

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.x.x
        netmask 255.255.255.0
        gateway 192.168.x.x
        bridge_ports eth0 eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
Ok i have 2 ip ranges eth0 192.168.1.251 local an eth1 10.0.0.5 to router (router ip 10.0.0.254)
so do i only put in my internal network ip address?

---

### Post by viperce on 2010-11-22
when i try to restart the network after i added 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo br0
iface lo inet loopback

# The primary network interface
iface br0 inet static
        address 192.168..251
        netmask 255.255.255.0
        gateway 10.8.0.1
        bridge_ports eth0 eth1
        bridge_fd9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

i get this error
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:14: option with empty value
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:14: option with empty value
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

any ideas?

---

### Post by jpl888 on 2010-11-22
AFAIK each "auto" statement should be separate i.e. "auto lo" "auto br0".

That's probably what the syntax error is.

Bridging the network interfaces together you will end up with one interface which is actually up and an ip address. All machines behind the bridge will also get addresses in this range, presumably from the DHCP server on your router. So given the info you have provided this is how your /etc/network/interfaces should look.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 10.0.0.5
        netmask 255.255.255.0
        gateway 10.0.0.254
        bridge_ports eth0 eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

We would also want to add DHCP to the firewall to allow the workstations get addresses, so /etc/rules-save would now look like this:-

[HTML] Generated by iptables-save v1.4.4 on Fri Aug  6 20:53:42 2010
*filter
:INPUT ACCEPT [33394:2816896]
:FORWARD ACCEPT [73745:4845726]
:OUTPUT ACCEPT [18134:2282560]
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 20:23,25,43,80:81,443,465,587,843,873,995,1935,3389,5222 -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 5900,8008,8080,9002,11371,18990,20913 -j ACCEPT
-A FORWARD -p udp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 67,123,623,1194,5060 -j ACCEPT
-A FORWARD -p icmp -m physdev --physdev-in wlan1 --physdev-out eth0 -j ACCEPT
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j DROP
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j DROP
COMMIT
# Completed on Fri Aug  6 20:53:42 2010[/HTML]

---

### Post by viperce on 2010-11-22
Ok i did all that now i can ping router ip address 10.0.0.254, but i can not ping the 192.168.1.0 range which has all my clients on it.

---

### Post by viperce on 2010-11-22
Hope this helps you to see what i have [IMG]http://img547.imageshack.us/img547/8416/setupi.jpg[/IMG]
The second server is the server we are busy with atm

---

### Post by jpl888 on 2010-11-22
That's a lovely diagram but I digress ...

You seem to be struggling with this conceptually. Bridging is not the same as routing/NATing. By creating a bridge on the Linux server we have effectively turned it into a software switch, it won't route one network to another only forward traffic at the MAC layer.

As I touched on earlier the clients will need to have their address in the 10.0.0.0 range too.

Do you understand where I am coming from?

---

### Post by viperce on 2010-11-23
ok i can work around that so i need to set my router to the same ip range as my clients on the 192.168.1.0 range. the other clients i will find a work around or just set that proxy server to route through the 2nd proxy server?? that should work i hope :D

thanks for that was trying to get my head around it

---

### Post by viperce on 2010-11-23
ok i have changed the routers ip address 192.168.1.200 what is the next step

---

### Post by viperce on 2010-11-23
interfaces looks like this

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.1.251
        netmask 255.255.255.0
        gateway 192.168.1.200
        bridge_ports eth0 eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


iptables-save looks like this

Generated by iptables-save v1.4.4 on Fri Aug  6 20:53:42 2010
*filter
:INPUT ACCEPT [33394:2816896]
:FORWARD ACCEPT [73745:4845726]
:OUTPUT ACCEPT [18134:2282560]
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 20:23,25,43,80:81,443,465,587,843,873,995,1935,3389,5222 -j ACCEPT
-A FORWARD -p tcp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 5900,8008,8080,9002,11371,18990,20913 -j ACCEPT
-A FORWARD -p udp -m physdev --physdev-in eth0 --physdev-out eth1 -m multiport --dports 67,123,623,1194,5060 -j ACCEPT
-A FORWARD -p icmp -m physdev --physdev-in wlan1 --physdev-out eth0 -j ACCEPT
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j LOG --log-prefix "iptables denied: "
-A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -j DROP
-A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -j DROP
COMMIT
# Completed on Fri Aug  6 20:53:42 2010

---

### Post by jpl888 on 2010-11-23
Well we should be at the stage where the clients could talk to the internet if they had the router set as their default gateway.

You can also test that the proxy server is working.

Once you have that verified that just install HAVP:-

```
apt-get install havp
```

Then edit the config /etc/havp/havp.config and uncomment the following 2 lines:-

```
# PARENTPROXY localhost
# PARENTPORT 3128

```

"3128" being the port Squid is listening on. By default HAVP listens on 8080, so you can either change HAVP to 3128 and Squid to 3127 to save reconfiguring the clients or leave both the proxies alone and change the port in the client config.

Once you have that working maybe we could look at setting up an auto-discovery script.

---

### Post by viperce on 2010-11-23
:D so far so good
i can ping my router from my laptop so thats working & i can connect to my proxy server which is sweet
emails seem to be coming in nicely internally & externally.

thanks so much dude :P

---

### Post by viperce on 2010-11-23
just a question if i wanted to block off a port say for torrents/skype is it possible to do this on the server as well?

---

### Post by jpl888 on 2010-11-23
You're welcome, glad to be a help.

Check if you can get access, but I always set my firewalls up for access by exception so you probably won't get skype or torrent access using the script I gave you. So it's already blocked AFAIK.

If you need to get access to a service that's blocked at the moment add it to the relevant line and bear in mind you cannot have more than 15 arguments per rule (a port range counts as 2). In which case you would need to add another rule (if you look at the script there are already 2 separate rules for tcp traffic).

If you have a lot of clients the proxy auto-discovery I mentioned earlier will be useful:- [http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol](http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol)

You may also want to sign up to OpenDNS to get content filtering and stop people from looking at others nether regions. [http://www.opendns.com](http://www.opendns.com)

Let me know if you have any questions.

---

### Post by jpl888 on 2010-11-23
I just realised there's a typo in that script:-

```
-A FORWARD -p icmp -m physdev --physdev-in wlan1 --physdev-out eth0 -j ACCEPT
```

Should read:-

```
-A FORWARD -p icmp -m physdev --physdev-in eth0 --physdev-out eth1 -j ACCEPT
```

It also worth noting that the router is acting as the firewall for the internet side of the equation in this setup. That's why there aren't really any rules related to incoming traffic.

The network segment between the bridge and the router can also be considered a DMZ where a machine will get unrestricted access to the net.

If you want to get into more advanced setup we can also setup an IDS to monitor for virus/spyware activity amongst others (it uses up a lot of memory though).

---

### Post by viperce on 2010-11-24
thanks again I have forwarded the ports i needed on the router to the server all seems to be working well :D

could we do the virus/spyware monitoring as well please :P i am learning alot & that would be handy to have.

---

### Post by jpl888 on 2010-11-24
If you did the HAVP bit you are already scanning web access for viruses and some spyware with ClamAV.

The other monitoring I mentioned related to an intrusion detection system called Snort.

Snort is primarily designed to check traffic for potential break-ins and exploits in action, but there are also rule sets to check for virus and spyware activity. However it is prone to false positives and obviously neither Snort nor HAVP will check encrypted traffic because it can't decrypt the stream (that would be a man in the middle attack).

It can also be configured to automatically block hosts at the firewall if said traffic is detected but I have found this causes more problems than good (as I previously mentioned false positives)

In my opinion a combination of HAVP + OpenDNS plus you checking the firewall log using logwatch is as good and likely to keep you as safe + give an indication if a machine is infected.

For instance a tell tale sign of infection is when a host tries to send a large amount of packets to a non-standard port (this is where the access by exception idea comes into play). I had a host the other day try to send over 40000 packets and I have warned the customer the machine is probably infected, with a view to disinfection. 

Please look at the following sites for more information.

[http://www.snort.org/](http://www.snort.org/)
[http://www.bleedingsnort.com/](http://www.bleedingsnort.com/)
[http://www.snortsam.net/](http://www.snortsam.net/)
[http://www.server-side.de/](http://www.server-side.de/)
[http://www.opendns.com/](http://www.opendns.com/)
[http://linuxcommand.org/man_pages/logwatch8.html](http://linuxcommand.org/man_pages/logwatch8.html)

So in summary stick with HAVP + OpenDNS + logwatch unless you want some headaches.

---

### Post by viperce on 2010-11-24
Ok i have HAVP installed can i draw reports from it?
I dont have Clamav installed i will try install that now
will look for logwatch as well :D

---

### Post by jpl888 on 2010-11-24
HAVPs' logs are in /var/log/havp. It may be possible to configure Logwatch to report on them but I don't bother. I rely on the iptables section of Logwatch and the mail server logs, to tell me if a machine is infected. Obviously if a virus is sending on ports which are allowed through the firewall then it won't tell you about these. 

ClamAV will have been installed as a dependency of HAVP, so you don't need to do that.

To install logwatch:-

```
apt-get install logwatch
crontab -e
```

and add a line to run logwatch and send it to yourself at least once a day:-

```
0 23 * * * /usr/sbin/logwatch --mailto yourself@yourdomain.com --range today >/dev/null 2>&1
```

The "/dev/null 2>&1" stops the results of the cron job from being mailed to root filling up his mailbox.

I assume you are already using OpenDNS's DNS servers for your network?

---

### Post by viperce on 2010-11-24
thanks dude for all your help.....this is helping me a lot & i am learning a lot about linux :D have not even scratched the surface yet by the looks of things

---

### Post by jpl888 on 2010-11-24
ClamAV was already installed when you installed HAVP. HAVP pulls it in.

And no you don't need to configure it. In Ubuntu it will work out of the box.

---

### Post by viperce on 2010-11-24
i am getting this error after i have edited & added the line 

0 23 * * * /usr/sbin/logwatch --mailto [EMAIL="yourself@yourdomain.com"]yourself@yourdomain.com[/EMAIL] --range today >/dev/null 2>&1

crontab: installing new crontab
"/tmp/crontab.5fbRmn/crontab":1: bad day-of-week
errors in crontab file, can't install.
Do you want to retry the same edit? 
Im sure its me doing something wrong..

---

### Post by jpl888 on 2010-11-24
Did you copy and paste the command or type it in?

---

### Post by viperce on 2010-11-24
yup then edited the email address

---

### Post by viperce on 2010-11-24
re did it & it is working now..dame forgot to edit the mail address this time....

---

### Post by viperce on 2010-11-24
it asked me to setup postfix O_o after i installed logwatch

if i just set the relayhost = smtp.myisp.co.za im guessing it wont just work :P

---

### Post by viperce on 2010-11-24
this should be all i have to change right?

myhostname = computername.domain.co.za
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = computername, localhost.localdomain, , localhost
relayhost = smtp.myisp.co.za
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

---

### Post by jpl888 on 2010-11-24
Actually I think it may just be as simple as that but YMMV.

Sorry I forgot that Logwatch requires an SMTP server.

You can run the command from the cmd line without the cron blurb like so to test:-

```
/usr/sbin/logwatch --mailto yourname@yourdomain.com --range today
```

And check syslog for obvious problems by typing:-

```
tail -f /var/log/syslog
```

---

### Post by viperce on 2010-11-25
all working managed to setup postfix & get that going is there anything else i am missing? or should consider installing.

---

### Post by jpl888 on 2010-11-25
Well there is always stuff to install and configure, it's tinkerer's paradise ;)

I'll tell you the kind of setup I generally use.

To further minimise exposure to viruses/malware get all your email going through your shiny new mail server.

So for POP3/IMAP accounts you have Fetchmail -> Amavis + Spamassassin -> Postfix -> Courier POP/IMAP.

Fetchmail collects the POP/IMAP email, passes it on to Amavis, which scans it for viruses/malware/SPAM, which passes on to Postfix for final delivery to Maildir's, which are then served up to you clients using Courier POP/IMAP.

Similarly if you have your own domain point the MX to this server and use the same setup, minus fetchmail or use both.

It's currently 98.70% accurate (I have a little script that calculates the accuracy every time someone goes on the website).

Are you game?

---

### Post by viperce on 2010-11-25
could i ask you a unrelated question....i am having a problem with a local webserver (keep in mind im clueless) it works [http://localhost](http://localhost) no problem but if i try access it from anywhere else i get 
**Forbidden**

 You don't have permission to access / on this server.


any idea what that can be?

---

### Post by jpl888 on 2010-11-25
Either the address the server is bound to in the config OR it's restricted by acl.

Check /etc/apache2/sites-enabled/000-default

---

### Post by viperce on 2010-11-25
thanks will check it out :P

---

