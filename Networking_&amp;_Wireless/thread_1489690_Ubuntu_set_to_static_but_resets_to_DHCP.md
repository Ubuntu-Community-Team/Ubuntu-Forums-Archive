---
title: "Ubuntu set to static but resets to DHCP"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by baytownl on 2010-05-21
Ok here is a problem that was previously posted but not resolved and I could not renew the old thread.

[http://ubuntuforums.org/showthread.php?t=278537](http://ubuntuforums.org/showthread.php?t=278537)

**So basically I set the static ip address:**
auto lo
iface lo inet loopback

auto seth0
iface seth0 inet static
address 192.168.219.25
netmask 255.255.255.0
gateway 192.168.219.1

**Restart networking:**
"sudo /etc/init.d/networking restart"

Everything is fine but 24 hours later the server resets to the DHCP address assigned to it. I have not installed any GUI im just running Ubuntu 10.04 LTS in Hyper V. After it resets to DHCP I log into it using the dhcp address and reset the networking service "sudo /etc/init.d/networking restart". It goes back to the static IP specified in interfaces. I have rebooted several times but every 24 hours it resets.

BTW - Before someone asks about iface seth0 instead of it being iface eth0. It is a Hyper V module running. You can read about it [here]("http://fawzi.wordpress.com/2010/05/03/ubuntu-server-10-4-in-hyper-v/") if you wish. ([http://fawzi.wordpress.com/2010/05/03/ubuntu-server-10-4-in-hyper-v/](http://fawzi.wordpress.com/2010/05/03/ubuntu-server-10-4-in-hyper-v/))

Also FYI-
# ps -ef | grep dhclient
root      1234     1  0 May19 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.seth0.pid -lf /var/lib/dhcp3/dhclient.seth0.leases seth0
btportal  7405  7376  0 10:09 pts/2    00:00:00 grep --color=auto dhclient

---

### Post by chili555 on 2010-05-21
What does this tell us?```
ps -ef | grep -i network
```

---

### Post by iponeverything on 2010-05-21
> **baytownl said:**
> 
# ps -ef | grep dhclient
root      1234     1  0 May19 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.seth0.pid -lf /var/lib/dhcp3/dhclient.seth0.leases seth0
btportal  7405  7376  0 10:09 pts/2    00:00:00 grep --color=auto dhclient

bit confused, if you have it configured static via interfaces -- why do you have dhclient running?  

Your interface is switching to dhcp address because the lease is expiring. 

I don't want to sound mean or anything, but kill off dhcpclient and -- all should be good.

---

### Post by baytownl on 2010-05-21
@[chili555]("http://ubuntuforums.org/member.php?u=35909")
```
ps -ef | grep -i network
btportal  7533  7517  0 10:50 pts/1    00:00:00 grep --color=auto -i network
```@[iponeverything]("http://ubuntuforums.org/member.php?u=643833")
I don't know why the dhcp client is running. How do you kill it permanently? 
BTW -  I don't care if your mean as long as you can help me. I am very new to Ubuntu so I expect to get the occasional "duh" attitude. :)

---

### Post by iponeverything on 2010-05-21
> **baytownl said:**
> @[chili555]("http://ubuntuforums.org/member.php?u=35909")
```
ps -ef | grep -i network
btportal  7533  7517  0 10:50 pts/1    00:00:00 grep --color=auto -i network
```

@[iponeverything]("http://ubuntuforums.org/member.php?u=643833")
I don't know why the dhcp client is running. How do you kill it permanently? 
BTW -  I don't care if your mean as long as you can help me. I am very new to Ubuntu so I expect to get the occasional duh attitude. :)

by mean, just talking about asking you to "kill" something ;)

no idea either what is starting dhclient for you. 

you can bludgeon the process to death with:

```
sudo killall -v -9 dhclient3

```

and prevent it from restarting with:

```
sudo chmod -x /sbin/dhclient3
```

please note though that dhcp will be borked on your system until you reset the execute bit with:

```
sudo chmod +x /sbin/dhclient3
```

---

### Post by baytownl on 2010-05-21
@[iponeverything]("http://ubuntuforums.org/member.php?u=643833")
That is perfect, that you so much. This should be a case closed, although I am very curious as to why this would be happening. I wonder if it has anything to do with the synthetic driver for Ubuntu. But I don't think so since it happened to the person in the previous thread and they were running the legacy driver.

:guitar:

---

### Post by iponeverything on 2010-05-21
Don't forget that your execute bit off, a couple of months from now you might spend hours trying to figure out why dhcp is broken!

---

### Post by Iowan on 2010-05-21
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?
You didn't mention if the machine was originally set up with DHCP address... perhaps a previous lease decided to keep renewing.  There's another thread (or so) that mentioned where DHCP leases are kept- flushing this file might help... but use what works!

---

