---
title: "Samba Networking Issues - It will work once, but never again."
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by santims on 2010-04-16
So for about 3 weeks i have attempting to setup some sort of filesharing from my Ubuntu (9.1) machine to a) xbox running xbmc, and b) a windows XP sp3 laptop.  I have an airport extreme base station (802.11a/b/g/n) setup although everything is currently hardwired.

On the windows machine i found the folders i want to share, right click, share and i am all set.

On the Ubuntu 9.1 machine I started with a fresh install. Mounted the HD i wanted, right click - Share files - "you need to install packages" *yes*. i then share a few more folders from the HD.

On the xbox i boot up into XBMC, search for my samba shares and find my windows machine, my Ubuntu machine i mount evertying and i am able to read/write/edit/stream all the files i want.

But after i turn off my xbox, ubuntu box, windows box and restart everything i can no longer find any shares at all!  I have been going through this for several weeks now.

This morning i had a great moment, i went on my windows computer, reshared the directory and my windows and ubuntu shares showed up on my xbox!!!!! but i tried accessing them and complete failure ensued. so i restarted and now i cant find anything.  i made sure that samba was running using /etc/init.d/samba start (also tried stop/start and restart)

I have tried various methods of setting up samba. from the samba.org website, the ubuntu wiki, a video on youtube, and even the forums 'setup samba peer to peer with windows' post.

---

### Post by Morbius1 on 2010-04-16
> I have tried various methods of setting up samba. from the samba.org website, the ubuntu wiki, a video on youtube, and even the forums 'setup samba peer to peer with windows' post.It's unlikely that this is the cause of your problem but just in case you might want to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type [B]testparm -s
[/B] 
There are two completely different methods of using samba to share directories. Using both at the same time can cause problems. Those commands will tell us what method you're using and how the shares are set up.

> But after i turn off my xbox, ubuntu box, windows box and restart everything i can no longer find any shares at all! I have been going through this for several weeks now.Just so I understand, are you trying to access the shares through Nautilus and you end up with a blank panel. Or no machine anywhere on the network can see anyone else's shares.

---

### Post by santims on 2010-04-16
Morbius - thanks for the quick response.  I am at work and unable to run those commands right now on my home machine.  but to answer your second question:

No machines are able to see any shares.
xbox xbmc cannot see ANY shares (except one quick time)

Even on my ubuntu machine - using the drop down to navigate to* Places* - 'network' (or It brings up a window that has a folder with an RJ-45 port icon on it. i click that and it says that it cant find anything.

Windows xp cannot see any shares at all

Do static IPs play a role?

---

### Post by Morbius1 on 2010-04-16
If none of your machines can see each other then I don't think it's Samba or SMB that's the issue. Maybe the router?

As for static ip addresses it depends. If your "mapping a network drive" in windows or the equivalent in Linux by ip address and your ip address changes everytime you boot because your set up with DHCP then that's a problem.

If you have static ip addresses on all your boxes then this would help the issue hot hinder it.

---

### Post by santims on 2010-04-16
I will setup static IPs when i get home tonight.

I dont know if i would point my finger at the router because once everything finishes its initial setup i have been able to see and access the shares. my main problem happens after i begin restart computers

---

### Post by santims on 2010-04-16
does the fact that the router issues a 10.0.x.x ip address to all the  devices make a difference in this situation? i know most routers issue a 192.168.x.x ip.

---

### Post by Morbius1 on 2010-04-16
I don't think so. So called "Private" ip address an be 10.xxx, [FONT=Arial]172.16.xxx, or the most common 192.168.xxx

What you might want to investigate is whether your router can assign static ip address based on the unique MAC address of each machine. You would leave each machine set to DHCP as it is now but have the router supply the exact same ip address to the exact same box each time that box boots. It's easier to set up and requires no configuration on the OS side.

Depending on the router this feature can be called:

"DHCP Address Reservation"
"Static DHCP"
 "Reserved DHCP"
"reserved leases", 
"Pre-assigned DHCP" 

And other oxymoronic variations of the above :)


[/FONT]

---

### Post by santims on 2010-04-16
thanks.

i have a lot of homework to do tonight!!

---

### Post by santims on 2010-04-16
here is the output from those commands.

```
chris@chris-desktop:~$ net usershare info
[tv shows]
path=/media/1TB Drive/TV Shows
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n

[music]
path=/media/1TB Drive/Music
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n

[pictures]
path=/media/1TB Drive/Pictures
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n

[movies]
path=/media/1TB Drive/Movies
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n

[videos]
path=/media/1TB Drive/Videos
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n

chris@chris-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[TV Shows]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
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
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[TV Shows]
    path = /media/1TB Drive/TV Shows
    valid users = chris

[Music]
    path = /media/1TB Drive/Music
    guest ok = Yes
chris@chris-desktop:~$ 

```

---

### Post by Morbius1 on 2010-04-17
First let me give you my little shpeel about samba sharing. There are two completely different methods of file sharing within the samba framework: Nautilus-share ( right click > sharing options ) and Classic-sharing. You can use both methods but it becomes hard to manage so I always recommend using one method or the other. You're using both methods and in two cases on the same target with different parameters:

Nautilus-share:
> [tv shows]
path=/media/1TB Drive/TV Shows
comment=
usershare_acl=S-1-1-0:R,
guest_ok=n
Classic-share
> [TV Shows]
    path = /media/1TB Drive/TV Shows
    [COLOR=Blue]valid users = chris[/COLOR]
The Nautilus-share will allow everyone with a valid username and password to gain access. The Classic-share will allow only "chris" to gain access. If you want only chris to gain access then I would "unshare" the Nautilus-share for [TV Shows].

Nautilus-share:
> [music]
path=/media/1TB Drive/Music
comment=
usershare_acl=S-1-1-0:R,
[COLOR=Blue]guest_ok=n[/COLOR]
Classic-share
> [Music]
    path = /media/1TB Drive/Music
    [COLOR=Blue]guest ok = Yes[/COLOR]
As you can see the two methods contradict each other about guest access. I would get rid of one share or the other depending on what you want to do about guest access.

Based on your original description of the problem I don't know if this will fix everything, but using both sharing methods - especially on the same target - often has unpredictable results.

Try to fix these problems , restart samba ( **sudo service samba restart** ) and see if  anything improves.

---

### Post by santims on 2010-04-19
thank you for the info!!! and based on the info i decided to do the following:

Since i had nothing to lose on this install and HD i decided to start fresh on this one.  Re-installed 9.10 ran all updates and then used the right-click ->sharing method.  i havent touched a single thing with filesharing since then.  everything appears to be working correctly for now!

I was trying to do too much to setup the file sharing and screwing it all up in the process!

thank you for the guidance.

---

