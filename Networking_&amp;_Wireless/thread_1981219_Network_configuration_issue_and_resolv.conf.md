---
title: "Network configuration issue and resolv.conf"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by cirrust on 2012-05-16
Hi everyone.  First post.

I am using Ubuntu 12.04 server with a gui.

When I boot my server with a static ip configured I receive the following for about 2 minutes:

Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting Server without full networking configuration...

After it boots there are no dns servers configured.  I solve this by going into system->network->Network Settings and adding the DNS servers there.

The dns servers then appear in resolv.conf.

After I reboot the resolv.conf is cleared.

I'd like to fix this problem, not just lock the resolv.conf or add a script to edit it on startup.

---

### Post by jonobr on 2012-05-16
Hello


NM applet is used to populate the resolv.conf file.

When you restart the networking piece by reboot or by
/etc/init.d/networking restart

The configuration in Nm applet is written to resolv.conf

So it appears that if it is rewriting it is not taking your dns entries or at least thet are not staying there after a reboot
If you were to add in resol.conf directly, again, the gui overwrites the setting of resolv.conf.

I dont want to speak for everyone, but I got away from using that GUi in anything I use with a GUI.
There always appeared to be trouble with it in previous versions.
It may be better, but I never went back as manual config just worked for me.

IF you disable it, all you would need to do is enter your ip settings (whether DHCP or static) in the /etc/network/interfaces file and add an entry to resolv.conf.

---

### Post by cirrust on 2012-05-16
Thanks for the reply.

Currently I have configured my network in /etc/network/interfaces which is likely what is causing the conflict.

I absolutely would like to disable the network manager gui configuration.  

So the question is how do I do that?

I went into the network manager and uncheck "enable this connection"
That didn't help the bootup issue or even allow the network to restart.

---

### Post by jonobr on 2012-05-16
Hello


If I recall its in


```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Go to the line that says managed=true
change to false.
Or you could just uninstall.
Once you do that you need entries in
/etc/network/interfaces 
as well as /etc/resolv.conf
restart networking or reboot

Cheers

Jonobr

---

### Post by chili555 on 2012-05-16
> I absolutely would like to disable the network manager gui configuration.

So the question is how do I do that?You could certainly remove Network Manager altogether. Then populate /etc/network/interfaces like this, substituting your details, of course:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 2.4.6.blah

```

---

### Post by cirrust on 2012-05-16
I tried editing the 
/etc/NetworkManager/NetworkManager.conf 
file, but the managed=false changed back to managed=true on reboot

I attempted uninstalling network-manager by
 ```

sudo aptitude purge network-manager
sudo apt-get install --purge network-manager 
sudo apt-get install --purge network-manager-gnome
 
```None of this has had any affect on my issue. :(

There are still some files in the /etc/NetworkManager/system-connections 

This also may be of interest:

```

sudo /etc/init.d/networking restart
[sudo] password for rob:
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          ssh stop/waiting
ssh start/running, process 23223
run-parts: /etc/network/if-up.d/postfix exited with return code 75
RTNETLINK answers: File exists
Failed to bring up eth0:0.
RTNETLINK answers: File exists
Failed to bring up eth0:1. 

```                                                                         [ OK ]

---

### Post by chili555 on 2012-05-16
Mind if we have a look?```
cat /etc/network/interfaces
```Thanks.

---

### Post by cirrust on 2012-05-16
No problem

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address xxx.xxx.74.50
        netmask 255.255.255.240
        network xxx.xxx.74.48
        broadcast xxx.xxx.74.63
        gateway xxx.xxx.74.49
        # dns-* options are implemented by the resolvconf package, if installed
        #dns-search scrapper
        #dns-nameserver 208.67.222.222
        #dns-nameserver 208.67.220.220

auto eth0:0
iface eth0:0 inet static
        address xxx.xxx.74.51
        netmask 255.255.255.240
        gateway xxx.xxx.74.49

auto eth0:1
iface eth0:1 inet static
        address xxx.xxx.74.56
        netmask 255.255.255.240
        gateway xxx.xxx.74.49



```

Let me know if the ifconfig will be helpful.   

The computer has 4 ethernet ports, and only 1 is used.  

Also there is a VMWare Workstation install which has some virtual network adapters in the ifconfig.

---

### Post by chili555 on 2012-05-16
> The computer has 4 ethernet ports, and only 1 is used.
I guess I don't understand, then, what the aliases eth0:0 and eth0:1 are for. 'auto' tells the system to start everything.

As well, you still don't have DNS nameservers specified as I suggested. It should be dns-nameserver[COLOR="Red"]s[/COLOR] 208.67.222.222 208.67.220.220

---

### Post by SeijiSensei on 2012-05-16
> **chili555 said:**
> I guess I don't understand, then, what the aliases eth0:0 and eth0:1 are for. 'auto' tells the system to start everything.

He's using aliasing to give a single adapter multiple IP addresses.

> As well, you still don't have DNS nameservers specified as I suggested. It should be dns-nameserver[COLOR="Red"]s[/COLOR] 208.67.222.222 208.67.220.220

Yes, replace these

```
[s]#dns-nameserver 208.67.222.222
#dns-nameserver 208.67.220.220[/s]
```

with this

```
dns-nameservers 208.67.222.222 208.67.220.220
```

Note the "s" on "dns-nameservers".

---

### Post by cirrust on 2012-05-16
Thanks chili555


I added the line

```

dns-nameserver[COLOR=Red]s[/COLOR] 208.67.222.222 208.67.220.220 	

```

And the DNS issue is resolved!!!   :p

> 
The computer has 4 ethernet ports, and only 1 is used. 			 		


There is an eth1, eth2, eth3 that do not have cables attached to them.


The slow booting with the networking is still an issue.

```

Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting Server without full networking configuration...

```

---

### Post by chili555 on 2012-05-16
I suspect it has something to do with aliasing. As well, I wonder if you need netmask 255.255.255.[COLOR="Red"]0[/COLOR]. I hope SeijiSensei will step in here.

---

### Post by SeijiSensei on 2012-05-16
I've never created aliased interfaces in /etc/network/interfaces.  I've always just added a couple of ifconfig statements to /etc/rc.local like this to declare them.  However I notice that your configuration has gateways for each one.  I'd **remove the gateways from the alias declarations** and see if it helps.  There should only be one default gateway, and it should be defined for eth0.  The aliased interfaces will use that as well.  I'd also **add "broadcast" directives for the aliased interfaces** identical to the one for eth0.

If those changes do not fix the problem, then I'd just remove the alias declarations from /etc/network/interfaces and declare them manually in /etc/rc.local like this:

```
/sbin/ifconfig eth0:0 xxx.xxx.74.51 netmask 255.255.255.240 broadcast xxx.xxx.74.63
/sbin/ifconfig eth0:1 xxx.xxx.74.56 netmask 255.255.255.240 broadcast xxx.xxx.74.63
```

chili, he's got the right subnet mask.  He's apparently been allocated a 14-host subnet xxx.xxx.74.48/28 from his ISP.

---

### Post by cirrust on 2012-05-17
Everything is work great now!

SeijiSensei I sincerely thank you for your help, and I am a little surprised and embarrassed that all my issues where just a screwed up config file.

---

### Post by SeijiSensei on 2012-05-18
No problem; it's why I'm here. 

Don't be embarrassed.  Configuration files are very fussy, and we've all made our share of mistakes with them.

---

