---
title: "PLEASE can we get an idiot proof gui for setting up networking"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by scratman on 2009-02-09
I am trying to network an Ubuntu 8.04, Ubuntu 8.10 and Windows XP machine.  I am having a nightmare.  I am not especially technically minded, and am on the verge of giving up.  Instead of doing the usual, "I'm stuck, please do this for me *sob*" post, I thought it might be useful to ask whether there is a GUI where all you need to do is fill in boxes for IP addresses, usernames etc.  If there is, I'd be interested to know what it is.  If there isn't, can it be suggested for Ubuntu 09.04 or 09.10 and make life easier for everybody?  This is the one thing about Ubuntu that is a major bugbear of mine.  I'd appreciate your comments.

---

### Post by Coreigh on 2009-02-09
Well... I am not sure if this is true but I think the developers idea of that is the "Connect To Server" wizard in the places menu. I am not a big fan of it because the connections don't seem to be persistent (I have seen several complaints about this), and there are either too many options or not enough explanation of the options for the average user to use it easily.

In the mean time what kind of networking are you trying to implement? Shared folders? Or ... ?

---

### Post by FishRCynic on 2009-02-09
you can try gadmin-samba but it seems to be overkill to me
and i'm pretty sure the gnome gui shares aren't handled by it

shares in ibex can be created by in the nautilus gui - however these shares do not show up in the regular samba configuration file.  (i learned that yesterday exciting eh?)

samba is installed by default, but for some reason the gnome/nautilus/gvfs has trouble resolving the machine names.  i have retreated to using a wins server (pick one machine and activated in /etc/samba.conf) which actually has helped a lot.

other than the wins ubuntu should be set up already

---

### Post by scratman on 2009-02-12
Thanks for the replies, but my point still stands.  The Ubuntu raison d'etre is to "Just work", and as far as my experience extends, networking just doesn't.  To be frank, if you are transferring data over a wired network, or a wireless network that has been secured sensibly, security should not be a huge issue.  If you are not sharing your Root folder, os any of the system folders, just folders that hold your music/video collection or other non essential data, then why make life so blooming difficult.  As long as all of your systems are on the same network, you should be able to pt them on the same workgroup, and make it possible to set up the O/S so that you can right click a folder, select sharing, give it a sensible name so that users on other systems understand what's on it, and then just click apply.

If this is not possible, can't we have a GUI that operates a shell command or some clever code that just asks how you want to set up sharing, and then makes all of the relevant adjustments for you.

From there, can't we have a facility to save the configuration settings to a memory stick or cd, and plug that into any other Ubuntu/Windows PC on the network, which will make all the necessary adjustments for you?

As you can tell, I'm not overly technically minded, but unfortunately, a lot of Ubuntu users fit that demographic, and as I said previously, the mission for Ubuntu is to create a system that just works, and currently, I'm not sure that this does.

Any comments would be appreciated, especially if you can explain why what I have mentioned is impossible.

---

### Post by Reiger on 2009-02-12
You want to access shared data? Then on a Vista box it is as easy as ensuring that the PC is discoverable in the network -- and having a suitable account & partition set up (of course you can use the C drive too, but...)

Anyways, for the shared data on the Ubuntu side you can use FTP. There also is a desktop sharing thing, but I haven't experimented with that one...

Just lock the FTP folder with a password and if you want better: whitelist a certain domain from which to accept requests (ought to be possible with VSFTP, since it is with the WWW counterpart Apache2).

---

### Post by Dssnz on 2009-02-14
This thread walks you through it for anyone looking:

HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba.conf](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba.conf)

---

### Post by Carl H on 2009-02-14
I'm sure there's a "Shared Folders" menu item somewhere ('Places' ?), cos that's what I used. I'm at work at the mo and my Ubuntu machine is at home so I can't be more specific, sorry. 

It was a while ago now when I set all mine up, but I do remember being pleasantly surprised at how easy it was. Sorry, I doubt that's any help. :(

---

### Post by jimv on 2009-02-14
YOu know, I'm not usually a mean person, but did you even look before you started complaining?  In Ubuntu, right click a folder, and click Sharing Options.  Check all the boxes, then click Create Share.  BAM, your done.

Want to manually set your IP?  Right click on the NetworkManager icon in the tray (looks like two little computers) and click Edit Connections.  Find the connection that you want to edit, and click Edit.  Click the IP tab and change the network settings to whatever you want.

And "networking" is not a specific action or thing.  You need to tell us what you want to do exactly.

---

### Post by jimv on 2009-02-14
>From there, can't we have a facility to save the configuration settings to a memory stick or cd, and plug that into any other Ubuntu/Windows PC on the network, which will make all the necessary adjustments for you?

Setting up file sharing between computers has gotten to the point where if you can't do it, you're not even trying.  There's no IP's to configure, they do that on their own with DHCP.  There's no settings that need to be transferred anywhere.  All you have to do in Windows or Ubuntu is open up Network Places and there are all your computers (the ones that are sharing anything).  Sure, there are more complex setups that can be used, but out of the box, Windows and Ubuntu keep it very simple.

>Any comments would be appreciated, especially if you can explain why what I have mentioned is impossible.

It's impossible for Ubuntu to allow you to share files if you can't be troubled to right click on a folder and notice the Sharing Options menu item.

If three fairly intuitive check boxes and a button that says Create Share isn't "idiot proof", I don't know what to tell you.

---

### Post by FishRCynic on 2009-02-14
it just doesn't always work regardless of os and/or tools

the more computers on the network the bigger the hassle

windows networking has been problematic for years

rule #1 for local peer to peer networks using micrsoft/samba appears to be to set up a dns server or a wins server for name resolution.

for the last 2 years my son's xp machine refused to been seen by any other
machine (xp or linux (incl redhat, mandriva, debian, ubuntu and their variants (i know i have one variant listed already) or solaris) until i set up wins on my home network. 

this thread says and explains it all
(the title is somewhat misleading but still true)
[i wish i had found it before today]

[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

---

### Post by kgas on 2009-02-14
It is easier to have a network with ubuntu. With GNOME DE I could connect all my three PC and could share data thro' a shared folder. Installing samba will help you. Community documentation and wiki are there for help.

---

### Post by detroit/zero on 2009-02-14
I'm with the OP. Sharing isn't all that easy, especially for someone with little or no networking knowledge. And for someone to say "you must not be trying," I find not just a little bit insulting. Setting up an FTP server just to share a folder adds a level of complexity that simply doesn't need to be there; the same can be said for other methods, like sshfs.

I've been trying for two solid weeks to share an external HDD formatted FAT32 that contains all my video/music/documents between two dual-boot laptops on the same local network. I've been trying to set up samba (because of the dual-booting of both PCs) and found it all but impossible to share a FAT32 drive without in-depth knowledge of how samba works. The other shared folders on the PCs (specfically, the Public folders included in each users' home directory by default) come and go; hosts are sometimes discoverable and sometimes not, sometimes accessible and sometimes not. At every boot, each of us has to open a root-nautilus window and go reset the sharing options for the Public folder. ( A user can set sharing permissions for a folder in their home directory, but only root has the power to share the folder on a network.) Then, of course, samba has to be restarted from a terminal to make it all work. Sometimes just logging out and logging back in does the trick, but not always.

I finally managed to share the external drive and public folders between both comps when in Linux by using NFS and editing fstab, but this doesn't do anything for us when one of us is using Windows, and I don't think editing fstab is really a beginner-level task; you can screw up a lot of things by editing fstab and not knowing exactly what you're doing. Not only that, but now that the drive is in fstab and being shared by NFS, mounting and un-mounting it has to be done forcibly by root from a terminal, and only after issuing commands to shut down the nfs server. I can do that, sure, but I'm not sure how my wife is going to handle it, her being new to Linux and all. I made her a little cheat-sheet of commands, but she finds the process to be a pain in the rear. I do, too.

[Posts for help]("http://ubuntuforums.org/showthread.php?t=1068015") [on the issues]("http://ubuntuforums.org/showthread.php?t=1066645") [largely go unanswered]("http://ubuntuforums.org/showthread.php?t=1064345"). I shudder to think of when I'll get around to trying to make these shares accessible from either of our computers from anywhere on the internet. (I do a lot of traveling for work, and would rather leave my media in one place, given the [problems a traveler might encounter]("http://uk.gizmodo.com/2008/07/11/g8_wants_airport_security_to_c.html").)

Like OP, I think there's definitely room for improvement in the ease-of-use and ease-of-configuration side of Linux networking, especially considering that most people are sharing between their Linux installs and another OS, be it Mac or Windows or whatever.

---

### Post by jimv on 2009-02-14
>And for someone to say "you must not be trying," I find not just a little bit insulting.

Seriously, the OP didn't seem like he even looked before complaining.  I booted up my Ubuntu machine with a default install of 8.10, and was able to share a folder by right-clicking on it and clicking Sharing Options.  It was then visible to the Windows machines.  This is more than enough for MOST users.

---

### Post by detroit/zero on 2009-02-14
> **jimv said:**
> >And for someone to say "you must not be trying," I find not just a little bit insulting.

Seriously.  I booted up my Ubuntu machine with a default install of 8.10, and was able to share a folder by right-clicking on it and clicking Sharing Options.  It was then visible to the Windows machines.
Congratulations.

You call that "trying"?

It doesn't always work out that easy for everyone else - the fact that there's a forum dedicated to "Networking & Wireless" says as much.

---

### Post by cariboo on 2009-02-14
A lot of sharing problems are because the windows shares are not setup properly most Linux distributions can automagically see windows shares and access them with out any extra setup. It is because Microsoft doesn't acknowlege any other type of networks with out addons that Samba is needed for Windows to access shares on a Linux based computer.

I have to agree the Ubuntu's way of trying to make sharing is kind of flaky, sometimes it works and other times it doesn't, whereas a properly setup /etc/samba/smb.conf file is just set it up and forget. I've been using essentially the same smb.conf file for about 10 years, I always make sure I have a couple of backups just in case, then it is just a matter of copying the configuration file to the correct place and restarting samba.

Jim

---

### Post by jaqrah on 2009-02-14
I, too, would like to agree with op.  It is not as easy as pie.  I only have two comps, an Ubuntu laptop and a dualboot XP/Ubuntu desktop.  It should be easy to share across a simple network but nooo it is not. Setting up the Ubuntu to Ubuntu sharing was super easy with Samba and an online tutorial.  Within 5-10 minutes, my Ubuntu laptop could see my Ubuntu desktop and vice versa.  I restart, booting into XP.  Nothing.  XP refuses to see Ubuntu laptop and laptop has only seen XP once for a fifteen minute stretch (who knows what I managed to do).  I have looked at many Youtube tutorials.  I have read pages and pages of threads.  I can't get it to work.  I have tried.  I wish it would work.  I wish it was as easy as JimV suggests but it is not.

---

### Post by scratman on 2009-02-15
Thanks to everybody who's replied.  I'd like to give a little more information to people so that it doesn't look like I'm just posting for the sake of it.  I have a 1TB external dive and would like it to be accessible to the other computer users in the house.  We have two Ubuntu 8.10 and 1 Windows XP machine, with a Mac an occasional guest.  Now, I realise that in a perfect world, simply right clicking , selecting "Sharing Options" and ticking Share This Folder, Allow people to write in this folder, and guest access would do the trick.

I may be missing a trick here, but if my machine, and the other Ubuntu machine are on the same workgroup, surely the other machine should be able to connect to my shared drive? If I go to Places > Network, I am able to see the names of three PCs, mine included, and Windows Network.  if I click on one of the other machines, I get the message Unable to mount location, Failed to retrieve share list from server.  There are shared folders on the other Ubuntu machine, created following the same process as on my machine.  My PC is getting data to the router, otherwise I would not be able to make this post!  Am I being monumentally stupid, or is this being harder than it should be?

Oh, I have just checked and we are on the same workgroup in smb.conf.

---

### Post by jivabill on 2009-02-15
Well, I would take issue with the concept that setting up a network in Ubuntu being so easy now.  Not in my experience.

I had a win98se machine, a Compaq desktop running Ubuntu 8.04 and a HP Laptop running Ubuntu 8.04.  I knew little or nothing about setting up a network.  So...
I used synaptic, searched on Samba.  re-installed or installed every samba package that looked faintly useable.  Zowie!  My printer sharing and folder sharing worked across the network.  The win98se machine was the server, the Ubuntu machines were apparently also servers. That did not seem to matter everything worked.  I had no idea what I was doing other than just throwing every samba package at it.

NOW THEN

My son, a big time geek, he sent me a new to me Dell 4400 desktop running XP Pro, I could not install Ubuntu on it for reasons that have nothing to do with this discussion.

I thought, OK, I'll just plug it in place of the win98se box, set up windows networking using the network wizard. That all went fine, marked all the shared folders and shared the printer.

BUT, now the Ubuntu machines can see the shares on the XP machine but they can't open them.  After a long time, 3 minutes or so, I get a message says the share can't be mounted.  When I try to print to the network printer from the Ubuntu machines, a ONE LINE page take more than 5 minutes.  And along the way I get a message says can't connect to CIFS will try again in 60 seconds.

I have no clue what to do about this.  I have read about 50 pages of "how to set up a network in Ubuntu", only a lot of it was command line magic and the rest did not help.

Oh, one last thing:  The win98se machine can see and manipulate the shares on the XP Machine and vice versa.  And I can print to the network printer from the win98se machine no problem.

So, I have to differ: setting up a network IS NOT EASY.
My two cents
bill

---

### Post by scratman on 2009-02-17
I had been banging my head against a wall as it appears that my HDD cannot be shared by Ubuntu, as it is FAT32, and not a Linux file system.  I had managed to get access to my Public directory from another machine on the system via Firefox by typing smb://MY.IP.ADDRESS.X/ into the address bar, so I could see the machine.  I copied the folder settings of my home/public/ folder to the folders I wished to share on my USB HDD.  Nothing doing.

Then I had a brainwave.  I opened up terminal and typed 
```
sudo fdisk -l
```

This revealed that my external drive was mounted to /dev/sdb/.

I typed ```
sudo umount /dev/sdb1/
```

This made my hard drive disappear.  I then typed ```
sudo mount /dev/sdb1/ /home/myusername/Public
```

I then browsed to my home/public/ folder, and voila, my folders appeared!!!

I opened Firefox and typed smb://MY.IP.ADDRESS.IN/ and I could access my shared folders!!!  Clicking through I can access the folders and files that I have shared!

I then copied this address into Nautilus, and it still worked.

Navigating to my Hard Drive, I can set up write permissions for those that I wish to be fully accessed, and leave the remainder as read only.  Any folders that are not shared remain invisible.

As I said, this is an ugly solution, but it does mean that I have access.

Does anybody have any better ideas, because this is complicated!

---

### Post by Yellow Pasque on 2009-02-17
> "idiot proof"
One thing I was taught when I went to school for Computer Engineering was that there's no such thing. If you build an idiot-proof system, the world will build a more clever idiot. :P

---

