---
title: "SSH + VPN + VNC = I'm confused"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by yc2 on 2009-11-19
I want to remotely control my Linux computer and the network it is on. Not only the web-server but also directly access files for word processing and surfing using that computer as a proxy.

My experience is very limited. I used SSH for CLI control of my computer webserver for a while. (Using Putty as an SSH client in Windows and Filezilla for sftp.)

**My problem is that I do not understand how VPN works in practice.** What I think I understand is that VPN (PPTP, poptop) will connect the remote computer (IP-layer) to the LAN of the computer I want to control.

If I have understood correctly, I can for example surf from the remote computer but it will appear to the sites I go to like if I am surfing from the host-LAN.

BUT HOW DO OTHER FUNCTIONS WORK?
If I f.ex. want to access files on the host computer, how is that done? Just being connected to the LAN of the host will not give me that function.

I have tried to collect information in the Internet but I can not find good examples. My question is maybe too simple. **Will I get a graphical desktop environment of the host computer when I use VPN?** If I start a word processor program and edit files, will the program and files be the program and files of the host computer?

Thanks. Please keep the answer simple. **[COLOR="Red"]I just want to know how these methods work when they are running.[/COLOR]** The details about installation I will try to find out later.

---

### Post by dmizer on 2009-11-19
Depending on how you configure your VPN, you will get access to any resource on the remote LAN because VPN essentially makes you part of the remote LAN.

For example, if you set a VPN connection to your home network. Then you go to a hotel and connect to your home network from your hotel, you'll be able to connect to your LAN's samba shares, VNC, SSH, or any other network resource in just the same way you do when you are at home.

It may be of interest for you to note that SSH can do most of this without the need for VPN.

---

### Post by yc2 on 2009-11-20
[QUOTE=dmizer]VPN essentially makes you part of the remote LAN.[/QUOTE]
Thanks dmizer for very clear reply.

VPN
I now understand that VPN will connect my client to the host LAN. I can access files that I may have put on SAMBA-shares, I can CLI-control my host computer through VPN+SSH. I can also GUI-control my computer through VPN+VNC.  (Tasks that I could also do without VPN.) Whatever programs I start on the client that use the connections of the client computer (like web-browsing or ftp) it will appear to the remote computers that I am connected to the host computer.

SSH
Thanks for pointing out SSH.
I have understood that SSH works on the application layer (whereas VPN works on the internet layer).
In this case I must somehow set up port-numbers (whereas VPN will "transfer" my entire client connection to the host LAN.)

I found information that I can start an SSH tunnel and then set my browser to use that port (instead of port 80) for sending requests.
```
ssh -D 8080 -f -C -q -N myuser@myserver.com
```

I assume I could do a similar thing for the VNC?

The difference in surfing through port 8080 and using VNC would be that in using port 8080 I would use the browser of the client computer (like in VPN). Using VNC I Would use the browser of the host computer. I guess VNC would give a slower connection, but naturally be very versatile, being able to control any aspect of the host in GUI.

If I wanted to control the host computer and also surf with it at the same time, using SSH, I guess i would have to open two tunnels at the same time?
```
ssh -D 22 -f -C -q -N myuser@myserver.com
ssh -D 8080 -f -C -q -N myuser@myserver.com
```

I guess implementing either SSH or VPN will give me some interesting problems/headache. ;) I will have to think further which one to choose.

Thanks dmizer.

---

### Post by drseuk on 2009-11-20
> **yc2 said:**
> Thanks dmizer for very clear reply.

VPN
I now understand that VPN will connect my client to the host LAN. I can access files that I may have put on SAMBA-shares, I can CLI-control my host computer through VPN+SSH. I can also GUI-control my computer through VPN+VNC.  (Tasks that I could also do without VPN.) If I start programs that use the connections of my client computer (like web-browsing or ftp) it will appear to the remote computers that I am connected to the host computer.

SSH
Thanks for pointing out SSH.
I have understood that SSH works on the application layer (whereas VPN works on the internet layer).
In this case I must somehow set up port-numbers (whereas VPN will "transfer" my entire client connection to the host LAN.)

I found information that I can start an SSH tunnel and then set my browser to use that port (instead of port 80) for sending requests.
```
ssh -D 8080 -f -C -q -N myuser@myserver.com
```I assume I could do a similar thing for the VNC?

The difference in surfing through port 8080 and using VNC would be that in using port 8080 I would use the browser of the client computer (like in VPN). Using VNC I Would use the browser of the host computer. I guess VNC would give a slower connection, but naturally be very versatile, being able to control any aspect of the host in GUI.

If I wanted to control the host computer and also surf with it at the same time, using SSH, I guess i would have to open two tunnels at the same time?
```
ssh -D 22 -f -C -q -N myuser@myserver.com
ssh -D 8080 -f -C -q -N myuser@myserver.com
```I guess implementing either SSH or VPN will give me some interesting problems/headache. ;) I will have to think further which one to choose.

Thanks dmizer.

Personally I'd say that tunnelling over SSH would meet all your needs - remember the "X Windowing System" is and always has been designed to be "network-transparent" for exactly the kind of needs you require ...

Google "FreeNX" and enjoy!

---

### Post by yc2 on 2009-11-20
[quote=drseuk]Google "FreeNX" and enjoy![/quote]
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Thanks drseuk!

So, to me FreeNX seems to be  the final solution to "Life, the Universe and Everything" ;) ;)

It will give everything in one package? Just like sitting in front of your remote computer?

So now I have these choices:

[LIST=1]
[*]**VPN **(must be complemented with SSH or VNC to control the computer, surfing will work instantly, files must be "put on SAMBA")
[*]**SSH **(separate tunnels for CLI and surfing or maybe just one tunnel for VNC; files will have to be put on sshfs?)
[*]**FreeNX **(based on SSH)
[/LIST]

**Thanks for the replies in this thread, I think things have become more clear to me now.** However I still have problems to choose. It seems, from your advice, that VPN is "difficult" and SSH is "simple". I guess that describes the installation the servers and clients.

I guess the choice between these three alternatives will be based on practical issues.

**Does anyone have any more advice to give about which method to choose?**

Naturally it seems practical to be able to reach all the files on my host immediately and not only those I put on SAMBA-shares. - I haven't used nfs or sshfs yet. sftp is maybe a good complement.

---

### Post by Lars Noodén on 2009-11-20
Using ssh as a socks5 proxy, or in any other capacity where forwarding is used, you can specify multiple ports in one action:
```

ssh -D 80 -D 8080 -f -C -q -N myuser@myserver.com

```

For Firefox, you'll also want the dns requests to go via your proxy, so changing about:config needs network.proxy.socks_remote_dns set to true
It'll be the same for other programs.  

You can tunnel samba over ssh, too.  
SSHFS works, too.

---

### Post by yc2 on 2009-11-20
Thanks Lars,

I will gradually have to learn about this. What is not clear to me is how the ssh host server knows what to do with the requests that come in on "unfamiliar" ports. Will I have to setup the ssh server so that it knows f.ex. that I want requests on port 22 to be CLI input and requests on port 8080 to be transmitted as requests for port 80? (or are these port numbers maybe already assigned by default to the respective actions? )

I have used Putty for giving CLI commands to my SSH (web) server, but at that time I wasn't aware of the broad versatility of the SSH server that I have just got help understanding.

I like your Windows refund signature. Hearing your name I want to ask if you too are from Sweden?

---

### Post by Lars Noodén on 2009-11-21
> **yc2 said:**
> Thanks Lars,

I will gradually have to learn about this. What is not clear to me is how the ssh host server knows what to do with the requests that come in on "unfamiliar" ports. Will I have to setup the ssh server so that it knows f.ex. that I want requests on port 22 to be CLI input and requests on port 8080 to be transmitted as requests for port 80? (or are these port numbers maybe already assigned by default to the respective actions? )

I have used Putty for giving CLI commands to my SSH (web) server, but at that time I wasn't aware of the broad versatility of the SSH server that I have just got help understanding.

I like your Windows refund signature. Hearing your name I want to ask if you too are from Sweden?

The server only listens to ports it is told to listen to, the default is 22.  That is used to make a connection.  The client can forward local ports to the server.  

I made a correction above, the -D should not have been for port 22, that might have caused some confusion.

Regular forwarding (-L or -R) is 1:1.  A port on one machine and a port on another machine are for many purposes one and the same

Dynamic forwarding leaves one end of the connection 'to be announced later'  

I think it's hard to explain.  You can watch most web site connections using [tcpdump](http://linux.die.net/man/8/tcpdump) and see the outgoing port number change as you surf:

```

sudo [tcpdump](http://linux.die.net/man/8/tcpdump) -q -l -i eth0 "port 80"

```

The "port 80" part is a matching expression which selects packets going to or from port 80 on either the source or the destination.  

To over simplify, if you get a web page, one of the connections will be TCP to port **80** on a remote machine and a reply from port **80**.  If you have web server on your local desktop that uses port 80, you would see a connection like **a** and **b** below.  You see the outgoing port, in this case 35053, will be different each time.  So you can't really know in advance which port the client will use for the out going connection.  

**edit** 2009-11-23 : a,b,c,d,e and f below are output from [netstat](http://manpages.ubuntu.com/manpages/karmic/en/man8/netstat.8.html).

```

  Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
**a** tcp        0      0 127.0.0.1:35053         127.0.0.1:**80**          ESTABLISHED
**b** tcp        0      0 127.0.0.1:**80**          127.0.0.1:35053         ESTABLISHED

```

But if **e** is a tunnel with dynamic forwarding, 

[indent]ssh -D 80 -f -C -q -N [email]myuser@myserver.com[/email][/indent]

it will still look the same on your desktop (client).

```

  Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
**c** tcp        0      0 127.0.0.1:35053         127.0.0.1:80          ESTABLISHED
**d** tcp        0      0 127.0.0.1:80            127.0.0.1:35053       ESTABLISHED
**e** tcp        0      0 client:60985            server:22             ESTABLISHED

```

However, the connection **f** appears on the sever, on demand, and finishes the connection to the remote service.  **g** is the other half of the tunnel.  

```

  Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
**f** tcp        0      0  server.4641      91.189.94.12.**80**        ESTABLISHED
**g** tcp        0      0  server.22        client.60985           ESTABLISHED

```

In other words, with dynamic forwarding **c**, **d**, and **f** are all part of the same connection even though the port numbers (high port numbers) change at any time.  



[indent]
I did some studies and worked in, around and next to Sweden with Swedish teams for some years. 

Re. the sig,[SIZE="1"] 80 EUR is 80 EUR.  It's not enough for a new monitor by itself, but it is enough for a nice HD or other peripheral.  Or it is enough to turn 100 EUR into enough for a new monitor.

However, if the guidelines (SFS) and regulations published by the Swedish government, including articles of the constitution, are anything to go by 
then it's [more than a matter of money](http://www.expressen.se/ledare/1.1663751/johanna-nylander-microsoft-hotar-var-demokrati).[/SIZE]
[/indent]

---

### Post by yc2 on 2009-11-23
Thanks Lars, very clarifying.

Maybe I haven't understood completely or maybe not all data are there?

Shouldn't there also be records for the packets comping back from Canonical to your SSH-server?
```
tcp        0      0  91.189.94.12.80         server.4641           ESTABLISHED
```

I am unfortunately not sitting in front of Ubuntu now. (Which is one reason for wanting to use remote connections.) So I cannot try out tcpdump right now, I but I definitely will at first opportunity.

Thanks a lot.

---

### Post by Lars Noodén on 2009-11-23
> **yc2 said:**
> Thanks Lars, very clarifying.

Maybe I haven't understood completely or maybe not all data are there?

Shouldn't there also be records for the packets comping back from Canonical to your SSH-server?
```
tcp        0      0  91.189.94.12.80         server.4641           ESTABLISHED
```


netstat shows the connections.  tcpdump shows the packets.  The above were from netstat.

> **yc2 said:**
> 
I am unfortunately not sitting in front of Ubuntu now. (Which is one reason for wanting to use remote connections.) So I cannot try out tcpdump right now, I but I definitely will at first opportunity.

Thanks a lot.

These work fine from Mac OS X or any Internet-safe system you would have at work.  However, they require root level access or at least permission via sudo.  

```

%groupofyc2  ALL=(ALL) NOEXEC: NOSETENV: NOPASSWD: /usr/sbin/tcpdump, /bin/netstat

```

Or you can grab a live CD or usb stick and boot from that.  The Ubuntu Live CD may not have the right tools, but Finnix should.

---

### Post by yc2 on 2009-11-23
Thanks Lars,

all good help to me.

Unfortunately I move around and almost always use Internetcafés which do not approve of CDs, in fact the modern Internetcafés seem to have good computers, but no CD-players at all.

I don't know if I can make some tests as a regular user in Win.

But like you say, booting from USB stick is at least possible technically even if I don't know if I could make the staff of the Internetcafé allow me.

I try to write some simple instructions about Ubuntu in Swedish on web-pages, but I don't even know if it comes out OK in FF/Linux since I haven't been able to run Linux. [[Link]("http://web.telia.com/~u17103363/doc/ubu_nav.htm")]

The last time a person let me run the Live-CD I never got it running. On first try the desktop background came up but no more. (ctrl/alt/F1 worked but gave error messages even on shutdown command. When I tried next time the computer didn't even recognize the CD in the boot-order sequence)

I have only read the instructions for making a bootable USB-stick, I do not have the invironment right now to try it out. I have seen the avatar you use and now I also know that it comes from Finnix. Will have to check out the distro of my firendly neighouring country when I have the possibility.

Thanks

---

### Post by Lars Noodén on 2009-11-24
> **yc2 said:**
> ... from Finnix. Will have to check out the distro of my firendly neighouring country when I have the possibility.


[USA](http://www.finnix.org/Frequently_Asked_Questions#Why_the_name_.22Finnix.22.3F_Is_it_related_to_.22Knoppix.22.3F)?  ;)

If you're logging in via public Windows machines it would be safe to assume they are cracked six ways from Sunday and any passwords you enter would get compromised.  

Keys would help a little, and should be used for authentication, but some kind of challenge-response back up method is needed, too.  One-time passwords are a way to do that and donkey and opie are two open source ones.  Those give you some codes to print out and then when you log in, it asks you to type in one of the lines like the banks do.

---

