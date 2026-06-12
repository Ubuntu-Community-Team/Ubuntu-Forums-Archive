---
title: "??? local IP adress changing on same cable?"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by flyingsliverfin on 2009-09-10
We have a linksys router, to which this computer is connected. However, yesterday my 'ifconfig' IP is different from what i have today! now the ending is .103 instead of .102! Im still using the same cable, and nothing i know of changed.

reason y im even cheking this is becuz i have an ssh server running here. Not that its used to much, but it would be useful to know y the local IP is changing!

---

### Post by chili555 on 2009-09-10
You have selected DHCP as the method for your computer to connect to the router. That's what your Linksys is doing, using any number it feels like. Of course there is a possibility that someone else has x.102 today: roomie/spouse/kidz/neighbor who has cracked your encryption, etc.

If you want x.102 permanently, right-click Network Manager, edit connections and use the manual method and set it up. Don't forget DNS nameservers:```
cat /etc/resolv.conf
```

---

### Post by Whiffle on 2009-09-10
Except you shouldn't assign yourself a static ip that is within the range that the router assigns ip's, otherwise someone could end up with the same ip and that would cause problems.

---

### Post by chili555 on 2009-09-10
> **Whiffle said:**
> Except you shouldn't assign yourself a static ip that is within the range that the router assigns ip's, otherwise someone could end up with the same ip and that would cause problems.Excellent catch! If your Linksys assigns 50 addresses srating at x.100 and ending at x.149 (most Linksys are set like this by default), I'd set the number down to a reasonable number to cover your home network plus a guest, ten, let's say and then use a static IP of x.115.

---

### Post by Whiffle on 2009-09-10
Or just put it out of the range entirely, like 192.168.1.150 and above.

Some routers (well, mine does, with dd-wrt), will allow you to assign ip addresses based on MAC addresses.  So all my machines are setup with dhcp, but they always receive the same address from the router.  Its pretty slick :)

---

### Post by flyingsliverfin on 2009-09-10
im not a networking guy, so i have Q's about it.

what do u mean 'set it up'?
and, for setting it up, do i have to edit the router itself? as in open firefox, type in 192.168.1.1 as the url and then do it? 

whats a DNS whatchamacallit and what does it do? I like to understand what im doing for future refernce so i can do it myself again next time i need  to.

under the 192.168.1.1 in the URL it says that the starting is .100 and the max users is 50 or something like that. im assuming it means that i can only have a max of .149...

what is IPv4 and IPv6? ive seen this around the area of networking and servers.


apart from that "roomie/spouse/kidz/neighbor" LOL im 13 (sorry i cant afford but to laugh, every1 always misjudges my age!!!!! :lolflag: AND don't apollogize plz like every1 does. Oh and dont tell any1, i always get a good laugh). Sadly enough im the only person in my family that knows ANything about administration/networking/linux etc. my mom always asks me to do everything for her! my brother knows but hes off to college....

---

### Post by chili555 on 2009-09-10
> do i have to edit the router itself? as in open firefox, type in 192.168.1.1 as the url and then do it?To do it right, yes you do. Go into the router and change the max users under DHCP to some sane number, ten for example. Make sure the range is then x.100 to x.109 in my example. Apply changes and close out of the router. Use a number that meets your needs, if not ten. You surely don't, and never will have 50 computers in your house!

DNS nameservers translate 'www.google.com', which the internet doesn't really understand, to IP addresses, such as 74.125.159.106, which the internet does understand. Without DNS nameservers, you will either have to type in numbers (you have all the internets IP addresses memorized, right?) or else you will get an 'address not found' error for any named address you try. When you request an IP address from the router by DHCP, behind the scenes, you also get appropriate DNS nameservers. They are stored in a file called /etc/resolv.conf (*not *resolv[COLOR="Red"]e[/COLOR]!) If you read out that file with cat as I suggested above, and jot them down on paper, you will have them for the next step.

On your computer, right-click the Network Manager icon, the four little bars, select edit connections, select wired or wireless, whichever you are using, edit your network to change ipv4 settings from DHCP to manual. Put in the IP address you want, outside the range you established in the router, x.115, for example. You will need netmask, 255.255.255.0, also gateway, 192.168.1.1 in your case and the DNS nameservers you wrote down; just the numbers, not all the wordings.

[http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)  Some here suggest disabling IPV6 but I never found it to help and, in fact it slowed my connection down. Please don't "fix" it unless you *know *you have a problem.> Oh and dont tell any1, i always get a good laughI get a few laughs when people find out I am 66, too. We all help each other without regard to a/s/l, race, religion, or what have you. We are just glad to have you join the Ubuntu party!

---

### Post by flyingsliverfin on 2009-09-19
did that! (fiinally got down to it)

are there any new security risks, etc. i should know about since i now use static ip?

i do have a firewall (firestarter), if that helps anything...

do u know anything about the package 
sudo apt-get install gnome-lokkit

my dad's computer repairer guy from his work said that the reason my ssh server isn't allowing anyone (even on the local network) to ssh into the computer has something to do with iptables (whatever those are) and lokkit...

i cant seem to install it.. is it becuase i have 64-bit ubuntu? i might reinstsall though soon

---

### Post by chili555 on 2009-09-19
> are there any new security risks, etc. i should know about since i now use static ip?None whatever.> something to do with iptables (whatever those are)Iptables is the firewall and firestarter is the GUI front end that makes it easy to configure.> do u know anything about the package sudo apt-get install gnome-lokkitNope, sorry.> i might reinstsall though soon I'd try harder to fix what I had, first. These forums and the search function have bailed me out of many a crisis.

---

### Post by flyingsliverfin on 2009-09-19
thx.

well, im still considering to reinstall cuz ive had some problems with the 64 bit alpha flash (wont play videos) and this problem.

---

