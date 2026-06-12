---
title: "unable to mount location failed to retrieve list from server"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by mcglnx on 2011-05-07
All,

After upgrade to 11.04 I have no way to access SMB shared drives using Nautilus.

When I click on "Network / Windows Network" I have the message: "unable to mount location failed to retrieve list from server"

Couple of remarks:
[LIST]
[*]This is a regression
[*]It's not only a "Windows" network - this label has to be renamed
[*]The messge does not help the average user at all - this is a geeky way of communicating with the end-user
[/LIST]

---

### Post by filosofic on 2011-05-17
Got the same problem here... upgraded to 11.04 and Samba shares no longer accessible.  Same error messages.

---

### Post by CyrusCT on 2011-05-22
I have this problem too.  I am experiencing it on a 32-bit install of  maverick that was upgraded to natty, a 32-bit install of natty that was  installed during the beta 2 period, a 32-bit install of natty, and a 64  bit install of natty.  All four systems have the current set of updates  installed.  I have not experienced this problem with these systems in  the past using maverick, lucid, karmic, jaunty, intrepid, hardy, or  gutsy.

I can access the computers and their shares using their IP addresses.  

To  see the IP address of a computer runing windows, you can go to the  command prompt (run "cmd") and use the command "ipconfig" to find the IP  address.

To see the IP address of a computer running Ubuntu, open the terminal and enter "ifconfig"

Unfortunately,  most computers get their IP addresses dynamically by DHCP, and portable  computers and devices often need to do this if they participate in  multiple networks, so this is at best a temporary work-around.

---

### Post by Morbius1 on 2011-05-22
> Unfortunately,  most computers get their IP addresses dynamically by  DHCP, and portable  computers and devices often need to do this if they  participate in  multiple networks, so this is at best a temporary  work-around.See if your router has a function called "DHCP Reservation". It can go by many other names but it allows the router to assign the same ip address to a specific machine based on the physical address of the network adapter ( MAC Address ) . That address never changes. This way all the machines can still have their default dhcp client setup and have static ip address at the same time.

Worth investigating.

---

### Post by CyrusCT on 2011-05-22
Thanks Morbius1.

That is definitely the preferred method for networks where the DHCP server can be configured.  It prevents the need to reconfigure each computer on the network, and I have been using this method with the networks that I administer (temporarily until I can get samba working properly).

I still consider accessing samba shares by IP address a temporary workaround, because this method is often not practical for connecting a personal computer to a corporate network.

---

### Post by capscrew on 2011-05-22
> **mcglnx said:**
> All,

After upgrade to 11.04 I have no way to access SMB shared drives using Nautilus.

When I click on "Network / Windows Network" I have the message: "unable to mount location failed to retrieve list from server"

Couple of remarks:
[LIST]
[*]This is a regression
[*]It's not only a "Windows" network - this label has to be renamed
[*]The messge does not help the average user at all - this is a geeky way of communicating with the end-user
[/LIST]

**A regression to what?**  There are several bugs but no regression. I would check to see if you have nameservices running.  This can easaly be checked like this```
ps -ef|grep mbd
```

You should get something like this```
root       934     1  0 15:45 ?        00:00:00 smbd -F
root       963     1  0 15:45 ?        00:00:00 **[COLOR="Red"]nmbd[/COLOR]** -D
root       979   934  0 15:45 ?        00:00:00 smbd -F
root      2850   934  0 19:51 ?        00:00:00 smbd -F
bruce     2868  2503  0 19:55 pts/0    00:00:00 grep --color=auto mbd

```

It is a **Windows Style Network** (but that would be too long).  What do you think it should be?  Have you suggested anything to the devs?
[B]
I think the message says a great deal[/B].  If the User doesn't understand then all that is needed is a question to this forum.  What do you think would be the correct message?

To me it says that either:
[LIST=1]
[*]No Browse list was created
[*]The user does not have permission to access the share
[/LIST]

One could diagnose this with ```
smbtree -d3
```

---

### Post by capscrew on 2011-05-22
> **CyrusCT said:**
> Thanks Morbius1.

That is definitely the preferred method for networks where the DHCP server can be configured.  It prevents the need to reconfigure each computer on the network, and I have been using this method with the networks that I administer (temporarily until I can get samba working properly).

Hmmmm.  You always should use non-changing IP addresses with any server, be it Samba (serving files) or Apache (web server) or BIND (DNS server), etc.  What is the workaround in that? > 

I still consider accessing samba shares by IP address a temporary workaround, because this method is often not practical for connecting a personal computer to a corporate network.

Of course it is.  But all you need to do is have proper nameservices available.  If you can connect to the shares by IP address then the Samba server is working.  To use the browsing facility you should have nmbd running and (as the Samba development folks envisioned it) DNS properly running on the LAN.  The nmbd daemon converts DNS hostnames to NetBIOS COMPUTERNAMES.

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823&highlight=atomicben") for more.

---

### Post by CyrusCT on 2011-05-23
capscrew,

I meant that is is the preferred method for making local IP addresses static.  Making the local IP address static, and using the local IP address to access the network shares is the workaround for "**unable to mount location failed to retrieve list from server**."

Assuming that the "-D" means that nmbd is not running, then the questions become:
"What must one do to cause nmbd to start during boot, or after boot?" and
"If we have been using the same procedures to setup Windows compatible networking that we have been using with past versions of Ubuntu, then what was changed to cause nmbd no to run at startup, why was the change implemented, who does it benefit and who do we need to contact to fix it?"

---

### Post by capscrew on 2011-05-23
> **CyrusCT said:**
> capscrew,

I meant that is is the preferred method for making local IP addresses static.  Making the local IP address static, and using the local IP address to access the network shares is the workaround for "**unable to mount location failed to retrieve list from server**."


Two points here.  First, if you get that message and can access the shares with an IP address then you definitely have a nameservices problem and not a permissions problem. 
 
Secondly, I have to gently disagree with you on some finer points of static and reserved IP addressing.  But first some definitions. ```
[COLOR="Green"]**Static**[/COLOR] = IP address is manually configured via files
[COLOR="Purple"]**Reserved**[/COLOR] = IP address configured via DHCP server
**[COLOR="Blue"]Fixed[/COLOR]** = IP address doesn't change 
```
An IP address can be made **[COLOR="Blue"][B]fixed**[/COLOR][/B] in to ways.  This is by **[COLOR="Purple"]reserving[/COLOR]** it or by **[COLOR="Green"]statically[/COLOR]** configuring it.

The benefit configuring statically over reserved is that there are less processes that can go wrong.  You do not have to consider the DHCP server when diagnosing networking problems with a statically assigned IP address.

In my opinion I will always prefer static addressing for hosts that do not move (desktops, routers, dedicated servers) and reserved addressing for those hosts that can move that I am in charge of administering (laptops, tablets, cell phones).  Everything in my network has a fixed address.  Some via DHCP and some not. 
 

> 

Assuming that the "-D" means that nmbd is not running, then the questions become:
"What must one do to cause nmbd to start during boot, or after boot?" 
This assumption is wrong.  The D stands for Daemonized (the process is running all the time as a server)> 

"If we have been using the same procedures to setup Windows compatible networking that we have been using with past versions of Ubuntu, then what was changed to cause nmbd no to run at startup, why was the change implemented, who does it benefit and who do we need to contact to fix it?"

The use of upstart has caused the init scrips to change the method and timing of various processes initializations.  The bug has already been reported.  There are several methods to get around this.  When it happens to me ( and it does) I just restart the nmbd daemon.  But I'm lazy that way. :-)

---

### Post by CyrusCT on 2011-05-29
With additional testing, I have determined the following:
1.)  I do not experience the problem when I start my computer with the network cable attached and leave it attached.
2.)  After starting with the network cable attached, I start to experience the problem if I disconnect the network cable, and use my wireless connection.
3.)  If I start my computer without the network cable attached, I will experience the problem, however, connecting the network cable, disconnecting from the wireless network, then using "sudo restart nmbd" and waiting a few minutes will allow me to see and mount the location, but for only that computer's own network shares.

---

### Post by capscrew on 2011-05-29
> **CyrusCT said:**
> With additional testing, I have determined the following:
1.)  I do not experience the problem when I start my computer with the network cable attached and leave it attached.
As it should be.  :-)> 
2.)  After starting with the network cable attached, I start to experience the problem if I disconnect the network cable, and use my wireless connection.
Is the wireless on a different subnet?  Samba is no way to change its configuration dynamically for subnet changes.  I'll bet once it is bonded to an interface it stays there.> 

3.)  If I start my computer without the network cable attached, I will experience the problem, however, connecting the network cable, disconnecting from the wireless network, then using "sudo restart nmbd" and waiting a few minutes will allow me to see and mount the location, but for only that computer's own network shares.
I'm sure it has never bonded with the wireless connection.  When the wired connection is restored it bonds and you can see the local share. After that it rebuilds the "Master Browse List" in 10 to 15 minutes.

---

### Post by mcglnx on 2011-05-31
On my case I'm using DHCP reservation for the reason mentioned before.
I do not use wireless, I have a cabled network.

The issue still persist.

---

### Post by capscrew on 2011-05-31
> **mcglnx said:**
> On my case I'm using DHCP reservation for the reason mentioned before.

And that reason would be what?  What was mentioned before?> 

I do not use wireless, I have a cabled network.

The issue still persist.

How about re-reading my post #6 and on in this thread.  Without diagnostic information we can't really advise you on what to do.  Telling us *"The issue still persist" * means nothing.

---

### Post by Morbius1 on 2011-05-31
> Originally Posted by **mcglnx **
On my case I'm using DHCP reservation for the reason mentioned before.
> **capscrew said:**
> And that reason would be what?  What was mentioned before?
Um ... that would be me ;) 
> Originally Posted by [B]Morbius1
[/B]See if your router has a function called "DHCP Reservation". It can go  by many other names but it allows the router to assign the same ip  address to a specific machine based on the physical address of the  network adapter ( MAC Address ) . That address never changes. This way  all the machines can still have their default dhcp client setup and have  static ip address at the same time.If he's using DHCP reservation on all his machines he no longer needs to browse to the other machines on his network as he already knows where they are.

Let's say you have a machine named Bob that's at 192.168.0.100. Open up a terminal and type:
```
nautilus smb://192.168.0.100
```Once Nautilus opens up to that ip address bookmark it: Bookmarks > Add bookmark. It will show up on the left side panel of nautilus. You can even rename it to "Bob".

---

### Post by capscrew on 2011-05-31
> **Morbius1 said:**
> Um ... that would be me ;) 
If he's using DHCP reservation on all his machines he no longer needs to browse to the other machines on his network as he already knows where they are.

Let's say you have a machine named Bob that's at 192.168.0.100. Open up a terminal and type:
```
nautilus smb://192.168.0.100
```Once Nautilus opens up to that ip address bookmark it: Bookmarks > Add bookmark. It will show up on the left side panel of nautilus. You can even rename it to "Bob".

Yes that is true.  That is a pragmatic view; one that settles for what you have rather than proper configuration.  The OP can have both.  I never bookmark my shares.  I just browse to them.  All of my desktop and server hosts have static IP addresses.

---

### Post by CyrusCT on 2011-06-01
> **capscrew said:**
> As it should be.  :-)Is the wireless on a different subnet?  Samba is no way to change its configuration dynamically for subnet changes.  I'll bet once it is bonded to an interface it stays there.
I'm sure it has never bonded with the wireless connection.  When the wired connection is restored it bonds and you can see the local share. After that it rebuilds the "Master Browse List" in 10 to 15 minutes.

For my home network, both wired and wireless connections use Mask  255.255.255.0 and the router does not support using a different mask for  wireless.  

I'm not entirely sure what is meant by "bond" in this context and would greatly appreciate a brief explanation.

When I could see the other computers with the wired connection before, those computers had been on overnight.  After a fresh boot, each can only see itself on the network through the wired connection.  Waiting several minutes and refreshing regularly does cause the other computers to appear.  The computers running Ubuntu appeared before the computers running Windows.  Although the computers appear, when I try to open them using their name on the network, it still doesn't work.

That said, in the above, wired circumstance, the computers do not appear in Network, so I must go to Windows Network then WORKGROUP to see sthem, where double-clicking on them to see their shares gives me "Error Failed to retrieve share list from server" followed by "Error The specified location is not mounted."  If I try by specifying the location using either smb://workgroup/[ComputerName]/ or smb://[ComputerName]/ I get "Error: Failed to mount Windows share Please select another viewer and try again." and I can still only see the computer's shares by going to smb://[ComputerIP]/

In the above, wired scenario, "sudo restart nmbd" causes the computers to no longer be visible from within WORKGROUP and WORKGROUP to no longer be visible from within Windows Network.  "sudo restart smbd" does not cause either to re-appear on refresh.

If I don't disconnect my wireless connection, I cannot browse to see these computers.  Apparently, if both connections are active, the wireless one is being used by default. 

With previous versions of Ubuntu, I could go to Places --> Network --> Windows Network --> WORKGROUP --> and see all of the computers on the network right away, with both wired and wireless connections.  Now I have to wait several minutes before this works, and it only works with a wired connection.  With a wireless connection, I get "Unable to mount location Failed to retrieve list from server" as soon as I try to open Windows Network.  I can no longer double-click on the computer name to see the computer's shares with this version of Ubuntu.

---

### Post by capscrew on 2011-06-01
> **CyrusCT said:**
> For my home network, both wired and wireless connections use Mask  255.255.255.0 and the router does not support using a different mask for  wireless.

The question was regarding *[COLOR="Blue"]subnets[/COLOR]* not *[COLOR="Green"]subnet masks[/COLOR]*.  You mentioned that the host in question has both a wireless connection and a wired connection, I wondered whether the IP addresses were in separate networks.  What are the IP addresses of the wired and wireless interfaces?
>  

I'm not entirely sure what is meant by "bond" in this context and would greatly appreciate a brief explanation.

Samba can be configured to connect (bond) with a either an interface (i.e eth0) or a network (ip range (192.168 )) or a specific IP address (i.e 192.168.250.12)> 

When I could see the other computers with the wired connection before, those computers had been on overnight.  After a fresh boot, each can only see itself on the network through the wired connection.  Waiting several minutes and refreshing regularly does cause the other computers to appear.  The computers running Ubuntu appeared before the computers running Windows.  Although the computers appear, when I try to open them using their name on the network, it still doesn't work.

Typically this is a symptom of either a *_lack of nameservices_* (i.e DNS or hosts) or some naming misconfiguration.  Samba is really a suite of applications.  Browsing visually (GUI) is only one part of the suite.  When you browse you are looking for a host by NetBIOS name.  Specifically a SMB resource (e.g. //COMPUTER_NAME/share_name.

Your Ubuntu host has hostname.  This is converted to a NetBIOS name by the daemon (server) *[COLOR="Purple"]nmbd[/COLOR]* and added to the Master Browse List by the Local Master Browser (LMB).  If you not have a LMB or a incomplete Browse List, you will get the error messages that you are receiving.
> 

That said, in the above, wired circumstance, the computers do not appear in Network, so I must go to Windows Network then WORKGROUP to see sthem, where double-clicking on them to see their shares gives me "Error Failed to retrieve share list from server" followed by "Error The specified location is not mounted."  If I try by specifying the location using either smb://workgroup/[ComputerName]/ or smb://[ComputerName]/ I get "Error: Failed to mount Windows share Please select another viewer and try again." and I can still only see the computer's shares by going to smb://[ComputerIP]/

As I said before: Samba is working.  The nameservices is either not working or is misconfigured.

All of this has been mentioned before.  Look again at [**_[COLOR="Blue"]this link[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823&highlight=atomicben") where there was a successful resolution.
> 

In the above, wired scenario, "sudo restart nmbd" causes the computers to no longer be visible from within WORKGROUP and WORKGROUP to no longer be visible from within Windows Network.  "sudo restart smbd" does not cause either to re-appear on refresh.

If I don't disconnect my wireless connection, I cannot browse to see these computers.  Apparently, if both connections are active, the wireless one is being used by default.


Sort of.  This is why I asked the question about the IP addresses for the wired and wireless connections.

You are most likely using Network Manager to handle the connections and I believe it will favor your wireless connection over your wired one.  You can't have both connected at the same time and have them both in the same network.
>  

With previous versions of Ubuntu, I could go to Places --> Network --> Windows Network --> WORKGROUP --> and see all of the computers on the network right away, with both wired and wireless connections.  Now I have to wait several minutes before this works, and it only works with a wired connection.  With a wireless connection, I get "Unable to mount location Failed to retrieve list from server" as soon as I try to open Windows Network.  I can no longer double-click on the computer name to see the computer's shares with this version of Ubuntu.

I feel that this update has revealed some misconfiguration.  Ubuntu has not changed (Not withstanding the new Unity interface).  You need to straighten out the nameservices in your network.  I'm sure you are getting frustrated restating your problem.  I'm sure frustrated restating what is wrong.

So let's start with some network information: we can start with the hostname, the O/S (Natty?) and IP address of 4 hosts in question. 

For of each host provide the output of following commands```

uname -a
cat /etc/hostname
cat /etc/hosts
cat /etc/network/interfaces 

```

[LIST]
[*]Are all of the hosts Samba [COLOR="Magenta"]***servers***[/COLOR]?  
[*]Are all the hosts Samba [COLOR="DarkSlateGray"]***clients***[/COLOR]?
[*]Are all of the smb.conf files for the servers the same except for the shares that are defined? 
[*]How did you define the shares on each host? (Note: If you have shares on a host then it is by definition a Samba server)
[/LIST]

---

### Post by CyrusCT on 2011-06-02
> **capscrew said:**
> The question was regarding *[COLOR=Blue]subnets[/COLOR]* not *[COLOR=Green]subnet masks[/COLOR]*.  You mentioned that the host in question has both a wireless connection and a wired connection, I wondered whether the IP addresses were in separate networks.  What are the IP addresses of the wired and wireless interfaces?
Samba can be configured to connect (bond) with a either an interface (i.e eth0) or a network (ip range (192.168 )) or a specific IP address (i.e 192.168.250.12)
Typically this is a symptom of either a *_lack of nameservices_* (i.e DNS or hosts) or some naming misconfiguration.  Samba is really a suite of applications.  Browsing visually (GUI) is only one part of the suite.  When you browse you are looking for a host by NetBIOS name.  Specifically a SMB resource (e.g. //COMPUTER_NAME/share_name.

Your Ubuntu host has hostname.  This is converted to a NetBIOS name by the daemon (server) *[COLOR=Purple]nmbd[/COLOR]* and added to the Master Browse List by the Local Master Browser (LMB).  If you not have a LMB or a incomplete Browse List, you will get the error messages that you are receiving.
As I said before: Samba is working.  The nameservices is either not working or is misconfigured.

All of this has been mentioned before.  Look again at [**_[COLOR=Blue]this link[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823&highlight=atomicben") where there was a successful resolution.


Sort of.  This is why I asked the question about the IP addresses for the wired and wireless connections.

You are most likely using Network Manager to handle the connections and I believe it will favor your wireless connection over your wired one.  You can't have both connected at the same time and have them both in the same network.


I feel that this update has revealed some misconfiguration.  Ubuntu has not changed (Not withstanding the new Unity interface).  You need to straighten out the nameservices in your network.  I'm sure you are getting frustrated restating your problem.  I'm sure frustrated restating what is wrong.

So let's start with some network information: we can start with the hostname, the O/S (Natty?) and IP address of 4 hosts in question. 

For of each host provide the output of following commands```

uname -a
cat /etc/hostname
cat /etc/hosts
cat /etc/network/interfaces 

```
[LIST]
[*]Are all of the hosts Samba [COLOR=Magenta]***servers***[/COLOR]?
[*]Are all the hosts Samba [COLOR=DarkSlateGray]***clients***[/COLOR]?
[*]Are all of the smb.conf files for the servers the same except for the shares that are defined?
[*]How did you define the shares on each host? (Note: If you have shares on a host then it is by definition a Samba server)
[/LIST]


I don't know where in smb.conf to check for the bonding methodology, and it's not something I know how to configure, so it should be whatever the default is.
For my home network, the DCHP server in my TEW-631BRP assigns addresses in the 192.168.1.x range of addresses.  After a reboot, if the network cable is connected to a computer running Ubuntu, that computer will, according to my router, have two IP addresses, one which corresponds to the MAC address of the computer's wireless adapter, and another which corresponds to its wired adapter.  Furthermore, I can access this computer's shares using either/both of it's IP addresses.  These are laptops/tables, so presumable they use the same adapter for both wireless and wired connections. 

From a default install of Natty, I have done the following:
Installed samba and winbind with Synaptic
Edited smb.conf as follows:

added to [global] below workgroup:
client lanman auth = Yes
   wins support = yes

under ####### Authentication ####### added:
   security = share
guest account = cyrusct

At the end added:
[NetShare]
path = /home/cyrusct/Desktop/NetShare
available = yes
browsable = yes
public = yes
writable = yes
force user = cyrusct
only guest = yes
force group = cyrusct
create mask = 0775
directory mask = 0775
guest ok = yes
read only = no

Other than the above edits, everything networking related is default for my Ubuntu installations, with the exception that there are different folders being shared on other computers.  

All of the edits above were done to create a share, fix problems with permissions of local but remotely created files/folders, and set "security = share" to resolve username and password issues with folders shared by Windows XP that do not use either.

Other than restarting nmbd, I don't know how to configure the nameservices, so those settings should also be the defaults.

I beg to differ about Ubuntu not having changed.  Using the same network configuration process for Natty that I have used for previous versions of Ubuntu, is no longer sufficient to be able to access shares by computer name now that I am using Natty.

Using
sudo apt-get purge winbind
sudo service smbd restart
sudo service nmbd restart
has not resolved the problem for me, and I don't know what else I am supposed to get from the other post.

Rather than post the output of the commands for each of the computers, let's start with one of them and only worry about it being able to access the shares on a computer running Windows XP for the time being.  (The computers on my home network running Windows XP can access shares on the computers running Ubuntu using their names, irrespective of how the computers are connected to the network).

The computer I will start with is a 32-bit Ubuntu system with a Natty installation done by Wubi (because I don't have permission to repartition that machine).

cyrusct$ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
cyrusct$ubuntu:~$ cat /etc/hostname
ubuntu
cyrusct$ubuntu:~$ cat /etc/hosts
127.0.0.1          localhost
127.0.1.1          ubuntu.ubuntu-domain     ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localhost
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
cyrusct$ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet


Thanks for all of your patience and all of your help.

---

### Post by capscrew on 2011-06-02
> **CyrusCT said:**
> I don't know ...

:-)> 
...
I beg to differ about Ubuntu not having changed.  Using the same network configuration process for Natty that I have used for previous versions of Ubuntu, is no longer sufficient to be able to access shares by computer name now that I am using Natty.

Hmmmmmmm...> 
...
Rather than post the output of the commands for each of the computers, let's start with one of them and only worry about it being able to access the shares on a computer running Windows XP for the time being.  (The computers on my home network running Windows XP can access shares on the computers running Ubuntu using their names, irrespective of how the computers are connected to the network).

The computer I will start with is a 32-bit Ubuntu system with a Natty installation done by Wubi (because I don't have permission to repartition that machine).


I really don't want to get into a discussion of whether Ubuntu has changed in some fundamental way or not.  Flat out: ***There is no change in the way Natty handles Samba from the way Lucid or Hardy does***.

Attached you will find a screen shot of a LiveCD 11.04 host running on my Sony Vaio laptop.  I have done **No Samba Configuration** on this host.  Note that it shows a folder from my Samba server (MALIBU) and the share called ISO.  It is actually looking at the iso and md5 file I used to burn the LiveCD running this host.  In the terminal I have queried the server to display all its shares.  In fact I moved the JPG to my Ubuntu desktop (10.04LTS) via Samba.

I asked for data so I could make a suggestions for your benefit.  You have decided you know better and want do do something else.  If you ask for help you need to accept it.  Anything else is doomed to failure.

Let me know what you want to do.

---

### Post by mcglnx on 2011-06-03
> **capscrew said:**
> Telling us *"The issue still persist" * means nothing.
Thanks to be kind with beginner users :)

---

### Post by mcglnx on 2011-06-03
> **capscrew said:**
> **A regression to what?**
Regression of the SMB connectivite. Before it was working, after update to 11.04 it does not work anymore - THIS is a regression.

---

### Post by capscrew on 2011-06-03
> **mcglnx said:**
> Thanks to be kind with beginner users :)

Kind or not; how do you would you diagnose a problem with no specific information?

---

### Post by capscrew on 2011-06-03
> **mcglnx said:**
> Regression of the SMB connectivite. Before it was working, after update to 11.04 it does not work anymore - THIS is a regression.

That's not a definition of regression.  See post #19 of this thread.  I'll bet you have misconfigured your system.  Regression does not account for misconfiguration.

---

### Post by CyrusCT on 2011-06-03
> **capscrew said:**
> :-)Hmmmmmmm...

I really don't want to get into a discussion of whether Ubuntu has changed in some fundamental way or not.  Flat out: ***There is no change in the way Natty handles Samba from the way Lucid or Hardy does***.

Attached you will find a screen shot of a LiveCD 11.04 host running on my Sony Vaio laptop.  I have done **No Samba Configuration** on this host.  Note that it shows a folder from my Samba server (MALIBU) and the share called ISO.  It is actually looking at the iso and md5 file I used to burn the LiveCD running this host.  In the terminal I have queried the server to display all its shares.  In fact I moved the JPG to my Ubuntu desktop (10.04LTS) via Samba.

I asked for data so I could make a suggestions for your benefit.  You have decided you know better and want do do something else.  If you ask for help you need to accept it.  Anything else is doomed to failure.

Let me know what you want to do.

I would like to continue.  Either by re-configuring the existing computers, or identifying the steps needed to configure a live CD (I could not duplicate your success with a live CD).

I did not provide the contents of the commands for the other computers and wanted to work toward getting it to work with just the computer running Windows because:
1. I am very risk averse, when it comes to posting information about my home network
2. I thought it would be faster and easier to work with a representative subset of the computers on my home network
3. I wanted to include a computer running Windows, because not all members of the household use Linux
4. I wanted to slow down and try to configure one computer at a time instead of all at once

For another computer on my home network, I have:
cyrusct@Inspiron1420n:~$ uname -a
Linux Inspiron1420n 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
cyrusct@Inspiron1420n:~$ cat /etc/hostname
Inspiron1420n
cyrusct@Inspiron1420n:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    Inspiron1420n

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
cyrusct@Inspiron1420n:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

cyrusct@Inspiron1420n:~$ 

The systems you are missing the commands for are as follows:
1.  Computers on the home network running Windows
2.  A computer that should be identical to the one I first provided the commands for, except for username and hardware ID
3.  Non-computer network devices such as printers, cell phones and e-readers
4.  The Ubuntu installation on one of the computer that has dual boot with Windows XP, where Ubuntu is present but unused because of driver compatibility issues with antiquated hardware

If you still need the output of the commands for any of the above systems, then let me know and I will provide it.

I could not duplicate the success shown in your screenshot using a live cd.  I have attached a screenshot showing the results of:
1. start computer from live USB (because it has no CD drive), with network cable connected
2. join wireless network
3. install samba (from synaptic) and close synaptic
4. Attempt to find a network share using Nautilus (Could not open workgroup)
5. Adjust the font size for terminal to fit two on the screen
6. In each terminal, run smbclient for a computer's name to show how it fails
7. In each terminal, run smbclient for a computer's IP address to show how it works
8. Repeat steps 6 & 7 after waiting fifteen minutes.

From the live USB, do you know of anything I did that I should not have done, or anything that I didn't do but should have done?

As far as I know the misconfiguration that you mention must be part of the pre-configuration and/or default configuration since I have not changed what I have been doing to configure the computers.  While I don't know to what extent the programs have or have not changed from previous versions of Ubuntu, I do know that I can no longer access network shares using a computers name, even though I am using the same methodology for the part of the configuration which I perform.  I apologize for being unable to comprehend how doing the same thing but getting different results does not indicate a change.

---

### Post by capscrew on 2011-06-04
> **CyrusCT said:**
> I would like to continue.

Great.> 

Either by re-configuring the existing computers, or identifying the steps needed to configure a live CD (I could not duplicate your success with a live CD).

I did not provide the contents of the commands for the other computers and wanted to work toward getting it to work with just the computer running Windows because:
1. I am very risk averse, when it comes to posting information about my home network
2. I thought it would be faster and easier to work with a representative subset of the computers on my home network
3. I wanted to include a computer running Windows, because not all members of the household use Linux
4. I wanted to slow down and try to configure one computer at a time instead of all at once

I can understand your reluctance to divulge *personal* Information. Let me assure you that no information that I asked for is unique to your network other than the *hostnames* you have given your computers.  The reason I asked for information on all hosts is to check for errors across all hosts in the network.

Windows hosts do not need any configuration to work with Samba.  We will not change their configuration (unless their COMPUTER NAMES (NetBIOS names) are longer than 15 characters.  My guess is that you can't do that anyway as Windows won't allow you to enter more than the max of 15 characters.

Ultimately we will configure 1 host at a time, but an overview of the entire network is needed.
>    

...

The systems you are missing the commands for are as follows:
1. Computers on the home network running Windows
2. A *[COLOR="Red"]computer that should be identical[/COLOR]* to the one I first provided the commands for, except for username and hardware ID
3. Non-computer network devices such as printers, cell phones and e-readers
4. The Ubuntu installation on one of the computer that has dual boot with Windows XP, where Ubuntu is present but unused because of driver compatibility issues with antiquated hardware

If you still need the output of the commands for any of the above systems, then let me know and I will provide it.

No computer (host) should have an identical hostname or be assigned the same IP address.  Those need to be  unique in the network.> 

I could not duplicate the success shown in your screenshot using a live cd. &#8230;

From the live USB, do you know of anything I did that I should not have done, or anything that I didn't do but should have done?
Yes.  That's what I have been trying to tell you.  You need to configure LAN side name services before Samba will work.> 

As far as I know the misconfiguration that you mention must be part of the pre-configuration and/or default configuration &#8230;

The *misconfiguration*, if you want to call it that, is that **Name Services** (DNS (hosts)) need configuration before you can have success with Samba.  This has always been the case.

Let me state that again: We need to configure local LAN DNS on any Ubuntu host on your network as a prerequisite to configuring Samba itself.  There are other ways to provide name services, but using LAN DNS means that there is almost no configuration (modification) needed to the /etc/samba/smb.conf file.  This means that the smb.conf file will work even if the O/S is updated.

It would be helpful to have some common terminology
[LIST]
[*]Host = A running instance of an O/S (hosting applications)
[*]Server = A process running that is ready to service requests (Samba, DHCP, DNS, etc.)
[*]Client = Any requester of services provided by a server (smbclient)
[*]hostname = The name applied to a running O/S (Linux/UNIX) configured via /etc/hostname
[*]COMPUTER NAME = The name applied to a running O/S (Windows) AKA NetBIOS Name
[*]hosts = A Linux/UNIX method of mapping IP addresses to hostnames in the LAN
[*]DNS = A method of combining hostnames with domain names to provide a FQDN (i.e hostname.domainname.suffix)
[*]DHCP server = A server that supplies IP addresses (and other info) to a host requesting an IP address.
[*]Reserved IP = a method of supplying a fixed (immutable) IP address via a DHCP server
[*]Static IP = a manually configured IP address that is fixed via /etc/network/interfaces file
[/LIST]
Samba expects each Ubuntu host to be able to identify itself by name for successful browsing.  We have a couple of options.  If you want to use DHCP services in your router, then the router needs to be able to supply the hostname of your choice when it supplies the IP address in the DHCP exchange.  If it is not able to do that we will need to use an IP addressing scheme that uses *non-changing* IP addresses via DHCP reservation or manual configuration and add the hostname to IP mapping in the /etc/hosts file.

This is the main difference between my use of the LiveCD and your results of the same LiveCD.  My network has LAN side DNS resolution.  Samba used those names (hostnames) to build the **Browse List**.  This is the list referred to in *"failed to retrieve list from server"*

The screen shot I created was using an unmodified LiveCD that I downloaded, burned and used in my Sony Vaio that normally runs Windows Vista.

First order of business is to find out if your router can handle the LAN side DNS duties while using DHCP.  Do you know how to do that?  Do you have the manual for your router?

[COLOR="Blue"]**Edit:** I have found on-line what I believe is your router manual.  You can reserve a specific IP address and provide a hostname for each Ubuntu host.  This appears to be pretty easy to do.  Have you visited your router's admin page?[/COLOR]

---

### Post by CyrusCT on 2011-06-04
Thank you! Thank you! Thank you!

I did not know that the DNS settings for the network hardware were in  the scope of what you were talking about when you were mentioning name  services.  I wasn't thinking outside the box (or in this case inside the  correct box).  I changed the DNS servers and now things are working  correctly again.  

Apparently, the Secure DNS servers I had been using (since 2009) are not  as Ubuntu friendly as they used to be, so the company will be hearing  from me.

---

### Post by Morbius1 on 2011-06-04
Now that's interesting.

Both capscrew and I suggested "DHCP Reservation" to assign what is in affect static ip address to each of the machines in your LAN. The only difference with our two approaches is how the user wants to connect to the remote share: Booksmarks vs browse ( /etc/hosts ).

There is no indication that the router uses LAN side dns resolution. The Users Maunual states under the "Add/Edit DHCP Reservation" section:
> Computer Name
You can assign a name for each computer that is given a reserved IP address. This may help you keep track of which computers are assigned this way. Example: Game Server.This sounds like bookkeeping not LAN side dns resolution.

But unless I'm reading far more into your last post than is acutally there what you did is something else entirely. You changed the DNS server itself.

Here's my theory. Some ISP's use DNS Redirection within their DNS servers: From [http://en.wikipedia.org/wiki/DNS_hijacking](http://en.wikipedia.org/wiki/DNS_hijacking)
> If one were to query the invalid domain name (fakeexample.com), one should get a NXDOMAIN response - informing the application that the name is invalid and taking the appropriate action (for example, displaying an error or not attempting to connect to the server). However, if the domain name is queried on one of these non-compliant ISPs, one would always receive a fake IP address belonging to the ISP. In a Web browser, this behavior can be annoying or offensive as connections to this IP address display the ISP redirect page of the provider, sometimes with advertising, instead of a proper error message. However, other applications that rely on the NXDOMAIN error will instead attempt to initiate connections to this spoofed IP address, potentially exposing sensitive information.
What I have been suggesting to folks with this type of problem was to change the order of name resolution and put the default method first in smb.conf:
```
name resolve order = bcast host lmhosts wins
```I wasn't the first to suggest this BTW: About the Name Resolve Order: [http://opensuse.swerdna.org/susesambabrowse.html](http://opensuse.swerdna.org/susesambabrowse.html)
> The reason many if not most openSUSE Samba users initially have difficulty seeing servers on their Samba LAN is that this order operates by default and the first three options are simply not configured initially for Samba. Only bcast is useful when Samba is initially installed, and since it is placed last, browsing with openSUSE's default Samba installation can be very flaky.

If nothing else is done to the default Samba installation, it should at least have the name resolve order set with bcast first. I think the default mechanism send the samba client off to the DNS servers in some circumstances and it basically gets caught in this conundrum. By setting bcast first the only thing required of the browser at that point is to not block bcast within the LAN.

---

### Post by capscrew on 2011-06-04
> **CyrusCT said:**
> Thank you! Thank you! Thank you!

I did not know that the DNS settings for the network hardware were in  the scope of what you were talking about when you were mentioning name  services.  I wasn't thinking outside the box (or in this case inside the  correct box).  I changed the DNS servers and now things are working  correctly again.  

Apparently, the Secure DNS servers I had been using (since 2009) are not  as Ubuntu friendly as they used to be, so the company will be hearing  from me.

I mentioned DNS when I stated nameservices (i.e *"...Name Services (DNS (hosts)) need configuration "* and *...configure local LAN DNS"*).

LAN side DNS is not Internet side DNS.  I was referring to DNS resolution for your network, not resolving DNS for web sites you might visit on the Internet.

But...If your happy then I'm happy!  :-)

> **Morbius1 said:**
> Now that's interesting.

Both capscrew and I suggested "DHCP Reservation" to assign what is in affect static ip address to each of the machines in your LAN. The only difference with our two approaches is how the user wants to connect to the remote share: Booksmarks vs browse ( /etc/hosts ).

There is no indication that the router uses LAN side dns resolution. The Users Maunual states under the "Add/Edit DHCP Reservation" section:
This sounds like bookkeeping not LAN side dns resolution.

But unless I'm reading far more into your last post than is acutally there what you did is something else entirely. You changed the DNS server itself.

Here's my theory. Some ISP's use DNS Redirection within their DNS servers: From [http://en.wikipedia.org/wiki/DNS_hijacking](http://en.wikipedia.org/wiki/DNS_hijacking)
What I have been suggesting to folks with this type of problem was to change the order of name resolution and put the default method first in smb.conf:
```
name resolve order = bcast host lmhosts wins
```I wasn't the first to suggest this BTW: About the Name Resolve Order: [http://opensuse.swerdna.org/susesambabrowse.html](http://opensuse.swerdna.org/susesambabrowse.html)
 I think the default mechanism send the samba client off to the DNS servers in some circumstances and it basically gets caught in this conundrum. By setting bcast first the only thing required of the browser at that point is to not block bcast within the LAN.
My feelings are: In a network with properly configured local DNS server, Samba needs no modification of the smb.conf to the resolve order parameter.  In fact the only parameters that need configuration are those needed for the share definitions.  

The WORKGROUP is a nice touch to integrate Samba into other systems shares, but it is not absolutely needed.

I configured nothing in the smb.conf file when I browsed the shares in my network using the LiveCD.  I just booted the LiveCD and browsed to the shares.

---

### Post by CyrusCT on 2011-06-04
It sounds like where I went that fixed the problem wasn't where you were trying to lead me, and that it shouldn't have fixed the problem.  That said, without your help, I wouldn't have got there, and it's working now, so I'm very happy.

I changed the Internet DNS because I am using DNS relay.  Simply  un-checking the box for DNS relay did not resolve the problem for me,  and while the router's documentation mentioned turning off DNS relay in  conjunction with setting up a virtual server for DNS, I could not find the documentation I would have needed for how to setup the virtual server for that purpose.  I  did not find other DNS configuration options while poking around in the  router's configuration pages, but I stopped looking as soon as things started working.

---

### Post by capscrew on 2011-06-04
> **CyrusCT said:**
> It sounds like where I went that fixed the problem wasn't where you were trying to lead me, and that it shouldn't have fixed the problem.  That said, without your help, I wouldn't have got there, and it's working now, so I'm very happy.

I changed the Internet DNS because I am using DNS relay.  Simply  un-checking the box for DNS relay did not resolve the problem for me,  and while the router's documentation mentioned turning off DNS relay in  conjunction with setting up a virtual server for DNS, I could not find the documentation I would have needed for how to setup the virtual server for that purpose.  I  did not find other DNS configuration options while poking around in the  router's configuration pages, but I stopped looking as soon as things started working.

Sometimes we get to our destination on a crooked path.  You achieved your goal, but not using the configuration I would have used.  The root problem is still DNS configuration.  You method may not be correct when you upgrade to the next version of Ubuntu (11.10), but you can cross that bridge when you get there.

In your case I would suppose that you were using DNS relay so that you could point to the routers IP address as the primary DNS server.  I would imagine there is a lightweight caching DNS server built into the router.

---

### Post by 9000cse on 2011-06-18
Hi, I'm getting the same thing. This used to work. 
Main System UNBUNTU 10.10, GNOME ver. 2.32
Sys2  Windows XP Pro, SP3
Sys3 Windows XP Home SP3
Sys4 Windows XP Home SP3
Sys5 Windows 7

Mine is used as a server for the above, and also for me to work on.
For some reason, I keep getting permission failure.
Setting up a share on sys2.   sys3, sys4, sys5 can see and read it. My main sys cannot.
None of the systems can see the Main one & the main one cannot read any of the others.
> 
Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

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
ACCEPT     all  --  base-address.mcast.net/4  anywhere            
ACCEPT     all  --  anywhere             base-address.mcast.net/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

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

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 

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
asjmm@asjmm-Saviour:~$ smbclient -L ROMULUS
Enter asjmm's password: 
Connection to ROMULUS failed (Error NT_STATUS_CONNECTION_REFUSED)
asjmm@asjmm-Saviour:~$ ps -ef|grep mbd
root      1179     1  0 13:39 ?        00:00:00 smbd -F
root      1288  1179  0 13:39 ?        00:00:00 smbd -F
root      1815     1  0 13:40 ?        00:00:00 nmbd -D
asjmm     2878  2747  0 14:28 pts/0    00:00:00 grep --color=auto mbd
asjmm@asjmm-Saviour:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::225:22ff:fe11:916e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter asjmm's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1b>
resolve_wins: Attempting wins lookup for name SAVIOUR<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.70
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.70
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.51
asjmm@asjmm-Saviour:~$ samba smb://192.168.1.70
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
asjmm@asjmm-Saviour:~$ sudo restart nmbd
[sudo] password for asjmm: 
nmbd start/running, process 2955
asjmm@asjmm-Saviour:~$ uname -a
Linux asjmm-Saviour 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:41:54 UTC 2011 x86_64 GNU/Linux
asjmm@asjmm-Saviour:~$ cat /etc/hostname
asjmm-Saviour
asjmm@asjmm-Saviour:~$ cat /etc/host
cat: /etc/host: No such file or directory
asjmm@asjmm-Saviour:~$ cat /etc/hostname/interface
cat: /etc/hostname/interface: Not a directory
asjmm@asjmm-Saviour:~$ cat /etc/hostname/interfaces
cat: /etc/hostname/interfaces: Not a directory
asjmm@asjmm-Saviour:~$ sudo apt-get install samba4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-29 linux-headers-2.6.35-29-generic
  chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdcerpc0 libgensec0 libldb0 libndr-standard0 libndr0 libregistry0
  libsamba-hostconfig0 libsamba-util0 libtevent0 python-dnspython python-ldb
  python-samba python-tdb samba-ldb-tools samba4-common-bin
Suggested packages:
  bind9 phpldapadmin swat2
The following NEW packages will be installed:
  libdcerpc0 libgensec0 libldb0 libndr-standard0 libndr0 libregistry0
  libsamba-hostconfig0 libsamba-util0 libtevent0 python-dnspython python-ldb
  python-samba python-tdb samba-ldb-tools samba4 samba4-common-bin
0 upgraded, 16 newly installed, 0 to remove and 2 not upgraded.
Need to get 7,897kB of archives.
After this operation, 37.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libtevent0 amd64 0.9.9~git20100522-3ubuntu1 [24.5kB]
Get:2 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libldb0 amd64 1:0.9.13~git20100908-2ubuntu1 [95.5kB]
Get:3 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libsamba-hostconfig0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [39.2kB]
Get:4 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libsamba-util0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [344kB]
Get:5 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libndr0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [164kB]
Get:6 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libndr-standard0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [789kB]
Get:7 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libgensec0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,159kB]
Get:8 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libregistry0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [87.9kB]
Get:9 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libdcerpc0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,183kB]
Get:10 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-updates/main python-dnspython all 1.8.0-1ubuntu0.1 [91.3kB]
Get:11 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-ldb amd64 1:0.9.13~git20100908-2ubuntu1 [25.5kB]
Get:12 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-tdb amd64 1.2.1-2 [12.9kB]
Get:13 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-samba amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,664kB]
Get:14 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-samba amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,664kB]
Get:15 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba-ldb-tools amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [92.5kB]
Get:16 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba4-common-bin all 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [12.8kB]
Get:17 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba4 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [2,112kB]
Fetched 7,412kB in 4min 18s (28.7kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package libtevent0.
(Reading database ... 219125 files and directories currently installed.)
Unpacking libtevent0 (from .../libtevent0_0.9.9~git20100522-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libldb0.
Unpacking libldb0 (from .../libldb0_1%3a0.9.13~git20100908-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libsamba-hostconfig0.
Unpacking libsamba-hostconfig0 (from .../libsamba-hostconfig0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libsamba-util0.
Unpacking libsamba-util0 (from .../libsamba-util0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libndr0.
Unpacking libndr0 (from .../libndr0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libndr-standard0.
Unpacking libndr-standard0 (from .../libndr-standard0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgensec0.
Unpacking libgensec0 (from .../libgensec0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libregistry0.
Unpacking libregistry0 (from .../libregistry0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libdcerpc0.
Unpacking libdcerpc0 (from .../libdcerpc0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-dnspython.
Unpacking python-dnspython (from .../python-dnspython_1.8.0-1ubuntu0.1_all.deb) ...
Selecting previously deselected package python-ldb.
Unpacking python-ldb (from .../python-ldb_1%3a0.9.13~git20100908-2ubuntu1_amd64.deb) ...
Selecting previously deselected package python-tdb.
Unpacking python-tdb (from .../python-tdb_1.2.1-2_amd64.deb) ...
Selecting previously deselected package python-samba.
Unpacking python-samba (from .../python-samba_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package samba-ldb-tools.
Unpacking samba-ldb-tools (from .../samba-ldb-tools_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package samba4-common-bin.
Unpacking samba4-common-bin (from .../samba4-common-bin_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_all.deb) ...
Selecting previously deselected package samba4.
Unpacking samba4 (from .../samba4_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libtevent0 (0.9.9~git20100522-3ubuntu1) ...
Setting up libldb0 (1:0.9.13~git20100908-2ubuntu1) ...
Setting up python-dnspython (1.8.0-1ubuntu0.1) ...
Setting up python-ldb (1:0.9.13~git20100908-2ubuntu1) ...
Setting up python-tdb (1.2.1-2) ...
Setting up samba4-common-bin (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libndr0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libndr-standard0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libsamba-hostconfig0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libsamba-util0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libgensec0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libdcerpc0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up samba-ldb-tools (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libregistry0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up python-samba (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Processing triggers for python-central ...
Setting up samba4 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
 * Starting Samba 4 daemon samba                                                Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
                                                                         [ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
asjmm@asjmm-Saviour:~$ name resolve order = bcast host lmhosts wins
No command 'name' found, did you mean:
 Command 'named' from package 'bind9' (main)
 Command 'namei' from package 'util-linux' (main)
 Command 'lame' from package 'lame' (universe)
 Command 'cname' from package 'cfs' (universe)
 Command 'uname' from package 'coreutils' (main)
 Command 'nama' from package 'nama' (universe)
 Command 'mame' from package 'mame' (universe)
 Command 'nam' from package 'nam' (universe)
name: command not found
asjmm@asjmm-Saviour:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::225:22ff:fe11:916e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter asjmm's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1b>
resolve_wins: Attempting wins lookup for name SAVIOUR<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
asjmm@asjmm-Saviour:~$ 

I have been reading the past threads and trying to solve the problem myself. Getting nowhere.
Routers are a LinksysWAG-160N, direct to BB.
And a BT Home hub 2 linked to linksys via RJ45.
Both running wifi, BT one for my sons DS, the other for Sys4 & 5. All others wired.
I want to upgrade the  UBUNTU 11, but need to sort out these problems first.
Not knowing enough about UBUNTU is driving me mad.
So, now calling for help.
Cheers
Andy

---

### Post by capscrew on 2011-06-18
> **9000cse said:**
> Hi, I'm getting the same thing. This used to work. 
Main System UNBUNTU 10.10, GNOME ver. 2.32
Sys2  Windows XP Pro, SP3
Sys3 Windows XP Home SP3
Sys4 Windows XP Home SP3
Sys5 Windows 7

Mine is used as a server for the above, and also for me to work on.
For some reason, I keep getting permission failure.
Setting up a share on sys2.   sys3, sys4, sys5 can see and read it. My main sys cannot.
None of the systems can see the Main one & the main one cannot read any of the others.

I have been reading the past threads and trying to solve the problem myself. Getting nowhere.
Routers are a LinksysWAG-160N, direct to BB.
And a BT Home hub 2 linked to linksys via RJ45.
Both running wifi, BT one for my sons DS, the other for Sys4 & 5. All others wired.
I want to upgrade the  UBUNTU 11, but need to sort out these problems first.
Not knowing enough about UBUNTU is driving me mad.
So, now calling for help.
Cheers
Andy

Andy,

Do you really expect someone to go through that mess you just posted? 

I suggest that you edit it.  Put the individual results in their own [code] blocks.  You can do this by ticking the # button at the top of the editor.

Try and put some order (where why) to what you have diagnosed about your situation.  

In the future I suggest you start your own thread for your problem rather than at the tail end of someone else's journey.

---

### Post by 9000cse on 2011-06-18
I think I have just been told off, OK, I can take it.
I'll break it down and start a new thread. 
My Humble apologises.

---

### Post by cmann_97 on 2011-06-19
Chiming in on this. I loaded 9.10 version on a test pc. All of the windows PC's and NAS drives I have (13) showed up under network in Ubuntu. I then proceeded to assign static addressing and loaded updates, Then I couldn't see the windows machines anymore. And this was **before** I started modifying the smb.conf file. My windows workgroup name is not "workgroup". It's odd that all the Win PC's and NAS drives were visible from the out of the box 9.10 install....

---

### Post by 9000cse on 2011-06-19
> **cmann_97 said:**
> Chiming in on this. I loaded 9.10 version on a test pc. All of the windows PC's and NAS drives I have (13) showed up under network in Ubuntu. I then proceeded to assign static addressing and loaded updates, Then I couldn't see the windows machines anymore. And this was **before** I started modifying the smb.conf file. My windows workgroup name is not "workgroup". It's odd that all the Win PC's and NAS drives were visible from the out of the box 9.10 install....

Now that's  what i have been getting, finding.

---

