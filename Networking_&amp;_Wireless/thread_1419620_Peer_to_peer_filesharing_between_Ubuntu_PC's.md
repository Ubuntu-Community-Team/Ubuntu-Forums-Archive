---
title: "Peer to peer filesharing between Ubuntu PC's"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Mylorharbour on 2010-03-02
I know I'm missing something absolutely basic here but when I search the forums for filesharing I only seem to get info referring to Windows filesharing/SAMBA etc.

We have 3 Ubuntu machines at home and a printer on a Windows machine. How can we best fileshare:

1) between Ubuntu machines
2) reliably between Ubuntu and the Windows machine

Printing across the network is ok except for the Karmic NBR machines but that's another thread.

---

### Post by inclusivedisjunction on 2010-03-02
The best solution for number one is probably setting up an NFS share. NFS shares are mounted just like disks, only over a network.

For number two, that is what Samba is used for. Samba is an implementation of the file sharing protocol used in Windows.

I don't have any experience with networked printers, but this is also supported by Samba.

---

### Post by thebigob on 2010-03-02
inclusivedisjunction is correct.

To map ubuntu to another machine you will have to have some port open to allow them to communicate.

To do this securely you can use ssh. These are easy to set up if you google ssh server ubuntu you will find a decent guide.

Then to connect to this in ubuntu just click places -> connect to server select ssh and complete the details. This will mount the filesystem for you.

You can also connect to the windows share using this method however you will need samba-client installed on the ubuntu machine.
 
Then you just click places -> connect to a server windows share.

As for connecting the windows machine to the other hosts winscp is good if you decide to go down the ssh route.

---

### Post by Morbius1 on 2010-03-02
I'm probably missing some nuance in your original post but what are the problems you are encountering using samba to share files between the two OS platforms?

If you were to go into Nautilus and right click on say .. /home/your_user_name/Documents, select "Sharing Options", decide what kind of access you want to permit, and select "Create Share, you will create a share on that box.

Is there a problem in getting access to that share from the other machines on your network?

---

### Post by juancarlospaco on 2010-03-02
**[sudo apt-get install giver]("apt:/giver")**

---

### Post by Pritamsng on 2010-03-02
what ever all mentioned here all are correct.. 
there is some tool also which you can use..
check out the link..

[http://linuximagination.blogspot.com/2010/02/tools-to-connect-linux-system-from.html](http://linuximagination.blogspot.com/2010/02/tools-to-connect-linux-system-from.html)

---

### Post by Mylorharbour on 2010-03-03
Thanks for the replies guys.

**Pritamsng** - I wasn't looking for FTP clients etc. I wanted something more mainstream and that my mother could use easily. We're not that network minded.

**juancarlospaco** - Giver doesn't allow us to pull files from other machines.

Nice one **Morbius1** - We can at least share files between the Ubuntu machines now. I still need to work on how to integrate the Windows machine into this though.

**thebigob & inclusivedisjunction** - I've followed some of the links to NFS and ssh setup but it ain't easy is it? There's lots of talk of servers, clients and ports etc. Which machine would be the server? They're not all on at the same time. Or have I missed something..... perhaps they should all have client & server apps loaded? Do you have a link or two that a beginner would find helpful?

---

### Post by Morbius1 on 2010-03-04
>  Nice one **Morbius1** - We can at least share files between the Ubuntu machines now. I still need to work on how to integrate the Windows machine into this though.I don't understand the nature of the problem. 

Are you asking how to create a shared folder in Windows?

Or are you asking how to access the Linux share from Windows?
If it's the latter, does going to My Network Places, Entire Network, Microsoft Windows Network, Workgroup, Computer, and Folder, not work?

Does it give you an error?

---

### Post by Mylorharbour on 2010-03-04
I don't get that far Morbius1. I can go to My Network Places but I can only see drives & partitions on the XP machine. There is no Entire Network. If I click on View Workgroup Computers again I only see the XP machine. 

Hang on though, when I clicked on View Workgroup Computers the Other Places box changed giving Microsoft Windows Network as an option. I click on that and I get a choice of my network or Workgroup. I choose Workgroup, then one of the two displayed Ubuntu machines, lets call it Ubuntu-1, and get the error 'xxxxx server (Samba, Ubuntu) is not accessible. You might not have permission...etc'

If I choose Ubuntu-2 I see the two shared folders. Click on one of the folders and I get the same error message. Click on the other folder and I'm asked to input the username and password then it lets me in. I can then also open the folder that returned the error message.

I still can't access Ubuntu-1 though even though I've checked the folders on it can be shared. That's what I meant by 'reliably' in the original post. I can access files on Ubuntu-1 from Ubuntu-2 though so the only thing that doesn't work at all is accessing Ubuntu-1 from Windows.

Getting there.....

---

### Post by ionospheric on 2011-03-05
Here's what I did to share files between Ubuntu computers:

Connect both computers with an ethernet cable (a standard straight-through cable works on more recent computers, does not need to be a cross-over cable)

Install Samba:
```
sudo apt-get install samba
```

Create a wired connection on each computer with a manual IP address, the first three digits need to be the same.
Example:
IP: 192.168.1.100 and 192.168.1.101
submask 255.255.255.0

more Details at:
[[COLOR="Blue"]http://www.ehow.com/how_7193141_set-up-ubuntu-crossover-cable.html[/COLOR]]("http://www.ehow.com/how_7193141_set-up-ubuntu-crossover-cable.html")

Left-Click on network manager, connect wired connection on both computers


To access the files on the other computer:
Share a folder on one computer:
right-click the folder in Nautilus, select sharing options and share the folder
(allow guest access)

On the other computer, go to Places -> Network

Open Windows network, then workgroup, then the shared folder on the other computer appears.

---

### Post by SiGraybeard on 2011-03-22
My question should be even easier, but I've been reading these forums for four hours trying to figure out how to do it. 

I have two Ubuntu machines, an old one that I'm replacing with a new one. 

Old and new are plugged into an Ethernet router.  Old and new can ping each other.  Old and new can both see the Internet (both are logged into this forum) and the outside world.  Old has much more software installed on it and has been in use since around December 1.  

I want to connect them as peers so that I can transfer documents from the old to the new.  I don't care which one I work from as along as I can copy files from old to new.  I can do this in Windows, which is "next", after I get this done.  If I had a thumbdrive bigger than 1 gig, I might just do it sneakernet.  But I'll wear out the pins on the USB connector that way.  

Help???  Please?

---

### Post by SeijiSensei on 2011-03-22
rsync is probably the easiest solution, especially if we're talking about a one-time transfer rather than a permanent link.

You should probably take this slowly to avoid messing up the directory structure of the target machine.  Let's start with an obvious example, transferring the contents of /home/joe on the old machine to create a duplicate /home/joe on the new one.  On the old machine,

```
cd /home
sudo rsync -av joe ip.of.new.machine:/home

```

That will create a copy of /home/joe on the new machine.  You'll be prompted for your password because you're using sudo.

Remember that for all file ownerships and permissions to be correct, you'll need to have the same user and group IDs on the new machine as on the old.  The simplest method is to copy /etc/passwd, /etc/group, and /etc/shadow from the old machine to the new one.

Another alternative is to remove the hard drive from the old machine and install it into the new one.  Then you'll have all the files at your disposal and can move them around however you wish.

---

### Post by SiGraybeard on 2011-03-22
> **SeijiSensei said:**
> rsync is probably the easiest solution, especially if we're talking about a one-time transfer rather than a permanent link.

You should probably take this slowly to avoid messing up the directory structure of the target machine.  Let's start with an obvious example, transferring the contents of /home/joe on the old machine to create a duplicate /home/joe on the new one.  On the old machine,

```
cd /home
sudo rsync -av joe ip.of.new.machine:/home

```That will create a copy of /home/joe on the new machine.  You'll be prompted for your password because you're using sudo.

Remember that for all file ownerships and permissions to be correct, you'll need to have the same user and group IDs on the new machine as on the old.  The simplest method is to copy /etc/passwd, /etc/group, and /etc/shadow from the old machine to the new one.

Another alternative is to remove the hard drive from the old machine and install it into the new one.  Then you'll have all the files at your disposal and can move them around however you wish.

Thanks for the suggestion, but i get an error message that says new box won't accept a connection from new box:
```

ssh: connect to host 192.168.2.5 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

```I've tried calling my self superuser in a terminal on new box with no effect.  This is almost a completely new installation from the 10.10 disk, last night.  I have not engaged any firewalls or anything.  Don't know how to convince it to accept the connection.

---

### Post by Morbius1 on 2011-03-23
On whatever machine is 192.168.2.5:
Open Nautilus
Right click on your Documents folder
Select "Sharing Options"
Select all three boxes
Select "Create Share"

On the machine that is not 192.168.2.5:
In a terminal:
```
nautilus smb://192.168.2.5
```If you can't connect by ip address then disable all firewalls on both machines  ( this might also enable ssh if it's a firewall related problem ).

---

### Post by SeijiSensei on 2011-03-23
> **SiGraybeard said:**
> Thanks for the suggestion, but i get an error message that says new box won't accept a connection from new box:
```

ssh: connect to host 192.168.2.5 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

```

rsync uses SSH to set up the copying session between machines.  Install the openssh-server package on the target and see if that fixes the problem.

I forgot about the problem with root not having a login in Ubuntu, so my initial suggestion won't work.  You'd either need to set up SSH keys on both ends or, much easier, assign root a password on the target.  I'm [not allowed]("http://ubuntuforums.org/showthread.php?t=1486138") to tell you how to do that under forum rules, but you can read the [RootSudo]("https://help.ubuntu.com/community/RootSudo") guide to see how.

The method Morbius suggests works fine for files in your /home directory, but if you need to move other things, you may need to use rsync as root.

---

### Post by Morbius1 on 2011-03-23
> **SeijiSensei said:**
> The method Morbius suggests works fine for files in your /home directory, but if you need to move other things, you may need to use rsync as root.

"gksu nautilus" will allow you to share anything. But I can appreciate the purist's view that using Samba between 2 Linux machines is nothing short of an abomination ;)

---

### Post by Garland Fox on 2011-11-20
Yes 3 machines do not share
Upon reboot share option in folder gets unchecked.
I bow out - will start another thread - excuse me please

---

