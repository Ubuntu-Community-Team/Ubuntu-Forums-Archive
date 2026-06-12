---
title: "Ubuntu 8.10 Samba sees windows network but folder is empty."
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Stuart1745 on 2008-12-19
I run a small mixed OS network (Ubuntu 8.10, 8.04, XP, Vista, and Fedora 5) and Im havng problems with the ubuntu 8.10 computer not seeing the windows Shares. it can tell that there is a windows network but its blank on the inside, also all the other computers cannot see the shares that are on this computer.

I have searched for a few months on what is the problem. I changed my name resolve order to be  lmhosts wins bcast hosts, with hosts at the end. I tried various updates to samba . . still cant see any shares. here is my config file if that would be any help. thank yall for the help

[global]
netbios name = DeusMachina
server string = 
workgroup = MSHOME
    announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
security = user
null passwords = no
username map = /etc/samba/smbusers
name resolve order = lmhosts wins bcast hosts
wins support = yes
    printing = CUPS
printcap name = CUPS
    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no
; Uncomment if you need to share your CD-/DVD-ROM Drive

;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

[Video]
path = /multimedia/Video
comment = No comment
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = yes
printable = no
share modes = no
locking = no

---

### Post by Iowan on 2008-12-19
Might need to install winbind and edit nsswitch.conf  [This]("http://ubuntuforums.org/showthread.php?t=288534") thread may cover those topics.

---

### Post by Stuart1745 on 2008-12-19
Well thank you for your quick response, but unfortunately that did not seem to do it. I installed winbind and edited the nsswitch.conf file still having the same issue. 

as an added help when I did a smbtree I got no shares just a new line. also yes I am sure that my workgroup is MSHOME.

---

### Post by spcwingo on 2008-12-19
You have samba and smbfs installed, correct?

---

### Post by Stuart1745 on 2008-12-19
yes yes I do

---

### Post by wwusnobrdr on 2008-12-20
I suggest you check the ntfs/sharing permissions on the windows machine.  You may not have read permissions on those folders.  There are a few things that may cause this but that is the first thing that comes to my mind.

---

### Post by Stuart1745 on 2008-12-20
no because the other Linux boxes are able to read and write to the windows boxes. also the 8.10 box does not see the 8.04 box or the fedora 5 box. nor do they see it. so I don't think its a windows file permission thing.

again I thank every one for their help

---

### Post by Stuart1745 on 2008-12-20
ok just as an update I did stop winbind and it worked for a while. . . then I rebooted and the problem came back, I stopped the winbind again and still it would not show the "windows network"

---

### Post by mpokrywka on 2008-12-21
Does it work when you try:
smbclient //ip_of_other_host/share

Maybe there is a problem with "master browser" election?
Have you tried "wins support = no" ? (read man smb.conf, there is a warning "you should NEVER set this to yes on more than one machine in your network")

---

### Post by borlosky on 2008-12-21
I've also been having same issue. On my network I'm running 1 dual boot xp 32 bit/ubuntu 8.10 64bit, 2 win xp 32 bit, 1 ubuntu 8.10 32 bit. all pc's able to access each other fine, EXCEPT when i boot into ubuntu on the dual boot pc. for some reason, once I'm in ubuntu, i can't see any of the pc's anymore, even though i see my network work group. when i'm on winxp on the dual boot, i can access both xp boxes, and the ubuntu 32 bit just fine, and all those pc's can access the dual boot when in xp as well. but in ubuntu, other pc's no longer see the dual boot pc. 

...very strange because i remember setting up samba on 32 bit pc before i got the new (dual boot), and it was a breeze, up and running and accessing my windows shares with no trouble. I've even completely formatted the ubuntu partition, and did a clean install of 8.10 (had same issue with 8.04 btw) but issue still persists. should mention i've tried both 64 and 32 bit versions of both 8.04 and 8.10.

will check for this when i get home though, this may possibly be it, because the pc that sharing works fine on was the first ubuntu pc i had, and that setting is prolly enabled. will repost if that did the trick:
> **mpokrywka said:**
> Does it work when you try:
smbclient //ip_of_other_host/share

Maybe there is a problem with "master browser" election?
Have you tried "wins support = no" ? (read man smb.conf, there is a warning "you should NEVER set this to yes on more than one machine in your network")

ok, so tried that, looks like it's already set to "wins support = no"

i'm afraid I'm still stuck on this. for the time being, it's not a big issue since this is happening on my dual boot, and i can just boot into windows to gain fill access to all my windows and ubuntu network shares.

---

### Post by mpokrywka on 2008-12-21
One more thing to try: disable built in firewall to see if it helps:
**sudo ufw disable**
If this is firewall problem, let me know and I will dig ufw internals to configure rules that allows samba to function.

---

### Post by borlosky on 2008-12-21
> **mpokrywka said:**
> One more thing to try: disable built in firewall to see if it helps:
**sudo ufw disable**
If this is firewall problem, let me know and I will dig ufw internals to configure rules that allows samba to function.

actually,i don't run any software firewalls on any of the pc's, i use a hardware firewall/router. (unless there's one enabled by default in ubuntu i don't know about, but i doubt thats the case)...still at work though, haven't had a chance to try the other steps yet, but i will look into it as well later tonight when i get home just to be sure.

---

### Post by -Stevey-Wonder-1990- on 2008-12-24
im having the same problem.  when i type in the location of a shared folder or whatever it does come up.  Its just when I click on the network it doesnt show anything.  I have set up bookmarks to my shared folders to make things easier but it would be great to if they were visable.  Any suggestions?

---

### Post by Stuart1745 on 2008-12-26
OMG 

sudo ufw disable

worked . .  give that man a cookie!!!

seriously 6 months working on this  . . and fixed by a 1 liner command.

again thanks for all your help

---

### Post by dtmfdan on 2008-12-28
I've tried disabling the firewall and I still can't see any of my shares. Any other ideas? Thank you.

---

### Post by mpokrywka on 2008-12-28
This must be bug in samba client libraries or in gnome (gnomevfs?). Maybe someone else have some ideas how to debug this problem.

---

### Post by thomasr on 2008-12-28
This worked for me:

Go to Places-->Connect to server
Use the drop down ox to select windows share
fill in server field with the servers IP
fill in share field with the share name
fill in user name
click on connect

If this works for you, you can bookmark it in Nautilus.

Seems Ubuntu 8.10  is unabke o browse shares, but can connect to a spcified share.

---

### Post by mach87 on 2009-01-18
Well that's all great that now I can see the files...but is there any way to get the network sharing to work again without disabling the firewall?

I had everything working fine. I had 3 computers on my network (1 windows XP and 2 Ubuntu 8.10) I was sharing between the two 8.10 machines often, then my personal machine stopped showing up. I even still had access to one of my 6 shared folders at the time. I just could not see any of the others.

---

### Post by flipgeek on 2009-02-07
> **thomasr said:**
> This worked for me:

Go to Places-->Connect to server
Use the drop down ox to select windows share
fill in server field with the servers IP
fill in share field with the share name
fill in user name
click on connect

If this works for you, you can bookmark it in Nautilus.

Seems Ubuntu 8.10  is unabke o browse shares, but can connect to a spcified share.
[FONT="Tahoma"][SIZE="3"]
This worked for me. Thanks![/SIZE][/FONT]

---

### Post by BigGeoff on 2009-02-08
Well give the man a whole packet of cookies, disabling the firewall solved my problem too. I didn't even know there was a firewall running - this just happened. I can now browse my shares on two pc's (Ubuntu and Mythbuntu) and a NAS. Oddly my eeePC 701 can see the shares on the NAS but not on the Mythbuntu system and although it can see the shares it can't access them despite the shares being public! Hmmmmmmmm

Geoff

---

### Post by tobydeemer on 2009-03-15
Hey guys- 

Here's some info on correcting the UFW firewall to enable Samba sharing withouth turning off the firewall.

Info sourced from this blog post:
[http://log.logfish.net/node/31](http://log.logfish.net/node/31)

And here's lines to add to config files:

Edit default UFW config >>
sudo gedit /etc/default/ufw

Add this to bottom:
# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

Then edit UFW sysctl config >>
sudo gedit /etc/ufw/sysctl.conf

and add this to bottom, adjusting for your LAN IP range:

allow from 192.168.1.0/255 to Samba
allow Samba

#Samba sharing [1]
sudo ufw allow proto tcp to any port 135 from 192.168.1.0/255
sudo ufw allow proto udp to any port 137 from 192.168.1.0/255
sudo ufw allow proto udp to any port 138 from 192.168.1.0/255
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/255
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/255

This all corrected the issue for me, and I don't have to have the firewall turned off, which if nothing else just makes me feel better...

Post again if this still doesn't work for anyone.

Cheers.

---

### Post by SpEcIeS on 2010-06-20
This little tidbit was very helpful. Thanks... :KS

> **tobydeemer said:**
> Hey guys- 

Edit default UFW config >>
sudo gedit /etc/default/ufw

Add this to bottom:
# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"


---

