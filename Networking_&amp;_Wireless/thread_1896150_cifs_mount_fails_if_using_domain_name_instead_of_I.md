---
title: "cifs mount fails if using domain name instead of IP"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by Sidrabs on 2011-12-16
Hello,

Why is that

$ sudo mount -t cifs //192.168.0.100/http -o username=myUsr,password=myPwd ./FolderName

works on my Ubuntu 11.10, while

$ sudo mount -t cifs //domain.name/http -o username=myUsr,password=myPwd ./FolderName

doesn't? The domain.name is defined in the hosts file and resolves to the 19.2168.0.100, if pinged for example. The same is true if I try to connect to the server using Nautilus File / Connect to Server: with IP goes fine, with domain name - fails.

---

### Post by KeithKris on 2011-12-16
What errors are you getting (if any?)  What's the process doing?  Try adding an strace in there and post the output (sudo strace mount -t cifs //domain.name/http -o username=myUsr,password=myPwd ./FolderName)

---

### Post by capscrew on 2011-12-16
> **Sidrabs said:**
> Hello,

Why is that

$ sudo mount -t cifs //192.168.0.100/http -o username=myUsr,password=myPwd ./FolderName

works on my Ubuntu 11.10, while

$ sudo mount -t cifs //domain.name/http -o username=myUsr,password=myPwd ./FolderName

doesn't? The domain.name is defined in the hosts file and resolves to the 19.2168.0.100, if pinged for example. The same is true if I try to connect to the server using Nautilus File / Connect to Server: with IP goes fine, with domain name - fails.

As far as I know there are only 2 correct ways to use mount.cifs.  You can use **//IP_address/share_name** or you can use **//NETBIOS_NAME/share_name**.

There is a 15 character limit on NetBIOS names.  Samba can convert the machines hostname into a NetBIOS name or you can explicitly create a NETBIOS name in the smb.conf file

The hosts file (/etc/hosts) maps the hostname to IP address.  The FQDN should be listed as an alias.```
192.168.0.5  hostname hostname.domain
```

---

### Post by N00b-un-2 on 2011-12-16
It was my understanding that this is normal behavior when accessing anything on your local network.  The only time I type in a name instead of an ip address is when I access my DNS from a remote location outside of local network (like ssh from my cell phone for example)

---

### Post by capscrew on 2011-12-16
> **N00b-un-2 said:**
> It was my understanding that this is normal behavior when accessing anything on your local network.  The only time I type in a name instead of an ip address is when I access my DNS from a remote location outside of local network (like ssh from my cell phone for example)

You can have local (LAN) DNS style name resolution with, either a local DNS server or a /etc/hosts file on each machine.

---

### Post by Sidrabs on 2011-12-17
> **KeithKris said:**
> What errors are you getting (if any?)  What's the process doing?  Try adding an strace in there and post the output (sudo strace mount -t cifs //domain.name/http -o username=myUsr,password=myPwd ./FolderName)

Attached is the console output, it's too big to be politely inserted in the message body.

> **capscrew said:**
> As far as I know there are only 2 correct ways to use mount.cifs.  You can use **//IP_address/share_name** or you can use **//NETBIOS_NAME/share_name**.

There is a 15 character limit on NetBIOS names.  Samba can convert the machines hostname into a NetBIOS name or you can explicitly create a NETBIOS name in the smb.conf file

The hosts file (/etc/hosts) maps the hostname to IP address.  The FQDN should be listed as an alias.```
192.168.0.5  hostname hostname.domain
```

Well, if I replace the IP address with the Windows box NetBIOS name, it fails to find it with error "mount error: could not resolve address for MyNetBIOSName: Unknown error"

Also, if I complemented my hosts file with the hostname, as in you example, it resulted in the same error as previously with domain.name.

Regarding the smb.conf file, I am not sure how I should edit it to make the system treat the domain.name correctly, resolving it according to normal practices, to get the IP address, can you please tell me?

---

### Post by capscrew on 2011-12-17
> **Sidrabs said:**
> ...

Well, if I replace the IP address with the Windows box NetBIOS name, it fails to find it with error "mount error: could not resolve address for MyNetBIOSName: Unknown error"
That's not consistent with your earlier comment (e.g "*Why is that $ sudo mount -t cifs //192.168.0.100/http -o username=myUsr,password=myPwd ./FolderName **[COLOR="Indigo"]works on my Ubuntu 11.10[/COLOR]**.*....> 

Also, if I complemented my hosts file with the hostname, as in you example, it resulted in the same error as previously with domain.name.
Not sure what you mean here.

Maybe this is a semantics problem.  To me a *domain name *refers to the DNS domain assigned to your network (i.e mydomain.com).  The term FQDN refers to the DNS name assigned to a specific host in the network such as *[COLOR="Red"]hostname[/COLOR].[COLOR="Blue"]domain[/COLOR].TLD*.  TLD refers to the Top Level Domain such as .com or .org, etc. > 

Regarding the smb.conf file, I am not sure how I should edit it to make the system treat the domain.name correctly, resolving it according to normal practices, to get the IP address, can you please tell me?

What name are you really referring to?  The hostname (FQDN) or domain name (DNS domain).  Samba converts hostnames into NetBIOS names and ultimately maps that name to the IP address.

Once again what do you mean by **[COLOR="Green"]domain.name[/COLOR]**?

---

### Post by Sidrabs on 2011-12-18
> **capscrew said:**
> Once again what do you mean by **[COLOR="Green"]domain.name[/COLOR]**?

It's just more convenient to refer to PCs in the LAN (including the virtual machines with individual IP addresses), using a human-readable ID. So, I keep a list of local IP addresses in my hosts file, using domain names like server1.vm.win2008server and server1.vm.ubuntu11

I am not sure where I got inconsistent when I said using the Winbox NetBIOS name did not work. Previously I tried using IP address (and that worked) and using domain.name, hoping it would be resolved according to hosts file (and that did not work).

---

### Post by capscrew on 2011-12-18
> **Sidrabs said:**
> It's just more convenient to refer to PCs in the LAN (including the virtual machines with individual IP addresses), using a human-readable ID. So, I keep a list of local IP addresses in my hosts file, using domain names like server1.vm.win2008server and server1.vm.ubuntu11
I understand the hosts/DNS mechanism for TCP/IP.  Samba (using *nmbd*) converts the hostname portion of the DNS FQDN to a NETBIOS name.  The problems you are having are related to this internal conversion.  I feel part of the problem we are having in discussing this issue might be the nomenclature (names) we use to ID the hosts.

Please post the output of ```
cat /etc/hosts
```> 

I am not sure where I got inconsistent when I said using the Winbox NetBIOS name did not work. Previously I tried using IP address (and that worked) and using domain.name, hoping it would be resolved according to hosts file (and that did not work).
Samba consists of 2 daemons.  These are *smbd *and *nmbd*. You can see these with this command```
pgrep -l mbd
```  You should have at least 2 of *smbd* and 1 of *nmbd*.

I believe you will find the problem is that Samba is having trouble building the Browse list (BL).  The BL is what is used by Samba to display the shares.

You can check the browsing capabilities from the command line using *smbtree*.  Please post the output of ```
smbtree -d3
```

Use the code blocks feature (the # icon) at the top of the editor to enclose the text.

---

### Post by Sidrabs on 2011-12-18
> **capscrew said:**
> Please post the output of ```
cat /etc/hosts
```
That file is pretty big and that would be kind of weird to publicly post all my LAN IPs. I can confirm that when I do ```
$ ping internal.domain.name
```, I see it properly resolved and the ping itself is successful. The line defining that domain name in the hosts file is similar to this:
```
192.168.0.100	internal.domain.name
```

> **capscrew said:**
> Samba consists of 2 daemons.  These are *smbd *and *nmbd*. You can see these with this command```
pgrep -l mbd
```  You should have at least 2 of *smbd* and 1 of *nmbd*.

Indeed, I have two cmbd daemons and one nmbd daemon.

> **capscrew said:**
> I believe you will find the problem is that Samba is having trouble building the Browse list (BL).  The BL is what is used by Samba to display the shares.

You can check the browsing capabilities from the command line using *smbtree*.  Please post the output of ```
smbtree -d3
```

The output from this command is pretty huge and contains a lot of information about my local samba config (ie share names and IP addresses), so I don't think it's a good idea to dump all of it here. Perhaps there is some specific part of this output that would be meaningful to quote?

I can say that output contains no trace about the share on the Windows server what I was trying to mount on my Ubuntu, only references to my local adapter IP addresses and my local samba shares, and couple of other Ubuntu's with samba shares. But I don't have problems with samba shares on my Ubuntu, I have problems with connecting with native Windows share on Windows PC (well, it's a VM, but there's no difference). The output contains also several times "SPNEGO login failed: Logon failure", I don't know if that's of any significance.

---

### Post by KeithKris on 2011-12-19
> **Sidrabs said:**
> Attached is the console output, it's too big to be politely inserted in the message body.


Keep in mind that I'm no Samba expert, but the system call trace you posted makes it look like it's not even trying to resolve the name.  Note these lines:

```
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffc87ff4000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7ffc87ff4000, 4096)            = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3

```

It opens nsswitch.conf, closes it, but never bothers to go to DNS.  Either Samba isn't supposed to support what you want to do, or something's going on with name resolution.  What does your nsswitch.conf look like?

EDIT:  I found this also, which may help:  

> 7.3.4.4 dns proxy

If you want the domain name service (DNS) to be used if a name isn't found in WINS, you can set the following option:

[global]
    dns proxy = yes

This will cause nmbd to query for machine names using the server's standard domain name service. You may wish to deactivate this option if you do not have a permanent connection to your DNS server. Despite this option, we recommend using a WINS server. If you don't already have any WINS servers on your network, make one Samba machine a WINS server. Do not, however, make two Samba machines WINS servers (one primary and one backup) as they currently cannot exchange WINS databases.

Is dns proxy set up in your smb.conf?  Source:  [http://oreilly.com/openbook/samba/book/ch07_03.html](http://oreilly.com/openbook/samba/book/ch07_03.html)

---

### Post by capscrew on 2011-12-19
> **KeithKris said:**
> Keep in mind that I'm no Samba expert, but the system call trace you posted makes it look like it's not even trying to resolve the name.  Note these lines:

```
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffc87ff4000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7ffc87ff4000, 4096)            = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3

```

It opens nsswitch.conf, closes it, but never bothers to go to DNS.  Either Samba isn't supposed to support what you want to do, or something's going on with name resolution.  What does your nsswitch.conf look like?

Samba has its own lookup order.  In the global section of the smb.conf file, see```
name resolve order = lmhosts host wins bcast 
``` > 

Is dns proxy set up in your smb.conf?  Source:  [http://oreilly.com/openbook/samba/book/ch07_03.html](http://oreilly.com/openbook/samba/book/ch07_03.html)

This is a book about Samba 2.0.  I believe this was before Win2k when windows NT and Win95/98  was current.

---

