---
title: "A Simple how to for Sharing internet connection"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by ario on 2009-07-15
Hi
I have an Ubuntu 9.04 installed PC that connects to interenet with a DSL modem. The DSL modem itself connects to my PC trough LAN. Its cable connected to eth0.
I also have another PC with Windows Xp Sp2 in it. It must been connected to internet trough my Ubuntu one.
I read forums a lot, It seems that obviously its too hard to connect too PC's togather.
Can anyone here explain me how to share my internet connection from Ubuntu 9.04 to windows xp? I now how to do it from windows. I must enter IP address of my windows box and then 255.255.255.0 and then the ip of my Ubuntu box as default gateway.
But please explain me what is the commands for Ubuntu side?
Thanks for your attention guys.
I hope this post will be a great HOWTO.;)

---

### Post by martinbaselier on 2009-07-15
There are a lot of tutorials about it already. You would neet to configure your ubuntu machine as a router (or as a gateway). Just use google or search in the forums and you can find all the tutorials you'll need.

---

### Post by ario on 2009-07-15
EDITED - After 19 months of having network problems and asking lots of questions in forums and searching allover Internet, finally today I solved the problem and I'm here to edit this post for others to not repeat my mistakes again:)
The problem was, when you share your Internet connection with method below, normal local network connection between your server and other PCs/Laptops hadn't been established until you have a working Internet connection! So you couldn't i.e. access some files on your server or remote to that until you bring your Internet connection i.e. by moving to server and do something with your DSL modem! Now don't worry because the mistake is corrected and marked as bold below:
---------------------------------------------------------------
Oh My God!
It was too damned easy;)
I have solved my problem as here:
I went to this address:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
There was a simple howto for this. All I've got was this:
An Ubuntu installed PC with a DSL modem to connect to Internet. And an Ethernet card to connect to another PC. The Ethernet card's name was "**eth1**". And the Ip address of my Ubuntu on that network was **192.168.0.2**. **The Ethernet card to connect to DSL modem is named eth0.**
Then I did this steps (be careful to place your own numbers for eth1 or 192.168... when coping commands below:
```

sudo su

```
I entered my password and then:
```

ifconfig eth1 192.168.0.2
iptables -t nat -A POSTROUTING -o **eth0** -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
apt-get install dnsmasq ipmasq

```
Then it asked me for installing some stuff and I entered **y**.
```

/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq

```
Then it asked me some questions and I **didn't**pressed <enter> for all of them**!**;). **Remember on "When should ipmasq be started?" you must choose "After network services have been started". Or else (i.e. by selecting default option) you can not access your server until Internet connection brought up.**
```

ifconfig eth1 192.168.0.2
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
gedit /etc/sysctl.conf

```
Then it opened an editor window. I searched trough it for **net.ipv4.ip_forward** and find a line that contains this sentence in it. I removed the **#** sign from first of line and then I've got this:
```

net.ipv4.ip_forward = 1

```
Closed editor and saved the file and then restarted my pc. turned on windows xp installed pc and then:
Start>My Computer>My Network Places (In the left sidebar)>Show my Network Connections (again in left sidebar)>Right Click on Local area connection and then:
```

IP: 192.168.0.3
Subnet mask: 255.255.255.0
Default Gateway: 192.168.0.2
Prefered DNS Server: 192.168.0.2

```
And Viola!):P

---

### Post by martinbaselier on 2009-07-15
It's voilà.And ubuntugeeks is a wonderful site, lots of great info there. :)

---

### Post by Macchi on 2009-07-15
You could also try Firestarter, a graphical firewall administration tool that is in the standard Ubuntu repositories and has built-in internet connection sharing.


It  works fine for easy and fast setup on a wide range of applications. I did that to set up servers to administer, distribute, and filter a mobile broadband internet connection on a small LAN.

---

### Post by ario on 2009-07-16
Here you are! I restarted my linux box and then Internet Connection Sharing is just a dream:(
I tried to run all commands again. but no success. tried to run firestarter and config it as in its site but no success. I don't know what to do. I don't want to install a windows xp just to share the connection.

---

### Post by Macchi on 2009-07-17
Hi Ario,

On a fresh installation Firestarter is very easy to configure for internet connection sharing. It needs only a few clicks on a graphical user interface, given that you have a correct configuration of your network cards. 

Unfortunately after a manual tweak through the command line your system may be at an erroneous state. For instance, a typo could cause a problem with routing for iptables. Personally this is one of the reasons that I prefer not having to rely on changes that cannot be reverted easily. You could check your network interfaces, restart and try to apply again those tweaks. 

OBS: I am sorry but don't have a better answer for the moment. Nowadays Linux and Ubuntu work wonderfully, but often it is a good idea to have a spare system or virtual machine to perform experiments, in case anything goes wrong. I always have a separate home partition and backups of user data and system configuration. In the worst cases I confess that I had to do a new fresh installation to problems after moderately wild experiments. A new installation takes only a few minutes of active time and afterwards you are back at a known system state.

---

### Post by martinbaselier on 2009-07-17
Maybe something went wrong with your iptables?

What's the output of 
**sudo iptables -L**
?

I don't know firestarter, but letting two tools do the same thing could give conflicts.

**ps -e**
will show you all the running processes. 

When you add **| grep ** to the line,you can filter the output.
**grep dns**, for example will only show the lines containing dns.
**grep -v dns** will filter out all lines containing dns.
you can also use **less** behind the **|** to scroll through the output.

When you use a different tool, it's best to undo your original steps. 

**sudo apt-get remove dnsmasq ipmasq**
**sudo iptables -F**
(the ip- forwarding thing is necessary in any configuration, so no need to remove that)

---

### Post by ario on 2009-07-20
Thanks a lot ladies and gentlemen.
I've compeletely removed ipmasq and then reinstalled it. Then rentered all of the above commmands and tweaks. Now I have to turn on my Ubuntu machine, Then Windows Xp machine, Wait for some minute and maybe try repair netwrok connection in windows xp.
Then the internet connection is shared again. So it's something like solved now:D
By the way. Here you are output of sudo iptables -L command:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
^TACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  192.168.195.0/24     anywhere            
ACCEPT     all  --  192.168.108.0/24     anywhere            
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  192.168.195.0/24     anywhere            LOG level warning 
DROP       all  --  192.168.195.0/24     anywhere            
LOG        all  --  192.168.108.0/24     anywhere            LOG level warning 
DROP       all  --  192.168.108.0/24     anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             89.165.81.13        
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  192.168.108.0/24     192.168.195.0/24    
ACCEPT     all  --  192.168.195.0/24     192.168.108.0/24    
ACCEPT     all  --  192.168.195.0/24     anywhere            
ACCEPT     all  --  192.168.108.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             192.168.195.0/24    LOG level warning 
DROP       all  --  anywhere             192.168.195.0/24    
LOG        all  --  anywhere             192.168.108.0/24    LOG level warning 
DROP       all  --  anywhere             192.168.108.0/24    
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             192.168.195.0/24    
ACCEPT     all  --  anywhere             192.168.108.0/24    
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  anywhere             192.168.195.0/24    LOG level warning 
DROP       all  --  anywhere             192.168.195.0/24    
LOG        all  --  anywhere             192.168.108.0/24    LOG level warning 
DROP       all  --  anywhere             192.168.108.0/24    
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  89.165.81.13         anywhere            
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

```
and the output of "ps -e | grep dns" command:
```

 3201 ?        00:00:00 dnsmasq

```
What does all of those means?:)
Thanks for your helpful attention.

---

