---
title: "Updated connecting to windows network shares fix 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by conorturton on 2009-04-24
Sorry people, 

Following on from the instructions I put in [http://ubuntuforums.org/showthread.php?t=1134738](http://ubuntuforums.org/showthread.php?t=1134738)

I have done this on 3 fresh installs of Ubuntu 9.04 which have been unable to browse or connect to Windows network shares.

You need to install winbind too.

So new instructions are:

Install winbind 

> 
sudo apt-get install winbind


Edit /etc/nsswitch.conf

> 
sudo gedit /etc/nsswitch.conf




Look for the line...

hosts: files (etc)

If yours is like mine was when it didn't work, it'll read something like:

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

..although what is there will vary but files and dns will be there.
What is missing is an entry for wins.

You need to add wins after files so it looks like (alter as required):

hosts: files wins mdns4_minimal [NOTFOUND=return] dns mdns4


Save the file and reboot.

Please post your findings.

---

### Post by JGUbun on 2009-04-25
Thanks!

I was having the same problem and that fixed it.

---

### Post by alpo on 2009-04-25
Thank you very much for the tips. I successfully found the Windows shares. I have another problem. I installed winbind with a wired connection. After unhooking the wired ethernet cable and activating the wireless connection, the internet works but my network Windows shares no longer appear. How do I configure winbind to access both wired and/or wireless, depending on which one is active?

Thanks.

---

### Post by Jimmy9pints on 2009-04-26
Dumb question probably: Should the steps you outline (installing windbind etc) be done on the server or the client?

---

### Post by Exile09 on 2009-04-26
Thanks for that!

You have just made my life MUCH easier! :P

---

### Post by jcomaling on 2009-04-27
I used several "solutions" including this one and all i got was i saw my own computer and print$ folder, i used the work around for accessing files over the network using IP address and its working fine, BUT its a different story in printing. network printers can be installed using static ip address of the print server using the appsocket/hp jetdirect option in add network printers tree ie 192.168.0.11 as the host and the default 9100 as the port number. but keeps on saying that the printer might not be connected. this is maybe due to the issue that i cannot see other computers over the network - file browser window.

Im in a office network having several domains and several computers connected to it windows xp/98 workstations.the print server im trying to connect to is windows 98 and it worked fine on ubuntu 8.04 printer is hp 1020.

please take note. that in ubuntu 8.04 there are NO problems with windows network file/printer sharing. i just got these errors when i upgraded to 9.04. im new with ubuntu please help.

And please dont tell me to stick to ubuntu 8.04 :)

---

### Post by Iowan on 2009-04-27
> **Jimmy9pints said:**
> Dumb question probably: Should the steps you outline (installing windbind etc) be done on the server or the client?My chance to start the day by being wrong...
> The service provided by winbindd is called `winbind' and can be used to resolve user and group information [COLOR="Blue"]from a Windows NT server[/COLOR]This [definition]("http://linux.about.com/cs/linux101/g/winbind.htm") references a Windows server - which *suggests* it goes on the client.

---

### Post by XopherH on 2009-04-28
> **conorturton said:**
> 
Install winbind 
Edit /etc/nsswitch.conf
Save the file and reboot.

Please post your findings.

no luck.

---

### Post by conorturton on 2009-04-30
> **Jimmy9pints said:**
> Dumb question probably: Should the steps you outline (installing windbind etc) be done on the server or the client?

Everything is done on the client.

Point to note:

If you're using aMSN, if you install winbind then aMSN crashes as soon as you try to connect to anything.

Pidgin works fine still.

If someone knows how to configure networking so that winbind only works on local addresses then that will solve this issue.

---

### Post by adonet on 2009-05-01
> **jcomaling said:**
> I used several "solutions" including this one and all i got was i saw my own computer and print$ folder, i used the work around for accessing files over the network using IP address and its working fine, BUT its a different story in printing. network printers can be installed using static ip address of the print server using the appsocket/hp jetdirect option in add network printers tree ie 192.168.0.11 as the host and the default 9100 as the port number. but keeps on saying that the printer might not be connected. this is maybe due to the issue that i cannot see other computers over the network - file browser window.

Im in a office network having several domains and several computers connected to it windows xp/98 workstations.the print server im trying to connect to is windows 98 and it worked fine on ubuntu 8.04 printer is hp 1020.

please take note. that in ubuntu 8.04 there are NO problems with windows network file/printer sharing. i just got these errors when i upgraded to 9.04. im new with ubuntu please help.

And please dont tell me to stick to ubuntu 8.04 :)

I got the same network printing problem, and the [workaround http://ubuntu-install.blogspot.com/2008/11/use-printserver-in-ubuntu-804-hardy.html]("http://ubuntu-install.blogspot.com/2008/11/use-printserver-in-ubuntu-804-hardy.html") that worked for me in 8.04 doesn't work in 9.04. The network printer works fine in 8.10.

---

### Post by cicciobello on 2009-05-01
I am having the same problem. I had version 8.01, I installed all the components recommended in this forum, edited /etc/nsswitch.conf to include "wins" and, finally, I could see my Vista desktop, and my Vista desktop could see my Ubuntu laptop. Life was good. 

Then I upgraded to 9.04 and I have a DNS problem. I can still do everything, even print,but only by IP address. None of the hosts are found. Vista cannot ping the Ubuntu host by name and Ubuntu cannot ping Vista by name.

I tried reinstalling samba and winbind after the upgrade, no luck... Is there an issue with v9.04?

---

### Post by hhoyt on 2009-05-02
WOW, thanks so much- worked like a charm.
I also ran across this on my linux Granular box.

Thanks !

Howard

---

### Post by Merel 469 on 2009-05-02
It didn't work for me and didn't change my problem. I can see and access another PC in my existing Windows network (with all the shared folders) but my own PC is not even detected as being part of my existing Microsoft home network, named "Thuis").

I created (in Ubuntu) a new shared "TEST" folder on my own PC.
As a result Ubuntu created (not asking for permission for it) a "new" second network, named MSHOME, showing only my own PC, and this shared test file only.

I have now a second network, which I can't even delete, because Ubuntu does not allow it to be deleted.

---

### Post by Merel 469 on 2009-05-02
> **jcomaling said:**
> I used several "solutions" including this one and all i got was i saw my own computer and print$ folder, i used the work around for accessing files over the network using IP address and its working fine, BUT its a different story in printing. network printers can be installed using static ip address of the print server using the appsocket/hp jetdirect option in add network printers tree ie 192.168.0.11 as the host and the default 9100 as the port number. but keeps on saying that the printer might not be connected. this is maybe due to the issue that i cannot see other computers over the network - file browser window.

Im in a office network having several domains and several computers connected to it windows xp/98 workstations.the print server im trying to connect to is windows 98 and it worked fine on ubuntu 8.04 printer is hp 1020.

please take note. that in ubuntu 8.04 there are NO problems with windows network file/printer sharing. i just got these errors when i upgraded to 9.04. im new with ubuntu please help.

And please dont tell me to stick to ubuntu 8.04 :)
I have the same remark about the fact that there was [COLOR="SeaGreen"]_NO problem_[/COLOR] at all with all of my  previous Ubuntu versions to acess Windows shares.

So in your case ... all you see is your own PC ?
In my case ....I don't see my own PC !

In your case ... You don't see other PC'S ?
In my case ... I do see another PC, but not the NAS (Network drive).


So; does anybody can explain **why good working tools were modified for no reason to such mess ??** Makes no sense. If it works don't fix it !

This kind of things would encourage anybody to abandon Ubuntu and stick to Windows. I spend more time trying to make this "operating" system running  as I can spend to work with it.

---

### Post by Ittiger on 2009-05-02
> **Merel 469 said:**
> It didn't work for me and didn't change my problem. I can see and access another PC in my existing Windows network (with all the shared folders) but my own PC is not even detected as being part of my existing Microsoft home network, named "Thuis").

I created (in Ubuntu) a new shared "TEST" folder on my own PC.
As a result Ubuntu created (not asking for permission for it) a "new" second network, named MSHOME, showing only my own PC, and this shared test file only.

I have now a second network, which I can't even delete, because Ubuntu does not allow it to be deleted.

Have you got the Samba GUI installed?  (If not install it from add/remove).

It will be in System>Administration>Samba

Open it and it will ask for password

Click on Preference then server settings.  Change the Workgroup name to "Thuis" then click okay.

You may have to log out then in again.

---

### Post by cicciobello on 2009-05-02
> **Ittiger said:**
> Have you got the Samba GUI installed?  (If not install it from add/remove).

It will be in System>Administration>Samba

Open it and it will ask for password

Click on Preference then server settings.  Change the Workgroup name to "Thuis" then click okay.

You may have to log out then in again.


Thanks, but can you specify the exact package name for this Samba GUI? I found many different GUIs for Samba. Also, I already made sure that the workgroup is set to  "WORKGROUP" (same as my Vista desktop) in /etc/samba/smb.conf:

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

Would update it through the UI change something else too?

Thanks for your help.

---

### Post by coodtec on 2009-05-03
Still not work for me.

---

### Post by taget on 2009-05-03
Install winbind and editing nsswitch.conf worked well for me, thanks for the tip.

---

### Post by jcomaling on 2009-05-03
> **Merel 469 said:**
> I have the same remark about the fact that there was [COLOR=SeaGreen]_NO problem_[/COLOR] at all with all of my  previous Ubuntu versions to acess Windows shares.

So in your case ... all you see is your own PC ?
In my case ....I don't see my own PC !

In your case ... You don't see other PC'S ?
In my case ... I do see another PC, but not the NAS (Network drive).


So; does anybody can explain **why good working tools were modified for no reason to such mess ??** Makes no sense. If it works don't fix it !

This kind of things would encourage anybody to abandon Ubuntu and stick to Windows. I spend more time trying to make this "operating" system running  as I can spend to work with it.

Ubuntu 9.04 out of the box installation or even the live version. does not see any computers even my own in the network. the 8.04 version works very well.

if this can help, the office have a zyxel zywall 5 network firewall equipment mostly for the internet connection authorization. again ubuntu v8.04 works fine with this. 

using a "simple" network setup, such as a 100/10mb switch hub to connect computers. work fine on both v8.04 and v9.04

---

### Post by cmorestuff on 2009-05-06
The fix worked great.  This problem has been in my head for 4 days, now I can rest.  Thanx for the help.....:)

---

### Post by macbcn on 2009-05-07
It WAS working fine "out of the box" on 9.04 until yesterday's updates... now I can't see any of the other computers on the network... not with the winbind process, not with the samba one either... :-(

Any useful ideas?

Thx

---

### Post by XopherH on 2009-05-07
Try this.

Places > Connect to Server

Windows Share, Server : LAN IP, Folder: shared folder on server, My server user name, and Domain: your samba workgroup.

smb4k still doesn't connect as well as Network, and this must be done after reboot. Also, rebooting the server does not allow immediate access to all mounted folders and you have to use the link under Places before the desktop icon will work.

---

### Post by Hyperion_1984 on 2009-05-08
I had this issue until I realized that during my upgrade from 8.10 to 9.04, my ufw (firewall) setting were changed. I had to set them back to there original settings. Now, everything is working find.

---

### Post by mgmiller on 2009-05-08
This became a problem for me after some update for 8.04, then network browsing died.  Also true of 8.10 and 9.04 installs that I have.  Some are clean installs, some are upgrades, some 32 bit, some 64 bit.  Doesn't matter.  None of them will browse samba shares in 2 mixed Windows Xp / Ubuntu networks that I maintain.

Here is how I fixed it.  It worked on every machine I own.  I did not need to install any packages beyond the default install.

```
gksu gedit /etc/samba/smb.conf
```Scroll down to:
# What naming service and in what order should we use to resolve host names
# to IP addresses

and change the entry from:
```
; name resolve order = lmhosts host wins bcast
```to this:
```
name resolve order = lmhosts wins bcast host
```Notice, I removed the ; from the front of the line as well as changed the order of the items.

Log off and and back on.  (Maybe restart if that does not do it).

The Places > Network gui will now work as expected.

---

### Post by thefoxhero on 2009-05-09
still no luck darn!

---

### Post by mgmiller on 2009-05-09
Have your tried installing the samba gui?  It makes configuring everything much easier.  You shouldn't have to join the windows workgroup, but maybe by doing so it will help.  It's easily set from the gui.

```
sudo apt-get install system-config-samba
```

You'll find it in System > Administration > Samba

You can also try entering the following in a terminal for a quick samba gui:
```
shares-admin
```

---

### Post by Hariharakadan on 2009-05-09
Hello, after bouncing around many websites and forums I managed to find a winning combination to get Windows sharing with Vista to work.

[http://paste.ubuntu.com/168069/](http://paste.ubuntu.com/168069/)

Most of the information was obtained from this forum. 

[http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/](http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/)

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Also on the Vista machines make sure to enable everything that involves sharing including password sharing. I had trouble with one machine and after I turned on password sharing it was viewable. I hope this helps someone else.

-Edit I forgot to add this. This was on 9.04 Ubuntu. I reinstalled it after thinking I did something to foobar the network viewing function in Nautilus but that wasn't the case. After reinstalling it still didn't work. Failed to mount / failed to retrieve share list was the errors it would spit out.

---

### Post by Merel 469 on 2009-05-09
Maybe this is redundent or maybe it adds some new information.
It was collected from several sources :

Many users have a problem with their Window Network not appearing in 9.04
The solution is to install SAMBA (not included in 9.04)
and more important ... edit the original smb.conf as written here below.

This worked also for me. But I have questions left about ...
- the used syntax interfaces = interfaces = 127.0.0.1/8 192.168.1.0/24
- the need and use of the new lines (at point 8 )


Sources of text :

1. English Ubuntuforums. Author DenysT (Kansas)
[http://ubuntuforums.org/showpost.php?p=7148118&postcount=5](http://ubuntuforums.org/showpost.php?p=7148118&postcount=5)

2. Dutch Ubuntu Forum :
[http://forum.ubuntu-nl.org/server-en-netwerk/netwerk-niet-zichtbaar-in-9-04-(wat-te-doen)/](http://forum.ubuntu-nl.org/server-en-netwerk/netwerk-niet-zichtbaar-in-9-04-(wat-te-doen)/)

The information from DenysT was relayed and some adjustments related to IP ranges of router were added.


**_Howto Make your existing Windows Network visible in Ubuntu 9.04 "Network"_**


1. Open a terminal window.
   Applications -> Accessories -> Terminal

2. Type
   sudo gedit /etc/samba/smb.conf

   You will have to enter your password, followed by Enter (no dots are shown)

3  The window Gedit opens the file smb.conf file
   In section [global], search the line
   workgroup = WORKGROUP

   If your own Windows workgroup is named differently, change the line to read

   workgroup = YOUR_WORKGROUPNAME

4. Next scroll down a few lines until you find the line (Note: changed sequence !)
    name resolver order = lmhosts wins bcast host         
   and delete the semicolon at the beginning of the line.
 
5. Save the changes and exit. (Reboot maybe necessary ?)

6. When you next go to Places - > Network
   you should see the network workgroup and   computers attached to it.

7. From there you can open/connect to a computer and see it's shares.

   It's not like XP, where you just have a list of all shares in My Network Places
   but at least you can see them.

8. Finally change some lines to fit the IP range used by your router.
This must be something like 192.168.0.xxx or **192.168.1.**xxx (in following example)
   

   hosts allow = 127.**192.168.1.**
   interfaces = 127.0.0.1/8 **192.168.1**.0/24    [COLOR="Red"](correct syntax ?)[/COLOR]
   bind interfaces only = yes

   remote announce = 192.168.1.255      [COLOR="red"]     (did not find this line ; reason to be added ?)[/COLOR]
   remote browse sync = 192.168.1.255      [COLOR="red"]     (did not find this line ; reason to be added ?)[/COLOR]
============================================================

---

### Post by adonet on 2009-05-11
> **Hariharakadan said:**
> Hello, after bouncing around many websites and forums I managed to find a winning combination to get Windows sharing with Vista to work.

[http://paste.ubuntu.com/168069/](http://paste.ubuntu.com/168069/)

Most of the information was obtained from this forum. 

[http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/](http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/)

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Also on the Vista machines make sure to enable everything that involves sharing including password sharing. I had trouble with one machine and after I turned on password sharing it was viewable. I hope this helps someone else.

-Edit I forgot to add this. This was on 9.04 Ubuntu. I reinstalled it after thinking I did something to foobar the network viewing function in Nautilus but that wasn't the case. After reinstalling it still didn't work. Failed to mount / failed to retrieve share list was the errors it would spit out.

These sites seem to be a bit outdated. And they didn't solve my problem yet. It doesn't seem that the samba configuration is part of the problem. With exact the same configuration Intrepid and Hardy are doing well.
Till now Jaunty isn't great. It doesn't see shares and it doesn't print to networkprinters.

---

### Post by Hariharakadan on 2009-05-11
I am sorry to hear that. Mine just stopped working again after I installed Firestarter. Can't see any shares or anything. Enabled Ports 137-138 for Samba. It seems very touché.

---

### Post by harryscode on 2009-05-20
It's works fine for me. Thanks for the tip

---

### Post by solonvip on 2009-05-22
Yes!!!! Prefect.. thanks a lot, it works perfect..

---

### Post by ftinius on 2009-05-22
Thanks works for 8.10 also, was having the same problem could see the servers but not the shared folders.

---

### Post by adonet on 2009-05-23
Could someone please explain exactly the steps to be done to get network printing and filesharing working again? All I read in this forum didn't work for me.
I would like to give it a last try before switching to another disto.

thanks in advance.

Jeroen

---

### Post by mannequin on 2009-05-25
For people that are having problems with winbind + amsn:
[http://www.amsn-project.net/forums/viewtopic.php?t=6343&highlight=amsn+winbind]("http://http://www.amsn-project.net/forums/viewtopic.php?t=6343&highlight=amsn+winbind")
[http://www.amsn-project.net/forums/viewtopic.php?t=6452&highlight=amsn+winbind]("http://http://www.amsn-project.net/forums/viewtopic.php?t=6452&highlight=amsn+winbind")

It looks like it's an issue with libnss_wins.so (which is part of winbind) that is causing a problem with aMsn.  It doesn't look like the guys at aMsn are going to try to fix it (if they can) on their end.

---

### Post by dredded on 2009-05-25
I got it working for mine, just edited the line in my smb.conf and it worked like a charm. I had been struggling with this for days and now I am so ecstatic, all the time in the past I have used smb4k and it always worked before. For whatever reason that I have not found or been told about it was not working on this version 9.04 now I can browse all the files on my Win box share files with no extra apps.

Thanx to all,

this community is the best! :D

---

### Post by conorturton on 2009-05-28
> **mgmiller said:**
> 
Here is how I fixed it.  It worked on every machine I own.  I did not need to install any packages beyond the default install.

```
gksu gedit /etc/samba/smb.conf
```Scroll down to:
# What naming service and in what order should we use to resolve host names
# to IP addresses

and change the entry from:
```
; name resolve order = lmhosts host wins bcast
```to this:
```
name resolve order = lmhosts wins bcast host
```Notice, I removed the ; from the front of the line as well as changed the order of the items.

Log off and and back on.  (Maybe restart if that does not do it).

The Places > Network gui will now work as expected.

I suspect that your fix works on a similar vein to mine by ensuring 'wins' is in the protocols and also upping its priority in the order of protocols. Yours if it works for people is likely to be better than mine as it is truly system wide whereas mine, due to being in the nsswitch.conf file, is basically Gnome/GDM specific.

Either way, I'm happy. Not being able to browse Windows networks the same as in 7.10 was a dealbreaker for me. Now if only I could get the performance back on my lappy's Intel 945 graphics... :)

---

### Post by dmizer on 2009-05-28
For reasons I mention here: [http://ubuntuforums.org/showpost.php?p=7364005&postcount=38](http://ubuntuforums.org/showpost.php?p=7364005&postcount=38), this:

> **conorturton said:**
> hosts: files wins mdns4_minimal [NOTFOUND=return] dns mdns4

Should be this:
```
hosts: files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

---

### Post by talynpower on 2009-05-29
Thanks. This is a godsend!!!!!

---

### Post by amadeus266 on 2009-05-29
Following this thread got me able to see the other computers on the network and browsing the shares on my Win2K3 DC (I'm using Active Directory for authentication) but I still cannot browse the shares on the WinXP computers nor can any computers on the network see this machine. What might I be missing?

My smb.conf...
```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	name resolve order = lmhosts wins bcast host
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	wins server = 192.168.2.100
	guest ok = yes
	map to guest = bad user
	null passwords = yes
	winbind trusted domains only = yes
;	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = yosemite3
	unix password sync = yes
	workgroup = IBMUSIK
;	os level = 20
	syslog = 0
	security = domain
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host names
# to IP addresses

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
;	guest account = nobody
	password server = 192.168.2.100
	realm = IBMUSIK 	#[global]

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = yes
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Public]
	comment = Adam's Public Files
	path = /home/IBMUSIK/adam/Public
	writeable = yes
;	browseable = yes
	guest ok = yes
```

My nsswitch.conf...
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat lwidentity
group:          compat lwidentity
shadow:         compat
hosts:          files wins dns mdns4_minimal [NOTFOUND=return] mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

edit: dmizer, I tried your suggestion but it caused me to lose internet.

---

### Post by dmizer on 2009-05-29
> **amadeus266 said:**
> edit: dmizer, I tried your suggestion but it caused me to lose internet.

Most likely, that's because you're connected to a DC. This is not a common configuration.

I suggest that you take a look at the 6th link in my sig. If you are still having problems, please post and I'll be more than happy to help. Though, I admit I do not have much experience with AD.

---

### Post by amadeus266 on 2009-05-29
I read the thread you pointed to an d changed my nsswitch.conf to your recommendation and I still have internet (albeit a little slower). 
Here is the output from iptables
```
sudo iptables -L

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.0/24       anywhere            tcp dpt:loc-srv 
ACCEPT     tcp  --  192.168.2.0/24       anywhere            tcp dpt:netbios-ns 
ACCEPT     tcp  --  192.168.2.0/24       anywhere            tcp dpt:netbios-dgm 
ACCEPT     tcp  --  192.168.2.0/24       anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  192.168.2.0/24       anywhere            tcp dpt:microsoft-ds 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
administrator@yosemite3:~$ 

```

---

### Post by dmizer on 2009-05-29
That's some special routing you have going on there. Are you running your box as a gateway? I'm terrible with UFW and IPtables :( Unless you need it, I would suggest disabling it but that may not be the best advice.

---

### Post by amadeus266 on 2009-05-29
Personally, I couldn't make heads or tails of the output. I think it was all auto-generated. I do need the firewall on due to the fact that this is for a small business that runs credit cards and therefor MUST be compliant with PCI DSS (Payment Card Industry Data Security Standards) which is why I am using AD for authentication. I am considering downgrading to Hardy (8.04) for the LTS and working network browsing. Although I believe that the same problem exists on my laptop with 8.04. The machine I am working on is going to be my proof-of-concept to do away with Windows XP.

---

### Post by amadeus266 on 2009-05-29
UPDATE: I just used webmin to reset the firewall to basic configuration and now it works. I can now browse the shares on the Winxp computers as well as the server. I can see this computer from a WinXP computer but still cannot browse any shares. I have a printer share and a Public folder share set up. On the WinXP machine, when I try to browse this computers shares I get "Trust relationship between this workstation and the primary domain failed." I can browse all other computers from that workstation.

EDIT: I fixed the relationship problem by dropping the samba security level from "domain" to "user". Thanks dmizer for your help.

---

### Post by amadeus266 on 2009-05-29
Well, it was working perfectly until I rebooted the machine. At that point, I could no longer browse the network.

---

### Post by Visserys on 2009-08-05
This fix worked great. I worked for my Ubuntu 9.04 install and My Linux Mint 7. Anyone having issues accessing their Windows shares from Linux should absolutely try this.

---

### Post by dmizer on 2009-08-05
> **amadeus266 said:**
> Well, it was working perfectly until I rebooted the machine. At that point, I could no longer browse the network.

I don't think I can help you much more than this. I suggest opening a new thread detailing your problems and what you've done so far. Someone with more AD experience than I should be able to help you.

---

### Post by Ecomonist on 2009-08-07
Thanks a lot, i have tried everything and nothing worked. This did it!

---

### Post by Visserys on 2009-08-10
post deleted

---

### Post by krucifux on 2009-08-10
Thanks, this fixed my problem in 8.10.

---

### Post by 9squirrels on 2009-09-05
Well, I've made the changes as suggested by various users above, updated nsswitch.conf, installed Samba, set the preferences, change the network name to match my windows network name and edited the smb.conf file.  At a couple of points in the process I seemed to be making headway.  At one point I could see the icon for my windows network (after installing Samba, but before changing any default settings), but still got the "Unable to retrieve..." message when clicking on it.  After a restart I couldn't see the network anymore.  After editing the smb.conf file and logging off and on again, I could see the network, and also my windows XP machine, but not the shares on that machine "Unable to retrieve..." again.  I restarted the Ubuntu machine again, and once again I can't see the network at all.  This is really frustrating.
I'm really new to Ubuntu, and Linux in general having literally installed it for the first time 4 days ago.  Is it always this difficult?
Is this particular part of Ubuntu broken?
Does anyone have any further suggestions?

---

### Post by mgmiller on 2009-09-05
>  Is it always this difficult?
Is this particular part of Ubuntu broken?
Does anyone have any further suggestions?

No, it's not normally this difficult.  Normally, you just click on Places > Network and away you go.

The only thing that ever messed things up for me was when my ISP started using DNS redirection and the edit for etc/samba/smb.conf where you change the resolve order and remove the leading semicolon [;] fixes that easily.

Try looking in this thread and see if you can get any more suggestions:
[http://ubuntuforums.org/showthread.php?p=7903963#post7903963](http://ubuntuforums.org/showthread.php?p=7903963#post7903963)

---

### Post by 9squirrels on 2009-09-07
Thanks, I might have a try at reading that tonight.  I also found this
[http://ubuntuforums.org/showthread.php?t=1155625&highlight=windows+network](http://ubuntuforums.org/showthread.php?t=1155625&highlight=windows+network)

which looks like it might be a reasonably simple way forward, though I might have to update my PC to fix the IP address.

I have to say, Ubuntu looks and feels really nice, but installing things seems to either just happen, or require command line input.  On the plus side though, I've had one install fail, but then tell me EXACTLY how to fix it (and it worked), and the forums seem to contain an awful lot of help and helpful people.
Cheers

---

### Post by dmizer on 2009-09-08
> **9squirrels said:**
> I have to say, Ubuntu looks and feels really nice, but installing things seems to either just happen, or require command line input.  On the plus side though, I've had one install fail, but then tell me EXACTLY how to fix it (and it worked), and the forums seem to contain an awful lot of help and helpful people.
Cheers

If that doesn't work, just take a look at the 6th link in my sig.

Also, keep in mind that just because directions are given with command line input, doesn't mean that there isn't a click and go method. It's just easer for people giving you support to give it via command line because all you have to do is copy-paste and we only have to give directions once. Otherwise we'd have to write at least 3 different tutorials. One for Ubuntu (Gnome), one for Kubuntu (KDE), and one for Xubuntu (XFCE4) including gobs of screen shots for each. And then, it would only work if your desktop is left in the default configuration.

---

### Post by mehoo on 2009-09-29
[conorturton]("http://ubuntuforums.org/member.php?u=489149") You just ended a 4hour search for why this suddenly started plagueing me after a fresh install. The old system had been updated from the 8.10 or 8.04 dont' remeber and lost the ability to see my other computers when freshly installed thanks a million

---

### Post by Iowan on 2009-09-29
**mehoo**:
Which tip(s) solved your problem?

---

### Post by jason10 on 2010-09-14
awesome.  thanks

---

