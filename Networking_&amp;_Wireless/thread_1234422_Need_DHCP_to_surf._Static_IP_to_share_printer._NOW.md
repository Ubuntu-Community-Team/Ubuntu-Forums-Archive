---
title: "Need DHCP to surf. Static IP to share printer. NOW WHAT?"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by ladasky on 2009-08-07
Hi folks,
 
One upon a time I ran Ubuntu 6 on my home's primary computer, to which an HP printer is attached.  I was able to share that printer with Windows and Mac laptops over wireless.  I could also share files.

The central router in my house is the popular Linksys WRT54G.  It serves up local IP addresses using DHCP.
 
When I upgraded to Ubuntu 8.04, I lost both file sharing and printer sharing.  
 
After several tedious months of shuttling files around on thumb drives in a house with a perfectly good LAN, I decided to experiment with various network configurations.  I decided to try giving my desktop machine a fixed IP address.  Bingo, printer sharing worked again!  From the Mac anyway -- I haven't tried a Windows machine yet.
 
But apparently, without DHCP (which I WILL need, as people come and go from our home all the time with wireless devices), the router won't connect me to the Internet.  I switched the desktop machine back to requesting its IP address by DHCP, and I can surf again.  But I can't print, except for locally.
 
Any help is greatly appreciated!

---

### Post by Iowan on 2009-08-07
I haven't used the Linksys WRT54G, so I'm not familiar with whether or not it can issue static leases (fixed addresses), but a static lease *might* solve both problems.

---

### Post by chili555 on 2009-08-07
> the router won't connect me to the Internet.Of course it will. If you got it to share the printer, it is connected to the router just fine. Did you set up */etc/resolv.conf* when you tried static? 

My desktop machine, and two other machines, are all are set with static IP's.

They all worked with my WRT54G until I had to replace it. They work perfectly now with AT&T's 2Wire device.

---

### Post by ladasky on 2009-08-07
> **chili555 said:**
> Of course it will. If you got it to share the printer, it is connected to the router just fine. Did you set up */etc/resolv.conf* when you tried static? 

 
Well, of course there must be some way to do it... that's why I'm asking for your help!  :)
 
Resolv.conf wasn't mentioned in the network troubleshooting docs which are part of the installation, so I didn't know to look for it.  A keyword search pulls it up.  I'll read the man pages and go through online help... but if you know what exactly it is I need to do, that would be great.

---

### Post by chili555 on 2009-08-08
When you set up your networking interface to use DHCP, it asks the router for nameservers; that is, the IP addresses that may be used to translate 'www.google.com' which the internet protocol doesn't understand, to '74.125.45.99' which the protocol uses. If you set up for static, it is assumed that you will obtain and supply proper nameservers.

The good news is that the IP address of the router will usually do it. In the setup for static IP, it should show a place to enter DNS nameservers. You can safely use the router's IP, 192.168.1.1, for example.

Since this is a stay at home, stationary computer, you can safely disable Network Manager. Then *sudo gedit /etc/network/interfaces* to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
```Proofread, save and close gedit. Substitue your details here. Pick an address outside the range of the DHCP server in the router. If I remember correctly, the default for the WRT54G is to start at x.100 and allow up to 50 IP addresses (far too many, in my opinion). You can then safely use x.160.

Edit */etc/resolv.conf* to look like: ```
nameserver 192.168.1.1
```Proofread, save and close. Restart networking:```
sudo /etc/init.d/networking restart
```You should be all set.

---

### Post by ladasky on 2009-08-08
Thank you chili555.  I tried what you suggested, and I can connect to the Internet using a static local IP.
 
Afterward, I also realized that you can use the GUI to get you the same result.  
 
From the Gnome menu bar: System > Administration > Network > Wired Connection > Properties.  On my first attempt, I had already changed the configuration here to static IP, and assigned an IP address.  What I didn't do was assign a subnet mask and gateway address.
 
Going back to the Network Panel, click on DNS and add the IP addresses of the domain name servers.
 
So far, so good.  HOWEVER: let me introduce one more wrinkle.  I had shared folders on my desktop which were visible to external machines under DHCP.  These folders were shared by right-clicking on the folders in Nautilus and selecting Sharing Options.  Some software was required (Samba?), duly downloaded, and the folders appeared.
 
I also have an Ubuntu laptop.  The shared folders appeared in Nautilus under the network:/// link.
 
When I switched to a static IP, those shared folders became inaccessible.  Can I get them back?
 
Thanks again...

---

### Post by ladasky on 2009-08-08
All right... I just discovered Samba, and read a few docs.
 
Now I have two Ubuntu machines, a laptop and a desktop, talking to each other nicely using DHCP.  They can both access the Internet through my router.  I have a shared printer on the desktop.  My shared folders on each machine have re-appeared.  It looks like Samba is also available for Mac OS X, which I will install on my wife's laptop.

Now, why it proved to be necessary to _add_ LAN software to my Ubuntu 8 installation, when I got the same capabilities out of the box with Ubuntu 6, is a bit of a mystery to me... :confused:

---

### Post by Iowan on 2009-08-09
> **ladasky said:**
> Now, why it proved to be necessary to _add_ LAN software to my Ubuntu 8 installation, when I got the same capabilities out of the box with Ubuntu 6, is a bit of a mystery to me... :confused:Ubuntu comes with client software for several apps, but the server must generally be installed. I don't remember a Desktop version that came with samba-server as far back as Breezy (not that my memory is all that good...).

---

### Post by ratcheer on 2009-08-09
I set up printing from my Ubuntu host to my printer connected to a Win XP host, last night. The instructions I was following said I needed to specify the fixed IP address. But, as I was following the instructions, the XP PC showed up with its DHCP host name and I decided to try it. It works, just fine.

Maybe I don't understand your problem, but my Ubuntu host is also using DHCP assigned by my router. Everything is working, very well.

Tim

---

### Post by chili555 on 2009-08-09
> Maybe I don't understand your problemWhen your XP gets a different IP address from the router, your Ubuntu machine will no longer be able to see the printer. Then, you will have to repeat the setup to find it again...and again.

---

### Post by ratcheer on 2009-08-09
> **chili555 said:**
> When your XP gets a different IP address from the router, your Ubuntu machine will no longer be able to see the printer. Then, you will have to repeat the setup to find it again...and again.

Ok, thank you. I had wondered about that.

But, if the Windows host gets a new IP, wouldn't you also have to reconfigure the printer for the new IP, as well? Or, are you saying that every host on the LAN needs to have a static IP?

Tim

---

### Post by chili555 on 2009-08-09
Only the computer that has the printer attached to it needs a static IP. (For example, in the case of my own network, 192.168.1.116) The printer itself needs no special configuration. All the other computers need to set up a networked printer at the static IP of the printer's host. (Again, in my system, 192.168.1.116)

Routers are creatures of habit. They tend to use the same pattern for many weeks or even years. Your XP machine may get the same IP address again and again and you may have no problems. But, I predict, some day you will. And then you will hear my least favorite sound of all; your loving partner yelling from the next room; "What's wrong with this dang computer?"

---

### Post by ladasky on 2009-08-09
> **chili555 said:**
> Only the computer that has the printer attached to it needs a static IP.

OK, we'll have to see how this goes, but I seem to have everything working now with the printer/file server on DHCP.  Installing and configuring the Samba server software did it for me.
 
Yes, I know that one day my router will issue a different IP number for my server than it is using now.  In fact, I've programmed my router to let connection licenses expire after 12 hours idle time.  
 
HOWEVER, my server is now broadcasting its name to the router.  That name shows up on the router's DHCP client table.  The Samba clients are connecting to the server using its name, not its IP address.  I'm confident that the client machines will be able to find the server even if its IP address changes.

One other side note: on the WRT54G router at least, there doesn't seem to be an easy way to track the presence of devices which are connected via static IP.  The DHCP client table does not show static IP connections, and there doesn't appear to be an "all clients" table anywhere.

My conclusion: printer sharing using DHCP is possible, with Samba.  That's the way I chose to go.  You can share a printer without Samba, if you are willing to used fixed IP addresses.

---

