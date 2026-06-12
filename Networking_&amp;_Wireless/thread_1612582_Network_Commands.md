---
title: "Network Commands"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by halen666 on 2010-11-03
HI guys, I like ubuntu so much that I "totally" abandoned Windows. The problem I have is that I really need some of the command prompt commands that I had in windows. I will type a list of some of those commands and please let me know about an alternative to that command in Linux. I does not matter whether I have to install extra packets.
*net view   <--- I really need this one, btw smbtree does now work for me, for I don;t get anything back from the command.

net share
net user
net use  
(Actually any net command in general)
nircmd  <-I know, this is extra command in windows, but it would be nice to have such a tool in ubuntu

Thank you guys and have a good one.

---

### Post by lukeiamyourfather on 2010-11-03
I don't know much about the net commands in Windows but I'll do my best.

> **halen666 said:**
> 
net view


Not sure about that one. Linux handles networking in general differently. For example if I wanted to get files from a network share I'd just mount the share to a folder on my desktop or the mounts folder (/mnt/whatever). Hopefully someone else has a better answer.

> **halen666 said:**
> 
net share


This depends on what protocol is being used. If using Samba for SMB, all of the shares will be in the Samba configuration file (/etc/samba/smb.conf if I remember correctly). You can get that information with any of these commands.

```

cat /etc/samba/smb.conf
more /etc/samba/smb.conf
tail /etc/samba/smb.conf

```

NFS shares will be in the exports file (/etc/exports). The same commands can be used to read that file: cat, more, tail, etc.

> **halen666 said:**
> 
net user


Each local user has a home directory so just list the contents of that and you have all the users (except for root which is /root).

```
ls /home
```

> **halen666 said:**
> 
net use


I assume this shows connected network drives? Because that's what it shows for me. In that case all automatically mounted drives will be specified in the file system table (/etc/fstab). Alternatively you can use the disk free command (df or df -h) to list all mounts and their free space available. 

> **halen666 said:**
> 
nircmd


I don't know this one but did a quick search. Most of the things it does are native commands in Linux anyway. That nircmd covers a lot of unrelated stuff so are there specific things you're looking for?

---

### Post by SeijiSensei on 2010-11-03
> **halen666 said:**
> *net view   <--- I really need this one, btw smbtree does now work for me, for I don;t get anything back from the command.

If you have a WINS server handling Netbios name resolution, you can use smbclient to list the available machines with "smbclient -L WINS-server-name".  Even without a WINS server, you may be able to get a list of available machines by using "smbclient -L" against any Windows machine on the network.

If you want to conduct a census of the machines on the network, you can run "nmap -sP 192.168.1.0/24" to ping all the hosts in that network block and return the ones it sees.  If you have reverse DNS properly configured, nmap will return the hostname for each resolvable machine.  If you want to know a machine's netbios name, you can use "nmblookup -A target.host.ip.addr".

I once wrote a script that used "nmap -sP" to enumerate all the hosts on a network, then used "nmblookup -A" to determine each one's Netbios name.  (The script then wrote the appropriate "zone" files and updated the local bind9 DNS server with the host/IP pairs.)

Traditional Windows network browsing relies on the machines all broadcasting their names.  *nix networks generally use the client/server model instead.  KDE once had a daemon called lisa that provided these kind of browsing services on mixed networks.  It seems to have been [removed from recent distributions]("http://packages.ubuntu.com/search?keywords=lisa") however.

> net use

*nix doesn't have the concept of "drive mapping"; instead resources are simply mounted into the directory tree.  So the equivalent of "net use" is probably "smbmount //server/share /some/mountpoint".  

> nircmd  <-I know, this is extra command in windows, but it would be nice to have such a tool in ubuntu

What does it do?

---

### Post by halen666 on 2010-11-05
THank you guys that was helpful. Nircmd is a multi command line tool that does tons of stuff. It can open the cd-rom, change screen resolution, hide/show windows, display messages, make computer beep, etc. I have found many tools to do some of these tasks in linux, but I haven't found one that does most of them in a single tool. Anyway, is is not important anymore.

Thank you

---

