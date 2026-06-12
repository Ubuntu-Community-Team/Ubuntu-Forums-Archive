---
title: "linux - linux network?"
date: 2006-03-03
forum: Networking &amp; Wireless
---

### Post by sdb2028 on 2006-03-03
I have several computers in my home, all set up to dual boot (one to tripple boot). I can connect from linux to Windows (XP, ME & 98), but not from linux to linux.
Any help or advice will be appreciated.

---

### Post by el3ktro on 2006-03-03
What exactly do you mean with "connect". Do you want to remotely control your machines or do you want to access files on the computers in your network?

Tom

---

### Post by sdb2028 on 2006-03-03
Access files for now. Eventually I would like to do both, but for now I would like for the to just see each other.

---

### Post by el3ktro on 2006-03-03
The best thing would be do use NFS for that. Install "nfs-user-server" and then share some directories. With Gnome, sharing directories is as easy as going to "System ->  Administration -> Shared folders" (I don't know the exact English menu, I have a German desktop). On the other machine, you can then mount those shared directories.

For instance, when you share your home directory "/home/jeff" on machine1, then you can mount this directory on another machine like this:

sudo mount machine1:/home/jeff /mnt/somedir

For this to work, a user that has access to this directory must exist on both machines with the same uid/gid!

Tom

---

### Post by sdb2028 on 2006-03-03
Not sure where to go from here, a window keeps popping up for me to log in. The domain keeps coming up as MSHOME, cant seem to change it. Won't let me log in no matter what I try.
All I can find is SMB in the shared folders settings, how do you get NFS installed?

---

### Post by el3ktro on 2006-03-03
Did you follow my instructions? Install nfs-user-server, then use the Gnome System menu to share some directories, and then you can mount them on your other machines.

Tom

---

### Post by sdb2028 on 2006-03-03
OK, I now have NFS installed. I am in the same place. When I go to network servers in the places menu, it keeps wanting me to log in but wont let me. The domain keeps coming up as MSHOME, which is my "Windows" work group. I don't have windows running at this point. I have ubuntu running on both of the machines I am working on right now. How do I set upthe work goups or domain name and log in to link the two machines? Details please.

---

### Post by sdb2028 on 2006-03-03
Anybody? I need more detailed instructions.

---

### Post by megamania on 2006-03-03
[QUOTE=sdb2028]Anybody? I need more detailed instructions.[/QUOTE]

I'm not an expert (quite the opposite, to be honest), but it looks like you are still using samba.

If you have NFS up and running, this is how you should be able to mount a file system on a remote computer:

```

sudo mount 192.168.1.64:/home /mnt/mule
```
that's what I use to mount on my primary computer the "home" fs on my emule machine. I can then access it by opening the /mnt/mule folder. Remember to create that folder first.

the machines are connected though a router, and 192.168.1.64 is my amule machine's address.

hope that helps a bit at least.

EDIT: remember to share the directories first, as **el3ktro** suggested

---

### Post by el3ktro on 2006-03-03
Okay I'll give you some more detailed instructions:

For a pure Linux network, you don't need any workgroups or domains. You just tell your computer which directories you want to have shared with other computers, and then the other computers can mount these directories, and access them as if they were local directories.

You can tell your computer which directories it should share this way: When you use Gnome, go to "System->Administration->Shared directories". Then select "NFS" and enter the name of a directory you want to share.

Now, go to another computer in the network. Create a new directory where you want the directory from the other computer to be accessible. Then you can mount the directory from the other computer so that it appears on the computer where you're sitting now. You have to type the following:

sudo mount ip-of-other-computer:/shared-directory local-directory

Now, you'll have the remote directory on the other computer on your local computer, and you can access the files in this directory just as if they where on your computer.


Tom

---

### Post by sdb2028 on 2006-03-03
Thanks that helps, 
Replace "shared directory" and "local directory" with the name of the directory to be shared and the directory I made on this computer- correct?
Wat if I want to shre more than one directory, do I have to set up and mount each seperatly?

---

### Post by megamania on 2006-03-03
[QUOTE=sdb2028]Thanks that helps, 
Replace "shared directory" and "local directory" with the name of the directory to be shared and the directory I made on this computer- correct?[/QUOTE]

Yes. The directory you create on the computer is called "mount point".

[QUOTE=sdb2028]
Wat if I want to shre more than one directory, do I have to set up and mount each seperatly?[/QUOTE]

Right. Unless you have specific needs, my advice is to just share /home, which should allow you to access all of your data.

---

### Post by el3ktro on 2006-03-03
[QUOTE=sdb2028]Thanks that helps, 
Replace "shared directory" and "local directory" with the name of the directory to be shared and the directory I made on this computer- correct?
Wat if I want to shre more than one directory, do I have to set up and mount each seperatly?[/QUOTE]

Yes thats correct. If you want to share two directories, then you have to mount them both seperately on the other computer.

Tom

---

### Post by sdb2028 on 2006-03-03
Thanks for all your help, I should be able to get it up and running now. I was under the mistaken impression that it would detect the shared files automaticaly.

---

### Post by sdb2028 on 2006-03-03
When trying to mount I get this error:
mount: RPC: Program not registered

---

### Post by el3ktro on 2006-03-03
I forgot, you also have to install & start the nfs-user-server on the machine which wants to mount the remote directory.

Tom

---

### Post by sdb2028 on 2006-03-03
Curiosity: what is the difference between nfs-user-server and nfs-kernel-server?

---

### Post by el3ktro on 2006-03-03
The user-server runs in user-mode, while the kernel-server runs in kernel mode. The latter is more insecure, since an error in the nfs module could affect the kernel, while an error in the user-server would proably just crash the NFS server, but would not affect the kernel and the stability of the whole system.

Tom

---

### Post by sdb2028 on 2006-03-03
So I should use the nfs-user-server? But shouldn't it work in iether one? Right now I have the nfs-kernel-server installed. (in both machines) Maybe I didn't start the server, how do I do that?

---

### Post by el3ktro on 2006-03-03
[QUOTE=sdb2028]So I should use the nfs-user-server? But shouldn't it work in iether one? Right now I have the nfs-kernel-server installed. (in both machines) Maybe I didn't start the server, how do I do that?[/QUOTE]

Well I strongly suggest that you use the nfs-user-server instead. You can start it by typing

sudo /etc/init.d/nfs-user-server start

It is also started automatically when you turn the computer on, so you just have to do this once for now, or you just restart your computer. But Linux usually never needs to be rebooted, so it's easier to do it this way.

Tom

---

### Post by sdb2028 on 2006-03-03
Thanks, I'll install the other one and go from there.

---

### Post by sdb2028 on 2006-03-03
/home failed, reason given by server: Permission denied

now what?

Your help is greatly appreciated, we are getting closer.

---

### Post by megamania on 2006-03-03
[QUOTE=sdb2028]/home failed, reason given by server: Permission denied
now what?
Your help is greatly appreciated, we are getting closer.[/QUOTE]

hmmm. Can you post the command you're entering?

**el3ktro** has far more knowledge than me, but if he's not around I'll try to help. And maybe somebody else will be able to help you too.

---

### Post by sdb2028 on 2006-03-03
Have a problem, When I go to the shared folders tab in Admin.- the window comes up empty and greyd out. I have to "force quit" to close ti. When I open the file browser and right click on a file then click on the "share folder" tab, nothing happens. It was working before, now I cant assign any folders to share.

---

### Post by sdb2028 on 2006-03-03
sudo mount 192.168.1.101:/home ubuntushop

---

### Post by sdb2028 on 2006-03-03
just checked prmisions on "home", shows root as owner. That could be the permission problem. However, now I can't assign any other folders.

---

### Post by megamania on 2006-03-03
[QUOTE=sdb2028]sudo mount 192.168.1.101:/home ubuntushop[/QUOTE]

1) are you sure that the nfs daemons are running on both machines?
2) is ubuntushop the mountpoint? why don't you create an "ubuntushop" directory in /mnt and then try to mount it with
sudo mount 192.168.1.101:/home /mnt/ubuntushop
3) are you sure that 192.168.1.101 is the correct address? one time I went crazy trying to connect two machines, and I was trying the wrong IP address...
4) look at the server's /etc/exports, if your client computer has the right to mount your home directory (this shouldn't be the problem though)

Hope that helps. Please keep in mind that I'm a newbie (my first time with linux was 6 months ago), so take my suggestions with care. Just trying to help you out... :-)

---

### Post by sdb2028 on 2006-03-03
Yes, nfs-user-server is running on both machines.
I try'd making a directory "mnt"
Yes I m sure that that is the correct address (how do I check to make sure?)
Here is what me export file say's:
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
 
/home/steve     192.168.1.0/255.255.255.0(rw)

---

### Post by sdb2028 on 2006-03-03
steve@yuznetmobile:~$ sudo mount 192.168.1.101:/home/steve /mnt/ubuntushop
mount: 192.168.1.101:/home/steve failed, reason given by server: Permission denied

Can anyone tell e how to get past this?

---

### Post by el3ktro on 2006-03-03
Hello, please look at the file /etc/exports on the server. Mine looks like this:

```

/home/thomas    192.168.1.20(rw,async,no_root_squash,insecure)

```

This exports my home directory, and only the computer with the IP 192.168.1.20 is allowed to access it. It's exported rewriteable, writes are asynchronous (faster, but a little unsecure, only use on stable local networks!)

You may ant to replace the IP address by a * which would allow any computer to connect to this export, or you can write here something like 192.168.1.* which would allow all the computers in your LAN to connect, but not any computers from other networks.

Tom

---

### Post by sdb2028 on 2006-03-04
Heres what mine looks like

/home/steve     192.168.1.101(rw)

---

### Post by sdb2028 on 2006-03-04
Progress----- I got the desktop to read the laptop- but the laptop still gets a permission error from the desktop.

---

### Post by sdb2028 on 2006-03-05
New problem from trying to set networking-sharing: I got this message on both my laptop and desktop-- 
> Your $HOME.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language  from being saved. File should be owned by user and have 644 permissions.
I set the permission of the file to 644 on both the laptop and desktop, I still get the same error message on the laptop. And the desktop- well I can log in- but when I click o anything it gives an error that it cannot open some file. I cant do anything on the desktop. The laptop works fine, except for the initial error message right after logon.
HELP!? please!?

---

### Post by WelterPelter on 2006-03-05
[QUOTE=sdb2028]New problem from trying to set networking-sharing: I got this message on both my laptop and desktop-- 

I set the permission of the file to 644 on both the laptop and desktop, I still get the same error message on the laptop. And the desktop- well I can log in- but when I click o anything it gives an error that it cannot open some file. I cant do anything on the desktop. The laptop works fine, except for the initial error message right after logon.
HELP!? please!?[/QUOTE]

There are several threads in this forum about this issue. Actually, it isn't much of a problem, except that it's annoying to get that message. It doesn't seem to hurt anything. 

In any case, using the "Search" function for this forum, you can find the answer(s) to this question.

---

### Post by sdb2028 on 2006-03-05
I did use the search function, read the threads-- All I found was people who had the problem and questions on how to fix it. I found no answers or proceedures to correct the problem.

---

### Post by sdb2028 on 2006-03-07
Hello, still trying to network my computers. Finaly got rid of the dmrc error.
Still cannot connect the laptop to the desktop. I have nfs server running on both machines, have set up my home folder to share between them, try'd to mount them. (once I get this to finaly work-- how do you get them to automaticaly mount when you start your computer?)
I try'd to enter the wild card (*) in the IP address. won't accept it from the -system-admin-shared folders-properties-add host window. Should I enter that directly into the exports file from gedit?
One more question (for now) what exactly do these attributes do?:
(rw,async,no_root_squash,insecure)
If your out there el3ktro, thanks for your help so far. Unfotunately I need more.

---

### Post by henriquemaia on 2006-03-11
[QUOTE=sdb2028]Hello, still trying to network my computers. Finaly got rid of the dmrc error.
Still cannot connect the laptop to the desktop. I have nfs server running on both machines, have set up my home folder to share between them, try'd to mount them. (once I get this to finaly work-- how do you get them to automaticaly mount when you start your computer?)
I try'd to enter the wild card (*) in the IP address. won't accept it from the -system-admin-shared folders-properties-add host window. Should I enter that directly into the exports file from gedit?
One more question (for now) what exactly do these attributes do?:
(rw,async,no_root_squash,insecure)
If your out there el3ktro, thanks for your help so far. Unfotunately I need more.[/QUOTE]

Hi,

About the attributes, they are:

**rw** - read/write allowed (opposed to ro - read only)
**async** - the transfers are made asyncronously - faster but less reliable
**no_root_squash** - if you connect as root to the other computer, you'll have root access there (root user won't be squashed by the nfs server)
**insecure** - this reverses the default nfs operation mode (i.e. secure). Under secure, your connections must be done from a reserved port number (below port 1024). In insecure, this does not apply.

If you want your shares to be available to any computer on your network and you want to use the graphical tool to add that, go to **System** - **Administration** - **Shared Folders**, and then on that tool choose your share and select **properties**. Under properties, on **allowed hosts**, select **add host** and click the [COLOR="Red"]**ok**[/COLOR] button leaving the option on the top on **Hosts in the eth0 network**. That will make your share available for anyone on your network.

To get your nfs shares mounted on boot, you'll have to add a line to your fstab file, located in /etc . That line will look something like this:

remote.computer.ip.address:/remote/shared/folder	/local/folder/where/it/is/mounted	nfs	auto,rw	0 0

but first it's better to have all your nfs problems solved.

Hope this helps. Good luck.

---

### Post by gertmul on 2006-03-15
For what it is worth: I just wasted some time by asking for the wrong share with nfs. 

if the /etc/exports file says   "/mnt/ubuntu5.10 192.168.1.0/255.255.255.0(rw)"

then the "mount" command should be:
"mount 192.168.1.2:/mnt/ubuntu5.10 temp"  

and NOT 
"mount 192.168.1.2:/ubuntu5.10 temp", 

the latter results in 
"mount: 192.168.1.2:/ubuntu5.10 failed, reason given by server: Persmission denied"

Not the best of errors messages I would come up with, but I guess NFS was born long before me!

---

