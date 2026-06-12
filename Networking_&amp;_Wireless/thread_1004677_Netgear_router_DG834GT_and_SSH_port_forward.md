---
title: "Netgear router DG834GT and SSH port forward"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by candtalan on 2008-12-07
Using Ubuntu 8.04

I am almost concluding here that my new netgear router does not work as it is supposed to......(!)

I successfully got into the basics of ssh, vnc and port forwarding recently when I was using my home vigor 2600 router. It was confusing at first but I think I got the hang of it and I could connect to one machine using its internet IP address, with vnc through an ssh tunnel, using keys, from another machine. The same  keys are still in place in the two machines so I am not expecting a problem with them (?)

I am now having trouble. With the same two machines, (a laptop trying to connect into a desktop), in a different location, and significantly now using a completely different router which handles port forwarding in a very different way to the way the vigor did.

The router instructions seem clear enough, and I am following them. However, it looks as if the port forwarding is not happening, or anyway, I get a response when using
ssh [IP address of desktop]
response is
ssh: connect to host [IP] port 22: Connection refused

This happens even if I set to use a non standard port such as 2222 or another, also. I am editing the files ssh_config (laptop) and sshd_config (desktop) for the port number.

If I sit at the desktop and ssh into itself at local host
ssh user@localhost
I was asked for the key pass phrase then the user password, and appeared to be connected ok.

Having set up router port forwarding for say incoming TCP port 222 at the  router, to go to (NAT) machine 192.168.0.192, is there a way to test this out?

I used the 'shields up' site to look at ports, and it sees a closed port (in this case) at 222, while other ports are full stealth. Is this a sign that the port forward setting on the router is having some effect at least?

What tests can I do to try to solve this lack of connection? The router ports?

Maybe I am doing something wrong here?
Comments most welcomed
tia

---

### Post by jmoorse on 2008-12-07
Tia,

You need to configure NAT to Forward external TCP22 to internal TCP22 at machines local IP. 

If that appears to be setup correctly you will want to test your SSH connection from a separate machine within the Local Network:

ssh (internal IP of server)

Case 1: No connection.  This means there is most likely a firewall on the ssh server blocking incoming TCP22

Case 2: Works fine.  Revisit port redirection and static NATs following manufacturer recommendations.

---

### Post by candtalan on 2008-12-07
Over the local network when trying to connect from the laptop I am asked to approve authentication of the desktop machine. So it is getting through ok. Although I do not understand why I am asked for approval since the public key of the laptop is in the authorized_keys file in the desktop (?)


So it looks as if case 2 applies.
However when I try to connect over the internet:

=======

   ssh -vvv user@[IP address]
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to (IP address) [IP address] port 2222.
debug1: connect to address [IP address] port 2222: Connection refused
ssh: connect to host [IP address] port 2222: Connection refused
=======

Which looks as if it is trying to make connection to the port, but it is refused, rather than the port does not exist whatever.

Does anyone know this router well? Netgear router DG834GT ?
Anyone actually done ssh using it please?

---

### Post by jmoorse on 2008-12-07
Here is a rough howto.  Focuses on eMule so just replace those ports with your own:

[http://portforward.com/english/routers/port_forwarding/Netgear/DG834G/eMule.htm](http://portforward.com/english/routers/port_forwarding/Netgear/DG834G/eMule.htm)

---

### Post by candtalan on 2008-12-08
Thanks. The more I look at this stuff the more I think I am actually doing what it says is needed (!) and it still does not work.

I have just found a comment which suggests this particular router  does not allow  the sort of tests I am attempting. My target desktop machine and the laptop which I use to try to connect into the desktop - are both in the same LAN, behind the router. My tests from the laptop of course use the full IP address of the desktop.

The comment I have seen is:
====
'Remember, with this router you cannot view from another computer which shares the same public IP as you, even if it's on the same network as your computer you want to access; you have to do it from another Inernet Connection'

this was seen in forum
[http://mybroadband.co.za/vb/showthread.php?t=23585](http://mybroadband.co.za/vb/showthread.php?t=23585)
====

After reading this, I have now also tried connecting in from the laptop by using a mobile phone internet connection at the laptop, and - it works ok(!)

Rats! I have spent a couple of days of frustration on this.

What is so special about this particular router that it will not allow outgoing from the laptop to an IP address which is the same as the router external IP?

---

### Post by mal on 2008-12-08
candtalan,

I'm not sure that I fully understand what your are trying to do here, but it should not be too difficult.

I often use SSH to connect between machines on my LAN and to connect to one of my machines from the internet, through a DG834 router.

However, to connect from your laptop to your desktop on your LAN, you don't need any port forwarding on the router.  You should be able to just connect directly to the local IP address of the server machine.  Make sure you use the local address, not the internet address of the router.

Once you get this working you should be able set up port forwarding on the DG834 to allow you to connect to your server from another location on the internet.

Mal

---

### Post by candtalan on 2008-12-08
Hi Mal, it is great to hear from a DG834 user!
I understand what you say, and am reassured that you are not having problems with ssh in from the internet.

I have tested things ok using the local addresses.

The special problem I have had is that I am setting up a computer and broadband access for an elderly relative (88 years), Ubuntu of course, carefully set up, and their home is situated across the other side of England meaning nearly a days car travel one way.

Feisty as they are, I will need to support by remote access ssh and vnc unless I want to be in the car a lot........ 

This would not be special if it were not for me being, until recently, totally ignorant of ssh, vnc, tunnelling, and port forwarding, and keys too. 

So recently I configured a PC suitably at my home, and arranged and tested out ssh with vnc keys etc etc and tested it with my laptop in the two situations - inside my home LAN locally, and also (still at home) using the full IP of the desktop from my laptop. This worked, proving not only that I had done the port fowarding correctly but that the other things were ok too.

It also gave me a small taste of what could be done or not done.

With modest confidence I then travelled way cross country and began to set up the relatives new broadband package (which I had arranged).

Initial good news it worked :-)

The bad news was that my tests - which I had done previously with my home vigor router - did not work at all when I used the supplied netgear DG834, which has port forwarding yes but using a different technique. I spent two frustrating days with an apparently perfect setup, trying to do certain tests which I now find apparently this particular router does not allow. I only found this out from the forum quote I gave in an earlier post. Searches reveal occasional posts from people like myself who have seemed to do the initial and obvious tests from home and fail, but then find it works from a friends house. 

My lack of experience in the initially confusing process of ssh vnc, keys and  tunneling, make it important that I can use an elegant method of testing the configuration. Recall that to travel physically to the site to learn new tricks is not really an option here. I need to test things well before I leave for home, also I need the minimum of experience with  what happens.

It looks as if most routers will react sensibly for people doing these tests, but not DG834.

If you find a way of doing so, please shout? I still have a few days on location here and I would welcome easier tests than using a mobile phone connection on the laptop to get out to the internet before connecting.

---

### Post by jmoorse on 2008-12-08
> **candtalan said:**
> 
What is so special about this particular router that it will not allow outgoing from the laptop to an IP address which is the same as the router external IP?

Routing from int directly to ext, back to internal is a common problem with  routers.  e.g.: Trying to connect to a vpn from within the network.

Basically what this is eluding to is that from within your network you will need to connect to your ssh box with its internal ip, the router apparently can't handle NAT/routing int > ext > int

---

