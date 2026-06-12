---
title: "WIRED Internet issues with toshiba Satelite A215 &amp; Ubuntu 10.04"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by E-P on 2010-08-23
I hate to post here one more topic about such an issues but can't find any answers after long search. 

I have installed Ubuntu (dual-boot) on my friends computer which is Toshiba Satellite A215-S4697. After installation the wireless card was not working but as I am more than familiar with this problem I thought I could solve it when I take the laptop to work and get it connected to Internet with cable, run all the updates and find the solution for the problem.

Anyway, after plugging the laptop on the wired Internet it does not work :mad: Everything seems fine. I plug it in and the little green light goes on to indicate the hardware works, ubuntu shows that the connection has been established, ifconfig shows fine as well. I read about deleting dhcp-client and establishing static connection from /etc/network/interfaces but I am not really sure if I want to do this as my friends won't probably know how to change it in the future (and are not happy to learn :D).

Not really sure what to do. Don't want to give the laptop back with Ubuntu that has no functioning Internet connection and Windows that will take now even longer to get started :D (as they have to choose the Windows recovery mode --> Start windows normally from the dual-boot list).

Thanks for the help. If I only could get the wired connection work I bet I would do fine.

---

### Post by dineshs on 2010-08-23
If you want to configure the connection manually do not edit /etc/network/interfaces ,but try this
[http://ubuntuforums.org/showpost.php?p=9733891&postcount=6](http://ubuntuforums.org/showpost.php?p=9733891&postcount=6)
then [COLOR="Blue"]restart[/COLOR]
Note:substitute your network values while configuring
Also please post the result of
```
route -n
```

---

### Post by E-P on 2010-08-23
Got the following outcome with the "route -n" command:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    UseIface
201.122.17.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         201.122.17.182  0.0.0.0         UG    0      0        0 eth0

---

### Post by E-P on 2010-08-23
> **dineshs said:**
> If you want to configure the connection manually do not edit /etc/network/interfaces ,but try this
[http://ubuntuforums.org/showpost.php?p=9733891&postcount=6](http://ubuntuforums.org/showpost.php?p=9733891&postcount=6)
then [COLOR="Blue"]restart[/COLOR]
Note:substitute your network values while configuring
Also please post the result of
```
route -n
```

Thanks for the advices dineshs unfortunately though they didn't help.

Other advices much appreciated!

---

### Post by dineshs on 2010-08-25
Can you ping 201.122.17.182
```
ping 201.122.17.182 -c3
```and
```
ping 4.2.2.1 -c3
```

---

### Post by E-P on 2010-08-26
So, with the manual ethernet settings there was posted earlier I pinged on the addresses above and got following outcomes:

```
javier@javier-laptop:~$ ping 201.122.17.182 -c3
PING 201.122.17.182 (201.122.17.182) 56(84) bytes of data.
64 bytes from 201.122.17.182: icmp_seq=1 ttl=255 time=3.03 ms
64 bytes from 201.122.17.182: icmp_seq=2 ttl=255 time=1.23 ms
64 bytes from 201.122.17.182: icmp_seq=3 ttl=255 time=1.18 ms

--- 201.122.17.182 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.182/1.816/3.031/0.860 ms
javier@javier-laptop:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2009ms
```

---

### Post by dineshs on 2010-08-26
Did you configure eth0 manually(I mean IP 201.122.17.XXX gateway 201.122.17.182 etc)
To what device your ethernet cable is plugged?

---

### Post by E-P on 2010-08-26
> **dineshs said:**
> Did you configure eth0 manually(I mean IP 201.122.17.XXX gateway 201.122.17.182 etc)

Hmmm, not really sure what you mean by this. Yes, I configured with the values you were giving in the link (on your first post) but not with this values you gave here.

> **dineshs said:**
>  To what device your ethernet cable is plugged?

It is plugged on the wall (what ever it is called) where it is connected to the server of the department where I work. Unfortunately only one who knew something about those things quit his job few weeks ago. Now when I think about it I should probably find out the IP etc. for the server and "force" the connection? Not sure, really noob with these things.

---

### Post by dineshs on 2010-08-27
Try to configure eth0 via Network manager as done before but Method=Automatic DHCP addresses only and give  DNS as 4.2.2.1 then apply.
Now run```
sudo service network-manager stop
sudo service network-manager start
```and see if there is any progress.
If not
Do you have a, say ,windows machine which works fine when the same cable is plugged in?If yes connect the machine and  post the command output of
```
ipconfig /all
```
Also post the output of
```
cat /etc/network/interfaces
```
( ubuntu machine)

---

