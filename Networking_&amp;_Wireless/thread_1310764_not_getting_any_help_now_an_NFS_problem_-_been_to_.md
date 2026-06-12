---
title: "not getting any help now an NFS problem - been to #nfs, here, usenet ..."
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by cedentary on 2009-11-02
I have tried to get help here[B]

 [http://ubuntuforums.org/showthread.php?p=8202348#post8202348](http://ubuntuforums.org/showthread.php?p=8202348#post8202348)

with no reply so have reverted to NFS which I never got working anyway -- I illustrate the problem with that here - I have been at this 2 days to set a basic network up following instructions carefully enquiring on usenet here, irc.freenode.net #nfs .... am frozen in time with this somebody please help me

[/B]If I can't fix this I will have to subscribe to canonical basic support which I really don't want to do because 1. it costs £37 and 2. I cannot be sure that they will even address an NFS problem

I have been trying to set up a network which will give me mounted directories for a few days now -- tried once using smb-share (worked partially) ... I posted about that in the link above (no help) ... I've given up on that and decided to try basic NFS again ... as before I get the situation where one client connects and one client does not.

2 clients (dan-couch and dan-laptop) running 9.10 (things were the same with 9.04) and a server (dan-server) running 9.10

my /etc/exports file on the server looks like this (the last line is the relevant line):

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
/home/dan/keep dan-laptop(rw,no_root_squash) dan-couch(rw,no_root_squash)

^ here I understand I do not need 'no_root_squash' if I am not exporting the root - I will
remove that later - btw did somebody mention having to use a TAB character to separate fields in this file?

my /etc/fstab on both client machines looks like this (the last line is the relevant line): 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1b25c960-57a5-4d9e-a087-da6eb3e3a849 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=323b03e0-50be-46e7-8816-ea9f652a481d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dan-desktop:/home/dan/keep /home/dan/keep nfs rw 0 0

I issue the command 'sudo mount -a' on client 1 it connects ok (well in fact 
it connects upon boot) -- on client 2 the command gives me the message:

mount.nfs:: access denied by server while mounting dan-desktop:/home/dan/keep

I issue showmount -e dan-desktop (dan-desktop is the server hostname)[FONT=Verdana] on client 1
(the working client)  and get :

Export list for dan-desktop:
/home/dan/keep ubuntu.home,dell-desktop.home


on client 2 (the non working client):  I get:

Export list for dan-desktop:  

^ 
nothing

checking the exports on the serverusing nslookup (client hostname) - command
nslookup dan-couch gives me :

Server:        192.168.1.254
Address:    192.168.1.254#53

Name:    dan-couch.home
Address: 192.168.1.66

[/FONT]nslookup dan-laptop gives me:  

Server:        192.168.1.254
Address:    192.168.1.254#53

Name:    dan-laptop.home
Address: 192.168.1.64

I got some advice from #irc.freenode.net #nfs to check that

"for nfsv3, the server, and all clients need to have the exact same matching uid/gid numbers - user names are ignored"

by issuing the command :  getent passwd | grep dan

dan : x :1000:1000:dan,,,:/home/dan:/bin/bash   <- spaces distorted in this to stop me getting smilie :x 

this issues the same output on the server and both clients --
-- no difference they match

somebody please help me

can't get mounted directories through sharing (right click / folder sharing) in file browser

can't get mounted directories by setting up samba (followed smb-share correctly) 
that only partially worked -- see my previous post on the subject please

[http://ubuntuforums.org/showthread.php?p=8202348#post8202348](http://ubuntuforums.org/showthread.php?p=8202348#post8202348)

nobody has replied to it -- If somebody could sort that one out then I 
could go back to smb and I would be happy but like I say in the post it only 
partially works (explained in the post) ....  [B]problem with setting times or rsync?

I have set up hosts.allow and hosts.deny as is advised with  no resolution (not having them and I can still connect 1 client so I do not think)
that is the problem -- anyway I do not think they are required at all

I am now SCREAMING FOR HELP !!!! I need this working 
[/B]

---

### Post by Aearenda on 2009-11-02
I just replied on the other thread regarding smbfs. I don't know NFS, can't help here.

---

### Post by cedentary on 2009-11-02
bump  #-o

---

### Post by cedentary on 2009-11-02
ok I went back to SMB and fixed it - should have set fstab to sync 

solution  here

[http://ubuntuforums.org/showthread.php?p=8202348#post8202348](http://ubuntuforums.org/showthread.php?p=8202348#post8202348)

:D

my fault - should have read the nfs HOWTO before manually configuring the client

---

