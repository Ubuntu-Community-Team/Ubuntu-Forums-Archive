---
title: "NFS not working at boot"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by brel on 2009-07-15
Yes, another person having problems with NFS mounts not being mounted on system startup. Like everyone else: ```
mount -a
``` mounts my nfs drive no problem if I type it in manually after booting up.

I've tried a few of the solutions proposed but have had no success:
-I rearranged the order in init.d/mountall but that didn't work
-I've put ```
mount -a
``` in my rc.local

I ended up manually logging the output from the rc.local mount -av command and what I get is:
```
mount.nfs: DNS resolution failed for 192.168.0.3: Name or service not known

```

First question: why is nfs doing a dns lookup on an IP address?

I suppose rc.local is getting run before some required networking service comes up. However from what I can tell, rc.local runs as S99 and so is presumably the last to go. There are a few other S99 commands but they don't seem network related. 

My next plan of attack is to install autofs but all this seems like a lot of hoops to jump through for such a simple need.

Any help would be appreciated.

---

### Post by renkinjutsu on 2009-07-15
try setting a static IP for yourself instead of using DHCP .. i don't know if that has anything to do with it, but automounting NFS works for me

also, test if your network configurations work right at bootup .. so right after your computer boots up, don't log in to a gnome session.. press CTRL+ALT+F1 to login through a terminal and try to ping google or something.. i remember having a problem with networking not working until i logged in through gdm

---

### Post by paulisdead on 2009-07-15
Try putting an entry in the client's /etc/hosts file with the name and IP of the server.  I've seen NFS stall while mounting if there's no DNS or hosts entry for the server.

---

### Post by dmizer on 2009-07-16
Strange ...

What's your current /etc/fstab mount line for your share? Are you running through OpenDNS by chance? How about net connection sharing? Any other unusual network configurations (ie. something other than: modem -> router -> networked computers).

---

### Post by brel on 2009-07-16
Thanks for the ideas.

I've checked my /etc/hosts and there is an entry for 192.168.0.3 so it's not that.

Here's the line from my fstab:
```
192.168.0.3:/volume1    /mnt/hugo   nfs rw,nosuid,hard,intr   0   0
```

As I said, once the computer is up and running, mount -a works fine. And my setup couldn't be more basic : router connecting my computer and the nas. I'm not running opendns (as far as I know). 

I'll next check if I can run mount -a before logging into kde.

---

### Post by dmizer on 2009-07-16
Are you connected wirelessly, perhaps with WPA2 encryption or the like?

Please post the output of:
```
sudo iptables -L
```

---

### Post by DesiBabu on 2009-07-17
root@i7Ubuntu:/etc# mount -av
mount.nfs: timeout set for Fri Jul 17 01:47:53 2009
mount.nfs: text-based options: 'rsize=8192,wsize=8192,timeo=14,soft,intr,addr=127.0.1.1'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting i7ubuntu:/u01/shared

root@i7Ubuntu:/etc# mount -a
mount.nfs: access denied by server while mounting i7ubuntu:/u01/shared
root@i7Ubuntu:/etc# 

/etc/exports has the following:


/u01/shared 192.168.15.111(rw,no_root_squash,no_subtree_check,async)
/u01/shared 192.168.15.112(rw,no_root_squash,no_subtree_check,async)
/u01/shared 192.168.15.100(rw,no_subtree_check,async)
/u01/shared 192.168.15.131(rw,no_root_squash,no_subtree_check,async)
/u01/shared 192.168.15.132(rw,no_root_squash,no_subtree_check,async)

/etc/fstab has the following

i7ubuntu:/u01/shared /shared_u01 nfs rsize=8192,wsize=8192,timeo=14,rw,soft,intr 0 0


root@i7Ubuntu:/etc# mount /shared_u01
mount.nfs: access denied by server while mounting i7ubuntu:/u01/shared
root@i7Ubuntu:/etc# 

ls -latr of / gives

drwxrwxrwx   3 root root  4096 2009-07-17 00:58 u01
drwxr-xr-x   2 root root  4096 2009-07-02 20:34 shared_u01



This used to work a few days back. Not sure what happened.

The server and client are on the same machine....

Any idea where I should look?

Thanks

---

### Post by dmizer on 2009-07-17
> **DesiBabu said:**
> The server and client are on the same machine....

Any idea where I should look?

If the server and client are on the same machine, then you'll have to export to localhost.

---

### Post by brel on 2009-07-18
I checked to see if I could mount before logging into kde and I can so I still don't really know where the problem is. I think I'm just going to try and get autofs setup.

Thanks again for all the help.

---

### Post by brel on 2009-07-18
Installed autofs and it works like a charm. Followed the guide here: [https://help.ubuntu.com/community/SettingUpNFSHowTo#Automounter](https://help.ubuntu.com/community/SettingUpNFSHowTo#Automounter)

---

