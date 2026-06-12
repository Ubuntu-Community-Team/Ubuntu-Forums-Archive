---
title: "LAN access by server name"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by PhilOSparta on 2006-04-23
I have two Breezy desktops sitting side by side and I want to share files between them.  Everything worked fine under samba, but I wanted to go Ubuntu all the way and installed NFS.  There is a Linksys router between the two of them.  Since everything is DHCP, I want to use the server name(s) for addressing.

My server **/etc/hosts**  file has the correct server name  peglegpete
My server **/etc/nsswitch.conf** file has the line  **hosts:  files dns**
My **/etc/exports** file has [B]/ 10.10.10.*/255.255.255.0(rw,async,no_root_squash)  [COLOR="Red"](I know this is not a secure procedure, but it is great for testing.)  [/COLOR]
[/B] where 10.10.10.xxx is the DHCP address assigned by the router to the client(s)  
My client **/etc/fstab** line is:
**peglegpete:/  /mnt/nfs  nfs rw,hard,intr 0 0 **

The client doens't mount the server file system.
The client generates the error:
mount: can't get address for peglegpete

Any ideas would be appreciated.](*,)

---

### Post by RedBoot on 2006-05-06
[QUOTE=PhilOSparta]I have two Breezy desktops sitting side by side and I want to share files between them.  Everything worked fine under samba, but I wanted to go Ubuntu all the way and installed NFS. [/QUOTE]

I've got a similar setup and am attempting the same thing!  I'll share what I've found and maybe we'll both get this going. 

From the CLI, what do you get from the server PC from the command [FONT="Fixedsys"]showmount -e[/FONT]? When on the client PC what do you get with [FONT="Fixedsys"]showmount -e peglegpete[/FONT]?

Did you really mean to share the root directory?

The last time I setup NFS (on SuSE), I neglected to create a blank directory on the client PC with appropriate permissions for the mount command.
Commands that worked on client:
[FONT="Fixedsys"]showmount -e linuxsrv
mkdir /shared
chmod 777 /shared
mount -o rw,soft linuxsrv:/shared /shared[/FONT]

> ...where 10.10.10.xxx is the DHCP address assigned by the router to the client(s)
I setup my NFS server as static because I didn't want DHCP to swap IPs. Maybe you know a way to avoid this? 

> There is a Linksys router between the two of them.  Do you mean that both PCs are connected to its switch ports? Technically, a router between two PC would require them to be on different networks, right? 

Hope some of this helps. If we get yours going, maybe I can fix my GUI/NFS Dapper issues.

---

### Post by PhilOSparta on 2006-05-09
> From the CLI, what do you get from the server PC from the command showmount -e?
Export list for peglegpete:
/ 10.10.10.*/255.255.255.0

> When on the client PC what do you get with showmount -e peglegpete?
showmount:  can't get address for peglegpete
> Did you really mean to share the root directory?I'm the SU on both machines.  It seems to be an easy approach.

I have already made a directory on the client /mnt/nfs which is rwx for all.

On the client, the command sudo mount -o rw,soft peglegpete:/  /mnt/nfs gives  ***mount: can't get address for peglegpete***
> I setup my NFS server as static because I didn't want DHCP to swap IPs. Maybe you know a way to avoid this?  The whole idea behind this situation is to use the ***server name*** not the IP address per se.
> Do you mean that both PCs are connected to its switch ports? Technically, a router between two PC would require them to be on different networks, right?
  Well, my understanding is that the router has two ends, one facing the ISP/Internet and the other facing, in this case, 4 ports on a LAN (plus wireless laptops). 

The LAN is made up of my two PCs.  The router uses DHCP to assign each of the PCs it's own IP address based on when it is hooked up to the router at power up.  

One is usually 10.10.10.101 and the other would usually be 10.10.10.102.  However, I have two children with wireless connections to their laptops.  I power down at night (both desktops) and the router assigns new IPs, yadda, yadda.  You know the story.  Well, the server names, peglegpete and panpiper are constant.

I need some way to get the mount command on the client to find out the server name.

Thanks for your assistance.   I will be investigating the mount, rpcinfo and any other commands that seem to lead someplace.

Some additional sources of info:
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#SYMPTOM3]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#SYMPTOM3")
[https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo]("https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo")

---

### Post by ranf on 2006-05-11
You need to tell your DHCP clients to send their hostnames to the router.
This is done in `/etc/dhcp3/dhclient.conf'. Look for 

send host-name

---

### Post by PhilOSparta on 2006-05-12
ranf,

Thanks.  Adding  send host-name in the `/etc/dhcp3/dhclient.conf' on both machines worked.  i.e. It has allowed each machine to see the other for ping etc.  The automatic mount by '/etc/fstab' on the client didn't work, but the 
***sudo mount -t nfs peglegpete:/home/phil  /mnt/nfs***  worked.
The '/etc/fstab' file currently has the line 'peglegpete:/home/phil    /mnt/nfs  nfs  rw,hard,intr   0   0
Now I will try to figure out how to get it to automount when the client boots.
At least now I have connectivity.

Thanks again.

Phil

---

