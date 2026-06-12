---
title: "Mounting, automounting, setup troubleshooting HELP"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by smcrossman on 2011-06-18
I need help to figure out mounting.  I have 3 computers running Natty. 1 a desktop 64bit dual boot with Win7 (64) Home Prem; a dell inspiron mini (32bit) dual boot with Win7 Home Prem, and an old 486 Intel based PC running ONLY Ubuntu.  My Samba shares are on an external HD currently residing on the 64 bit.  

I installed Mount Manager...still  trying to figure out how it works exactly.  I'd like to auto-mount the  shares "routinely accessed" (shared network drive, network personal for each machine) allowing  as needed access.  Then the other personal network drives I would like  to mount only when needed. Leaving local home drives password/share protected ... using the network personal folders as a place to add files or such that need to go to a local drive.

{basically I have 3 computers which each have a local home folder, and a network home folder; then I have a network shared share where open shares will be stored (email, calendar, most documents,  theetc)  each computer has a primary ubuntu user (user id 1000).  I have 3 windows ids on 2 computers. each of these ids has been paired with an ubuntu user in smbusers; after this weekend I will only have 1 windows share and 1 user hopefully! so the other two ubuntu users will have non-existent windows IDs}

Right now I can (from a non-server machine) access the shared network  drive, but cannot access any others. (Makes sense...that share is  totally open).  On the remote drive I have samba the the installed but no samba  directory and it hasn't been configured (obviously).

On the standalone (where the HD is attached) I can access any of them by  mounting them where they are listed under Places, but through the  network menu I can access the shared drive, and the personal drive with  just one password entry (my login or sudo password).   The others  whenever I enter my login/sudo password I  get an unable to mount  error. 

I currently have 3 Ubuntu users & 3 windows users.  I've assigned  each Ubuntu user an window user name hoping that would make the  authorizations easier.  I'm currently using a generic Samba password and  a generic Ubuntu login password but they are different. So one password  for each, each user has the same passwords.  I do allow guests using  the guest group (not nobody, but I could change that easily enough)

If I weren't so stubborn I'd just ditch the passwords, make all shares  open to everybody, but eventually I hope to be able to do remote access  (via mobile) and would rather just do it all from the beginning than  mess with it later.

I've been hesitant to mess with programming in the mount/unmount process because I'm not sure I understand it that well (which is why I installed Mount Manager).  Problem is I don't understand it well enough to figure out how to use Mount Manager.  I did see where **[COLOR=Purple]automount[/COLOR]** will not work if you have to authenticate the share before mounting. One of the reasons I only want to automount the 2 shares for each machine. That particular process sounded like what i want for those 2 connections on each.  But first I need to figure out mounting period I guess.

here's where my usage of the term came from :
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

I may be really confused, or trying to do something that I with my limited knowledge and needs really don't want or need to do....wouldn't be surprising! I'm known to make things more complicated than needed.  If a simpler approach seems more logical feel free to share!

Thanks for any help & guidance!

---

### Post by Morbius1 on 2011-06-18
Did not understand any of that. It isn't even clear to me if the automount is referring to a remote samba share or a local partition.

Pick one machine and determine if the question relates to the mounting of a local partition, the creating of a samba share, or the mounting of a remote samba share.

If it's a local partition post the output of these 3  separate commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```It this is about creating samba shares so others on the lan can access them then post the output of these 2 separate commands:
```
net usershare info --long
testparm -s
```It this is about accessing remote samba shares then post the output of this command:
```
smbtree
```

---

### Post by smcrossman on 2011-06-18
I can understand WHY you can't figure it out!  I am actually dealing with all 3 (depending on which machine I'm on of course).  

If I start with the gateway desktop (64 bit) I CAN mount all the drives (they would be local, the USB samba shares, and the same HD different volume/partition Windows share) as local drives. Using file manager and choosing them out of the left column. I can also mount 2 of the usb samba shares via the network path.  I'm not seeing the Windows shares yet so I don't believe I've hooked into them properly yet.

The others it is all a matter of remote shares, i.e., samba shares not on a local or attached device.

So I will run the first set of commands from the "host" computer.  Back in a moment!

---

### Post by smcrossman on 2011-06-18
Okay here are the results of the first three.  On the host computer, computer 1  for easier reference!

```
[COLOR=Magenta]root@gateway-suzanna:/home/suzannag# sudo blkid -c /dev/null[/COLOR]
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="System Reserved" UUID="122808D92808BE2B" TYPE="ntfs" 
/dev/sda2: UUID="E0EC0AE8EC0AB934" TYPE="ntfs" 
/dev/sda5: UUID="97e0c3d2-c0d6-499a-94bd-7f841bb73571" TYPE="swap" 
/dev/sda6: UUID="3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac" TYPE="ext4" 
/dev/sda7: UUID="472ad73f-3029-487e-8bc5-d32d140df238" TYPE="swap" 
/dev/sdb1: LABEL="srvzannasu" UUID="92afa7d5-df41-4423-be97-d5f3fed4e768" TYPE="ext3" 
/dev/sdb2: LABEL="suzannag" UUID="6e3e3254-a96d-4ea3-9168-db7249eab8dd" TYPE="ext3" 
/dev/sdb3: LABEL="suzannad" UUID="fdd3d4ad-d0fb-43c7-88a8-0cf3f6cef878" TYPE="ext3" 
/dev/sdb4: LABEL="suzannaog" UUID="03efd567-f6b4-490c-a609-8c088f1d8d79" TYPE="ext3" 
/dev/sdg1: LABEL="/home/suzannaog/" UUID="3c3946ba-8e92-43d2-86a4-c1edef8d21f1" TYPE="ext3" 
r[COLOR=Magenta]oot@gateway-suzanna:/home/suzannag# cat /etc/fstab[/COLOR]
UUID=97e0c3d2-c0d6-499a-94bd-7f841bb73571 swap swap sw 0 0
UUID=472ad73f-3029-487e-8bc5-d32d140df238 swap swap sw 0 0
UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac / ext4 defaults 0 1
[COLOR=Magenta]root@gateway-suzanna:/home/suzannag# mount[/COLOR]
/dev/sda6 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suzannag/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suzannag)
/dev/sdg1 on /media/_home_suzannaog_ type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb4 on /media/suzannaog type ext3 (rw,nosuid,nodev,uhelper=udisks)root@gateway-suzanna:/home/suzannag# sudo blkid -c /dev/null
/dev/sdb3 on /media/suzannad type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2 on /media/suzannag type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/srvzannasu_ type ext3 (rw,nosuid,nodev,uhelper=udisks)
root@gateway-suzanna:/home/suzannag# 

```

---

### Post by Morbius1 on 2011-06-18
> If I start with the gateway desktop (64 bit) I CAN mount all the drives  (they would be local, the USB samba shares, and the same HD different  volume/partition Windows share) as local drives.Can't imagine why you are mounting "the USB samba shares" and the "same HD different volume/partition Windows share" on the same machine where these partitions already exist.

---

### Post by Morbius1 on 2011-06-18
OK, so I'm assuming you want one of these to automount at boot? 

Let's take this one as an example:
>  /dev/sdb2: LABEL="suzannag" UUID="6e3e3254-a96d-4ea3-9168-db7249eab8dd" TYPE="ext3"[1] Unmount it
```
sudo umount /media/suzannag
```[2] Create a permanent mount point:
```
sudo mkdir /media/suzannag
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=6e3e3254-a96d-4ea3-9168-db7249eab8dd /media/suzannag ext3 defaults,noatime 0 2
```[5] Save the file, exit gedit, and back in the terminal run the following command to test for errors and also to mount the partition without a reboot:
```
sudo mount -a
```Use the above as a template for all the other ext3 partition you want to automount substituting the correct UUID and mountpoint for each different partition.

---

### Post by smcrossman on 2011-06-18
I'm attempting to be pro-active.  I'm placing the "network shares" on an external hard drive. Eventually this ehd will become a network hard drive hooked in at the router/gateway.  In the meantime this allows me to set up and work out my lack of knowledge and fine tune things so I'm using the same file management across the board.

I know that to access these shares the "host" computer one must be powered up and active (I don't think it will work if the pc is in hibernation or sleep).  The main thing is that if there isn't an issue with the set up here then I need to figure out how to set up the other 2 computers to access these samba shares effectively.  Computer 2 is a netbook and will likely be also set up as a standalone host (so if need be the EHD can be switched to it). The third one will simply be a client.  

The only windows share I will have after this weekend will also be on Computer 2.

Okay..well I don't know what changed but my network link is working fine from computer 2 (the netbook). I can access all the shares with 1 password (the login/sudo) and it sets up a temporary bookmark until i manually unmount them. I haven't tried moving files yet but will do that of course.

You are really good! Fixed it and I didn't do a thing!

---

### Post by Morbius1 on 2011-06-18
I didn't understand your last post at all but I get the feeling that you are happy - and so too am I.

---

### Post by smcrossman on 2011-06-18
Okay I have the two automounts set up for Computer 1. Seems to be working fine.  I no longer can access the samba shares (ehd/c1) from computer 2.

So now how do I set up the mounting of remote shares? I do have the Wndows Network with Computer 1 and then the shares are all listed2, but when trying to access the samba shares it either does a long string of password requests or it gives me an unable to mount error.

Is it time to run the second set of diagnostics?  If so on which computer?  the host (computer 1) or the client not able to access (computer 2)?

---

### Post by Morbius1 on 2011-06-18
> I no longer can access the samba shares (ehd/c1) from computer 2.And where might those samba share be? On what machine? And what do you mean you cannot access them? It doesn't show up under network? It gives you an authentication error? What?

Why not post the output of the following command so others can see what's going on here:
```
smbtree
```Doesn't really matter what machine you run it from so run it from the machine your using at the moment.

---

### Post by smcrossman on 2011-06-18
```
HOME
    \\GATEWAY-SUZANNA        gateway-suzanna server (Samba, Ubuntu)
        \\GATEWAY-SUZANNA\IPC$               IPC Service (gateway-suzanna server (Samba, Ubuntu))
        \\GATEWAY-SUZANNA\suzannaog-h        Local Home
        \\GATEWAY-SUZANNA\suzannad-h         Local Home
        \\GATEWAY-SUZANNA\suzannad           Network Home
        \\GATEWAY-SUZANNA\suzannaog          Network home
        \\GATEWAY-SUZANNA\suzannag           Network home
        \\GATEWAY-SUZANNA\suzannag-h         Local home file
        \\GATEWAY-SUZANNA\Zannasu server     Zannasu Server
        \\GATEWAY-SUZANNA\print$             Printer Drivers
root@gateway-suzanna:/home/suzannag# 

```


3 computers (#1= sg-h, #2= sd-h, #3 = sog  who doesn't have a local home yet being installed now)....1 external hardHOME
    \\GATEWAY-SUZANNA        gateway-suzanna server (Samba, Ubuntu)
        \\GATEWAY-SUZANNA\IPC$               IPC Service (gateway-suzanna server (Samba, Ubuntu))
        \\GATEWAY-SUZANNA\suzannaog-h        Local Home
        \\GATEWAY-SUZANNA\suzannad-h         Local Home
        \\GATEWAY-SUZANNA\suzannad           Network Home
        \\GATEWAY-SUZANNA\suzannaog          Network home
        \\GATEWAY-SUZANNA\suzannag           Network home
        \\GATEWAY-SUZANNA\suzannag-h         Local home file
        \\GATEWAY-SUZANNA\Zannasu server     Zannasu Server
        \\GATEWAY-SUZANNA\print$             Printer Drivers
root@gateway-suzanna:/home/suzannag# 
HOME
    \\GATEWAY-SUZANNA        gateway-suzanna server (Samba, Ubuntu)
        \\GATEWAY-SUZANNA\IPC$               IPC Service (gateway-suzanna server (Samba, Ubuntu))
        \\GATEWAY-SUZANNA\suzannaog-h        Local Home
        \\GATEWAY-SUZANNA\suzannad-h         Local Home
        \\GATEWAY-SUZANNA\suzannad           Network Home
        \\GATEWAY-SUZANNA\suzannaog          Network home
        \\GATEWAY-SUZANNA\suzannag           Network home
        \\GATEWAY-SUZANNA\suzannag-h         Local home file
        \\GATEWAY-SUZANNA\Zannasu server     Zannasu Server
        \\GATEWAY-SUZANNA\print$             Printer Drivers
root@gateway-suzanna:/home/suzannag# 
 drive with the shares on it.  External hard drive is connected directly to #1.  Shares work fine & mounting work fine.

on #2 in file manager I see Network -->Windows Network-->gateway-suzanna (#1) -->list of all my windows shares.  I click on one and get the password dialog...I enter my login/sudo pwd and get another, and another and another   OR I get an unable to mount error.

I have NOT done basic diagnostics yet. I can do that (checking pings and such) and try removing the valid users on the shares to see if that eliminates the password issue.  If it is a mounting on demand issue though that is what I haven' t done yet and was looking for help with.

Hope that helped some....since I am installing currently as well you can take plenty of time getting back to me....Or just tell me to do my diagnostics and then repost if I don't figure it out.

---

### Post by Morbius1 on 2011-06-19
To the forum community at large I seek your help and guidance. Instead of providing clarity every post by this user gets me more confused. If anyone out there can provide the Rosetta Stone that can help me unlock the scope of this problem I would be grateful.

Let's take the very first sentence of the last post as an example:
>  3 computers (#1= sg-h, #2= sd-h, #3 = sog who doesn't have a local home yet being installed now)....1 external hardHOME* I see only one host: GATEWAY-SUZANNA. Smbtree is displayed 3 times but they all relate to the same machine. Do you all think it's possible that all three machines have the exact same host name?

* I don't understand what "doesn't have a local home yet" means. How does one install a Linux OS without a local home?

* I don't understand what "1 external hardHome" means either. The user has a home partition on an external device? What is the significance of the term "hard" in this context?

There are also references to shares labeled "Network Home". Not sure what that means. The home partition points to a remote share on another machine?

Any help would be appreciated.

---

### Post by smcrossman on 2011-06-19
I'm sorry. I know I'm not communicating well...it's my stress levels showing.  I've attached a diagram of sorts that might make the system I'm trying to set up a little more clear.

I really think I need help figuring out how to mount Samba shares that are not directly connected or linked to the computer.  That is what I'm calling remote shares.

---

### Post by capscrew on 2011-06-20
> **smcrossman said:**
> I'm sorry. I know I'm not communicating well...it's my stress levels showing.  I've attached a diagram of sorts that might make the system I'm trying to set up a little more clear.

I really think I need help figuring out how to mount Samba shares that are not directly connected or linked to the computer.  That is what I'm calling remote shares.
I too have followed this confusing thread.  Sometimes a picture is worth 1000 words... 

I think I understand what you are attempting.  I don't think it will work.  But then again I am only guessing.  None the less I'm goin' in...

A small glossary:
[LIST]
[*]host = a computer
[*]hostname = the name assigned to the computer
[*]server = A process that is listening for request for services
[*]client = a requester of services from a sever
[/LIST] 

Using similar hostnames for your computers makes it a pain to follow what you are doing.  It would be best if you used a more distinct naming theme.  For example you could use the theme of ***flora*** (hmmmm, a good name for the workgroup) and name each computer (host) for a flower. It would look like this:
[LIST]
[*]workgroup = flora
[*]Computer#1 = iris
[*]Computer #2 = daisy
[*]Computer#3 = rose
[/LIST]

Now there will be no doubt which host we are talking about.
[LIST]
[*]*[SIZE="1"][COLOR="Blue"]There is a secondary notion to the naming scheme. Can you guess what it is?[/COLOR][/SIZE]*
[/LIST]

From a technical point of view, there is this notion of *local* file systems  and *remote *file systems.  Samba should be configured with shares that are mounted local files systems.  Using external drives as without them being permanently mounted (i.e moving them around) is a not a good idea.

Using a thumb drive for your /home directory and moving it around is a bad idea.  If you don't have a mounted home directory then you can't boot the system.

I think you should describe exactly what your end goals are.  You can use human non geek terms.  Then we can provide assistance from the beginning to help you build a stable network.  Start simple and then we can build upon that knowledge.

---

### Post by smcrossman on 2011-06-20
[QUOTE
I think you should describe exactly what your end goals are.  You can use human non geek terms.  Then we can provide assistance from the beginning to help you build a stable network.  Start simple and then we can build upon that knowledge.[/QUOTE]

Believe it or not...I actually asked for guidance on naming /passwords/etc prior to attempting this. I knew I was in over my head. but got little guidance. So THANK YOU....I'll rework the naming.

LONG TERM goal is to have 3 computers where I can pull up whatever I need to work on whenever.  The external hard drive will become a NETWORK DRIVE (a hard-drive located at the router for backups, etc).  It will be permanent but external. (That is the purple arrow....future NOT now....incompatible units right now)  

The thumb drive for Home files is because I currently have only a 10GB HD in that PC.  It is old, most likely candidate for needing work.  I thought using a thumb drive (also as a permanent not to be removed and travel) could solve the space issue and protect against possible hardware issues & file loss.

The only traveling piece to this puzzle will be the netbook.  I do want to be able to access files at home via mobile.  That way if I'm out and end up needing medical documentation, or shopping information, etc that I didn't use the netbook for I can connect in and get it.

I have found trying to synchronize files bothersome. I may make changes on multiple computers with a few hours.  It depends on the day, and what I am doing.  Remembering to sync each time I shut down a file or before opening a file isn't working for me. I'd like a centrally located file to be worked on locally and then re-saved centrally.  One version for 3 workstations.

Alternatives to the external hard drive to achieve that are welcome.  I need to reinstall a clean setup on the gateway so I didn't want to set up my system on it directly, and using the netbook seemed like a bad idea....much higher risk of loss.

Thoughts?  More questions?

---

### Post by capscrew on 2011-06-20
> **smcrossman said:**
> Believe it or not...I actually asked for guidance on naming /passwords/etc prior to attempting this. I knew I was in over my head. but got little guidance. So THANK YOU....I'll rework the naming.

Do you know how to rename the hosts?  It's pretty easy if you know how.  Let us know if you need help.

It looks like at this time you are the only user (login) on the network.  I suggest that the user name and password be the same on all hosts.

There is no reason for you to have a different login on each host and it will make life much easier.  In my system at home there are 6 hosts and each has 2 users.  They are my wife and myself.

This is not as easy as changing the hostname, but still something that can be done.> 

LONG TERM goal is to have 3 computers where I can pull up whatever I need to work on whenever.
If this is an all Linux network there are a couple of ways to accomplish your goal.  Samba is one way and Network File System (NFS) is another.  

Samba *shares* are just that: *shared*.  One advantage is that you can can visually browse to them.  

With NFS is *exports* (NFS shares) are mounted transparently to whatever local host you are logged into.  You could have one home directory from wherever you login, but it is located centrally on a single host (ultimately it could be the router). 

This home directory would be your home directory on whatever host you logged into. At one time I managed 200 Unix hosts.  I could login on any of them and my home directory was the same.  All my configurations were the same and all my data was there.  There would be no need to sync data from multiple home directories.
>  

The external hard drive will become a NETWORK DRIVE (a hard-drive located at the router for backups, etc).  It will be permanent but external. (That is the purple arrow....future NOT now....incompatible units right now)

What is incompatible about them?  If you use a router to also host your NAS then you will need one that has enough intelligence to understand and implement Samba and NFS.  Yes you can use both.   >  

The thumb drive for Home files is because I currently have only a 10GB HD in that PC.  It is old, most likely candidate for needing work.  I thought using a thumb drive (also as a permanent not to be removed and travel) could solve the space issue and protect against possible hardware issues & file loss.
Remember that thumb drives wear out faster than hard drives.  
> 
The only traveling piece to this puzzle will be the netbook.  I do want to be able to access files at home via mobile.  That way if I'm out and end up needing medical documentation, or shopping information, etc that I didn't use the netbook for I can connect in and get it.
This is dobale.  It could even be a VPN that would allow Samba or NFS. > 

I have found trying to synchronize files bothersome. I may make changes on multiple computers with a few hours.  It depends on the day, and what I am doing.  Remembering to sync each time I shut down a file or before opening a file isn't working for me. I'd like a centrally located file to be worked on locally and then re-saved centrally.  One version for 3 workstations.
:-)  See above.> 

Alternatives to the external hard drive to achieve that are welcome.  I need to reinstall a clean setup on the gateway so I didn't want to set up my system on it directly, and using the netbook seemed like a bad idea....much higher risk of loss.

Thoughts?  More questions?
At this point the only alternative to NAS storage (the external hard drive) would be a cloud storage solution.  This is something I don't like.  You are entrusting your data to someone else on the Internet.  Trivial data maybe.  Personal data is not a good idea and certainly not personal medical data..

In my opinion at some point you will want to end up with all your data stored in one place, accessible from any of your computers in your network.  This would mean that you only need to backup one set of data to separate media.  This could be a second external hard drive or other media.

---

### Post by smcrossman on 2011-06-20
Well I've spent the day playing with naming, installing a different version of Ubuntu onto the workstation and dealing with my internet going in & out.

The router is my dsl gateway. Does not have any usb connectors. My external HD is usb only.  That is the only incompatabililty.  I am still debating whether to upgrade to a DSL/Router with USB available (more power, more distance here at home anyway) and stick with my current hd, or if I just want to upgrade to a "network" hard drive that will go into the Ethernet jack.

Renaming the host(s) hasn't been an issue. Renaming the shares turned into a problem.  I use mv to rename them (not move them, but what little I had placed on those shares disappeared.  Rather than go hunting for them, I reformatted and re-partitioned to make the system a little cleaner and allow space between the shares. Added a share for storing network security into (encryption keys & passwords), and put the 3 "machine" shares into a larger extended partition. allowing me to use the unallocated if a need comes up.

Before starting to mess with networking all my user ids were identical & password is still the same across the 3.  I only chanaged the ids to try to clarify my networking attempts.  Now in my situation I've decided I might as well do "machine" shares....label them by the computer they line up to for backups since the  all shared will hold calendar, contacts, email, et; as well as master  documents.  The only windows share I will have is on the netbook, and I so rarely log into windows it's more a matter of getting the documents transferred over to linux.  I'm still getting mounting errors, but need some time to fine tune things before asking y'all for help with that again.

One brief question....Only 1 host is required?  Or should all 3 be stand-alone hosts?  While I"m working at this I'll read more about the NFS.

---

### Post by capscrew on 2011-06-20
> **smcrossman said:**
> Well I've spent the day playing with naming, installing a different version of Ubuntu onto the workstation and dealing with my internet going in & out.

The router is my dsl gateway. Does not have any usb connectors. My external HD is usb only.  That is the only incompatabililty.  I am still debating whether to upgrade to a DSL/Router with USB available (more power, more distance here at home anyway) and stick with my current hd, or if I just want to upgrade to a "network" hard drive that will go into the Ethernet jack.
I have real misgivings with your grasp of what is going on here.  If the the dsl gateway has not connectors then it also does not have any OS intelligence to mount a hard drive drive partition.  But, just because you have a USB or Ethernet port doesn't mean you have that capability either.  before you buy anything you need to have a good grasp of what you need out of these devices. 

The only functional advantage of hosting the NAS (external hard drive) on the DSL/gateway is that it is up and running already.  You  can use any host to perform the duties of a NAS.  

As an example I built my own NAS out of an old P3 Dell.  It runs Ubuntu 10.04 LTS.  The internal hard drive is a 300 GB SATA drive that it connected via a PCI SATA adapter with an eSATA port.  This allows me to attach a 700 GB SATA drive that I installed in its own external case.  This is a far better solution (capacity/price wise) than anything you can get off the shelf.

What I am try to get you to provide is the wish list.  Then we can assist you in making intelligent choices.  The choice will always be yours.  i would like to think that I can provide the expertise for you to draw upon.> 

Renaming the host(s) hasn't been an issue. Renaming the shares turned into a problem.  I use mv to rename them (not move them, but what little I had placed on those shares disappeared.  Rather than go hunting for them, I reformatted and re-partitioned to make the system a little cleaner and allow space between the shares. Added a share for storing network security into (encryption keys & passwords), and put the 3 "machine" shares into a larger extended partition. allowing me to use the unallocated if a need comes up.

I'm lost here.  The shares should only be defined in the /etc/samba/smb.conf file (classic shares).  The file system of the host does not need to be configured to accommodate Samba.  

As an example all of my data is stored under /srv in the Linux file system.  I have folders under that for backup, music, video, pictures and public.  They look like this ```

/srv
    /backup
    /music
    /video
    /pictures
    /public

```

When you see the shares they are like this:
```
\\SERVER\backup
\\SERVER\music
\\SERVER\video
\\SERVER\pictures
\\SERVER\public

```

I think you are confusing file system data stores with Samba shares of those data stores.
> 

Before starting to mess with networking all my user ids were identical & password is still the same across the 3.  I only chanaged the ids to try to clarify my networking attempts.  Now in my situation I've decided I might as well do "machine" shares....label them by the computer they line up to for backups since the  all shared will hold calendar, contacts, email, et; as well as master  documents.  
In the matter of the shares, this is just plan wrong.  In concept and in execution.  You are over complicating the whole thing. > 
The only windows share I will have is on the netbook, and I so rarely log into windows it's more a matter of getting the documents transferred over to linux.  I'm still getting mounting errors, but need some time to fine tune things before asking y'all for help with that again.

I would seriously consider creating one host that has the file system correctly laid out.  Then we can create the Samba shares.

At this point I would advise you to ask as many questions as you need to be comfortable with these concepts before we start moving files around.

FYI the mv command does move files.  When you move the file in the same directory by changing its name it is still moved.  The original file is unlinked and the new file (with a new name) is linked to a new inode.
> 

One brief question....Only 1 host is required?  Or should all 3 be stand-alone hosts?  While I"m working at this I'll read more about the NFS.
All hosts are stand alone.  They are equal peers in the network from a networking standpoint.  They may have different services running on them but they ar still peers.  The router is also a peer in a networking sense as well as a dedicated NAS.

So my question back to you is:  What do you mean by *"Only 1 host is required?  Or should all 3 be stand-alone hosts? "*?

---

### Post by smcrossman on 2011-06-20
Well, my hope was to be able to get my windows files moved onto the linux side off the desktop that is acting as host.  I really need to do a clean install on it and would like to just claim the whole hard-drive.  So I thought if I could get the shares set up I could put those windows files there.

Anyway...nomally the shares would just be normal directories & files on the pc, but since it's a hd of it's own....

Like I said much earlier I'm known for making things much more complicated than need be.My brain often skips steps and doesn't identify the simple logical solution.

So I should step back, get my clients able to ping my host....my host able to ping the clients, and then figure out how to access a directory assigned as shared on each machine from one or both of the others.  Probably without any security to speak of to make sure there is no confusion between accessing/mounting and passwords.

I was almost there last week with the netbook as host. Just never figured out the password issue.

I KNOW I need to do major research before I buy any equipment to move forward with a dedicated file server equipment.  This is one of the reasons I'm playing now even as I'm still figuring out exactly which versions of Linux/Ubuntu work best for each machine.  I am learning from my mistakes, and at the same time driving y'all crazy.

So I'll take a break of a day or so and get that "host" pc up to snuff and the basic networking setup with full open access first.  I can do that fairly simply at this time I think.

As far as host vs. client.....I'm just wondering if its easier or harder to troubleshoot with multiple "hosts".  So much of the documentation makes a big deal out of not needing to do the server setup or full Samba install on just clients. I've done enough tweaking that I'm pretty comfortable with the smb.conf, not as much so but okay with smbusers, etc.  The fstab and such are where I'm really uncomfortable just now.

Thanks!

---

