---
title: "Networking 2 Computers using a switch?"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-07
Hi,

I am an Ubuntu newbie. thanks in advance for any help.

I successfully installed Ubuntu 10.04 on 2 laptops (both are identical in terms of hardware). In addition, I connected both of them (using RJ45 cables) to a switch (just a switch; I don't have a router). 

Can anybody guide me what should I do / what settings should I specify in each laptop in order to be able to SSH from one laptop to another?

Thanks.

---

### Post by e79 on 2010-10-07
> **csharpplus said:**
> I successfully installed Ubuntu 10.04 on 2 laptops (both are identical in terms of hardware). In addition, I connected both of them (using RJ45 cables) to a switch (just a switch; I don't have a router).
 
Since you don't have a router that service DHCP on your network, you will have to manually edit your network connections so both laptop can 'speak' to each other.
 
Open System --> Preferences --> Network Connections
 
Click on your working network card (could be eth0, eth1 etc) and click 'Edit'
 
Go to 'IPv4 Settings' Tab, scroll down from DHCP to 'Manual', click 'Add' and input your values there. See the attached .PNG for examples.
 
By default the SSH services is not installed in ubuntu (well the client is but not the server). You will need an internet connection in order to install SSH server service on each laptop. Once you are connected to internet, simply type:
```
sudo apt-get install ssh
```
 
Then, all you would have to do is type the following from one laptop to connect to the other:
```
ssh user@laptop
```
or
```
ssh [EMAIL="user@IP_Address"]user@IP_Address[/EMAIL]
``` (if you are not using an internal DNS server)
 
Hope this helps

---

### Post by csharpplus on 2010-10-07
e79,

thank you so much! I appreciate your help.

In the example given, you have the following settings:

Address -- 192.168.0.100
Netmask -- 255.255.255.0
Gateway -- 192.168.0.1

let's assume that these settings will be given to laptop1. 

can you give an example what would be the settings for laptop2 (the other laptop)? I just want to make sure I understand which parameters {Address, Netmask, Gateway} I need to change there.

Thanks again.

---

### Post by e79 on 2010-10-07
I'm glad I could help !
 
You would only need to change the 'IP Address' for the second laptop; the NetMask and Gateway (if you have one) should always remains the same. So your second laptop could be somehting as :
 
Address -- 192.168.0.102
Netmask -- 255.255.255.0
Gateway -- 192.168.0.1
 
But again, these are only for example :)
 
In fact, you only need to set up the IP Address and Netmask so both machines can speak together, but without the Gateway (your 'door' to the internet) and DNS Server (ability to resolv (ie) [www.google.com]("http://www.google.com")), you wouldn't be able to surf the Net.

---

### Post by csharpplus on 2010-10-07
e79,

thanks again.

If I just need SSH access (without internet sharing), can I 'skip' the definition of Gateway?

Also, you mentioned earlier that I need to install SSH on every machine. Suppose that some day in the future, I will have more machines and will want to 'shoot' a command to be executed on several machines at the same time. I heard that I will need to use a program called parallel-ssh. the question is, should I also install parallel-ssh on every machine, or shall I just install it on the main (controlling) machine?

---

### Post by csharpplus on 2010-10-07
I was successful installing 'SSH' on the first machine. For the second, I got the following message:

> 
remoteuser@remoteuser-laptop:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate


any idea what tis means?

---

### Post by e79 on 2010-10-07
> If I just need SSH access (without internet sharing), can I 'skip' the definition of Gateway
Once the SSH service is installed, you can clear the 'Gateway' info if you really don't want this machine to access Internet; you don't need it to only allow both laptop to speak together.
 
As for pparallel-ssh, I never used it myself so I cannot tell (maybe someone else will be able to help you on that one).
 
For you second laptop, have you try to update the packages first ?
```
sudo apt-get update
```
then rety the
```
sudo apt-get install ssh
```
 
See if this resolve the issue

---

### Post by csharpplus on 2010-10-07
yes, it did the trick; Following the update, I was able to install SSH on the second laptop as well.

Yet, I am not successful logging in to one machine from another, getting 'Connection timed out' messages:

```

remoteuser@remoteuser-laptop:~$ ssh 192.168.0.100
ssh: connect to host 192.168.0.100 port 22: Connection timed out
remoteuser@remoteuser-laptop:~$ 
remoteuser@remoteuser-laptop:~$ ssh myusername@myusername
ssh: connect to host myusername port 22: Connection timed out
remoteuser@remoteuser-laptop:~$ 

```

any idea on what I might be doing wrong?

The IPs are:
myusername --> 192.168.0.100
remoteuser --> 192.168.0.101

---

### Post by e79 on 2010-10-07
Lets say your laptop1 has user1 as username and laptop2 has user2 as username, this would be the correct syntax to use:
 
From laptop1 to laptop2:
```
ssh user2@laptop2
```
 
From laptop2 to laptop1:
```
ssh user1@laptop1
```
 
Of course, laptop1 and laptop2 can be replaced by their respective IP addresses. The trick is to inpu the username you created on the DISTANT laptop to log in from your current laptop; hoping this does not confuse you  :)

---

### Post by csharpplus on 2010-10-07
e79,

Thanks so much, but this does not work:

> 
remoteuser@remoteuser-laptop:~$ ssh myusername@192.168.0.100
ssh: connect to host 192.168.0.100 port 22: Connection timed out
What am I missing? (thank you)

just to make sure: 'myusername' is the_ actual username_ of the other machine (explanation: this is a 'trial' installation of ubuntu -- hence, I did not choose a more significant name).

---

### Post by e79 on 2010-10-07
Are you able to ping both laptop ?
```
ping 192.168.1.100
```
or
```
ping 192.168.1.102
```
(assuming you gave the values I wrote as examples)

---

### Post by csharpplus on 2010-10-07
I tried to ping. the ping 'hangs' and does not do anything (I stopped it after a while).

```

remoteuser@remoteuser-laptop:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
^C
--- 192.168.1.100 ping statistics ---
57 packets transmitted, 0 received, 100% packet loss, time 56081ms

```Interestingly, few moments after I try to 'ping', I did see a message on the other machine (the one I was trying to ping into) saying 'time has expired'.

What am I doing wrong? thank you.

---

### Post by e79 on 2010-10-07
Ok, lets start all over again regarding your IP manual settings:
 
For the l**aptop1**
IP Address: 192.168.0.100
Netmask : 255.255.255.0
 
For the **laptop2**
IP Address: 192.168.0.101
Netmask : 255.255.255.0
 
Erase DNS Server and Gateway entries on both laptops and start over with the ping test, it seems like you have a connection (setting) issue.
 
Post back your results

---

### Post by csharpplus on 2010-10-07
e79,

thanks for your help.

these are the exact settings that I have:

__________________________
For the l**aptop1**
IP Address: 192.168.0.100
Netmask : 255.255.255.0
*[SIZE=2]Gateway: [/SIZE][SIZE=2]192.168.0.1[/SIZE]*
 
For the **laptop2**
IP Address: 192.168.0.101
Netmask : 255.255.255.0
[SIZE=2]*Gateway: 0.0.0.0*[/SIZE]
__________________________

I am trying to delete the gateway on **laptop1** or set it to 0.0.0.0, but _it does not let me do so_ (meaning, it is automatically, resets the gateway to *[SIZE=2]192.168.0.1[/SIZE]*). on **laptop2** , it automatically sets the gateway to [SIZE=2]*0.0.0.0*[/SIZE]  no matter what I do.

does it have anything to do with MAC address or other settings? (I got these computers from somebody, and it is possible they had other settings that need to be changed...). also, in case it helps, here is what 'ifconfig' says from 'laptop2':

```

remoteuser@remoteuser-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:41:57:92:e8  
          inet6 addr: fe80::216:41ff:fe57:92e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4104 (4.1 KB)  TX bytes:3888 (3.8 KB)
          Memory:ee000000-ee020000 

```

thanks again for everything!

---

### Post by e79 on 2010-10-07
> **csharpplus said:**
> ...does it have anything to do with MAC address or other settings? (I got these computers from somebody, and it is possible they had other settings that need to be changed...)
 
In your case, since you are only trying to ping on the 'LAN' side, MAC address, gateway and DNS are irrelevant to the cause. Even if one laptop has a gateway and the other hasn't you should still be able to ping from one to another....unless your switch is blocking the ping requests..(which I doubt). Do you have any type of firewall installed on any of the laptops ?
 
I honestly don't know the cause of those gateways setting by themselves to be honest, it is a strange behavior...
 
Could you try to set back the network interfaces (on both laptop) to 'DHCP', reboot the machine, and retry the 'Manual' configuration typing only the IP address and NetMask this time ?

---

### Post by csharpplus on 2010-10-07
e79,

thank you so much for your help!

I am a little ashamed to say, but things now work! I have no idea what was the reason for the technical difficulties that I experienced earlier. either way, things look fine now.

tell me please, is there anything I can do that will allow me to access a machine by a name (rather than by IP)? 

for example, instead of doing 'SSH myuser@myIP' I will be able to do 'SSH laptop1'. Is this possible to do with my current configuration (switch rather than a router)?

thanks!

---

### Post by e79 on 2010-10-07
I'm glad I could help you ! :P

> tell me please, is there anything I can do that will allow me to access a machine by a name (rather than by IP)? There is indeed something you can do without having too much trouble, populate the **hosts** file (for this example we will be opening the hosts file on **laptop1**):
```
sudo nano /etc/hosts
```The file should look like this :
```

127.0.0.1       localhost
127.0.1.1       laptop1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```Now simply add an entry that is corresponding with the laptop2's host name a IP address (shown in red):
```

127.0.0.1         localhost
127.0.1.1         laptop1
[COLOR=Red]192.168.0.101     laptop2[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```Now save the file, reboot the computer, and the next thing you'll know, is that you can ping laptop2 by its name (or ssh) !
You can in fact input any host name you want here and it will work the same as long as the IP address of the distant machine is correct.

Regards  :P

---

### Post by csharpplus on 2010-10-07
perfect. thank you, e79!

Just to make sure I understand you correctly -- in the example given:
```

127.0.0.1         localhost
127.0.1.1         laptop1
[COLOR=Red]192.168.0.101     laptop2[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

must I write the host name as 'laptop2' (as this is the real host name of that computer), or can I write (for the same IP, of course) a different, desireable name?  for example:

[COLOR=Red]192.168.0.101     living_room[/COLOR] 

laptop2 is placed in the living room. can I now use the name 'living room' to access it? or must I use the actual host name ('laptop2')?

also, must this 'hosts' file be placed in all machines, or just the 'accessing' machine (the one who SSHs into the rest)? 

thank you.

---

### Post by e79 on 2010-10-07
> must I write the host name as 'laptop2' (as this is the real host name  of that computer), or can I write (for the same IP, of course) a  different, desirable name?
You can put ANY name you want in this hosts file :
```

127.0.0.1                localhost
127.0.1.1                laptop1 
[COLOR=Red]192.168.0.101     laptop2
192.168.0.101     living_room
192.168.0.101     hello.world
[/COLOR]
```At some point, if you have many machines or your network or if you don't mind tinkering a bit, you might want to consider configuring a BIND9 DNS server that would service all the machines and allow you to resolve all their names on your LAN. Of course the easiest way would be to find a router that does service DNS :)

---

### Post by csharpplus on 2010-10-07
thanks so much, e79. You've been so helpful!

---

### Post by e79 on 2010-10-07
The pleasure is all mine !! :P

---

