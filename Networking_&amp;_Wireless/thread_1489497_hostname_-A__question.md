---
title: "hostname -A  question"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by pwaugh on 2010-05-21
My laptop on my wifi gives this:

patrick@laptop:~$ hostname -A
laptop.local

I like using the ".local" shorthand, and wanted to refer to my Ubuntu server with the hostname "server" using "server.local"but

patrick@server:~$ hostname -A
server

with no ".local" given.  Can someone educate me?  I want to change the laptop's hostname (I thought I did), and I also want to be able to easily ssh to it like this:

$ ssh server.local

and am not sure what I'm doing wrong.  Does this happen because my server is on ethernet to the wifi router, whereas the laptop is on wifi?

patrick

---

### Post by bab1 on 2010-05-21
> **pwaugh said:**
> My laptop on my wifi gives this:

patrick@laptop:~$ hostname -A
laptop.local

I like using the ".local" shorthand, and wanted to refer to my Ubuntu server with the hostname "server" using "server.local"but

patrick@server:~$ hostname -A
server

with no ".local" given.  Can someone educate me?  I want to change the laptop's hostname (I thought I did), and I also want to be able to easily ssh to it like this:

$ ssh server.local

and am not sure what I'm doing wrong.  Does this happen because my server is on ethernet to the wifi router, whereas the laptop is on wifi?

patrickA direct answer to your question is: Maybe...

I have some answers and some questions.  Let's start with what is a host name.  The convention for **Fully Qualified Domain Name** is this: *server.local*.  The hostname is *[COLOR="Blue"]server[/COLOR]*.  The domain suffix *[COLOR="Green"].local [/COLOR]*.  That being said you can define almost any name in the /etc/hosts file.  Note: the hostname is really defined in the file /etc/hostname not /etc/hosts.  Lastly the *hostname *man pages defines [FONT="Courier New"][SIZE="2"]hostname -a [/SIZE][/FONT]as ```
 -a, --alias
	      Display the alias name of the host (if used)
```

The /etc/hosts file is for DNS resolution not the definition of the hostname.  It is where I define aliases for my router and printer.  The routers hostname is *bb-gw1* and it's alias is *router*.  The printer is similar.  The hostname is bb-hp1 and the alias is *printer*.

In addition there is the protocol Avahi.  Avahi uses the DNS suffix *.local* for configuration Zeroconf hosts.  This is installed on most Ubuntu distributions the have a GUI desktop interface.  The Ubuntu version could be important as the configuration parameters have changed on the latest version.

What version of Ubuntu are you using for 2 machines?  How have you configured the IP addressing on these hosts?  How/where did you define the hostnames?  Post the contents of```
/etc/hosts
/etc/hostname
/etc/network/interfaces
```

---

### Post by pwaugh on 2010-05-27
patrick@laptop:~$ cat /etc/hosts
127.0.0.1	laptop	localhost.localdomain	localhost
127.0.1.1	laptop

192.168.1.20	server.hsd1.ky.comcast.net	server.local	server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

patrick@laptop:~$ cat /etc/hosts
127.0.0.1	laptop	localhost.localdomain	localhost
127.0.1.1	laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

patrick@laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

with the laptop using Ubuntu 10.04 LTS with updates to date.

The server is using Ubuntu Server 10.04 LTS, and is as follows:

patrick@server:~$ cat /etc/hosts
127.0.0.1	server	localhost.localdomain	localhost
127.0.1.1	server.hsd1.ky.comcast.net.

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

patrick@server:~$ cat /etc/hostname
server

patrick@server:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

and FYI, the hostname -A option is NOT the hostname -a option.  ;)

patrick

---

### Post by bab1 on 2010-05-27
> ...and FYI, the hostname -A option is NOT the hostname -a option.
Unless something has changed with Lucid (10.04), there is no hostname -A option in the man pages of [FONT="Courier New"]**hostname**[/FONT]

It sure makes it difficult to read when you don't use the [ code] [/code]brackets when sending the data.  Never the less;

I see that both the server and the client use DHCP?  Does the server have a reserved (never changing) IP address?

I don't see the laptop's output of: ```
cat /etc/hostname
```

I believe that you will find it best to name the loopback (lo) interface only as: localhost.  The loopback interface is internal to that host only.  

When you name interfaces (/etc/hosts) you are not defining the hostname. You should use the hostname as the primary name on the active interface (i.e. eth0 or whatever) all others can be considered aliases of that name.

The hostname (/etc/hostname) is not the FQDN such as host.domain.  If you want to use that as an alias in the /etc/hosts file that is fine, but it is an alias not really the hostname.

---

### Post by pwaugh on 2010-05-27
@bab1

While I appreciate your effort, as you clearly didn't read what I posted (which does indeed contain both the laptop and server output you requested) and you are not familiar with the -A option I imagine you are not the right person to attempt to help me.  Your post really didn't answer the question, or suggest a direction and so really hasn't added to the discussion.

I am familiar with and understand completely what you have posted.  The contents of the hosts and hostname were generated by Ubuntu.

For the benefit of anyone else I repost the outputs

**Laptop**
```

**patrick@laptop:~$ cat /etc/hosts**
127.0.0.1 laptop localhost.localdomain localhost
127.0.1.1 laptop

192.168.1.20 server.hsd1.ky.comcast.net server.local server

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**patrick@laptop:~$ cat /etc/hosts**
127.0.0.1 laptop localhost.localdomain localhost
127.0.1.1 laptop

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**patrick@laptop:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

```

**Server**
```

**patrick@server:~$ cat /etc/hosts**
127.0.0.1 server localhost.localdomain localhost
127.0.1.1 server.hsd1.ky.comcast.net.

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

**patrick@server:~$ cat /etc/hostname**
server

**patrick@server:~$ cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

And for the benefit of bab1:

> 
```
-A, --all-fqdns
              Displays all FQDNs of the machine. This  option  enumerates  all
              configured  network  addresses  on all configured network inter&#8208;
              faces, and translates them to DNS domain names.  Addresses  that
              cannot be translated (i.e. because they do not have an appropri&#8208;
              ate  reverse  DNS  entry)  are  skipped.  Note  that   different
              addresses may resolve to the same name, therefore the output may
              contain duplicate entries. Do not make any assumptions about the
              order of the output.
```


Basically, the question remains why without modification of Ubuntu generated setup can I use the .local with the laptop, but not the server?

patrick

---

### Post by bab1 on 2010-05-27
> **pwaugh said:**
> @bab1

While I appreciate your effort, as you clearly didn't read what I posted (which does indeed contain both the laptop and server output you requested) 
It really doesn't matter to me, but for clarity, I did read and understand.> 
and you are not familiar with the -A option 
Remember what I said " unless something has changed...:  Well it has.  On my Hardy systems -A is --fqdn.  but you must have mised that.  ;-)> 
I imagine you are not the right person to attempt to help me.  Your post really didn't answer the question, or suggest a direction and so really hasn't added to the discussion.
I'm not here to hold your hand.  You can do that.  But beggars can't be choosers and I don't see any other people interested in joining in the conversation.> 

I am familiar with and understand completely what you have posted.  The contents of the hosts and hostname were generated by Ubuntu.

So where is the contents of the command [FONT="Courier New"][SIZE="2"]**hostname **[/SIZE][/FONT]for the laptop?  When I can see all I don't need to guess.  My best guess is that you have Avahi running on the laptop generating the .local domain.  The server does not run that.  Avahi is part of the desktop environment. 

You really should learn to control you urge to be combative.  Even if I was a complete nut case, which I am not, your tone is condescending and out of line.

---

### Post by Iowan on 2010-05-27
I'm also running Hardy - so I also got: ```
Iowan@DELL:~$ hostname -A
hostname: invalid option -- A
```>  	
While I appreciate your effort, as you clearly didn't read what I posted (which does indeed contain both the laptop and server output you requested)Your laptop listing included the results of */etc/hosts* twice instead of */etc/hosts* and */etc/hostname*.

---

### Post by pwaugh on 2010-05-27
Yes, apparently in this post I didn't specifically state the obvious (see the -A), but here it is:

```

patrick@laptop:~$ hostname
laptop
patrick@laptop:~$ cat /etc/hostname
laptop
```

and yes, it does appear that Avahi is the "why".  Indeed it is running on the laptop, and not the server.  This is what another post had pointed to as the issue as well.  To bad it also failed to overview how avahi functions to do what it does.

Back when the Internet was created we didn't have Bonjour/Avahi etc., it was all hosts files then DNS.  I guess I will have to educate myself on Avahi, and until then just do it the old fashioned way.  Likely, just using the hosts file is the right way to go anyway since the server's IP will be fixed anyway, etc.

Given the initial post, where I clearly show the -A option you would have been better off running man or the command to see what it does, rather than try to tell me I was running -a, which really just confused the issue.  Perhaps you are not running 10.04 LTS and cannot do so easily.

At least I now have confirmation that it is an Avahi thing.

patrick

---

### Post by pwaugh on 2010-05-27
> **Iowan said:**
> I'm also running Hardy - so I also got: ```
Iowan@DELL:~$ hostname -A
hostname: invalid option -- A
```Your laptop listing included the results of */etc/hosts* twice instead of */etc/hosts* and */etc/hostname*.

Yes, this is on 10.04 LTS, not Hardy, so must be a new option, thanks.

```
patrick@laptop:~$ hostname -A
laptop.local 
patrick@laptop:~$
```

patrick

---

### Post by pwaugh on 2010-05-27
This post has helpful info on this zeroconfig/Bonjour-like thing:

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

if others need a "primer" on this subject.

patrick

---

