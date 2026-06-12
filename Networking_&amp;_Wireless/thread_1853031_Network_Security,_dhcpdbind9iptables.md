---
title: "Network Security, dhcpd/bind9/iptables"
date: 2011-10-01
forum: Networking &amp; Wireless
---

### Post by jdwilm on 2011-10-01
I've set up the network for my house (8 residents) to do all the routing through an ubuntu machine running dhcp3-server and bind9. The wireless is pushed through a linksys router operating purely as an access point with all other features disabled. I am concerned about how secure my network isn't. I'm using a script written by some ubuntu contributor to setup my iptables on startup, but it leaves my iptables in the following state:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
which is extremely open from what I can tell. My understanding of iptables is fairly limited, and I'm unaware of how a "secure" network should look from an iptables perspective. 

My googling has mostly turned up generic iptables tutorials or what amount to books written on the subject. The tutorials are helpful, but I would really like some links to overviews/discussions on securing a network in this fashion, or any advice you can offer to point me in the proper direction.

Thanks,
Joseph

Edit:
Modem connects to this machine, this machine is connected to a switch. The switch is connected to numerous other machines and the wireless access point.

---

### Post by Dangertux on 2011-10-01
Well iptables is a very complicated beast -- it's very flexible and to be honest if you want to be successful with it you have to have a very clear picture of where you're ultimately trying to end up.

I take it from your post that this machine is designed to be a router, so obviously you're going to need NAT functionality. Since you haven't provided the example script , or rules you're using I can't really help you much more then that. I also have no idea what services you actually need or you just want it to act as a router.

So here is the iptables/netfilter documentation, it's technical in nature but it's the most complete available: [http://www.netfilter.org/documentation/](http://www.netfilter.org/documentation/)

If you can post more information about the script you are using, what services you want running and what you're trying to accomplish I'm sure we can help you more.

---

### Post by jdwilm on 2011-10-01
The NAT functionality is setup (I believe) in this script along with the iptables:
```

  1 echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
  2 DEPMOD=/sbin/depmod
  3 MODPROBE=/sbin/modprobe
  4 
  5 EXTIF="eth0"
  6 INTIF="eth1"
  7 #INTIF2="eth0"
  8 echo "   External Interface:  $EXTIF"
  9 echo "   Internal Interface:  $INTIF"
 10 
 11 #======================================================================
 12 #== No editing beyond this line is required for initial MASQ testing == 
 13 echo -en "   loading modules: "
 14 echo "  - Verifying that all kernel modules are ok"
 15 $DEPMOD -a
 16 echo "----------------------------------------------------------------------"
 17 echo -en "ip_tables, "
 18 $MODPROBE ip_tables
 19 echo -en "nf_conntrack, " 
 20 $MODPROBE nf_conntrack
 21 echo -en "nf_conntrack_ftp, " 
 22 $MODPROBE nf_conntrack_ftp
 23 echo -en "nf_conntrack_irc, " 
 24 $MODPROBE nf_conntrack_irc
 25 echo -en "iptable_nat, "
 26 $MODPROBE iptable_nat
 27 echo -en "nf_nat_ftp, "
 28 $MODPROBE nf_nat_ftp
 29 echo "----------------------------------------------------------------------"
 30 echo -e "   Done loading modules.\n"
 31 echo "   Enabling forwarding.."
 32 echo "1" > /proc/sys/net/ipv4/ip_forward
 33 echo "   Enabling DynamicAddr.."
 34 echo "1" > /proc/sys/net/ipv4/ip_dynaddr
 35 echo "   Clearing any existing rules and setting default policy.."
 36 
 37 iptables-restore <<-EOF
 38 *nat
 39 -A POSTROUTING -o "$EXTIF" -j MASQUERADE
 40 COMMIT
 41 *filter
 42 :INPUT ACCEPT [0:0]
 43 :FORWARD DROP [0:0]
 44 :OUTPUT ACCEPT [0:0]
 45 -A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
 46 -A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
 47 -A FORWARD -j LOG
 48 COMMIT
 49 EOF
 50 
 51 echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```

You mention not being successful without knowing precisely where I want to end up. That very succinctly stated what I am trying to learn. Most of the services provided are fairly common (ssh, web, dns) and at least one less common (ps3 media server - UPnP over port 5001). 

I'm not looking for a list of rules for iptables (I would like to struggle through figuring that out), but more the philosophy of securing a network (the whats and whys) so that I can get to the point of designing the iptables rules.

---

### Post by Dangertux on 2011-10-01
Ok , the script you posted basically does one thing (I know it's alot for one thing huh?), it basically sets up Masquerading otherwise known in the rest of the world as NAT routing. This allows your internal machines to communicate with the outside world with the machine this script is running on acting as a router.

As far as securing your network , there are a lot of thoughts on that subject. A lot of it greatly depends on what external services you wish to run. So let's take a simple small network for example. We'll say we have the following set up, 5 client machines that are on the internal network, these are just used for the purposes of web browsing. The afforementioned router we've been discussing, and a Web/DNS/email server in a data management zone (pretty much exposed to the internet, but confined from the client machines)

In this scenario your checklist for securing said network would be something along these lines.

- Secure the router , making sure it uses strong credentials for any  type of administration login , if it is also a wireless access point  make sure that the encryption is strong (WPA or better), and has a  strong passphrase, harden it against arp/igmp/dns based attacks, make  sure the administrative interface is only accessible internally (unless  you need remote administration in which case harden that). Make sure it  has sufficient firewall rules that the needed traffic is allowed, and  unneeded traffic is either rejected or denied. Make sure that any  services running on the router, are not vulnerable to known attacks, if  there are services running on the router make sure you're using an  application firewall to confine them (apparmor/SELinux again). Consider running an IPS or DPI firewall on your router (more difficult to set up but worth it)

- Secure the exposed server this includes but is not limited to hardening, patching services as necessary, ensuring use of strong credentials, adding additional firewall rules to this machine (ie: we only want some networks having access), Applying application firewalls (apparmor or SELinux) , hardening the kernel against denial of service, and dns/arp based attacks (Man in the middle), and ensuring proper permissions on files and directories as well as proper ownership (people only can access what they need and not more)

- Client machines, make sure they are fully updated with all necessary security patches. Make sure they are properly protected by the router/firewall. Consider using a firewall for each machine seperately, implement anti-malware if necessary, make sure they do not have access to anything on the network they shouldn't (for instance if you don't want them ssh'ing to your web server make sure they can't). Make sure any accounts set up on the clients regardless of operating system are running with appropriate privileges with strong credentials(no one running as root or admin, unless absolutely necessary). Make sure their connections are physically secure (ie: you don't have wires running all over the outside of your house that someone can tap into), teach the users using these machines about basic security, make sure they understand web based threats, as well as malware, make sure they understand social engineering tactics like phishing. Also, make sure the browsers are protected with addons like noscript/notscript or internet explorer's anti-xss engine. 

This is just a very simple start, security becomes very complex very quickly, and the more you think about it the more you will have to do. It's a process not a one stop shop, there is no single device that can protect your network. Only vigilance and a lot of work.

Hope that helps.

---

### Post by jdwilm on 2011-10-04
Thanks dangertux for your reply. The security aspect of this router project is a bit overwhelming. I'm currently working on figuring out a set of firewall (iptables) rules to suit my needs. I looked into AppArmor and SELinux per your suggestion but am fairly intimidated by them at this point (and lacking the time to do the work to learn them -- physics GRE in less than 2 weeks!). The DPI firewall even more so.

Your post gave me a lot of security concepts to research, and it's become painfully clear that there is not a quick solution to network security.

Thanks again :)

---

