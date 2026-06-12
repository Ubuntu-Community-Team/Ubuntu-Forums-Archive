---
title: "newbie - Natty Samba only partially working"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by kevcoder on 2011-06-01
...using Ubuntu 11.04 (cat5 cable into the wireless router) and [WIN7 Ultimate N]("http://en.wikipedia.org/wiki/Windows_7_editions") (wireless connection to router)
...the belkin router is using mac address filtering to restrict to my three laptops and the wii
... used **sudo apt-get install samba** and installed **ubuntu-config-samba** from the sofware center

the last howto I followed is [here]("http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/")

...emancipated myself to linux going on 1 month now, but a .NET developer 10+ years now

I've followed a couple of how-to's online and have got to the point that I could see the WIN7 share from Nautilus as well as a workgroup icon called METALWAVE (the workgroup I defined in WIN7 and smb.conf).  I have never seen Ubuntu from WIN7.

I then re-booted both machines and now in Nautilus, under Networking, I only see the ubuntu share and a workgroup named WORKGROUP.  I checked smb.conf and it says ```
workgroup = METALWAVE
```The WIN7 machine still see no other shares.

I've pinged both machines and neither can find the other.

I'm pretty confused now!  

Can someone point me to a how-to guide that they know works!!

thanks

---

### Post by baarn on 2011-06-01
is your network working properly on both machines? network, internet etc?
if not what does
ifconfig
say on linux (eth0 or wlan0 would be the device) and what does
ipconfig
say on windows?

samba can be a bit nasty, just installing it mostly wont do the trick, you have to configure it (there should be some guides how to do this with ubuntu, i have a samba server running on my gentoo-machine but that took me some time and i am far away from explaining another person how that works ;) )

have you modified your /etc/samba/smb.conf?

```
#======================= Global Settings =====================================
[global]

   workgroup = DRONEHIVE
   server string = Samba Server

   security = user
   encrypt passwords = yes
   invalid users = root

   log file = /var/log/samba/log.%m
   max log size = 1000
   
   username map = /etc/samba/smbusers
   map to guest = bad user
   guest account = nobody


#============================ Share Definitions ==============================

[homes]
   comment        = Home Directories
   browseable        = no
   writable        = yes
   valid users        = %S
   writable        = yes
   create mode        = 0600
   directory mode    = 0700

[public]
   path            = /home/public
   guest ok        = yes
   writeable        = no
   write list        = @wheel
   browseable        = yes
   create mode        = 0664
   directory mode    = 0775

[html]
   path            = /var/www/localhost/htdocs
   comment         = Web Files
   browseable        = yes
   writable        = no
   write list        = @apache
   valid users        = @apache
   force group        = apache
   create mode        = 0664
   directory mode    = 0775

```
this is my minmal samba server file... i am not sure if this would work on your machine, as i said i use gentoo on my server and some things work a bit different than on ubuntu, but it should give you first hints...
i have to mention, that that "server" is just connected to the LAN, so that config might be unsafe if connected to the web directly.

---

### Post by Morbius1 on 2011-06-01
Why not post the output of the following commands so people can see how you are set up:
```
testparm -s
net usershare info --long
findsmb
smbtree
```

---

### Post by kevcoder on 2011-06-01
> **Morbius1 said:**
> Why not post the output of the following commands so people can see how you are set up:
```
testparm -s
net usershare info --long
findsmb
smbtree
```

when I get home tonight I will.. didn't expect such a quick response

---

### Post by kevcoder on 2011-06-02
The info from my box follows.  
A bizarre update is that now I can now see the WIN7 share from the Ubuntu box but only after connecting to the WIN7 via the Terminal Server Client. 

The WIN7 box still can't see Ubuntu though.

So what does all of this mean?
testparm -s
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = METALWAVE
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[shared]
    path = /home/shared
    read only = No
    guest ok = Yes
dev@kevcoder00:~$ 

```net usershare info --long does nothing but retun me to the command prompt

findsmb
```
                               *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.2.3     KEVCODER00    +[METALWAVE] [Unix] [Samba 3.5.8]
dev@kevcoder00:~$ 

```smbtree
```

Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```

---

### Post by dandnsmith on 2011-06-02
That lot says to me that Win7 isn't sharing - you're not getting it in the list of servers - not necessarily THE problem - and you're not seeing any shares from it.

On my local net, I can see my Windows PC as server, and also the shares, whereas my wife's Windows PC I see shares, but it doesn't show in the findsmb list (something which I never noticed before).

I'd look at security settings on the Win7 PC

---

### Post by Morbius1 on 2011-06-02
Needed to know what address or hostname you got the smbtree error from but I'm guessing that it's from your own samba server. If smbtree can't find the shares on the machine it's run from there no hope anyone else will see it either.

Edit /etc/samba/smb.conf as root and change this:
```
security = SHARE
```to
```
#security = SHARE
```Then restart samba:
```
sudo service smbd restart
```The "#" in front of that line will "comment out" the line and return things to the default ( USER ).

Every time you restart samba you need to wait a few minutes ( yes minutes ) for the network to settle down before you can use it again so be patient.

---

### Post by kevcoder on 2011-06-02
*>>[Morbius1] Needed to know what address or hostname you got the smbtree error from*
this was from the smba server itself, the Ubuntu box

*>>[dandnsmith] That lot says to me that Win7 isn't sharing ...*
OK that makes sense... but remember that **after **I  term serv into the WIN7 box I'm able to see it from the Ubuntu box and  have read-only accesss to the files (I watched a movie and copied over a  file).  I didn't think to run **findsmb** afterward... so I'll check that tonight.

once again thanks and ..

Where is **THE** definitive (yet user friendly) explanation of samba and its  configuration.  I've found tons of online how-tos and they all seem to differ wildly once  we get to configuring smb.conf

---

### Post by dandnsmith on 2011-06-02
> Where is THE definitive (yet user friendly) explanation of samba and its configuration. I've found tons of online how-tos and they all seem to differ wildly once we get to configuring smb.conf

I think the problem is in several parts, including:
1) every attempt at a guide is aimed at doing things the authors way - even if his start point and aim are not yours.
2) samba has developed through the releases and, having endured some of the changes from early days, I know that some of the guides have never been properly updated to align with current releases - I'm dreading Samba4 and what it may bring in the way of new gotchas.

I have a standard style smb.conf, developed to cope with the sites with which I work, and find I have to update it from time to time as things like default settings for things change - and also parameters can change names (and with it there are sometimes new meanings.

Currently, in case of problem I'd be looking for guides aimed at samba3 - I did once find a good one, but have mislaid the references.

---

