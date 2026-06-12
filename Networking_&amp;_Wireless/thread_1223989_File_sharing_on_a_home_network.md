---
title: "File sharing on a home network"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by Volume on 2009-07-26
What is the best way to share files on a simple (2 PC) home network?  Basically, I have 2 Ubuntu PCs, and both are plugged into a common router via some CAT6.  

Should I use something like SSH, or NFS?  What is the difference between the two?

Thanks all.

---

### Post by philcamlin on 2009-07-26
try samba:popcorn:

---

### Post by Volume on 2009-07-26
> **philcamlin said:**
> try samba:popcorn:

Super noob at this.  I really don't know where to start.  What is Samba used for?  I thought this was for Windows file sharing?

---

### Post by tomtheo on 2009-07-26
this samba how-to helped me out:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

you can also try giver (from add/remove programs) if you're looking to share just a few files

---

### Post by Volume on 2009-07-26
> **tomtheo said:**
> this samba how-to helped me out:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

you can also try giver (from add/remove programs) if you're looking to share just a few files

Thanks for the link, but I want to share files between 2 Ubuntu computers.  Neither PC has Windblows installed at all.

Any tips?

---

### Post by ericartman on 2009-07-26
I use amahi
[http://www.amahi.org/](http://www.amahi.org/)

Cart

---

### Post by dmizer on 2009-07-26
> **Volume said:**
> What is the best way to share files on a simple (2 PC) home network?  Basically, I have 2 Ubuntu PCs, and both are plugged into a common router via some CAT6.  

Should I use something like SSH, or NFS?  What is the difference between the two?

Thanks all.

SSH is encrypted and secure. If you are concerned about your data being accessed by an unauthorized person (as with a wireless network, or if you are accessing your data from remote), then SSH is one good way of insuring security. The downside to SSH is that because it's encrypted, some clock cycles are dedicated to encrypting and decrypting and this may slow things down depending on the capabilities of your computer.

Here is a good SSHFS howto: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

NFS is the standard file sharing protocol for Linux networks. It's faster than Samba, easy to set up, creates far less network traffic than Samba, and is more reliable than Samba. However, group and user permissions can be a real pain to work with if you don't give some thought to your network before setting it up

The 4th link in my sig outlines the steps necessary to configure both an NFS server and client.

Samba is the open source version of Windows proprietary file sharing protocol. It's good for networks which have a mix of various operating systems including Windows, Mac, and Linux. However, setting up a proper and seamless Samba file sharing network is extremely difficult and requires lots of CLI edits. While you can make basic file sharing work without the complexities of /etc/samba/smb.conf and /etc/fstab, you're bound to run into a host of limitations as a result.

The first link in my sig outlines the steps necessary to configure a robust Samba server. The second link in my sig outlines the steps necessary to configure a robust Samba client.

---

### Post by tomtheo on 2009-07-26
> **Volume said:**
> Thanks for the link, but I want to share files between 2 Ubuntu computers.  Neither PC has Windblows installed at all.

Any tips?

samba also works ubuntu-to-ubuntu. once you have it set up, i've found that sometimes the computer won't appear in the places > network folder but you can enter the computer's address in the location bar to connect (either smb://computer_name.local or smb://10.10.10.100). local ip address can be found by right clicking on the network manager applet > connection information.

---

### Post by Volume on 2009-07-27
Ok guys.  I got started with the NFS tutorial, but I'm running into a few problems:

```
mokrunka@Engineer:/$ sudo mount Nurse:/home 
mount: can't find Nurse:/home in /etc/fstab or /etc/mtab

```

Any suggestions?

Can I ask also that someone confirm that my network setup is valid, i.e. both computers should be able to communicate with each other? 

Both PCs have I-net access from the same router, and that router is connected to a DSL modem--each computer has a section of CAT6 running from it to the router.

---

### Post by dmizer on 2009-07-27
Do you have a static or DHCP network?

---

### Post by Volume on 2009-07-27
> **dmizer said:**
> Do you have a static or DHCP network?

Hmmm.  I don't know how too tell :confused:.

I am pretty sure my ISP has dynamic IPs, I thought they all did nowadays.  Is there any way I can find out?

---

### Post by lisati on 2009-07-27
samba should work, even if you don't have a Windows machine hooked up.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dmizer on 2009-07-28
> **Volume said:**
> Hmmm.  I don't know how too tell :confused:.

I am pretty sure my ISP has dynamic IPs, I thought they all did nowadays.  Is there any way I can find out?

If you have static IP, you would need to manually assign an IP address to each computer in your network (in other words, you would know if you had static IP). DHCP assigns IP addresses to your networked computers for you.

What router make and model number do you have?

---

### Post by Cavemann on 2009-07-28
Hello All

Do you mind if I join this thread as I too have a similar problem sharing files

I have 2 Windows computers and 2 Ubuntu (9.04)computers on my network.

All using DHCP and working, in that the windows computers see and access each other as well as the internet.

Each ubuntu computer sees the windows computers and can access them as well as the internet.

The ubuntu computers do not see each other on the network (ie show up when I click on the Network Places tab) however when I read the dhcp assigned ip address for the ubuntu computers I am able to ping each ubuntu computer from the other ubuntu computer but cannot access one ubuntu computer from the other.

I do not expect the windows computers to access the ubuntu computers at all (and hope they cant - different file system)

It seems as though the equivalent of windows sharing is not activated on the ubuntu computers?

Any help is appreciated

Regards
Peter

---

### Post by dmizer on 2009-07-28
> **Cavemann said:**
> Hello All

Do you mind if I join this thread as I too have a similar problem sharing files

I have 2 Windows computers and 2 Ubuntu (9.04)computers on my network.

All using DHCP and working, in that the windows computers see and access each other as well as the internet.

Each ubuntu computer sees the windows computers and can access them as well as the internet.

The ubuntu computers do not see each other on the network (ie show up when I click on the Network Places tab) however when I read the dhcp assigned ip address for the ubuntu computers I am able to ping each ubuntu computer from the other ubuntu computer but cannot access one ubuntu computer from the other.

I do not expect the windows computers to access the ubuntu computers at all (and hope they cant - different file system)

It seems as though the equivalent of windows sharing is not activated on the ubuntu computers?

Any help is appreciated

Regards
Peter

See the 6th link in my sig.

The file system doesn't matter. Ubuntu and Windows can share files between eachother with no problem.

---

### Post by madmax1735 on 2009-07-28
u can use p300 its a java based , so platform independent sharing software.... just make sure u have d latest java version installed... i think it version 6 update 14 rite now.

p300 works great for small networks..... get it from  [http://p300.eu/](http://p300.eu/)

---

### Post by Cavemann on 2009-07-28
Hi Guys

Thank you for your responses I will try it later tonight.

I had made the ubuntu computers on the same Workgroup as the other computers but obviously there is more to do.

Thanks again for your help - will be back later

Regards

Peter

---

### Post by Volume on 2009-07-28
> **dmizer said:**
> If you have static IP, you would need to manually assign an IP address to each computer in your network (in other words, you would know if you had static IP). DHCP assigns IP addresses to your networked computers for you.

What router make and model number do you have?

It is a Netgear 4 port router WGR614 V7.  I have done this once before with this router, I just can't remember how...  I'm taking notes this time, :).


Thanks for your help!

---

### Post by Freesprt30 on 2009-07-28
> **dmizer said:**
> See the 6th link in my sig.

.

well I am going to hitch hike too.  My prob is this.  I just set up a new ubuntu sys 8.10.  I have two XP machines that share together but I can not see my Ubuntu or vise versa.

   I followed everything above on link 6 as well as this guide [http://www.jonathanmoeller.com/screed/?p=532](http://www.jonathanmoeller.com/screed/?p=532)

When I click on network in places I see my 2 shares "print' and "test" as well as "windows Network"  

When i try to open it I get "Unable to mount location" Failed to retrieve share list from server

  Twice I have been able to see my windows machine but get that same message if a try to open the location.


 Last 2 time I can see my 2 xp machine but thats it.  

Any help would be appreciated


Sorry I hoped on this thread but thought it was about same thing

---

### Post by dmizer on 2009-07-28
> **Volume said:**
> It is a Netgear 4 port router WGR614 V7.  I have done this once before with this router, I just can't remember how...  I'm taking notes this time, :).


Thanks for your help!

No problem.

No matter what version of file sharing you decide to use, this configuration will be helpful.

Go to [http://www.routerlogin.net](http://www.routerlogin.net)

Default username and password is:
admin
password

If you've changed it, you'll need to enter the appropriate username and password. Now is a good time to think about changing the default username and password if you haven't already.

From the main menu of your router, go to "Advanced" and click on "LAN IP Setup".

From there, you should add both of your networked computers to the "Address Reservation" field. You can find them and their MAC addresses (if they are turned on and connected to the internet) under the "Attached Devices" menu. You may want to do this one at a time to each computer. Give each computer a different IP address, but make sure the IP addresses are within the range shown between the "Starting IP address" and "Ending IP Address". Make notes of which IP addresses are assigned to which computers.

Reboot both of your computers, report the results here (IP address and computer name)

Also post your current /etc/exports file from both computers.

---

### Post by Volume on 2009-07-28
Thank you Dmizer.  I am going to try your suggestions when I get home.  However, why do I have to assign the IP to each PC under the Address Reservation?  Is this simply to ensure that each PC gets the same IP address each time, thus the /etc/exports file will work if I associate an IP address to the hostname?

Steve

---

### Post by Volume on 2009-07-28
> **dmizer said:**
> No problem.



Also post your current /etc/exports file from both computers.

My PC (Engineer)

```
mokrunka@Engineer:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
mokrunka@Engineer:~$ 

```

2nd PC (Nurse)

```
jenandsteve@Nurse:~$ cat /etc/exports 
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

```

I was able to get SSH working from the GUI (PLACES--->Connect to Server).  How do I get it working from the command line, using host names rather than IPS?

Thank you very much so far!

---

### Post by dmizer on 2009-07-28
> **Volume said:**
> Thank you Dmizer.  I am going to try your suggestions when I get home.  However, why do I have to assign the IP to each PC under the Address Reservation?  Is this simply to ensure that each PC gets the same IP address each time, thus the /etc/exports file will work if I associate an IP address to the hostname?

Steve

Yes, once you've assigned IP addresses to each machine, then you can edit /etc/hosts and add each machine's IP address and name. That way, you can have name resolution.

Here is an example from my network:

I have two computers. One is named tokkyu and the other is named tsubasa.
tokkyu has an IP address of 192.168.1.20
tsubasa has an IP address of 192.168.1.21

Here is the /etc/hosts file from tokkyu:
```
127.0.0.1 localhost
127.0.1.1 tokkyu
192.168.1.21 tsubasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Here is the /etc/hosts file from tsubasa:
```
127.0.0.1 localhost
127.0.1.1 tsubasa
192.168.1.20 tokkyu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

So, when I "ping tokkyu" from tsubasa, I get replies. Once you've done this, then it's easy to get things working from the command line via host name.

---

### Post by magh-87 on 2009-07-29
> **dmizer said:**
> If you have static IP, you would need to manually assign an IP address to each computer in your network (in other words, you would know if you had static IP). DHCP assigns IP addresses to your networked computers for you.

What router make and model number do you have?

When I setup my router at my girlfriends there wasn't any need to assign IPs to the computers despite her being on a static. Perhaps today's routers are becoming more sophisticated? I have seen the option to assign IP's to routers however :/

---

### Post by dmizer on 2009-07-29
> **magh-87 said:**
> When I setup my router at my girlfriends there wasn't any need to assign IPs to the computers despite her being on a static. Perhaps today's routers are becoming more sophisticated? I have seen the option to assign IP's to routers however :/

No, this is not static. This is DHCP with permanent IP leases assigned according to MAC address. We're just locking your computers into a specific IP so that they don't move around when rebooted. This is a more sophisticated configuration for more sophisticated networking needs.

You can avoid doing this if you like, but you'll have to check IP addresses each time you boot otherwise. That, or you can install and configure Winbind and Samba to handle name resolution. But if you do that, you'll need to work through the 6th link in my sig.

You're better off configuring your router for address reservation. This way, you don't have the unnecessary overhead that Samba brings, and you won't have to work through the 6th link in my sig. This method also gives significant speed advantages, and causes less problems with name resolution overall.

---

### Post by Volume on 2009-07-29
> **dmizer said:**
> Yes, once you've assigned IP addresses to each machine, then you can edit /etc/hosts and add each machine's IP address and name. That way, you can have name resolution.

Here is an example from my network:

I have two computers. One is named tokkyu and the other is named tsubasa.
tokkyu has an IP address of 192.168.1.20
tsubasa has an IP address of 192.168.1.21

Here is the /etc/hosts file from tokkyu:
```
127.0.0.1 localhost
127.0.1.1 tokkyu
192.168.1.21 tsubasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Here is the /etc/hosts file from tsubasa:
```
127.0.0.1 localhost
127.0.1.1 tsubasa
192.168.1.20 tokkyu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

So, when I "ping tokkyu" from tsubasa, I get replies. Once you've done this, then it's easy to get things working from the command line via host name.

Great Deal! It works great now.  I'll figure out some way to break it though, and then I'll be back!  8-[

---

