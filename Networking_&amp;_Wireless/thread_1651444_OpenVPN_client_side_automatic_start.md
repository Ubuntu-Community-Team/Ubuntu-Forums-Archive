---
title: "OpenVPN client side automatic start"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by vladdg on 2010-12-23
Hi,

I hope that somebody can help me. My problem is with OpenVPN server / client  (Ubuntu 10.04) connection. 
The problem is that client machine will sit far away, burried in a  cabinet out of sight and out of mind.  If client machine restart, loose power... etc openvpn connection dies and won't restart. 

Im trying to configure on the client side, automatic Openvpn service start and reconnection to the OpenVPN server. I was trying to do that with crontab but without of luck. 

Please can someone help me with crontab syntax or maybe provide some other solution?

Tx

---

### Post by SeijiSensei on 2010-12-23
Just use the "remote" directive in the configuration file for your tunnel, and make sure OpenVPN starts at boot.  Usually it's configured to start automatically when installed, 

For instance, I have a Debian server in a remote location that uses this configuration:

```

dev tun
remote myvpnserver.example.com
ifconfig 192.168.1.2 192.168.1.1
secret /etc/openvpn/mykey.key
port 12345
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

You can designate any port you want, of course, as long as both ends agree on what it is.

---

### Post by TSJason on 2010-12-23
What I did was to create a script in /root that is called from /etc/rc.local (which runs at boot time). The script uses expect to sign into the openvpn server. 

/etc/rc.local looks like this:

```
cd /root ; ./autosignon &

```

and /root/autosignon looks like this:


```
#!/usr/bin/expect -f
set force_conservative 0 
if {$force_conservative} {
        set send_slow {1 .1}
        proc send {ignore arg} {
                sleep .1
                exp_send -s -- $arg
        }
}

set timeout -1
spawn openvpn remote.ovpn
match_max 100000
expect -exact "Enter Auth Username:"
send -- "username\r"
expect -exact "Enter Auth Password:"
send -- "password\r"
expect eof

```

autosignon is chmod +x so that it can be executed. I changed the username and password to generic entries. It's probably also worthwhile to note that my openvpn client certificates and .ovpn configuration files all live in /root. I also have "resolv-retry infinite" defined in my client configuration file.

---

### Post by hackeron on 2011-01-23
> **TSJason said:**
> What I did was to create a script in /root that is called from /etc/rc.local (which runs at boot time). The script uses expect to sign into the openvpn server. 

/etc/rc.local looks like this:

```
cd /root ; ./autosignon &

```

and /root/autosignon looks like this:


```
#!/usr/bin/expect -f
set force_conservative 0 
if {$force_conservative} {
        set send_slow {1 .1}
        proc send {ignore arg} {
                sleep .1
                exp_send -s -- $arg
        }
}

set timeout -1
spawn openvpn remote.ovpn
match_max 100000
expect -exact "Enter Auth Username:"
send -- "username\r"
expect -exact "Enter Auth Password:"
send -- "password\r"
expect eof

```

autosignon is chmod +x so that it can be executed. I changed the username and password to generic entries. It's probably also worthwhile to note that my openvpn client certificates and .ovpn configuration files all live in /root. I also have "resolv-retry infinite" defined in my client configuration file.

How will that automatically restart openvpn if say the network connection goes down or if the server config file changes?

---

### Post by TSJason on 2011-01-23
Your client configuration file should define 
"resolv-retry infinite"

---

### Post by hackeron on 2011-01-23
> **TSJason said:**
> Your client configuration file should define 
"resolv-retry infinite"

That only handles dns or network problems.

It doesn't handle:
1) Server config changes
2) Temporary errors from openvpn server
3) client-connect script problem (e.g. if you use the script to log to a database and it's still starting)
4) Connecting while openvpn server is starting
5) Other unforeseen temporary errors

Basically there are loads of things that can happen that will make that server 30 miles away suddenly disconnect and you have to drive over and manually restart openvpn there :(

I created an upstart config to use instead of the useless init.d script:

/etc/init/myopenvpn:

```

# Xanview OpenVPN Upstart Script

description "OpenVPN - virtual private network daemon(s)"
author "Roman Gaufman <roman@xanview.com>"
version "1.0.0"

start on runlevel [2345]
stop on runlevel [!2345]

respawn

exec /usr/sbin/openvpn --status /var/run/openvpn.client.status 10 --cd /etc/openvpn --config /etc/openvpn/client.conf --syslog openvpn

```

The respawn there will keep restarting openvpn in cast it dies. So far so good :)

---

### Post by SeijiSensei on 2011-01-23
OpenVPN will monitor the connection and restart automatically if you use the "ping" and "persist" directives I have above.  I've never had to run any other scripts to maintain connectivity even from remote machines behind firewalls.

(Actually, after re-reading the man page for openvpn just now, I don't think the "ping-timer-rem" directive is appropriate on the client.  It should be in the server's configuration, though.  It's probably ignored if it's found in the client's configuration.)

---

### Post by hackeron on 2011-01-23
> **SeijiSensei said:**
> OpenVPN will monitor the connection and restart automatically if you use the "ping" and "persist" directives I have above.  I've never had to run any other scripts to maintain connectivity even from remote machines behind firewalls.

(Actually, after re-reading the man page for openvpn just now, I don't think the "ping-timer-rem" directive is appropriate on the client.  It should be in the server's configuration, though.  It's probably ignored if it's found in the client's configuration.)

Not true in the slightest, OpenVPN runs as a single thread, it does not restart once shut down. What you mean is whenever the connection is lost, It will keep trying to reach the server but that's not what I'm talking about.

I'm talking about when the server actively tells the OpenVPN client that it can't connect right now - this generally shouldn't happen, but does whenever you do various maintenance to the server - in this case the client shuts down permanently and you have to restart openvpn manually.

---

### Post by SeijiSensei on 2011-01-24
> **hackeron said:**
> I'm talking about when the server actively tells the OpenVPN client that it can't connect right now - this generally shouldn't happen, but does whenever you do various maintenance to the server - in this case the client shuts down permanently and you have to restart openvpn manually.

How exactly does this happen?  I've taken down the server endpoint on connections like this a number of times.  When the server comes back on line, my remotes just reconnect automatically, since their daemons are waiting to see the server again thanks to the ping and persist directives.

If this weren't true, the whole notion of creating a client/server relationship between the machines would be meaningless.

What kind of "maintenance" are we talking about here?

---

### Post by hackeron on 2011-01-24
> **SeijiSensei said:**
> How exactly does this happen?  I've taken down the server endpoint on connections like this a number of times.  When the server comes back on line, my remotes just reconnect automatically, since their daemons are waiting to see the server again thanks to the ping and persist directives.

If this weren't true, the whole notion of creating a client/server relationship between the machines would be meaningless.

What kind of "maintenance" are we talking about here?

1) Simple example, you have a client-connect script that connects to the database, but the database is still starting - that script will return a non 0 exit code, telling all your openvpn clients to stop trying to connect.

2) For the sake of argument your server booted into a read only filesystem for whatever reason. Say your're trying to boot an unsupported kernel in your vps. All clients are told to stop trying to connect.

3) Hell you need to modify your openvpn server config, change some routes maybe, add that new connection and happen to make a mistake somewhere. All clients are told to stop trying to connect.

4) i can't confirm this 100% but I'm sure I had the server reject connections on startup - maybe for an unrelated reason but point is when the opnevpn is unavailable then the clients will keep trying, but when an openvpn server rejects a connection for any reason, the client stops trying to connect.

I have around 50 clients connecting to my openvpn server and I've had them all disconnect more than a few times now. Just generally even if you never touch your server or don't have client-connect scripts I don't think it's wise to trust a single thread process that may quit at any moment for one of many different reasons. Especially if your clients happen to be the kind you don't have physical access to for days/weeks.

---

### Post by SeijiSensei on 2011-01-24
> **hackeron said:**
> 1) Simple example, you have a client-connect script that connects to the database, but the database is still starting - that script will return a non 0 exit code, telling all your openvpn clients to stop trying to connect.

You mean the database client invokes the tunnel?  I've never set things up that way.  I just have the client machine start the tunnel at boot so it's up all the time.  If the DB client fails to connect in this scenario, the tunnel isn't affected.

> 2) For the sake of argument your server booted into a read only filesystem for whatever reason. Say you're trying to boot an unsupported kernel in your vps. All clients are told to stop trying to connect.

Not too likely for the users here, who'll generally be running software from the repositories. I haven't built a kernel from scratch for years now.  I find the stock kernels from the mainstream distros do everything I need, especially on servers where support for more fragile things like newer video and wireless hardware isn't needed.  My endpoint server is running CentOS 5.5 on an old P4.  Not much needed in the way of new kernels there.

> 3) Hell you need to modify your openvpn server config, change some routes maybe, add that new connection and happen to make a mistake somewhere. All clients are told to stop trying to connect.

I use separate configuration files for each tunnel, so a mistake in one of them doesn't stop the others from starting.  Both RHEL/CentOS and Debian/Ubuntu implementations iterate over every .conf file found in /etc/openvpn.

I'm not questioning your experiences with OpenVPN, but I suspect the problems you cite are not very common ones for people with simple tunnelling needs like the OP in this thread.

---

### Post by hackeron on 2011-01-24
> **SeijiSensei said:**
> You mean the database client invokes the tunnel?  I've never set things up that way.  I just have the client machine start the tunnel at boot so it's up all the time.  If the DB client fails to connect in this scenario, the tunnel isn't affected.

No, I mean a client-script logs that someone connected to the vpn - I use that to log to a pdns daemon that sets up dns. So when an openvpn connection happens, something like client4.domain.com is set up automatically and if no direct connection is available, traffic is reverse proxies to clients. That lets them run web servers.

> Not too likely for the users here, who'll generally be running software from the repositories. I haven't built a kernel from scratch for years now.  I find the stock kernels from the mainstream distros do everything I need, especially on servers where support for more fragile things like newer video and wireless hardware isn't needed.  My endpoint server is running CentOS 5.5 on an old P4.  Not much needed in the way of new kernels there.

I am talking about stock kernels. The stock kernels frequently can't run on the VPS you use because they use an earlier version.

> I use separate configuration files for each tunnel, so a mistake in one of them doesn't stop the others from starting.  Both RHEL/CentOS and Debian/Ubuntu implementations iterate over every .conf file found in /etc/openvpn.

You have a separate VPN for each client?

> I'm not questioning your experiences with OpenVPN, but I suspect the problems you cite are not very common ones for people with simple tunnelling needs like the OP in this thread.

I donno, I've been bit by this even before I started doing anything fancy with OpenVPN, adding an upstart config to automatically respawn is a couple lines of code and works better than the supplied init.d script for me.

---

### Post by SeijiSensei on 2011-01-24
> **hackeron said:**
> You have a separate VPN for each client?

Yes.  They're all shared-key connections, with each assigned automatically to a separate tun interface using "dev tun" in the connection's .conf file.  I'm not supporting roving users, just point-to-point connections between remote servers and here.

> I am talking about stock kernels. The stock kernels frequently can't run on the VPS you use because they use an earlier version.

Hmm.  I have a couple of VPS nodes at Linode; they run plain-vanilla CentOS 5.5.  They have Ubuntu 10.04LTS images available, too.

---

### Post by Khufucius on 2011-02-15
Thanks, TSJason!!!

A couple of small edits:  In the /etc/rc.local script, I had to use

```

cd /root ;
./autosignon &

```
instead of doing it all in one line -- bizarre.  I believe **expect **threw an error like "send: spawn id exp<some #> not open" when I had the rc.local script as a single line.  Changing it to run in two lines fixed this.

Also, for the expect script (autosignon), I had to change the --exact flag to "-exact" (one hyphen instead of two).

Thanks so much again, that was a HUGE help.

-K

---

### Post by Deadpan110 on 2011-10-16
> **hackeron said:**
> 
I created an upstart config to use instead of the useless init.d script:

/etc/init/myopenvpn:


I have been struggling to keep openVPN clients alive - they do not give me much of a clue why they are dying at inconvenient times.

Thanks hackeron - the upstart method works (the client respawns within a few seconds even after a 'killall openvpn').

On my version of upstart, the scripts need to end in '.conf' so the above script was:
/etc/init/myopenvpn.conf

Cheers

---

### Post by josephonthejob on 2013-03-15
Sorry for resuscitate an old post.

I am in this trouble now, my embedded system have to keep openvpn alive.

I choosed to use upstart so I did a script very similar to the one posted in the first posts with the

```
respawn
```

directive.
It starts very well but I do not know how to check if it works.

If "kill -9" the pid is a way to check it.. it doesn't work.. because after the kill openvpn dies until the reboot..

any ideas?

Thanks

---

