---
title: "Networking problem between Win7 and Ubuntu 11.10"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by wvcadle on 2011-11-13
I've got everything set up, per instructions here: [http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/).

The only thing I can't do is see my Windows shares in Ubuntu.  I can browse from Windows and see my Ubuntu shares.

I'm getting an error: Unable to mount location. Failed to retrieve share list from server.

Thanks in advance.

---

### Post by 2F4U on 2011-11-13
Do you use a firewall on Windows?

---

### Post by wvcadle on 2011-11-13
I do.  Windows firewall in Win 7 Ultimate.

Do I need to turn it off?  Is it possible to leave it on and configure it properly to allow my Ubuntu laptop to connect?

---

### Post by wvcadle on 2011-11-14
I turned the Windows firewall off and it still doesn't allow me to see the Windows shares from Ubuntu.

What are my next steps?

---

### Post by critin on 2011-11-14
I have just the opposite issue, I can't see ubuntu from windows.  All I need in ubuntu is Samba and it always works.

Windows says something about ubuntu not allowing remote views--gaa!

---

### Post by jonobr on 2011-11-14
If you can 
post output of command please:
```


findsmb


```


and also
```

sudo iptables -L


```

---

### Post by dendari on 2011-11-14
I am having the same problem. I have two win7 home premium computers and two ubuntu 11.04 and 11.10 on my home network. I cannot see or connect to any of them from the Ubuntu computers. 

Output from findsmb


                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
output from iptables 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by capscrew on 2011-11-14
> **wvcadle said:**
> I've got everything set up, per instructions here: [http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/).

The only thing I can't do is see my Windows shares in Ubuntu.  I can browse from Windows and see my Ubuntu shares.

I'm getting an error: Unable to mount location. Failed to retrieve share list from server.

Thanks in advance.

The tutorial that you followed assumes that you have some sort of name  services for the LAN configured.  By default Ubuntu Desktop does not make allowances for LAN side hosts/DNS or NETBIOS name services.  And why should it?  Local name services are not needed unless you are going to interact with another host (i.e communicating via either hostname of NETBIOS NAME).

If you are going to use the SMB/CIFS protocol then you will ultimately be using NETBIOS to identify hosts with SMB shares.

The easiest way to do that is to that is to configure Samba to explicitly broadcast its NETBIOS name.  This probably should be the same as the hostname as long as it is less than 15 characters.

To determine the hostname you can use the command *hostname *from the terminal.  The hostname of my desktop machine is *malibu*.  here is what is displayed ```
bruce@malibu:~$ hostname
malibu
```

To configure Samba to use the hostname as the NETBIOS name you need to edit the /etc/samba/smb.conf file.  To set the broadcast method you need to edit the same file.  The edited lines look like this on my machine```
netbios name = malibu
name resolve order = bcast 
```

These two lines should be added to the [global] section of the smb.conf file.  You need to edit this as root.  You can do this with this command from the terminal```
gksudo gedit /etc/samba/smb.conf
```

Now you need to restart the 2 samba daemons (processes) like this -- first the smbd daemon```
sudo service smbd restart
```

Then the nmbd daemon```
sudo service nmbd restart
```

If you have problems with restarting the services, just reboot the machine.

At this point you should be able to see the server and what ever shares you have.  For a more detailed description of what I just outlined you can see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1879527") (post #4 on) and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1872904&page=2") (post #14 on).

---

### Post by capscrew on 2011-11-14
> **dendari said:**
> I am having the same problem. I have two win7 home premium computers and two ubuntu 11.04 and 11.10 on my home network. I cannot see or connect to any of them from the Ubuntu computers. 

Output from findsmb
```


                                *=DMB
                                +=LMB
IP ADDR         **[COLOR="Red"]NETBIOS NAME[/COLOR]**     WORKGROUP/OS/VERSION 
```

The tool findsmb assumes your host broadcasts your NETBIOS NAME (see [COLOR="Red"]**red above**[/COLOR])> 

---------------------------------------------------------------------
output from iptables 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

You firewall is not blocking anything.

See my post right after your post.

---

### Post by dendari on 2011-11-15
This seemed to work perfectly thanks. 


> **capscrew said:**
> 

The easiest way to do that is to that is to configure Samba to explicitly broadcast its NETBIOS name.  This probably should be the same as the hostname as long as it is less than 15 characters.

To configure Samba to use the hostname as the NETBIOS name you need to edit the /etc/samba/smb.conf file.  To set the broadcast method you need to edit the same file.  The edited lines look like this on my machine```
netbios name = malibu
name resolve order = bcast 
```

These two lines should be added to the [global] section of the smb.conf file.  You need to edit this as root.  You can do this with this command from the terminal```
gksudo gedit /etc/samba/smb.conf
```



---

### Post by Morbius1 on 2011-11-15
Now that this is apparently solved I'm rather curious as to how you have come to the following conclusions:
> By default Ubuntu Desktop does not make allowances for LAN side hosts/DNS or NETBIOS name services.> To configure Samba to use the hostname as the NETBIOS name you need to  edit the /etc/samba/smb.conf file.  To set the broadcast method you need  to edit the same file.  The edited lines look like this on my machine
```
netbios name = malibu
name resolve order = bcast
```There may be issues with nmbd starting at boot but the setting of the netbios name to hostname happens by default in every Ubuntu and every Ubuntu derivative I've used. It won't show up in smb.conf explicitly but smb.conf is really a "diff" file that allows the user to modify samba's configuration without looking at the entirety of samba's default setup. If you run the following command without adding "netbios name" to smb.conf it should show you that the netbios name has already been set to the hostname:
```
testparm -sv | grep "netbios name"
```There is one big problem however and that has to do with Ubuntu's installer. If I install Ubuntu on my desktop and my name is alexander and I'm not paying attention, the installer will make the hostname: alexanders-desktop. That exceeds the 15 character length requirement and smb.conf can be used to correct it by adding the "netbios name" explicitly.

I have no issue with putting bcast first in the "name resolve order" ( or in your case the only option ) but I have been admonished for suggesting it by member redmk2: "I'm not big on altering the smb.conf file in idiosyncratic ways." Didn't seem idiosyncratic to me :)

---

### Post by capscrew on 2011-11-15
From the NMBD man pages...```
[COLOR="Blue"]       Amongst other services, nmbd will listen for such requests, and if its
       own NetBIOS name is specified it will respond with the IP number of the
       host it is running on. [B][I]Its "own NetBIOS name" is by default the primary
       DNS name of the host it is running on, but this can be overridden by
       the netbios name in smb.conf.[/I][/B][/COLOR]
```

> **Morbius1 said:**
> Now that this is apparently solved I'm rather curious as to how you have come to the following conclusions:
There may be issues with nmbd starting at boot but the setting of the netbios name to hostname happens by default in every Ubuntu and every Ubuntu derivative I've used. 

I'll bet that you are using static IP addressing and hostnames resolve to those IP addresses. If your LAN side IP addressing is configured to resolve hostnames via hosts/DNS (via your router or /etc/host name file), then indeed Samba will have the netbios name configured, but it comes from the conversion of hostname to NETBIOS name (see above in blue).  On the other hand, if you explicitly add the parameter to the smb.conf file then the *nmbd daemon will not use host/DNS names at all (again, see above in blue).*
> It won't show up in smb.conf explicitly but smb.conf is really a "diff" file that allows the user to modify samba's configuration without looking at the entirety of samba's default setup. 
This isn't exactly correct.  The testparm command **parses the smb.conf file and provides the output to stdout**.  The switches control what output is displayed.  From the man pages for testparm ```
[COLOR="Blue"]    -s
           Without this option, testparm will prompt for a carriage return
           after printing the service names and before dumping the service
           definitions.
[/COLOR]
```  In this case testparm dumps all the explicit user defined parameters (no defaults and no comments.```
[COLOR="Blue"]-v
           If this option is specified, testparm will also [B]_output all options_
           _that were not used in smb.conf_[/B](5) and are thus set to their
           defaults.
[/COLOR]
```

In this case we have *all but the defaults*.  If you add the 2 switches together you get both the default and the user explicitly defined parameters.> 

If you run the following command without adding "netbios name" to smb.conf it should show you that the netbios name has already been set to the hostname:
```
testparm -sv | grep "netbios name"
```
Ahhhh, but **this does not show how the NETBIOS name was configured**, *only that it has been configured*.  On a default install of Ubuntu Desktop the typical user allows the IP addressing to be configured via DHCP and there is no provision for mapping the hostname to the IP address of either the Ethernet (eth) or Wireless (wlan) interface.  > 
There is one big problem however and that has to do with Ubuntu's installer. If I install Ubuntu on my desktop and my name is alexander and I'm not paying attention, the installer will make the hostname: alexanders-desktop. That exceeds the 15 character length requirement and smb.conf can be used to correct it by adding the "netbios name" explicitly.

I have no issue with putting bcast first in the "name resolve order" ( or in your case the only option ) but I have been admonished for suggesting it by member redmk2: "I'm not big on altering the smb.conf file in idiosyncratic ways." Didn't seem idiosyncratic to me :)
I don't know the circumstances for your admonishment, but I assure you that it is normal and if you think about it the only correct conclusion.

If we break down what the name resolve order does we can eliminate the confusion.  From the relevant man pages```
[COLOR="DarkGreen"]name resolve order (G)

           This option is used by the programs in the Samba suite to determine
          *** what naming services to use and in what order to resolve host names***
           to IP addresses. [I]Its main purpose to is to control how netbios name
           resolution is performed.[/I] The option takes a space separated string
           of name resolution options.
[/COLOR]
```

So the *name resolve order* configures what database (file) we use for name resolution.  These are```
[COLOR="Purple"]lmhosts : Lookup an IP address in the Samba lmhosts file.

**host** : Do a standard host name to IP address resolution, using
               the system /etc/hosts , NIS, or DNS lookups

**wins** : Query a name with the IP address listed in the
               WINSSERVER parameter.

**bcast** : Do a _*broadcast on each of the known local interfaces*_
               listed in the interfaces parameter.
[/COLOR]

```

We can quickly eliminate 2 of the above parameters (lmhosts and wins) as they are not used it a typical installation.  If we have explicitly configured the NETBIOS name in the smb.conf file then the *hosts parameter* also can be eliminated as it is not going to be used either.  This leaves us with *bcast *only.

Make no mistake about it, one should only use this in conjunction with the explicit configuration of the NETBIOS name.  Thus, the following is correct ```
netbios name = <hostname> # less than 15 characters
name resolve order = bcast
```.

---

### Post by Morbius1 on 2011-11-15
[1] I am not using static ip addresses.

[2] My definition of the function of smb.conf is pretty much correct in that it will only show a subset of the available options and is not in itself the total of how samba functions. The "s" switch has to do with an intervening carriage return whereas the "v" switch has to with what level of detail you want to see. No "v" and you will see only smb.conf's contribution. With the "v" and you will see it all.

[3]
> [QUOTE]If you run the following command without adding "netbios name" to smb.conf it should show you that the netbios name has already been set to the hostname:
```
testparm -sv | grep "netbios name"
```Ahhhh, but this does not show how the NETBIOS name was configured, only that it has been configured. On a default install of Ubuntu Desktop the typical user allows the IP addressing to be configured via DHCP and there is no provision for mapping the hostname to the IP address of either the Ethernet (eth) or Wireless (wlan) interface. [/QUOTE]It does for every linux I have ever installed and that's how samba can automatically sets the netbios name to the hostname. 

[4] That's why I asked the question since your conclusion that the netbios name must be configured explicitly in smb.conf ignores the fact that it's set automatically.

Just to be clear I have no disagreement with the steps you provided dendari and have offered the exact same solution myself if there is a netbios name length and a name resolution order problem at the same time. And it certainly won't do any harm to suggest that everyone explicitly set the netbios name in smb.conf. I was just curious as to why you thought it was not functioning as designed.

---

### Post by capscrew on 2011-11-15
> **Morbius1 said:**
> [1] I am not using static ip addresses.

How is your hostname to IP mapping (host/DNS) handled?  Does the router handle that for you?  Most users routers do not have DNS setup for DHCP (ip pool).> 
...

It does for every linux I have ever installed and that's how samba can automatically sets the netbios name to the hostname.
See above.  The NETBIOS name is either converted from the hostname; configured by /etc/hosts or DNS (BIND9/DNSmasq) or the NETBIOS name is set explicitly.  Once again how do you set your name servces?> 

[... That's why I asked the question since your conclusion that the netbios name must be configured explicitly in smb.conf ignores the fact that it's set automatically.
If you think of the NETBIOS name as converted from host/DNS or defined in the smb.conf file, there is no automatically defined.  Stating that another way; Samba does not directly look at the /etc/hostname file or use the gethostbyname() function.  It is totally dependant on the configuration of the etc/hosts file or DNS if you are going to use DNS style naming (host name).  If it truly was automatic (as in using /etc/hostname or gethostbyname() ) then all those that needed help would have already had a NETBIOS name (as you say) and they would not be here looking for help. > 

Just to be clear I have no disagreement with the steps you provided dendari and have offered the exact same solution myself if there is a netbios name length and a name resolution order problem at the same time. And it certainly won't do any harm to suggest that everyone explicitly set the netbios name in smb.conf. I was just curious as to why you thought it was not functioning as designed.
It is functioning as designed.  You don't seem to understand the relationship between Samba and the hostname (DNS) name resolution.

---

### Post by Morbius1 on 2011-11-15
My router doesn't do squat except not interfere with things. In fact I can't ping this machine from another machine on the lan by name only by ip address.

I have not explicitly set my netbios name in smb.conf

And my name resolve order = lmhosts host wins bcast

My etc/hosts file has this relevant contents which won't provide much help:
> 127.0.0.1    localhost
127.0.1.1    morbius
And yet I can browse and be browsed by everyone on the lan - Windows, Linux, and Mac.
> If it truly was automatic (as in using /etc/hostname or gethostbyname() ) then all those that needed help would have already had a NETBIOS name (as you say) and they would not be here looking for help. That is the very core of my original inquiry. They do have a netbios name. It's right there in the default setting of samba. I'd be willing to bet that for a lot of users it's something like "matt-Satellite-L35" - a full 18 characters long. It's not their fault it's the way the Ubuntu installer created the original hostname. Having them set it explicitly in smb.conf and telling them about the character limit fixes that part of the problem.

The bcast first fixes another problem. Your post is a 2-fer.

This "discussion" has deteriorated rapidly and I'm not learning anything new. There doesn't seem to be much to gain from arguing over arguing's sake.

---

### Post by capscrew on 2011-11-15
> **Morbius1 said:**
> ... That is the very core of my original inquiry. They do have a netbios name. It's right there in the default setting of samba.
Where is the "default setting"?  How does the information get to "there"?  There must be something (usually a file) that the application (Samba) pulls data from for configuration.  I'm curious too.> 

This "discussion" has deteriorated rapidly and I'm not learning anything new. There doesn't seem to be much to gain from arguing over arguing's sake.
I'm not arguing at all.  Who says that you are the only one who wants to learn something.  Maybe you can be the teacher.

I believe you are that one that originated this line of conversation.  If you want to go away mad, who am I to stop you.  In my book that makes you the grumpy one.  ;-)

**Edit:** It should be pointed out that however the NETBIOS name is configured, it still needs to be resolved to the IP address of the machine.  That really is the core of this -- how Samba goes about mapping these 2 bits of information.

---

### Post by wvcadle on 2011-11-15
Original poster: Seems a bit technical, but I'll give your suggestions a try this evening.

---

### Post by Morbius1 on 2011-11-21
> **capscrew said:**
> Make no mistake about it, one should only use this in conjunction with the explicit configuration of the NETBIOS name.  Thus, the following is correct ```
netbios name = <hostname> # less than 15 characters
name resolve order = bcast
```.
I have made what I believe to be a good faith effort to try to reproduce the conditions that would make the [COLOR=Blue]explicit[/COLOR] setting of netbios name to hostname in smb.conf a requirement ( other than to correct for a length issue ) and as yet I have not been successful. Nothing I have done so far has prevented my netbios name from becoming my hostname automatically.  I'm beginning to believe that the thought that it has to be explicitly set came about because of a misunderstanding of what testparm does and what it displays as output.

Testparm is at one level a debugger but it's also an interpreter  and report builder:

If you run the command:
```
testparm 
```The system will take the following steps as it builds the report:

* Without specifying a file path it assumes /etc/samba/smb.conf so it runs: "testparm /etc/samba/smb.conf"
* It reads the file and interprets it ( So comments are removed and it will convert certain parameters like "writable = yes" to "read only = no" )
* It then compares it to the defaults set up when samba support was originally compiled for use in Ubuntu.
* Any additions that are not in the defaults are kept in the report.
* Any parameters that have values that are different from the defaults are kept.
* Any parameters that have values that are the same as the default are ignored.
* All of the default parameters that have not been modified are not saved to the report

What you will get as output is what affect your smb.conf alone will have on the defaults.
"netbios name" will only show up if you added it yourself to smb.conf [COLOR=Blue]**AND**[/COLOR] only if it's different from the defaults.

If you run:
```
testparm -v
```The system will do everything the previous command did except it will not only report any additions you have in smb.conf but also all of the default parameters and reflect either their default values or values that were modified by smb.conf. Here is where you will see the default value for "netbios name"

You can take this one step further if you run the following command:
```
testparm -v /dev/null
```This will force testparm to make a comparison to the defaults not from smb.conf but from a dummy empty file. Since there is nothing to add or modify the report will show you the pure unadulterated set of parameters and the default values that samba starts off with. This will show that "netbios name" was set to your hostname. It may be too long and force you to add it explicitly to smb.conf but it will be your hostname.

[COLOR=Black]Samba as implemented by Ubuntu is meant to work out of the box. It may need some help ( placing bcast first ) and it comes with rules ( netbios name must be 15 characters or less ) but it should work out of the box. If the Ubuntu installer would prevent the user from setting up a hostname in excess of 15 characters ( which is not a Linux requirement ) the netbios name would not be an issue for Samba.[/COLOR]

---

