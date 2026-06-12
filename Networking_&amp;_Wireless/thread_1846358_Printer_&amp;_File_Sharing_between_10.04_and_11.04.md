---
title: "Printer &amp; File Sharing between 10.04 and 11.04"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by kronix_00 on 2011-09-18
I think I'm having information overload -- there are tons of posts regarding the "right way" to get printer/file sharing set up between two Ubuntu machines, but none seem to work for my particular (simple?!) problem:

I've got a desktop machine running Ubuntu 10.04 (call it "*Desktop*"), a laptop machine running Ubuntu 11.04 (call it "*Laptop*"), and a Windows laptop running Win7 (call it "*Windows*").  I've installed Samba on both Ubuntu machines and have set some folders on each machine as shared.

(**1**) *Windows* can see both *Desktop* and *Laptop*, no problem.  All machines are accessible from the Windows machine.  (I'm using *Windows* for testing -- I'm more concerned about the two Ubuntu machines.)

(**2**) *Desktop* can see *Laptop* under the Nautilus' 'Network' icon... but can't actually connect -- I click on *Laptop*, and it eventually says 'Unable to mount location'.

(**3**) *Laptop* can see *Desktop*.  I can click on a shared folder, and it asks for a user name and password.  I've followed instructions and (I think) I've assigned a samba user and password on *Desktop* and *Laptop* both (via 'sudo smbpasswd -a USERNAME').  But no matter what username or password I use from *Laptop* (system usr/pwd or samba usr/pwd) it won't connect, and just keeps bringing up the usr/pwd box again.

Since both *Laptop* and *Desktop* can (almost) see each other, and *Windows* can access everybody, it seems that I've almost got it right... but how do I get the two Ubuntu machines to shake hands?

I think I'm stuck in "I-don't-know-how-to-troubleshoot-this" mode.  Any pointers on things I can check or test?

Thanks for your patience.

---

### Post by kronix_00 on 2011-09-23
Okay, so after some contortions and many failed attempts, it looks like my Laptop machine can see my Desktop machine and vice versa.  File sharing sometimes works -- not sure why it's intermittent.

Again, my biggest issue here is that I'm a little at a loss on how to troubleshoot something that feels as complex as Samba.  For a new user, what basic advice might you give to troubleshooting my Samba setup?

---

### Post by capscrew on 2011-09-23
> **kronix_00 said:**
> Okay, so after some contortions and many failed attempts, it looks like my Laptop machine can see my Desktop machine and vice versa.  File sharing sometimes works -- not sure why it's intermittent.

Again, my biggest issue here is that I'm a little at a loss on how to troubleshoot something that feels as complex as Samba.  For a new user, what basic advice might you give to troubleshooting my Samba setup?

How are you resolving the hostnames of the 2 Ubuntu machines?  Samba has a very complex method of doing that, but it all boils down to how you set up name services.  If you are using local hosts names then you have to use static IP addressing.  If you use NetBIOS names then you need to declare that in the /etc/samba/smb.conf file.

So the first question is how are you resolving the host names (machines) and how do you get an IP address.?

---

### Post by kronix_00 on 2011-09-23
> **capscrew said:**
> So the first question is how are you resolving the host names (machines) and how do you get an IP address.?(Blush)  I'm not entirely sure.  After reading a little bit, I think I'm using NetBIOS names.  For example, one machine might be called 'sys1-desktop' while the other might be 'sys2-laptop' etc.

This is NetBIOS referencing, yes?  What can I do to report how I get an IP address out of that?

(Thanks for your patience with a complete newbie.)

---

### Post by capscrew on 2011-09-23
> **kronix_00 said:**
> (Blush)  I'm not entirely sure.  After reading a little bit, I think I'm using NetBIOS names.  For example, one machine might be called 'sys1-desktop' while the other might be 'sys2-laptop' etc.

This is NetBIOS referencing, yes?  What can I do to report how I get an IP address out of that?

(Thanks for your patience with a complete newbie.)

No problems.  Lets start with one of the Ubuntu machines that you want to share a folder/file on.  From the terminal, provide the output from the following commands```
testparm -s

ifconfig -a

cat /etc/hosts
```

---

### Post by kronix_00 on 2011-09-23
Great, I can do that.  Forgive me for adding my own commentary, but I want to make sure I understand what I'm looking at.  If (when!) I get it wrong, please correct me.  

Here's the *testparm -s* output for the desktop machine:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_folder1]"
Processing section "[shared_folder2]"
...
Processing section "[shared_folder5]"

```

Up to here, I think I follow what's happening, although I'm not sure what the difference between 'printers' and 'print$' is.  I have a printer attached to the desktop, and I tried to share it.  I figured once I got file sharing to work, I'd worry about printers.  :)

```

Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

```

This doesn't concern me too much; I don't have any older Windows machines.  How do I check the version of Samba I'm using?

```

[global]
	workgroup = MYWORKGROUP
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	read only = No

```

I follow some of this.  Somewhere as I was trying to fix things, I recall changing the name resolve order, although I'm not clear on what each of the terms mean.  os level doesn't make sense to me, either.

```

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	guest only = Yes
	guest ok = Yes
	printable = Yes
	use client driver = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes


```

Again, why there are two of these, I don't know.  If I delete one, will I break things elsewhere?  That's one thing I'm still trying to understand about Ubuntu -- should I choose to use the GUI exclusively, or the CLI exclusively... or if I use the GUI to set some things and then the CLI for others, will I end up making a mess (like now)?  :)

```


[shared_folder1]
	comment = Shared Folder on sys1-desktop (Ubuntu)
	path = [...path to shared folder]
	guest ok = Yes

[shared_folder2]
	comment = Shared folder on [secondary drive]
	path = [...path to secondary drive]
	guest ok = Yes

... etc.


```

All shared folders have the exact same syntax as the two examples shown above.

Okay, that's it for testparm.  I'll post the other results separately.  Thanks for your help!

---

### Post by kronix_00 on 2011-09-23
Next, here is the output of *ifconfig -a*.  (I don't think there's anything terribly sensitive here, is there?  The IP addresses are all local to my network, I believe... if I post something unwise, please let me know!)


```

eth0      Link encap:Ethernet  HWaddr 00:07:e9:cf:1e:61  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fecf:1e61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5030233 errors:6 dropped:0 overruns:0 frame:6
          TX packets:4395664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:538622346 (538.6 MB)  TX bytes:2594715258 (2.5 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1158722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62212612 (62.2 MB)  TX bytes:62212612 (62.2 MB)

wlan0     Link encap:Ethernet  HWaddr 08:86:3b:0a:98:5d  
          inet6 addr: fe80::a86:3bff:fe0a:985d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6382 (6.3 KB)  TX bytes:4670 (4.6 KB)

```

Basically, the desktop system is connected to the wireless LAN via an ethernet cable, although there is a wireless adapter installed.  Currently, the adapter is a bit weak, and so I get much better performance if I use the ethernet cable.

---

### Post by kronix_00 on 2011-09-23
...And lastly, '*cat /etc/hosts*', as you requested:

```

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
127.0.1.1 sys1-desktop

```

Many thanks for taking a look at this.  Please feel free to post back as verbosely (and frankly!) as you'd like.  I'm very interested to learn as much as anyone will share.

---

### Post by capscrew on 2011-09-23
> **kronix_00 said:**
> Great, I can do that.  Forgive me for adding my own commentary, but I want to make sure I understand what I'm looking at.  If (when!) I get it wrong, please correct me.  

Here's the *testparm -s* output for the desktop machine:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_folder1]"
Processing section "[shared_folder2]"
...
Processing section "[shared_folder5]"

```

Up to here, I think I follow what's happening, although I'm not sure what the difference between 'printers' and 'print$' is.  I have a printer attached to the desktop, and I tried to share it.  I figured once I got file sharing to work, I'd worry about printers.  :)

```

Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

```

This doesn't concern me too much; I don't have any older Windows machines.  How do I check the version of Samba I'm using?

This seemingly simple question can lead to disastrous results if misunderstood.  The Samba package we are dealing with is named we are dealing with is smbd not Samba (as one would expect).  If you were to check like this```
smbd -V
```

You will find the version number for the Samba if it is 3.X.  Mine lookks like this```
smbd -V
Version 3.4.7

```

If you were to do this ```
samba -V
```

You will get this **VERY MISLEADING **message```
samba =V
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install **[COLOR="Red"]samba4[/COLOR]**

```

Samba4 is alpha and experimental.  It is incorporates lots of MS Active Directory compatibility.  None of this is needed for a simple workgroup situation.  
> 

```

[global]
	workgroup = MYWORKGROUP
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	read only = No

```

I follow some of this.  Somewhere as I was trying to fix things, I recall changing the name resolve order, although I'm not clear on what each of the terms mean.  os level doesn't make sense to me, either.

Every term is explained (to someone who understands the basics) [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  Hopefully it won't confuse you even more.  :-)> 

```

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	guest only = Yes
	guest ok = Yes
	printable = Yes
	use client driver = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes


```


Again, why there are two of these, I don't know.  If I delete one, will I break things elsewhere?  That's one thing I'm still trying to understand about Ubuntu -- should I choose to use the GUI exclusively, or the CLI exclusively... or if I use the GUI to set some things and then the CLI for others, will I end up making a mess (like now)?  :)

One is the shared printer spool and the other is the shared drivers.  Leave them both as they are.  I have a networked printer so I don't use Samba to print.  I leave this in anyway.> 

```


[shared_folder1]
	comment = Shared Folder on sys1-desktop (Ubuntu)
	path = [...path to shared folder] **[COLOR="Red"]<-- this is wrong[/COLOR]**
	guest ok = Yes

[shared_folder2]
	comment = Shared folder on [secondary drive]
	path = [...path to secondary drive] **[COLOR="Red"]<-- this is wrong[/COLOR]**
	guest ok = Yes

... etc.


```

All shared folders have the exact same syntax as the two examples shown above.

Okay, that's it for testparm.  I'll post the other results separately.  Thanks for your help!
In the future just edit the post to add data or...Just wait until you have it all.  I save the data in a separate window (desk) and cut 'n paste.  Like I will do here --

> Basically, the desktop system is connected to the wireless LAN via an ethernet cable, although there is a wireless adapter installed. Currently, the adapter is a bit weak, and so I get much better performance if I use the ethernet cable.

This will work.  Wireless and wired Ethernet are the same other than the medium to connect to the network at the PHY (layer1) level.

> ...And lastly, 'cat /etc/hosts', as you requested:
```
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
127.0.1.1 sys1-desktop
```
Many thanks for taking a look at this. Please feel free to post back as verbosely (and frankly!) as you'd like. I'm very interested to learn as much as anyone will share.


I see you have modified this -- but at least all the needed stuff is there.

So now all we need to know is; do you use DHCP to assign the IP address?  If so is the address reserved so that it is always the same?  Is the interface configured via Network Manager of via you configuring .conf files?

My guess is this host is configured via Network Manager and is assigned an IP address via DHCP.  I think we should use NETBIOS names and leave what you have in place.

---

### Post by kronix_00 on 2011-09-24
> **capscrew said:**
> This seemingly simple question can lead to disastrous results if misunderstood.
Thanks for the explanation!  My version of smbd is the same as yours (Version 3.4.7), and I don't have samba4 installed.

> **capscrew said:**
> In the future just edit the post to add data...Sorry!  Trying to maintain a little privacy, but I'll leave it pristine next time.

> **capscrew said:**
> My guess is this host is configured via Network Manager and is assigned an IP address via DHCP.Yes, that's correct.

> **capscrew said:**
> I think we should use NETBIOS names and leave what you have in place.So this implies that the above configuration is not wildly off?

Thanks, Capscrew, for your efforts, here.  I'm learning a lot!

---

### Post by capscrew on 2011-09-24
> **kronix_00 said:**
> So this implies that the above configuration is not wildly off?


I think you are close.  But then again the default install is close too.  The only thing needed is some way to locate the shares by name.  There are two things needed to make Samba look for the with NETBIOS naming.  

First you have to give it a NETBIOS name (see in red below) and secondly (as you have already done, make it announce it via broadcast (also in red below).

Note:  You can use *any name* for a NETBIOS name as long as it is below 15 characters in length.  This is a limitation of the NETBIOS protocol.

```
[global]
	workgroup = MYWORKGROUP
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	[B][COLOR="Red"]name resolve order = bcast host lmhosts wins
        netbios name = sys1-desktop[/COLOR][/B]
	printcap name = cups
	os level = 33
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	read only = No
```


These two parameters configure the nmbd daemon to use NETBIOS only when creating the browse list which maps the IP address to the NETBIOS name.

After this is configured you should reboot the system.  In most cases you would only need to restart the *smbd* and *nmbd* daemons, but in this case we need check the start up process completely.  After the reboot we will check to see if the daemons have really started upon boot up.  You use this command to check ```
pgrep -l mbd
```

This should return something like this ```
pgrep -l mbd
[COLOR="Green"][B]963 smbd
1067 smbd[/B][/COLOR]
**[COLOR="Blue"]1103 nmbd[/COLOR]**

```

---

### Post by kronix_00 on 2011-09-24
> **capscrew said:**
> This should return something like this ```
pgrep -l mbd
[COLOR="Green"][B]963 smbd
1067 smbd[/B][/COLOR]
**[COLOR="Blue"]1103 nmbd[/COLOR]**

```

Great, I've got something similar:

```

738 smbd
806 smbd
1639 nmbd

```

Incidentally, why are there two smdb entries?

---

### Post by capscrew on 2011-09-24
> **kronix_00 said:**
> Great, I've got something similar:

```

738 smbd
806 smbd
1639 nmbd

```

Incidentally, why are there two smdb entries?

Did everything work?

The reason for two entries for *smbd *is in the design of the process (daemon).  It forks (replicates itself) to be able to handle another request each time a share is requested.  So you have the original and one standing by waiting when booting up.  Open a few shares and check it again.  The *nmbd* daemon only handles name services so there is no need to fork.

---

### Post by kronix_00 on 2011-09-24
> **capscrew said:**
> It forks (replicates itself) to be able to handle another request each time a share is requested.  So you have the original and one standing by waiting when booting up.  Gotcha.  That makes sense.

> **capscrew said:**
> Did everything work?Sorry, I posted my response before checking the other machine (laptop) and reconfiguring it in the same way as you described above (it, too, was missing a netbios name).  Now, everyone appears to be talking nicely to each other!  I can see shares on both machines (and still on the windows box, too).  Success!

Thanks so much, capscrew!  Your help not only solved the problem, but I think I've got a much better idea of what's actually going on.

---

### Post by capscrew on 2011-09-24
> **kronix_00 said:**
> Gotcha.  That makes sense.

Sorry, I posted my response before checking the other machine (laptop) and reconfiguring it in the same way as you described above (it, too, was missing a netbios name).  Now, everyone appears to be talking nicely to each other!  I can see shares on both machines (and still on the windows box, too).  Success!

Thanks so much, capscrew!  Your help not only solved the problem, but I think I've got a much better idea of what's actually going on.

Glad I could help.

If you want to really see what is going on you can try this in the terminal```
smbtree -d3
```

This turns on a mild amount of debug and sends it to the terminal for you to see.

---

### Post by kronix_00 on 2011-09-24
> **capscrew said:**
> If you want to really see what is going on you can try this in the terminal```
smbtree -d3
```This turns on a mild amount of debug and sends it to the terminal for you to see.Gee, and here I thought I was starting to understand things.  ;)  Looks like there's always more to learn!

---

### Post by capscrew on 2011-09-24
> **kronix_00 said:**
> Gee, and here I thought I was starting to understand things.  ;)  Looks like there's always more to learn!

With 20+ years I'm still learning!  :D

---

### Post by Morbius1 on 2011-09-24
@capscrew, I hope you don't mind a follow-up question. It has to do with something outside of this topic - his Windows clients. 

Something didn't look right about the OP's smb.conf so I reproduced it  by having only guest shares and having one line missing as he does:
```
map to guest = Bad User
```I can't get access to the guest share. Windows will automatically send a username and password when it browses my shares but the server is set at the default of "map to guest = Never". I never created a username and password for the Windows user on my Linux machine because all I have are guest shares. So all I get on the client end is a prompt for credentials.

Doesn't he either have to create a username and samba password for the Windows client to access a guest share or set "map to guest" to "Bad User"?

It's very late for me - maybe I'm over-thinking this or maybe not enough :)

---

### Post by capscrew on 2011-09-24
> **Morbius1 said:**
> @capscrew, I hope you don't mind a follow-up question. It has to do with something outside of this topic - his Windows clients.

Something didn't look right about the OP's smb.conf so I reproduced it  by having only guest shares and having one line missing as he does:
```
map to guest = Bad User
```I can't get access to the guest share. Windows will automatically send a username and password when it browses my shares but the server is set at the default of "map to guest = Never". I never created a username and password for the Windows user on my Linux machine because all I have are guest shares. So all I get on the client end is a prompt for credentials.

Doesn't he either have to create a username and samba password for the Windows client to access a guest share or set "map to guest" to "Bad User"? 

It's very late for me - maybe I'm over-thinking this or maybe not enough :)

Hi Morbuis1,

A great question.  First, it's important to note that if the user (Sys Admin) does not declare a parameter, the default applies.  In this case the default is indeed ```
map to guest = never
```

If you want to see all the implied +  explicit parameters use this command```
testparm -v
```

Here are some of the implied paramiters that I don't declare in my smb.conf file) that show up with the above command
```
	debug timestamp = Yes
	debug prefix timestamp = No
	debug hires timestamp = No
	debug pid = No
	debug uid = No
	debug class = No
	enable core files = Yes
	smb ports = 445 139
	large readwrite = Yes
	max protocol = NT1

```

To my way of thinking there is no such thing as a "guest share".  You can have anonymous users (guests) access shares and you can have shares that *anybody * can access.  Is this semantics?  Maybe.  I call my "anybody can use" shares *Public*. ;-)

Just because you have *guest = ok * in a share parameter doesn't mean an anonymous user will have access.  In IT security there is a notion of Authenticate and Authorization.  In the OP's setup he has Authorized the guest but the guest can't be Authenticated.

All this boils down to:  Yes you need to declare the *map to guest = Bad user  * or it will default to *never * and anonymous users will be excluded.  In my network I authorized anonymous users, but none ever authenticate.  I'll bet the OP only uses authenticated users right now.

I have learned not to worry about Ubuntu users misconfiguration problems before they do.  *"You can't care more than the caretaker"*

Edit:  Let me restate one thing.  When you use *map to guest = Bad User* you have declared that any user that is not in the smb user database data base is to be mapped to the user  declared in *guest account = <some name>*.  This Authenticates that user with no login needed.  The default guest account user is the user *nobody*.  I used the account I created with a user named *smbguest*.  it is worth noting that _ALL users must be authenticated_ one way or another.

---

### Post by kronix_00 on 2011-09-24
> **capscrew said:**
> I'll bet the OP only uses authenticated users right now.That's exactly correct.  And now, thanks to Morbius1's comment, I've gone back and re-evaluated this situation.  Thanks, both of you.

> **capscrew said:**
> I have learned not to worry about Ubuntu users misconfiguration problems before they do.  *"You can't care more than the caretaker"*Probably very good practice... although for some of us newer users, it's not that we don't *care*, it's that we don't *know*.

---

### Post by capscrew on 2011-09-24
> **kronix_00 said:**
> That's exactly correct.  And now, thanks to Morbius1's comment, I've gone back and re-evaluated this situation.  Thanks, both of you.

Probably very good practice... although for some of us newer users, it's not that we don't *care*, it's that we don't *know*.

Sometimes it just dawns on you, or your needs change.  It's just a matter of time.  I could flood you with how I do things, but that usually just confuses the new user.  Not all new users start of with the same basic insight.

Glad you got it straightened out though.

---

