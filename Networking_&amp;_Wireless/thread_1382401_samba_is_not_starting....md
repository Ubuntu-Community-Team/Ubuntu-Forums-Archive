---
title: "samba is not starting...?"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Darth_tater on 2010-01-15
Read through the thread, but here is the gist:

- a bunch of services (samba, ssh, vnc) are not starting up!  I have to manually login and then start them through the command line.

it is thought that these services are dying because they dont have a network interface to bind to.

any ideas as to how to fix this? 

----------
orig post
----------


well, i cant figure this one out...

Samba wont start until i manually log in and run this command:

"sudo /etc/init.d/samba start"

when i run "sudo bum" it says that samba is already running (and set up to run @ boot time)

Just to be sure, i put the following code into my "/etc/rc.local" file

"/etc/init.d/samba start"

so, for sure, samba should be starting, but it isint.  

anybody got any ideas as to why?

---

### Post by Iowan on 2010-01-16
What is the indication that Samba isn't running? You've tried something like: ```
sudo ps -ef |grep mbd

```

---

### Post by Darth_tater on 2010-01-16
i have not...

my test was this:

try to connect to \\<ipaddy>\share from remote computers.

when that failed, i went and ran " sudo /etc/init.d/samba start " and was able to connect.

---

### Post by Morbius1 on 2010-01-16
I posted this in another thread and it seemed to work for that person:
[http://ubuntuforums.org/showthread.php?t=1379235](http://ubuntuforums.org/showthread.php?t=1379235)

> I'm wondering if samba is starting before the network is up. Perhaps a script added to /etc/network/if-up.d that would execute only after the network is up would resolve this matter. For example:

Open an editor as gksu and create a little script:
```
#!/bin/sh
/etc/init.d/samba restart 
```Save the file to say: /etc/network/if-up.d/sambaup
Make the file executable: sudo chmod +x /etc/network/if-up.d/sambaup 

---

### Post by Darth_tater on 2010-01-16
thats a good point, ill check that out.

Ill also go through the samba logs to see if i can figure out whats going wrong  (yes, i cant believe that i haven't gone through those yet, either!)

will post back in a few min w/ the results.

---

### Post by Darth_tater on 2010-01-16
UhOh.  inside my /etc/network/if-up.d folder there already is a samba script.

from waht i can tell, it just checks to see if samba is already up and running...

also, there was nothing in the log files to indicate, as far as i could tell, what was going on.

please help!

---

### Post by Darth_tater on 2010-01-16
OK, i think you might be on to something about the services starting up before the network is brought up.  

I say this because my SSH server, which is supposed to be running on boot, is not.

i had to manually start it just like i had to do w/ my samba connection as well.  

I also have a VNC server that is supposed to be running at start up as well...  it isint.


so how can i fix this?  Something has got to be wrong w/ my network configuration....

---

### Post by redmk2 on 2010-01-16
> **Darth_tater said:**
> OK, i think you might be on to something about the services starting up before the network is brought up.  

I say this because my SSH server, which is supposed to be running on boot, is not.

i had to manually start it just like i had to do w/ my samba connection as well.  

I also have a VNC server that is supposed to be running at start up as well...  it isint.


so how can i fix this?  Something has got to be wrong w/ my network configuration....

Most probably you are using **Network Manager **to configure your interfaces.  This means that a user has to be **logged in **before they are configured.  When Samba and other servers have no interface upon booting they die.  The cure is to **not use ** Network Manager for interface configuration.

I configure my interfaces with /etc/network/interfaces and /etc/resolv.  You need to disable Netork Manager's ability to configure the interface in question as it will overwrite the files upon a reboot.

---

### Post by Darth_tater on 2010-01-17
> **redmk2 said:**
> Most probably you are using **Network Manager **to configure your interfaces.  This means that a user has to be **logged in **before they are configured.  When Samba and other servers have no interface upon booting they die.  The cure is to **not use ** Network Manager for interface configuration.

I configure my interfaces with /etc/network/interfaces and /etc/resolv.  You need to disable Netork Manager's ability to configure the interface in question as it will overwrite the files upon a reboot.

thats what i am doing... how can i permanently killoff network manager?


here is my interfaces file:


auto lo
auto eth0
iface eth0 inet static
address 192.168.2.XXX
netmask 255.255.255.0
gateway 192.168.2.X
broadcast 192.168.2.255

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> thats what i am doing... how can i permanently killoff network manager?


here is my interfaces file:


auto lo
auto eth0
iface eth0 inet static
address 192.168.2.XXX
netmask 255.255.255.0
gateway 192.168.2.X
broadcast 192.168.2.255

As for 'killing off" Network Manager", I can't say for sure as I have never had it installed on any of my desktops or servers.  First thing I would do is to see if I could get it to not configure the interface (not manage it).  If that doesn't work I believe you could try to remove it with the Synaptic Package Manager.

Be prepared to completely configure all the networking parameters on that interface via the various configuration files.  They are:```
/etc/network/interfaces
/etc/resolv
/etc/hosts
```

---

### Post by Darth_tater on 2010-01-17
Ok... i just backed up my configuration files and uninstalled net manager.

server is rebooting now, i will post back in a few min w/ results!

---

### Post by Darth_tater on 2010-01-17
nope.  restarted and logged in.... still no samba,ssh, or VNC.

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> nope.  restarted and logged in.... still no samba,ssh, or VNC.


Look at the syslogs

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> nope.  restarted and logged in.... still no samba,ssh, or VNC.

Try changing the IP address to a number **outside **the DHCP range to see if your manually configured IP address is really coming up.

---

### Post by Darth_tater on 2010-01-17
> **redmk2 said:**
> Try changing the IP address to a number **outside **the DHCP range to see if your manually configured IP address is really coming up.

the address specified in the config file *is* outside the DHCP range.

---

### Post by Darth_tater on 2010-01-17
Here are the log files...

```
root@Coretana:/home/darth_tater# tail -f /var/log/syslog
Jan 16 21:55:00 Coretana gdm-binary[1000]: WARNING: Unable to find
users: no seat-id found
Jan 16 21:55:00 Coretana gdm-simple-slave[1015]: WARNING: Unable to
load file '/etc/gdm/custom.conf': No such file or directory
Jan 16 21:54:56 Coretana ntpdate[1033]: step time server 91.189.94.4
offset -6.039816 sec
Jan 16 21:54:58 Coretana console-kit-daemon[797]: WARNING: Couldn't
read /proc/796/environ: Failed to open file '/proc/796/environ': No
such file or directory
Jan 16 21:55:00 Coretana anacron[1129]: Anacron 2.3 started on 2010-01-16
Jan 16 21:55:00 Coretana anacron[1129]: Will run job `cron.daily' in 5 min.
Jan 16 21:55:00 Coretana anacron[1129]: Jobs will be executed sequentially
Jan 16 21:55:03 Coretana kernel: [   21.980056] eth0: no IPv6 routers present
Jan 16 22:00:00 Coretana anacron[1129]: Job `cron.daily' started
Jan 16 22:00:00 Coretana anacron[1380]: Updated timestamp for job
`cron.daily' to 2010-01-16
Jan 16 22:07:09 Coretana avahi-daemon[792]: Interface eth0.IPv4 no
longer relevant for mDNS.
Jan 16 22:07:09 Coretana avahi-daemon[792]: Leaving mDNS multicast
group on interface eth0.IPv4 with address 192.168.2.11.
Jan 16 22:07:09 Coretana avahi-daemon[792]: Withdrawing address record
for fe80::211:d8ff:fe9c:8adf on eth0.
Jan 16 22:07:09 Coretana avahi-daemon[792]: Withdrawing address record
for 192.168.2.11 on eth0.
Jan 16 22:07:09 Coretana kernel: [  748.171332] skge eth0: disabling interface
Jan 16 22:07:31 Coretana kernel: [  769.964140] skge eth0: enabling interface
Jan 16 22:07:31 Coretana avahi-daemon[792]: Joining mDNS multicast
group on interface eth0.IPv4 with address 192.168.2.11.
Jan 16 22:07:31 Coretana kernel: [  769.967809] ADDRCONF(NETDEV_UP):
eth0: link is not ready
Jan 16 22:07:31 Coretana avahi-daemon[792]: New relevant interface
eth0.IPv4 for mDNS.
Jan 16 22:07:31 Coretana avahi-daemon[792]: Registering new address
record for 192.168.2.11 on eth0.IPv4.
Jan 16 22:07:33 Coretana kernel: [  771.633000] skge eth0: Link is up
at 100 Mbps, half duplex, flow control none
Jan 16 22:07:33 Coretana kernel: [  771.633229]
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 16 22:07:34 Coretana avahi-daemon[792]: Registering new address
record for fe80::211:d8ff:fe9c:8adf on eth0.*.
Jan 16 22:07:35 Coretana ntpdate[1650]: step time server 91.189.94.4
offset -0.054825 sec
Jan 16 22:07:43 Coretana kernel: [  782.190021] eth0: no IPv6 routers present
```

that is the tail from these two commands:

```
darth_tater@Coretana:~$ sudo /etc/init.d/networking stop
[sudo] password for darth_tater:
 * Deconfiguring network interfaces...                                   [ OK ]
darth_tater@Coretana:~$ sudo /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting
```

could the error about upstart be the cause?

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> the address specified in the config file *is* outside the DHCP range.

Change it to another address in the 192.168.2.0/24 range (your network.

We want to see i the change is configured to the interface.

What about the syslogs?

---

### Post by Darth_tater on 2010-01-17
> root@Coretana:/home/darth_tater# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:9c:8a:df
         inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
         inet6 addr: fe80::211:d8ff:fe9c:8adf/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:1857 errors:0 dropped:0 overruns:0 frame:0
         TX packets:1765 errors:0 dropped:0 overruns:0 carrier:0
         collisions:2 txqueuelen:1000
         RX bytes:1867251 (1.8 MB)  TX bytes:328095 (328.0 KB)
         Interrupt:17
root@Coretana:/home/darth_tater# sudo gedit /etc/network/interfaces

root@Coretana:/home/darth_tater# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
root@Coretana:/home/darth_tater# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:9c:8a:df
         inet addr:192.168.2.22  Bcast:192.168.2.255  Mask:255.255.255.0
         inet6 addr: fe80::211:d8ff:fe9c:8adf/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:16 errors:0 dropped:0 overruns:0 frame:0
         TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:1789 (1.7 KB)  TX bytes:3860 (3.8 KB)
         Interrupt:17

Yep... address changed w/o problem.

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> ...

could the error about upstart be the cause?

A couple of things come to mind.  But before I comment how about we get look at the relevant samba log and what shows up when you use this command?```
ifconfig -a 
```

---

### Post by Darth_tater on 2010-01-17
> **redmk2 said:**
> A couple of things come to mind.  But before I comment how about we get look at the relevant samba log and what shows up when you use this command?```
ifconfig -a 
```

can you please post the exact logs you want access to?  there are a ton, and its hard to tell which ones are necessary. 

as for samba, there isint anything that i can tell is useful, but ill go though and check again.

```
root@Coretana:/home/darth_tater# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:d8:9c:8a:df
         inet addr:192.168.2.22  Bcast:192.168.2.255  Mask:255.255.255.0
         inet6 addr: fe80::211:d8ff:fe9c:8adf/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:534 errors:0 dropped:0 overruns:0 frame:0
         TX packets:489 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:315843 (315.8 KB)  TX bytes:126564 (126.5 KB)
         Interrupt:17

lo        Link encap:Local Loopback
         LOOPBACK  MTU:16436  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> can you please post the exact logs you want access to?  there are a ton, and its hard to tell which ones are necessary. 

as for samba, there isint anything that i can tell is useful, but ill go though and check again.



Is **192.168.2.22  **the IP address you configured?

The log we are interested in is:```
/var/log/samba/log.smbd
```

This is the log for the Samba daemon (smbd).  :-)

---

### Post by Darth_tater on 2010-01-17
> **redmk2 said:**
> Is **192.168.2.22  **the IP address you configured?

The log we are interested in is:```
/var/log/samba/log.smbd
```

This is the log for the Samba daemon (smbd).  :-)


yes,  i switched it from 2.11 to 2.22.

as for the samba daemon:

There was no log!  i had to manually start the server before the log came back.  i can post this if you want, but i doubt it will be useful...

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> yes,  i switched it from 2.11 to 2.22.

as for the samba daemon:

There was no log!  i had to manually start the server before the log came back.  i can post this if you want, but i doubt it will be useful...

I have looked through my logs and I don't see where the samba daemon loads relative to the eth0 interface either.  It seems strange that the smbd Daemon is not even attempting to start. 

Your posting history reveals that you have done lots of mods to the system in an effort to overcome this kind of problem.  I'm not sure if any of those mods or the change you mentioned earlier in this thread have anything to do with your problem.

If this was my machine I would return it to it's original state (not including Network Manager) and see it that solves your problems.

---

### Post by Darth_tater on 2010-01-17
> **redmk2 said:**
> I have looked through my logs and I don't see where the samba daemon loads relative to the eth0 interface either.  It seems strange that the smbd Daemon is not even attempting to start. 

Your posting history reveals that you have done lots of mods to the system in an effort to overcome this kind of problem.  I'm not sure if any of those mods or the change you mentioned earlier in this thread have anything to do with your problem.

If this was my machine I would return it to it's original state (not including Network Manager) and see it that solves your problems.



Those posts are not all for *this* system... but they havent caused any problems in the past.

in the next few days i go back to university, so i wont be able to directly access this machine; ill hope that i can  get SSH up and running reliably so that i can attempt to fix problems in my spare time.

oh well, thanks for your time.

---

### Post by redmk2 on 2010-01-17
> **Darth_tater said:**
> ...

oh well, thanks for your time.
Sorry I could not be of more help.

Good Luck!

---

