---
title: "One ubuntu can't see any other computers on network"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by mkendrick on 2013-04-17
Hello,

Apologies if I've missed something obvious (I'm relatively new to ubuntu). Over the past few weeks I've been trying to connect my main computer running ubuntu 12.04 LTS (64 bit) to my laptop running ubuntu 12.04 LTS (32 bit), with the eventual aim of adding a raspberry pi to the network to act as media hub. The network setup is simple as you would expect to find in any house with a central router connected to the internet and the machines connected to the router via wifi. 

The laptop is able to see other machines on the network but can't see the main pc, however it can ping it via the ping command.

The main pc can ping the laptop but cannot see any computers on the network either through nautilus or by using smbtree.

I've read a number of different posts including ([http://ubuntuforums.org/showthread.php?t=1861985](http://ubuntuforums.org/showthread.php?t=1861985)) and will try to give useful information/outputs. Note I have added the following lines to the [COLOR=#000000]/etc/samba/smb.conf file in the [global] section:

[/COLOR]```
[COLOR=#000000]netbios name = serenity
name resolve order = bcast host
[/COLOR]
```

Where serenity is my hostname for the main pc. The netbios name doesn't show up in testparm (which I don't know if this is normal or not). I also get a slightly different output on the main pc to the laptop. 
Output of testparm for the main pc:
```
martyn@serenity:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```
The line which is not present on testparm for the laptop is "username map = /etc/samba/smbusers"
Additionally smbtree outputs the following.
```
martyn@serenity:~$ smbtree
Enter martyn's password: 
WORKGROUP
HOME
    \\BTHUB3                 BT Home Hub 3.0A File Server
        \\BTHUB3\IPC$               IPC Service (BT Home Hub 3.0A File Server)

```


whereas the output on the laptop gives:
```
martyn@freebird:~$ smbtree
Enter martyn's password: 
WORKGROUP
       \\JOHNLAPTOP
       \\EM1K0
       \\FREEBIRD               Freebird server (Samba, Ubuntu)
                \\FREEBIRD\training$
                \\FREEBIRD\print$
                \\FREEBIRD\IPC$
HOME
    \\BTHUB3                 BT Home Hub 3.0A File Server

```

Hope I've included everything to get this sorted. 
Cheers,
Martyn

---

### Post by TheFu on 2013-04-17
Shots in the dark here, but ...
* are both machines on the same subnet?
* can both machines use the hostname to ping each other? (did you modify DNS or /etc/hosts for each machine?)
* Have you setup an smbpasswd for the "server"?

You need to add a section describing the are to be shared on the samba server machine.  Usually this happens after the [Global] section, but before the [Printers] section.  A few settings are necessary there. Here's the example from my smb.conf:

```

[cdrom]
  comment = Samba server's CD-ROM
  read only = yes
  locking = no
  path = /cdrom
  guest ok = yes

```
That should get you started. For more details, **man smb.conf** will explain everything.

---

### Post by mkendrick on 2013-04-17
Thanks for your reply TheFu. 
In general response to your questions aside from the changes I mentioned in the original post everything is as per default. But I'll have a go at answering your questions aswell:

[COLOR=#000000]* are both machines on the same subnet?
[/COLOR]I think I understand what you mean by subnet and ifconfig on both the computer and laptop show a mask of 255.255.255.0

[COLOR=#000000]* can both machines use the hostname to ping each other? (did you modify DNS or /etc/hosts for each machine?)
[/COLOR]I haven't modified the DNS or /etc/hosts on either machine. I've had some progress connecting through nautilus doing CTRL + L and typing smb://192.168.1.99 or smb://freebird which is the ip address and hostname, respectively, for my laptop. From there I can access my shares. However I still can't browse the network or navigate to this point. 

[COLOR=#000000]* Have you setup an smbpasswd for the "server"? I haven't setup any passwords beyond a password for my user account. Additionally I haven't designated any computer as a server and have simply used samba and associated programs that are downloaded when you first try to share a folder. Although it is worth mentioning I struggled to get this installed on the pc and had to change to the multiverse repository to get this to download. 

I haven't created a share in the conf file, although when I created a share on the laptop I didn't do it this way either, I did it the GUI way through nautilus with right click and sharing. The share created this way is visible as a share on the network from the laptop and was seen in the ouptut from smbtree [/COLOR]

---

### Post by mkendrick on 2013-04-17
Further update. 

As I mentioned in previous post I can access the shares on my laptop from the main pc. I can also access these from my raspberry pi. 
However, from my laptop I can't access my main pc or Rpi using smb://<ip> or smb://<hostname>. Although I can ping using $ping <ip>

---

### Post by TheFu on 2013-04-18
Those questions were really meant as hints for things that I'd setup to resolve the issue.

Having the same netmask does not necessarily mean each machine is on the same subnet. If you can easily ping each machine by IP address from the other machines, then the networking is probably just fine. It is just the name resolution that you are missing.  Modify the /etc/hosts file on every machine to point to the others (and itself). If you use DHCP, then you probably want to use dhcp reservations so that each machine has a static IP address without having to setup a static IP on each. Let the DHCP server on your network provide that service. Many home routers do this, but you need to look up the instructions for your specific router. Can't help you there. If that isn't a feature of your router, then you'll want each "server" to have a static IP.

Nautilus is amazing ... at least I hear it is. Don't use it myself.  If you want to share folders between systems, I do not recommend using nautilus, since those shares will probably not be restarted after a reboot and probably will not be available until the specific userid logs in post-reboot.  Doing it the "server way" (inside the /etc/samba/smb.conf) will ensure the shared directories are shared without any login. Seems like that would be important for your situation.  Use a text editor. There is no GUI way that I am aware.  Point-n-click is NOT your friend.

---

### Post by mkendrick on 2013-04-18
I think I get the general idea of what you're saying but I'm not too sure how to actually do it. 
I think what you said is to edit one of the host files in /etc/ of which there are a few options: host.conf    hostname     hosts        hosts.allow  hosts.deny 
However after looking at them I get the feeling you mean the file 'hosts' which currently on my main pc shows: 
```
127.0.0.1	localhost
127.0.1.1	serenity


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

What you want me to do is add the ip address and hostname for all the machines on the network that I want to access? 
The part about DHCP is about the fact that the router assigns the ip's dynamically and to make sure I always get through to the correct machine I should someone make it use static ip's for my machines using dhcp reservations. Setting dhcp reservations is done on the router? (in this case) or the server machine, which ever is applicable.

---

### Post by mkendrick on 2013-04-21
Ok got this solved:

I'm not entirely sure which part cured the problem but I did the following to get it working:
firstly on each machine ensure samba and associated software is installed by doing:
```
sudo apt-get install samba smbclient

```
Next, on each machine I wanted to access I made the following changes to '/etc/samba/smb.conf' I added after '[global]'
```
netbios name = [I]hostname
[/I]name resolve order = bcast host
```

Then to create a share I added a new section for each share like so:
```
[example]
comment=an example share
path = /<location of the folder you want to share>
writeable = Yes
only guest = Yes
create mask = 0777
directory mask = 0777
browseable = Yes
public = yes


```

Finally on each machine I added to the '/etc/hosts' file so that the start of the file looked like this:
```
127.0.0.1    localhost
127.0.1.1    computerA
192.168.1.B    computerB
192.168.1.C    computerC
```

Where computerA is the computer I was editting the file on. notice that for the computer you are on the ip is the local ip and not how you are found on the network (for example in my case computerA's ip was 192.168.1.87). the last digits B and C are whatever the ip address is for your computer (eg for computerB the ip was 192.168.1.99 such that B=99).

After all this is done you need only restart the samba service and it 'should' work, although a restart will guarantee it. to restart do:
```
sudo service samba restart
```

if this doesnt work try:
```
sudo service smbd restart
sudo service nmbd restart
```

To see if your share is visible on the network use 'smbtree' which will give you a break down of what is on the network, on occasion I found this didn't work and I'd have to resubmit 'smbtree' a couple of times before it displayed anything properly. You can also try connecting with smbclient (explanation can be found here [http://www.tldp.org/HOWTO/SMB-HOWTO-8.html](http://www.tldp.org/HOWTO/SMB-HOWTO-8.html))

Thanks very much to **TheFu** for your help, you enabled me to get past this problem and onto the next!

---

### Post by mkendrick on 2013-04-21
I'm afraid I don't know how to mark this as solved

---

### Post by matt_symes on 2013-04-21
Hi

Here's the temporary solution for how to mark a thread as solved.

[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

Thanks for asking. It'll help future people search the forums for a solution.

Kind regards

---

