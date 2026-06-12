---
title: "Computer finding the name of another computer under DHCP"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by hardtofindausername on 2010-09-10
Good day everyone!


I have two Linux computers and one small home router with DHCP functionality.  I configured the router with the "dynamic DHCP" setting, ie, the static DHCP with MAC-Address was not used.

Before that, I used the manual IP configuration, defining the two computers' names in the /etc/hosts file.

Example:
10.0.0.2   comp2
10.0.0.3   comp3

Now, with DHCP, the above example is no longer appropriate, because the DHCP server is supposed to tell the computer what IP number it will receive.

However, I am missing something, because I haven't figured it out yet how to make one computer know the other computer's name.

Is it that I haven't installed a name-finding package?  Is there a simple way to accomplish this (one computer finding the other computers' names)?

Thanks in advance!

---

### Post by BkkBonanza on 2010-09-11
Ideally a good DHCP server will provide local DNS as well. dnsmasq does this but your router may not or may not be configured to provide it. The DHCP server can get the hostname of each machine during discovery and record it in a local DNS table. Check your router if it has options about enabling local DNS. 

Your LAN machines should also get a DNS server assigned during IP assignment. In order to do local DNS for them the DHCP will usually assign itself as DNS forwarder so that it can filter DNS requests and handle local names. If it is assigning your ISP or other DNS servers directly to each machine then it cannot handle local names for the LAN. Each router potnentially has different options so your best initial bet is to see if you can configure the router to do this.

---

### Post by hardtofindausername on 2010-09-12
[BkkBonaza]("http://ubuntuforums.org/member.php?u=550406"), thank you for the ideas you forwarded.

From the web interface to my router, I could see that it has 0.0.0.0 as the Primary DNS. (The Secondary DNS has the same address but it's also marked as optional.) Now, I think I can tweak with these two options: one would be to experiment with that DNS field at the router. The other would be to make each Linux machine have the dnsmasq you mention.

Another interesting fact is that outside names are okay, ie, I can point to a URL at a browser and it'll work normally.

I hope it'll get to making one machine know the other machine's name.

---

### Post by Iowan on 2010-09-12
Check */etc/dhcp3/dhclient.conf*  - there's a line to "send host-name" that should be edited to include the machine's name.

---

### Post by kgas on 2010-09-13
another way to find the computer name is using dns
dig -x <your_computer_IP> and check in the answer section.

---

### Post by Bucky Ball on 2010-09-13
Just a question; is there any particular reason you are swapping from static to dynamic?

---

### Post by hardtofindausername on 2010-09-13
Bucky Ball, I wasn't using Static-DHCP before.  Previously I was "hardcoding" every 10.0.0.x-IP address (a very simple scheme...), in every computer, in their /etc/hosts files.  So at that time I was not using the router's capability to serve IP numbers as DHCP.

But you raised one interesting thought: would the computers be able to find each other's names by just using Static-DHCP instead of Dynamic-DHCP?  Okay, there is this overhead work of entering and administering the MAC identifiers; well, however, it's still an option!

---

### Post by hardtofindausername on 2010-09-13
kgas, thanks, but I'm afraid I don't have this command available.  I'll see to it if I can find how to install the package that brings it.

---

### Post by hardtofindausername on 2010-09-13
Iowan, thanks!

Just two issues: 1) I've checked in my distro (Fedora), it doesn't have this file (and paths are a little different too).  2) Perhaps, it will have it (the conf file) if I install or set up DHCP.  But that is what I've been meditating: the DHCP is in the router, not in the Linux machine.  Does it make sense?

---

### Post by Bucky Ball on 2010-09-13
I switched off all DHCP in my router and used System->Admin->Network to set static IPs on my three machines and works a charm. Names come up in Samba (which I don't use) but I use SSH and the IPs. 

Places->Connect to Server->SSH. Enter IP of the machine you want, you'll get asked for the machine's user name and password and you're there. You can place a link in 'Places' to the remote machine and from then you should only be asked for the User/pw details, not the IP.

Works for me. After initial setup nothing to it.

ps: As you use Fedora these details might be no good to you but there must be somewhere you can set the IP address of the machine on the machine (not the router). If you find it and set an IP, REMEMBER to switch of DHCP server on the router or you will get probs (machine telling router its IP while router trying to assign one to the machine).

---

### Post by BkkBonanza on 2010-09-13
I'm not sure if it's the default config for dhclient but my /etc/dhcp3/dhclient.conf has the following line,

send host-name "<hostname>";

which ensures that it sends the hostname when aquiring a lease. I'm sure it would do this for static or dynamic. A good dhcp server should be able to push that into the local DNS tables (dnsmasq does).

...
There are two sides to DHCP. There is a server on the router and a client on each machine. When booting the client says to the server, "hey, I'm here now can I get a lease", and the server responds "yup, here's you IP and network values, DNS etc". You need the client to say "I'm here and this is my hostname".

There are a few popular dhcp client programs around. dhclient3 is used usually on Ubuntu, but on Fedora you may have to check what they use and where it's conf file is located. Look for dhcpcd as well.

Most distros do install a dhcp client by default because it is the most common LAN setup and for most users "just works".

---

### Post by kgas on 2010-09-14
I corrected my previous post instead of dig i put dns :(.
for more details on dig read [this](http://www.madboa.com/geek/dig/)

---

