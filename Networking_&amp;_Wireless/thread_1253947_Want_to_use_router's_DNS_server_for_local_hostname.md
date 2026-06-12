---
title: "Want to use router's DNS server for local hostnames"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by BattlePanic on 2009-08-30
Can't ping hostnames from or to linux box

I'm configuring a small office LAN and one of the machines on the network is running linux (Ubuntu as well as other distros) while all the others are running windows xp.  I have run into an issue where the linux machine can't resolve the hostnames of all the other (windows) machines on the network and vice versa.  Interestingly, the windows machines are able to resolve each other's names using the 'ping' command  but can't see the linux box.  All of the machines are able to resolve domains outside of the network (e.g. ubuntuforums.org).

I have tried both assigning static IP's to all the machines and having them assigned automatically via the router's (a Linksys WRT54G) dhcp server.  With my limited networking knowledge, I suspect that the has more to do with the dns server I am using in my setup.  Originally I was using OpenDNS for my dns servers but I quickly realized that those servers would have no idea how to resolve a local hostname.  I then set the dns server to my router address which doesn't seem to resolve local hostnames but it does resolve everything outside my network.

I know that I can associate a hostname with an ip address by manually editing the hosts file, but this seems like it would be tedious and wasn't dns invented to solve this very problem?  I'm wondering why the windows machines can resolve each other's names but the linux machine can't.  Are the windows machines using a different protocol?  I've read about NetBIOS and wonder if the windows machines are actually using this protocol to find each other.  Does the windows 'ping' command do double duty, using both NetBIOS and DNS?  For what it's worth, 'nslookup' fails just as miserably on the windows machines as it does when trying to resolve a hostname from the linux machine which gives further evidence that some other protocol is being used.

Ideally, I'd like my router to act as a DNS server and handle caching of hostname/IP pairs if that's possible.  Is this something my router (Linksys WRT54G) can do?

---

### Post by Charly85551 on 2009-09-01
I think you are getting confused between local area network (LAN) and wide area network (WAN). Protocols are quite different. As long as your router is acting as a DHCP server all your PC's incl. the Linux machine are getting their IP-address from this router and are automatically within one common subnet, for example 192.168.1.x where each machine has just a different number for x and the router normally comes with 192.168.1.1 - at least that's how my WRT54G acts.
To communicate between the various PC's you need to be sure that all have the same domain or workgroup setting. Microsoft does a quite confusing naming by calling it just "workgroup". You can change it by calling it "homenet". But make sure all the PC's are set up for this (and you need to restart each machine after the change).
I am also running Ubuntu 9.04 on one machine and it is correctly showing all my PC's in "homenet".
As soon as you are starting a Web-Browser on any machine you are sending a WAN- message to the router which acts then as a DNS-server as well and forwards all the requests to the ISP's server. 
You can check all this on a Windows PC by going into the terminal mode (start/execute/cmd and enter "ipconfig /all". All your settings will be listed there.
Just one more word of caution: unless you have marked partitions or folders as shared you can not see/access anything on a neighbour's PC.:P
Hope this was not too confusing!
cheers

---

### Post by falconindy on 2009-09-01
Going to parrot the above poster -- I think you've confused the names that your LAN machines have with the DNS that provides you with access to the world outside your LAN. Your router may not even support the ability to offer anything but upstream DNS (provided by your ISP).

My 2 cents: I'm not convinced you ever really need to use DNS locally, especially from Linux. Samba handles 99% of the interactions you'll ever need to have with Windows machines, and it has its own set of host lookup parameters which can easily be configured to allow you to use machine names rather than IP addresses.

Are you able to use `smbclient -L windowshost` to view windows shares from the linux box? You should be able to do this by name. If not, open up your /etc/samba/smb.conf and find the line the starts with "name resolve order" around line number 56. Change the order of the directives to:
```
   name resolve order = lmhosts wins bcast host
```After saving that, you'll need to restart samba with `sudo /etc/init.d/samba restart`.

---

### Post by BattlePanic on 2009-09-01
Thanks for the advice.  For the moment, I'm not actually using DHCP in my setup and all the IP's are static and were assigned and configured by me on each machine.  I guess one of my unanswered questions is whether or not or my router, which is acting as the DNS server, is keeping any record of the hostnames of the machines on the local network.  If so, when and how are these names registered with DNS server?  If I was using DHCP, I thought that maybe the DHCP protocol might somehow coordinate the registration of local hostnames with the DNS server but as mentioned, I'm not currently using DHCP.  My suspicion is that my router is simply acting as a repeater for my ISP's DNS servers.  Anyone know much about the Linksys WRT54G router (with stock firmware)?

Samba and smbclient are actually what led me into this whole thing.  I actually figured out how to mount a windows share (using mount.cifs) but had to specify the IP address of the windows machine in the command line which made me wonder if I could just use the hostname instead.

---

### Post by listener on 2009-09-02
IMO, you really should just add your IP addresses for each machine, along with the hostnames, to the file '/etc/hosts'.  This is how your local network (LAN) resolves hostnames nearly always unless you have some sort of commercial (internet/WAN) server with a registered domain name.  It only takes a few seconds to do.  If you like, you can make one and put it on a floppy or USB stick.

Probably you know this, but the format is simply (example):

> 192.168.1.1              hostname1

for each machine.

You should (possibly depending on the router) be able to set up dhcp for your LAN with reserved IP addresses for each machine.  That way, the dhcp server in your router will always assign each machine the same address.  Same as static.  Actually, I think the dhcp client will request the same IP address each time, anyway, and should get it.

I'm really not that sure how Windows does it, but it does have the hosts file.  They do tend to set up things a bit more for the users, on the other hand when I started Linux and learned to do things correctly, I no longer had the constant networking troubles I did on Windows.

You may want to look into the package 'pyneighborhood' to help you find your Windows shares and mount them using cifs, it works really nicely, and is super-simple.

You only have to set up the hosts file once, btw.

Regards

Bob

---

### Post by BattlePanic on 2009-09-09
> **listener said:**
> IMO, you really should just add your IP addresses for each machine, along with the hostnames, to the file '/etc/hosts'.  This is how your local network (LAN) resolves hostnames nearly always unless you have some sort of commercial (internet/WAN) server with a registered domain name.  It only takes a few seconds to do.  If you like, you can make one and put it on a floppy or USB stick.


Thanks for the advice.  It sounds like editing the /etc/hosts file is the preferred solution.  The network I'm working on is relatively small so this shouldn't be too big of a job.  It just seemed odd to me that each machine would maintain a static, local copy of all the hostnames but I guess when this network is small, it's not a big deal and is probably simpler than trying to configure a local dns server.

---

