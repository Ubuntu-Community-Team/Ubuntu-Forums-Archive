---
title: "Can't see Natty Machine on home network"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Vardy on 2011-05-16
Hello

This is my first post - apologies if I do something wrong, or if I am posting a current problem that others have posted.

I have upgraded to Natty distro. since then, I can no longer see my Natty machine on any other computer in my network - I have 2 windows7 computers and a Mac. I can see the other computers from Natty, but not Vice-Versa. I also cannot remote desktop to the Natty machine from any other computer - they simply don't know it's there

So far...
- have changed the credentials on the Windows machine
- have changed security policies (via security manager) on Windows machine
- have installed Samba, and Samba GUI on Ubuntu machine
- Have confirmed Samba conf has correct workgroup - even added line NETBIOS name
- Have installed some extra lib packages and confirmed filesharing is set up correctly (getting desperate)

Any suggestions? I have the same problems whether I am connected wirelessly or through ethernet. I am running Natty 64bit on a Dell Inspiron 1520

Any help would be much appreciated
Cheers
Andrew:o

---

### Post by Vardy on 2011-05-18
Hey guys - no answer yet? I'm new to forums so not really sure how it all works. Does no answer means no one knows or that the answer is somewhere else or did I do something wrong?

Could someone please say something just so I know it's all working right :)

Cheers
Andrew

---

### Post by Vardy on 2011-05-21
Really - any answer would be good please, just so I know I am posting right...

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Could you see the Ubuntu shares from maverick? Also, can you access the shares with \\Servername\ShareName ? As its windows 7, it could be a DNS / WINS related issue.

---

### Post by Vardy on 2011-05-23
Cheers heaps for your reply

Yes, could see fine with Maverick. No, \\Servername\ShareName does not work.

You might be on the right track with WINS / DNS and Win7. Any suggestions as to where to go from here...

Cheers
Andrew

---

### Post by capscrew on 2011-05-23
> **Vardy said:**
> Cheers heaps for your reply

Yes, could see fine with Maverick. No, \\Servername\ShareName does not work.

You might be on the right track with WINS / DNS and Win7. Any suggestions as to where to go from here...

Cheers
Andrew

Can you see the share if you use the IP address of the server?  Like this: //192.168.num.num/share 

Maybe the nmbd daemon is not working.  What do you get with this```
ps -e|grep mbd
```

It should look something like this:```
root       979     1  0 09:23 ?        00:00:00 smbd -F
root      1102   979  0 09:23 ?        00:00:00 smbd -F
root      1937     1  0 10:30 ?        00:00:00 nmbd -D

```

---

### Post by kibaya on 2011-05-23
just try to share any folder on your natty computer then try locating it on  the network now

---

### Post by Vardy on 2011-05-23
looks like this...

ps -e|grep mbd
  680 ?        00:00:00 smbd
  810 ?        00:00:00 smbd
 1765 ?        00:00:00 nmbd
 3409 ?        00:00:00 smbd
 3411 ?        00:00:00 smbd
 3413 ?        00:00:00 smbd

I'm guessing those question marks are not good...

Cheers
Andrew

---

### Post by Vardy on 2011-05-23
I have a folder shared on the natty machine - in the windows machine, I can't even see the natty machine, let alone the shared folder...

Cheers
Andrew

---

### Post by capscrew on 2011-05-23
> **Vardy said:**
> looks like this...

ps -e|grep mbd
  680 ?        00:00:00 smbd
  810 ?        00:00:00 smbd
 1765 ?        00:00:00 nmbd
 3409 ?        00:00:00 smbd
 3411 ?        00:00:00 smbd
 3413 ?        00:00:00 smbd

I'm guessing those question marks are not good...

Cheers
Andrew

I don't like to guess.  The ? is not a bad thing. It is under the heading of TTY.  I tells you which terminal the processes is running in.  Here is the results of checking on grep in 2 different terminals```
4766 pts/0    00:00:00 grep

4785 pts/1    00:00:00 grep
``` The term pts stands for pseudo terminal.

I looks like nmbd is running and that you have forked the smbd a number of times for various shares.  Lets do some debug.  Post the output (wrapped in ```
 [ /code] blocks) of the this [CODE]smbtree -d3
```

Edit:  You can see the headers of the output of ps -e if you don't filter using grep.  They look like this ```
  PID TTY          TIME CMD

```

---

### Post by Vardy on 2011-05-24
Edit...

---

### Post by Vardy on 2011-05-24
Hello

Here is the terminal output - cheers for all your support

Just realised - yes, I can reach the Natty Machine if I type the IP Address into windows command box (not sure why I couldn't see it before). Thought you might want to know...

 Thanks again...
 Andrew

```
sabbas@sabbas-Inspiron-1520:~$ smbtree -d3
 lp_load_ex: refreshing parameters
 Initialising global parameters
 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
 params.cm_process() - Processing configuration file "/etc/samba/smb.conf"
 Processing section "[global]"
 added interface wlan0 ip=fe80::213:e8ff:fe9b:a0e1%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
 added interface wlan0 ip=192.168.1.6 bcast=192.168.1.255 netmask=255.255.255.0
 Enter sabbas's password: 
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 VARDIS
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 \\SABBAS-INSPIRON- sabbas-Inspiron-1520 server (Samba, Ubuntu)
 Connecting to host=SABBAS-INSPIRON-
 resolve_lmhosts: Attempting lmhosts lookup for name SABBAS-INSPIRON-<0x20>
 resolve_wins: Attempting wins lookup for name SABBAS-INSPIRON-<0x20>
 resolve_wins: using WINS server 127.0.0.1 and tag '*'
 Got a positive name query response from 127.0.0.1 ( 192.168.1.6 )
 Connecting to 192.168.1.6 at port 445
 \\SABBAS-INSPIRON-\IPC$ IPC Service (sabbas-Inspiron-1520 server (Samba, Ubuntu))
 \\SABBAS-INSPIRON-\Drop Box 
 \\SABBAS-INSPIRON-\print$ Printer Drivers
 \\ASUS 
 Connecting to host=ASUS
 resolve_lmhosts: Attempting lmhosts lookup for name ASUS<0x20>
 resolve_wins: Attempting wins lookup for name ASUS<0x20>
 resolve_wins: using WINS server 127.0.0.1 and tag '*'
 Negative name query response, rcode 0x03: The name requested does not exist.
 resolve_hosts: Attempting host lookup for name ASUS<0x20>
 resolve_hosts: getaddrinfo failed for name ASUS [No address associated with hostname]
 name_resolve_bcast: Attempting broadcast lookup for name ASUS<0x20>
 Got a positive name query response from 192.168.1.5 ( 192.168.1.5 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to 192.168.1.5 at port 445
 cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
```

---

### Post by capscrew on 2011-05-24
> **Vardy said:**
> Hello

Here is the terminal output - cheers for all your support

Just realised - yes, I can reach the Natty Machine if I type the IP Address into windows command box (not sure why I couldn't see it before). Thought you might want to know...

 Thanks again...
 Andrew

```
sabbas@sabbas-Inspiron-1520:~$ smbtree -d3
 lp_load_ex: refreshing parameters
 Initialising global parameters
 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
 params.cm_process() - Processing configuration file "/etc/samba/smb.conf"
 Processing section "[global]"
 added interface wlan0 ip=fe80::213:e8ff:fe9b:a0e1%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
 added interface wlan0 ip=192.168.1.6 bcast=192.168.1.255 netmask=255.255.255.0
 Enter sabbas's password: 
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 VARDIS
 resolve_lmhosts: Attempting lmhosts lookup for name VARDIS<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name VARDIS<0x1d>
 Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to host=192.168.1.6
 Connecting to 192.168.1.6 at port 445
 \\SABBAS-INSPIRON- sabbas-Inspiron-1520 server (Samba, Ubuntu)
 Connecting to host=SABBAS-INSPIRON-
 resolve_lmhosts: Attempting lmhosts lookup for name SABBAS-INSPIRON-<0x20>
 resolve_wins: Attempting wins lookup for name SABBAS-INSPIRON-<0x20>
 resolve_wins: using WINS server 127.0.0.1 and tag '*'
 Got a positive name query response from 127.0.0.1 ( 192.168.1.6 )
 Connecting to 192.168.1.6 at port 445
 \\SABBAS-INSPIRON-\IPC$ IPC Service (sabbas-Inspiron-1520 server (Samba, Ubuntu))
 \\SABBAS-INSPIRON-\Drop Box 
 \\SABBAS-INSPIRON-\print$ Printer Drivers
 \\ASUS 
 Connecting to host=ASUS
 resolve_lmhosts: Attempting lmhosts lookup for name ASUS<0x20>
 resolve_wins: Attempting wins lookup for name ASUS<0x20>
 resolve_wins: using WINS server 127.0.0.1 and tag '*'
 Negative name query response, rcode 0x03: The name requested does not exist.
 resolve_hosts: Attempting host lookup for name ASUS<0x20>
 resolve_hosts: getaddrinfo failed for name ASUS [No address associated with hostname]
 name_resolve_bcast: Attempting broadcast lookup for name [COLOR="Red"]ASUS[/COLOR]<0x20>
 Got a positive name query response from 192.168.1.5 ( 192.168.1.5 )
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
 Connecting to 192.168.1.5 at port 445
 [COLOR="Red"]cli_session_setup: NT1 session setup failed: **NT_STATUS_LOGON_FAILURE**[/COLOR]
```

The answer is in the last line.  The Samba user sabbas can't log in to the host ASUS.  Is there a user sabbas on the host ASUS?

On my system there is a Ubuntu user (cap) and a Samba user of the same name.  On my Vista and XP hosts there is also a user named cap.  All of these have the same password.

---

### Post by Vardy on 2011-05-24
> **capscrew said:**
> The answer is in the last line.  The Samba user sabbas can't log in to the host ASUS.  Is there a user sabbas on the host ASUS?

On my system there is a Ubuntu user (cap) and a Samba user of the same name.  On my Vista and XP hosts there is also a user named cap.  All of these have the same password.

Thank you for your response

Yes, there is a user sabbas on Asus, and it has the same password. Do I need to set up a Samba user on Natty?

Just as an afterthought, here is the global block of my SMB.conf...

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = VARDIS
	Netbios name = sabbas-inspiron-1520

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

	client use spnego = no 
```

Does it look ok - not sure about the WINS server / client differentiation.

Cheers :)
Andrew

---

### Post by capscrew on 2011-05-24
> **Vardy said:**
> Thank you for your response

Yes, there is a user sabbas on Asus, and it has the same password. Do I need to set up a Samba user on Natty?

Yes you need a Samba user of the same name as the Ubuntu user on Natty.  Look at the bottom of post # 6 [**_[COLOR="Blue"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823") for what is needed to successfully implement Samba. > 

Just as an afterthought, here is the global block of my SMB.conf...

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = VARDIS
	Netbios name = sabbas-inspiron-1520

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

	client use spnego = no 
```

Does it look ok - not sure about the WINS server / client differentiation.

You do not need to do anything with WINS for a simple Samba (home) installation.  In fact you only need to add the shares at the bottom and follow the bullet points I mentioned in the post I referred to above.  Adding the workgroup is really only a visual aid by lumping all the shares together.  You could have 2 workgroups if you wanted.

-Cappy

---

### Post by Vardy on 2011-05-25
> **capscrew said:**
> Yes you need a Samba user of the same name as the Ubuntu user on Natty.  Look at the bottom of post # 6 [**_[COLOR="Blue"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823") for what is needed to successfully implement Samba. You do not need to do anything with WINS for a simple Samba (home) installation.  In fact you only need to add the shares at the bottom and follow the bullet points I mentioned in the post I referred to above.  Adding the workgroup is really only a visual aid by lumping all the shares together.  You could have 2 workgroups if you wanted.

-Cappy

Hi again

OK - still having trouble. From the Windows machine, I can cmd the IP Address (statically set in he router) or the name of the Natty machine and see the shared folders within, but still can't see the machine itself through the windows gui. I have followed your bullet points however wasn't sure how would you provde DNS name resolution for LAN. Is this done through smb.conf? I would have thought my router did that...

Cheers again
Andrew

---

### Post by capscrew on 2011-05-25
> **Vardy said:**
> Hi again

OK - still having trouble. From the Windows machine, I can cmd the IP Address of the Natty machine and see the shared folders within, but still can't see the machine itself. I have followed your bullet points; how would you provde DNS name resolution for LAN? Is this done through smb.conf? I would have thought my router did that...

Cheers again
Andrew

Not all routers can provide local (LAN side) DNS services. No you can NOT configure LAN side DNS with smb.conf.

In looking at your smb.conf file again I realize you have created a problem with this```
	Netbios name = sabbas-inspiron-1520
```

Please modify this line to look like this```
[COLOR="Red"]#[/COLOR]	Netbios name = sabbas-inspiron-1520

```
Yes you are adding the hash mark (#) at the start of the line.  You do NOT need to declare a NetBIOS name and if you did declare one it should be 15 characters or less: sabbas-inspiron-1520 is 20 characters.

Post the output of ```
less /etc/hosts
```

I think we will be changing your hostname from sabbas-inspiron-1520 to something much smaller.  What do you like to use as a host name.  I use beaches that I like to visit they are: malibu, rincon, kona and manila.  Youcan use what ever you want.  Most folks have a theme: trees, flowers, cats, planets, etc.

This line is not needed either```
client use spnego = no
```
You can change it to = yes or remove it (which makes it the default (which is = yes)).

**Edit**: I think you are over thinking this.  Samba is real easy to set up.  You can change the WORKGROUP name and add the shares to smb.conf.  You DO NOT need anything else modified, changed or added.  Try and follow what I suggest.  I can't anticipate all the junk you can read and misinterpret.  Later you can ask all you want about why you do things.  Right now it is best that we get it running.  Maybe you should post the *entire *smb.conf file.

---

### Post by Vardy on 2011-05-25
> **capscrew said:**
> Not all routers can provide local (LAN side) DNS services. No you can NOT configure LAN side DNS with smb.conf.

In looking at your smb.conf file again I realize you have created a problem with this```
	Netbios name = sabbas-inspiron-1520
```

Please modify this line to look like this```
[COLOR="Red"]#[/COLOR]	Netbios name = sabbas-inspiron-1520

```
Yes you are adding the hash mark (#) at the start of the line.  You do NOT need to declare a NetBIOS name and if you did declare one it should be 15 characters or less: sabbas-inspiron-1520 is 20 characters.

Machine name changed to inspiron-1520. I have changed it in /etc/hosts and /etc/hostname. Added the hash mark

Post the output of ```
less /etc/hosts
```

```
127.0.0.1       localhost
127.0.1.1       inspiron-1520

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters 
```

I think we will be changing your hostname from sabbas-inspiron-1520 to something much smaller.  What do you like to use as a host name.  I use beaches that I like to visit they are: malibu, rincon, kona and manila.  Youcan use what ever you want.  Most folks have a theme: trees, flowers, cats, planets, etc.

I like to be able to identify the machines easily so I use the name of the the machine (boring, I know). This one is inspiron-1520 because I have another dell on the system.

Hope I changed it right - I know I went ahead of you but noted your edit after. You are correct, let's get this this thing going. Have much to ask / learn bat, as you say, that is not the priority.

This line is not needed either```
client use spnego = no
```
You can change it to = yes or remove it (which makes it the default (which is = yes)).

Changed to yes

**Edit**: I think you are over thinking this.  Samba is real easy to set up.  You can change the WORKGROUP name and add the shares to smb.conf.  You DO NOT need anything else modified, changed or added.  Try and follow what I suggest.  I can't anticipate all the junk you can read and misinterpret.  Later you can ask all you want about why you do things.  Right now it is best that we get it running.  Maybe you should post the *entire *smb.conf file.

Sorry - overthinking... the result of too much googling. As mentioned, we'll play it by your rules - then I've got some questions :P

Here is the smb.conf file...

```
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = vardis
#	Netbios name = inspiron-1530

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

	client use spnego = yes

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
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
	security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
	map to guest = bad user

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
#;   winbind enum groups = yes
#;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
;	guest ok = no
;	guest account = nobody
	username map = /etc/samba/smbusers

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
# [homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
	browseable = no
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

[Drop Box]
	comment = Drop Box
	path = /home/sabbas/Drop Box
;	available = yes
	valid users = sabbas
	read only = no
;	browseable = yes
	public = yes

```

Thanks again for all you've done / doing

Cheers
Andrew

---

### Post by capscrew on 2011-05-25
Andrew,

I think we should use a shorter name for insperion-1530.  Maybe we can use the hostname [COLOR="Blue"]**dell**[/COLOR].  There are 2 reasons for this.  The name is shorter and it has no dash (-) in the name.

Imagine having to type this: *[COLOR="Green"]ping insperion-1530[/COLOR]* a bunch of times or looking for it in a log file.  The names should be short, unique and not ambiguous.  Which leads me to another issue.  It looks like you have named the WORKGROUP as VARDIS and a host named vardis.  We need to change one of these.  The easiest is to change the WORKGROUP to a new name in the smb.conf file.  My suggestion would be ```

User = sabbas (these should be the same)
Samba user = sabbas

Workgroup = WORK (or your choice)

192.168.1.6 = vardis
192.168.1.5 = asus
192.168.1.1 = dell
```

You have also created a directory (folder) with spaces in it (i.e. folder name) this can cause problems.  You should use names that are short and have no spaces or special characters (- , & % $ # @ !).

I know it sounds like I'm picking on you.  I am not.  I have been doing this for  along time (20+ years) and i have seen the problems in these areas.

Now a little work on your part...

Please post the output of the following on the Ubuntu host 
```
cat /etc/hosts

cat /etc/hostname

cat /etc/resolv.conf

cat /etc/network/interfaces
```

Are you using Network-Manager to administer this interface?

What is the OS for each of your computers?.  I assume that the host dell (192.168.1.1 = insperion-1530) is the Ubuntu OS.

Once we have these in place we can deal with the LAN nameservices.

-Capscrew

---

