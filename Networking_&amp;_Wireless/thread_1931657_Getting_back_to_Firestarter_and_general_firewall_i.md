---
title: "Getting back to Firestarter and general firewall info"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by fixitdude on 2012-02-25
After messing around for hours I finally went back to the Firestarter firewall. I hope this info helps someone else.

First, you have to understand that all these firewall programs do is set up your iptables "config file". They actually don't "run" all the time, iptables does, iptables is really your running firewall.

So pick one, there are several. I messed with all of them and am now back at Firestarter because it makes outgoing connections permissive but keeps incoming connections out. And it's easy to configure.

Only problem is that it is not supported since 2005. But I think the Ubuntu guys may be keeping it working.

If you try the other firewalls, beware that they will install things that may linger and you have to manually remove them to get back to no firewall at all.

What you want to do is un-install all of them and only have the one you like installed and working.

If you get stuck like I did, you need to look (as root) in /etc/init.d/ for any of the other "init scripts" by the firewall name and move them out of that directory so they don't start up. I say move them rather than delete them so you can put them back. However, using synaptic package manager you can do a re-install in most cases and that will replace the file.

The init scripts to look for are "guarddog" "kmyfirewall" "firestarter" and "ufw". You can use synaptic package manager to remove these, but I know from experience that "kmyfirewall" does not remove it's init script, I had to delete it.

"kmyfirewall" will overwrite whatever "Firestarter" did earlier so you end up with a "kmyfirewall" setup instead of "Firestarter" even if you completely removed "kmyfirewall" with synaptic.

Sometimes you can tell what firewall wrote your iptables by looking at the table list.

iptables -L

If you see "KMF:" as a log parameter, that's "kmyfirewall" that is doing that.

If you see `Inbound ' and `Outbound ', you are looking at a Firestarter setup. Also "Policy" is a give away.

If you only see a few lines and nothing in there that says "ACCEPT" or "DROP", you have a clean system with no firewall at all.

Oh yea, and the "ufw" firewall is the ubuntu default firewall and will conflict with Firestarter so it needs to go if you want to run Firestarter.

If you want to restrict certain outgoing ports, then "Kmyfirewall" does that nicely, so does "guarddog". The problem with that is then if you access some sites that have their own video player, like news sites, they sometimes pick strange ports and you never know why or what ones so you sit there trying to figure out what is going on.

If you look in /var/log/messages you can usually see the dropped packets in the log, just look for the "DPT=" meaning the destination port, and if it says "KFM:" you know it's "Kmyfirewall" and if you see "Outbound" it's "Firestarter" etc....

Turn everything else off that accesses the net and only bring up that one news site, then watch your log and see what is blocked.

The tcpdump program can come in handy too for looking to see if your outgoing packets are making it out of your box, I'm not going to go into that, you can google it.


Just a note:

ls /var/lock/

Shows you the lock files for some of these firewalls that are "running", like "firestarter" is there and uses that file to detect if it is "running" or not.

Links:
[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by kcallis on 2012-02-28
Riddle me this FixItMan... I had to setup a bridge, and although it was was working, I didn't like the fact that there was no security in place. So considering that I was doing this to share my internet, I decided to turn off ip_forward since I assume that Firestarter would handle that. I then decided that I would add a little more in the mix by using dnsmasq and wondershaper to try for some QOS.

I stopped using NetworkManager since that make way to many issues, and just added my interfaces in /etc/network/interfaces. Now this is when the weirdness begins. When I boot it takes a minute for the system to come up. I am sure that is because of NM, so not a problem there. Dnsmasq is running, but is not reading it config files. So when I get ready to look at any site, I am informed that it can resolve.

That caused to me to start banging my head against the wall until I decided to start firestarter. Firestarted tells me that the is a problem with my configuration, and can't start. The moment that I click stop on firestarter, suddenly dnsmasq is resolving and working like a champ. If I try to start firestarter, dnsmasq fails with no resolution.

So with firestarter off, now I am able to answer dhcp request, etc. Of course, now the problem is that my inside clients are not able to get out. I am able to ping the interface, but I am not able to forward to the gateway. 

I am at a loss and any pointers would me me a very happy camper!

---

### Post by kevdog on 2012-02-28
Can you be more specific in what the problem is?  I like your style of writing since it reads like a funny novel, but it kind of sucks since it does not specifically address some of the nuances of your setup.

---

### Post by fixitdude on 2012-03-18
> **kcallis said:**
> Riddle me this FixItMan... I had to setup a bridge, and although it was was working, I didn't like the fact that there was no security in place. So considering that I was doing this to share my internet, I decided to turn off ip_forward since I assume that Firestarter would handle that. I then decided that I would add a little more in the mix by using dnsmasq and wondershaper to try for some QOS.

I stopped using NetworkManager since that make way to many issues, and just added my interfaces in /etc/network/interfaces. Now this is when the weirdness begins. When I boot it takes a minute for the system to come up. I am sure that is because of NM, so not a problem there. Dnsmasq is running, but is not reading it config files. So when I get ready to look at any site, I am informed that it can resolve.

That caused to me to start banging my head against the wall until I decided to start firestarter. Firestarted tells me that the is a problem with my configuration, and can't start. The moment that I click stop on firestarter, suddenly dnsmasq is resolving and working like a champ. If I try to start firestarter, dnsmasq fails with no resolution.

So with firestarter off, now I am able to answer dhcp request, etc. Of course, now the problem is that my inside clients are not able to get out. I am able to ping the interface, but I am not able to forward to the gateway. 

I am at a loss and any pointers would me me a very happy camper!One thing with Ubuntu, try not to go low level and modify things in config files if you possibly can. Use the Ubuntu tools, the GUI tools when possible.

One reason is upgrades, they have upgrades do a lot of things and read a lot of settings from their special files.

The other reason is that they have all sorts of special startup scripts all over the place that do all sorts of stuff. I've spent hours tracking them down in some instances, only to find that one scrip loads another and on and on. Doing it the simple easy, straight forward way doesn't seem to be the way things work for Ubuntu programmers.

It is possible they do it that way because of the upgrade situation and to be compatible with other linux kernel upgrades..

As for your specific problem, I would post this problem in it's own thread, maybe in this support category. And also make sure you look in the logs at the moment you have the problem, there's always more info in the logs.

Try some of the other firewalls, one at a time of course, and make sure the others are uninstalled. Some seem to handle connection sharing better than others.

Another thing that would help would be for anyone who makes a firewall to put a comment line in iptables stating what firewall made the changes so that anyone trying to figure this out can see who is overwriting who. It is possible to have two firewalls come up at boot if you are not careful.

---

### Post by fixitdude on 2012-03-18
> **kevdog said:**
> Can you be more specific in what the problem is?  I like your style of writing since it reads like a funny novel, but it kind of sucks since it does not specifically address some of the nuances of your setup.No problem here, just info for anyone searching for info when having firewall problems. Might help someone.

---

