---
title: "How to share files between 2 ubuntu computers?"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by SOME1 on 2009-05-04
Hi, 
I have 2 computers, both running Ubuntu 9.04. 
Both connected to the same router - one use wireless connection and the other wired connection. 

On the computer that use the Wireless connection, I have some files I want to read via the home networking with the pc that use the wired connection.

can someone please help me - How can I configure it in an easy way? 

thanks a lot.

---

### Post by aromo on 2009-05-04
You could do it with Samba but since they both are *nix I think it's easier to mount the share on the remote computer as NFS (do not confuse it with NTFS).

---

### Post by thedonkster on 2009-05-04
I have EXACTLY the same problem!

For the life of me I can't share folders between the two computers. I have created a dummy shared folder on each Ubuntu desktop - but neither computer can access the shared folder of the other.

I installed SAMBA - but I'm not even sure this is right because I think samba is for networking with Windows? Now when I click on 'Places', 'Network' - I have a 'Windows Network' that I'm unable to mount!! (And there's not a Windows PC in sight!!)

I'm not sure what NFS is...  I've googled - but really stuggled to find a good guide to networking Ubuntu PCs!

Thanks

---

### Post by jevharr on 2009-05-04
I am having the very same problem (sort of). My Jaunty desktop is wired into the router. My Jaunty laptop and XP desktop are connected via wireless. Everyone can ping each other. The wireless clients are able to share files. The wired Jaunty desktop cannot see the others or share over the network. It's like there are 2 networks on the same router, a wired one and a wireless one. Any thoughts on how to get everything on the same network??

---

### Post by thedonkster on 2009-05-04
I've installed Samba and I'm struggling with the settings...

In 'preferences', 'server settings' I originally tried giving both computers the same workgroup name - and I could view file one way but not vice-versa.  I've now given each computer a different workgroup name and i can -finally- view files both ways - BUT each computer has its own workgroup name (I'm not sure if that matters!).  Oh, and both workgroups sit in a 'windows network' directory - despite Windows being banished from the house!  

I'm fairly competent on Windows and I've found networking in Ubuntu difficult.  Hopefully future Ubuntu distros will include a simple GUI.

Good Luck!:)

---

### Post by jeff913 on 2009-05-04
I share files using NFS.  Google "ubuntu NFS" for general instructions.
you need to Install NFS Server Support and Install NFS Client Support, and create the shares on the server in the /etc/exports file.  I also configure static ISP addresses via DHCP in the router. For example, my wired server is 192.168.10.145 the wireless clients are 192.168.10.155 and 192.168.10.160 This allows you to define specific isp addresses for the exports file and to limit which client can access which files.  I hope this makes some sense.  Regards.....     Jeff

---

### Post by blackgr on 2009-05-04
GIVER!! IS the answer!

sudo apt-get install giver

P.S: both pcs must have it

---

### Post by thedonkster on 2009-05-04
Interesting reading - thanks for the suggestions.  NFS sounds too techie for me but I might check out Giver.

Incidentally, my Samba shares are set to 'Allow access to everyone' via 'properties' on the GUI.  Is this safe, or should I be creating users?!

Is there any reason why Ubuntu won't let me put both PCs in the same workgroup?!

Cheers...:)

---

### Post by stchman on 2009-05-04
> **SOME1 said:**
> Hi, 
I have 2 computers, both running Ubuntu 9.04. 
Both connected to the same router - one use wireless connection and the other wired connection. 

On the computer that use the Wireless connection, I have some files I want to read via the home networking with the pc that use the wired connection.

can someone please help me - How can I configure it in an easy way? 

thanks a lot.

Use NFS.  Samba is for Windows machines to connect to Linux machines.  Samba has no place on an all Linux network.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

---

### Post by Xzera on 2009-05-04
Have you tried to go to Nautilus and 
File -> Connect to server
Then choose SSH as service type and then fill in the ip and port to the computer you want to connect to. That's how I do it to connect my laptop and my other computer.

---

### Post by blackgr on 2009-05-04
> **thedonkster said:**
> Interesting reading - thanks for the suggestions.  NFS sounds too techie for me but I might check out Giver.

Incidentally, my Samba shares are set to 'Allow access to everyone' via 'properties' on the GUI.  Is this safe, or should I be creating users?!

Is there any reason why Ubuntu won't let me put both PCs in the same workgroup?!

Cheers...:)

As you said.. nfs needs config.  Its not for noobs. Samba is too complex too and slow! Both ways work , but its not for everyone. Giver is a fast userfriendly way to share fileS among ubuntu and linux distros in general. ON the other hand if you want something more portable, WebDAV and NFS is good for macs kai Samba for windows.

---

### Post by SOME1 on 2009-05-04
thanks for all the replies. 
I don't sure I understand: There is no easy solution to share it? 

If I understand it correctly, The easiest way is the program Giver, but its not sharing a whole directory - its more like sending files from one computer to another? 

I read also about the connect to server option. If it will work, Is there a way that you can set it up so every time after boot the ubuntu will connect to the shared library automatic? 

If I understand correct, samba is not for ubuntu to ubuntu connection - its for ubuntu to windows connection? 
and about nfs - I understand its not easy to set it... 

I don't know what to do. :(

---

### Post by blackgr on 2009-05-04
giver has option for folders and files. just give it a try and give us some feedback :)

sudo apt-get install giver

---

### Post by VastOne on 2009-05-04
> **blackgr said:**
> giver has option for folders and files. just give it a try and give us some feedback :)

sudo apt-get install giver

Tried this on several Jaunty machines with total failure to transfer any files.  I set up SSH  (sudo apt-get install ssh on both machines) and was instantly pleased and done....

Very poor documentation or support on Giver as well

---

### Post by ^_Pepe_^ on 2009-05-05
OK!

Here goes the noob way. Let's take a look to ssh and giver and so on.

1. In the origin computer, with Nautilus, go to the folder you want to share [share options, should be the literal], right button, share, put the permissions if needed and it is.

2. In the other one, with Nautilus, type smb://your_other_computer_ip/ and that folder should appear as shared.

This is for human beings.

With my wifi conection, I get 2 Mbps transfers rate, that is more than with NetBios.

I promise to have a look to ssh, and say if it's REALLY simple ;-)

Regards,
^_Pepe_^

---

### Post by SOME1 on 2009-05-05
I tried giver and ^_Pepe_^ connect suggestion: 

giver work, but I don't know how to configure boxee to work with it. 
aout ^_Pepe_^ suggestion, I can see the directory from the other computer but it keeps asking me for username and password and I can't figure out yet what this username or password is. I tried to configure username and password with this commands in the source computer 

sudo useradd username
sudo smbpasswd -a username

and type the username and password in the computer I want to view the files without success. 

please help. 
thanks.

---

### Post by ^_Pepe_^ on 2009-05-05
I didn't use smbuser at all.

Ok, perhaps my installation is not the most secure in the world, but it's functional to me.

Try this:

In the origin computer, go to the folder you want to share, and "unshare" it. Click right button and look for "open here as root" (perhaps you should install a Nautilus script to do that). Otherwise, there are methods to open a Nautilus as root, and surf to your folder. Share that folder as root. You will see more options for permission (x,r,w,...). I ticked all for everybody, because my sons are only 5 year and 1 month old. Perhaps in ¿4? year I should use more restrictions.

Giving "0777" permission to this folder, I can go to my netbook and type smb://my_other_computer_ip/my_folder and go for it. Even, I have no samba installed in my netbook. Only smbclient.

My /etc/samba/smb.conf file in the sharing machine is only changed to include my general Windows WORKGROUP, because I have 3 more Windows machines at home. Check this on your smb.conf [[#   security = user]]

I'm a noob as well. I feel panic giving you some advice, but you "are" "me" 6 month ago... :D

Regards,
^_Pepe_^

---

### Post by albinootje on 2009-05-05
> **VastOne said:**
> I set up SSH  (sudo apt-get install ssh on both machines) and was instantly pleased and done....

I'm a happy ssh user since many years. 
I use ssh and scp on the command line a lot, but if you need a GUI for it there's ssh support in :

- Gftp (choose SSH2 instead of FTP)
- Nautilus (sftp://)
- Konqueror (fish://)

---

### Post by ^_Pepe_^ on 2009-05-05
> **albinootje said:**
> I'm a happy ssh user since many years. 
I use ssh and scp on the command line a lot, but if you need a GUI for it there's ssh support in :

- Gftp (choose SSH2 instead of FTP)
- Nautilus (sftp://)
- Konqueror (fish://)

Ups!:confused: ¡¡EASY!! I've tried right now, and worked perfectly, out of the box. I have only had to install ssh in the "server" Ubuntu Machine. After this, I typed sftp://my_server_ip and voilá.

I can't check speeds now, because I'm over a linksys WiFi repeater which theoretically drops speed by half. But I could see good speeds also.

Happy! :lolflag:

I have included my sftp:// in favorites...

Regards,

---

### Post by albinootje on 2009-05-05
> **^_Pepe_^ said:**
> 
I can't check speeds now

Transfer speed with ssh/scp/sftp might be a little lower than with Samba or NFS because everything gets encrypted first. 
But that's another advantages of ssh over Samba and NFS : everything is encrypted.
With Samba you can encrypt the passwords but the rest of the data is not encrypted, and with NFS there's no passwords (That's already a security risk), and nothing is encrypted.
> 
I have included my sftp:// in favorites...

:)

---

### Post by SOME1 on 2009-05-06
thanks, the ssh method is great, but I have to problems with it: 
first its so slow... 
second, is there a way to set if so the user that connect to the computer can only read and no write? 

thanks.

---

### Post by albinootje on 2009-05-06
> **SOME1 said:**
> is there a way to set if so the user that connect to the computer can only read and no write? 


Use sshfs for read only mounts :
[http://ubuntuforums.org/showthread.php?t=715646](http://ubuntuforums.org/showthread.php?t=715646)

/etc/fstab example from that howto :
```

sshfs#share@bob-desktop: /media/bobs_share fuse ro,nosuid,nodev,max_read=65536,allow_other,IdentityFile=/home/joe/.ssh/id_share 0 0

```

---

### Post by ^_Pepe_^ on 2009-05-09
Hi everyone!

I've just posted the speed comparation between three methods here [http://ubuntuforums.org/showthread.php?p=7245511](http://ubuntuforums.org/showthread.php?p=7245511). Nothing important, but NFS wins the race.

Regards,
^_Pepe_^

---

### Post by SOME1 on 2009-05-09
> **albinootje said:**
> Use sshfs for read only mounts :
[http://ubuntuforums.org/showthread.php?t=715646](http://ubuntuforums.org/showthread.php?t=715646)

/etc/fstab example from that howto :
```

sshfs#share@bob-desktop: /media/bobs_share fuse ro,nosuid,nodev,max_read=65536,allow_other,IdentityFile=/home/joe/.ssh/id_share 0 0

```

thanks, I will try it. 
^_Pepe_^ , thanks for the comparation I'll take a look. :)

---

### Post by Maupertus on 2009-06-01
This may sound a bit MS-fanboy, but what I really liked in XP was that my roommate and me setup shared folders with read/write privileges and could just drop and delete what ever we wanted into it.

Which of the above methods would be best to get the same usability?

---

### Post by dmizer on 2009-06-01
> **Maupertus said:**
> This may sound a bit MS-fanboy, but what I really liked in XP was that my roommate and me setup shared folders with read/write privileges and could just drop and delete what ever we wanted into it.

Which of the above methods would be best to get the same usability?

Any of the above methods could do this. What you want to do is fairly basic file sharing, so any protocol will do: samba, nfs, ftp, scp (sshfs), or even http.

---

### Post by Maupertus on 2009-06-01
> **dmizer said:**
> Any of the above methods could do this. What you want to do is fairly basic file sharing, so any protocol will do: samba, nfs, ftp, scp (sshfs), or even http.

With these words of wisdom in mind, I thought it would be just a matter of cold-feet. And indeed...within two minutes I have a SSH set up that works like a charm


:)

---

### Post by albinootje on 2009-06-01
> **Maupertus said:**
> With these words of wisdom in mind, I thought it would be just a matter of cold-feet. And indeed...within two minutes I have a SSH set up that works like a charm 

Good choice, you have chosen the most reliable option (and the only one of those which does encryption by default).

And for MacOSX there's cyberduck, and for ms-windows there's WinSCP as scp/sftp clients.

---

### Post by technocp on 2009-06-05
just right click on the folder you want to share with other ubuntu PC select sharing option, select share this forlder (it may ask to install sharing services click on install to proceed and let it install from web) and allow others to read and write in this folder. go to other pc click on network in places menu select the other pc name available in the content area (right side) double click to browse through the contents of folder. its that easy

---

