---
title: "Getting Windows 7, XP, and Ubuntu to share files"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-09-22
Recently, I've again been trying to get file sharing working on my home network.  I made some progress last night, getting so far as having all the shares on my Windows XP desktop visible to a netbook running Ubuntu 10.04 & connected wirelessly.  But I ran into some snags.

Here's what I'm working with:

-a desktop running Windows 7 Ultimate
-a desktop which dual boots Ubuntu 9.10 64-bit and Windows XP Pro SP3
-a netbook which dual boots Ubuntu Netbook Remix 9.10 and Ubuntu 10.04.

Everything connects wired except the netbook, which connects wirelessly.  The router assigns each a specific internal IP address, so in effect all have static internal IP addresses, tied to the MAC addresses of their network adapters.

I have Samba Server Configuration Tool installed on both the desktop (Ubuntu 9.10) and netbook (Ubuntu 10.04).  Versions are 1.2.63 in both Ubuntu 9.10 and 10.04.

Here's as far as I got last night:

-Shares on the Windows XP machine were accessible from both the Windows 7 machine and Ubuntu 10.04 on the netbook, with no password required.

-I configured Samba on both machines to be part of the same workgroup (named PENGUIN) as the Windows 7 machine and the desktop when it's running Windows XP.  

-I set up a share in Samba on the netbook while running Ubuntu 10.04.  The share is visible on the network from the Windows 7 machine, but I couldn't access it.  I was asked for a username and login.  I had no idea which one to use, but no combination I tried worked.  Windows kept saying it couldn't find a "path" to the share.

-In the Nautilus "network" item on the netbook, I can see the shares on my Ubuntu 9.10 desktop.  But I can't access them.  Again, I get asked for a username and password, and I have no idea what to enter, or where the username and password can be set.

-I set up a share on the Windows 7 machine, allowing read-only access to everyone.  But it doesn't show up on either of the Ubuntu machines, at all, in the "Penguin" workgroup.
So I'm not sure how to proceed.

Do I need to explicitly configure the IPv4 settings on each machine to a static internal IP?  As I stated, each machine gets a predictable address assigned by the router, so in effect the machines do have static IP addresses.  However, I'm not sure that's all the same to Samba.

---

### Post by wyliecoyoteuk on 2010-09-22
the IP addresses are immaterial, unless you have set up access masks.
You will need a username and password to access shares, unless you enable the guest account.If you enable guest access, anyone can login as "guest"
This username and password will need to be consistent across all the machines, unless you enter it when required, but it will still need to exist on the target machine.
Note that Samba users are not necessarily the same as Linux users, i.e. you can have Samba users and Linux users seperately on the same Linux PC.

To enable guest access, go to places, home folder (you can only share folders in your own home folder), right click on the folder that you want to share, click the share tab, tick all the boxes then click create share.

Of course this is not really recommended, as it allows anyone to edit your files.

Windows 7 also disables guest account and network discovery by default, but you will need to google that.

---

### Post by Objekt on 2010-09-22
Network discovery is definitely enabled on the Windows 7 machine, as is the guest account.  However, I don't see why that matters, as I'm not wanting to log in to the Windows 7 machine with the guest account.  

I followed a walkthrough I found here:

[http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/]("http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/")

to ensure the share on the Windows 7 machine would be accessible from the rest of the network.  It's written for Ubuntu 10.04, but the same things should work for 9.10, right?

If I understand what you're saying, Samba usernames and passwords are distinct from Ubuntu usernames and passwords, and it's the Samba users that are important when configuring Samba shares. 

Is there no way I can share things outside my /home folder?  I have a couple of the items in /media set to "shared" in Nautilus, and I gave read-only access to "everyone" in Samba Server Configuration.  So why isn't that showing up on the Windows 7 machine?  It only sees its own shares.

I also don't see the Windows 7 machine's shares from the Ubuntu 9.10 desktop.  I'm looking in the proper workgroup ("Penguin") but the Windows 7 machine's share isn't there.  That doesn't make sense.

Don't quite know what's going on between the Ubuntu 9.10 desktop & Ubuntu 10.04 netbook.  I can access the desktop's Samba shares from the netbook, but not the other way around.

---

### Post by headvampyre@hotmail.co.uk on 2010-09-22
Hi, i run 4 virtual samba servers in a domain environment but i would like to point out that this example is extremely useful: [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554221](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554221) also, try searching through the samba wiki [http://wiki.samba.org/](http://wiki.samba.org/) and all there docs [http://samba.org/samba/docs/man/](http://samba.org/samba/docs/man/) i hope these sites help

---

### Post by Objekt on 2010-09-23
Thanks, but I'm not trying to do anything nearly so complicated.  I just want the ability to access files on my Ubuntu 9.10 machine from a Windows 7 machine on the same network (and the other way round as well).

I messed with it some more just now, and noticed 3 weird things:

1) The Windows 7 machine isn't visible in the workgroup it's supposed to be in on the Ubuntu 9.10 machine.  The Windows 7 machine is a member of the "PENGUIN" workgroup, but when browsing the "Network" in Nautilus, I find the Windows 7 machine in a workgroup just called "WORKGROUP."  That workgroup shouldn't exist.  The Windows 7 machine is the only Windows machine on the network, and it is only a member of "PENGUIN."

2) When I try to open the Windows 7 machine from the Ubuntu 9.10 machine to browse the share I setup there, I'm asked to log in.  But nothing I enter works, so I can't access the Windows 7 machine's share.  The dialog which pops up has my Ubuntu username (objekt910) entered automatically, the proper workgroup name (penguin), but my password does nothing.  I specifically set myself up as a Samba user, using the same username (objekt910) and password that I use to log into Ubuntu.  But it doesn't work.


What password could this dialog be expecting?  I don't understand.

3) From the Ubuntu 9.10 machine, I CAN see the Samba share on a netbook also on the network, which is running Ubuntu 10.04.  However, I can't access the share.  I just get an error dialog stating, "Unable to mount location - Failed to mount Windows share."

---

### Post by Objekt on 2010-09-25
I think I found one more piece of the puzzle.  When I'm running Windows XP on my machine, I can see, but cannot access, the share on the Windows 7 machine.  So it appears there is a problem to clear up on the Windows side of things before I can access anything with Samba while running Ubuntu.

Getting Windows 7 and XP to talk to each other is surprisingly difficult.  I enabled everything I could find on the 7 machine that had anything to do with sharing, but I'm not being allowed to open its share from the XP machine.  I don't even get a request to log in, just straight up "Access denied."  Go figure.

---

### Post by Objekt on 2010-10-14
I've made a little more progress, but I'm still having some absolutely unexplainable problems.

When running Ubuntu 10.04, I can designate shares in the Samba Server Configuration application, and they are all visible to the Windows 7 machine.  So that's some progress.

However, I can't actually access the shares from the Windows 7 machine!  Every time, I get an "Access denied" message, even though I set all shares to be accessible (both reading and writing) to "Everyone" in the Samba config app.

The only exception: a folder that is in my /home folder.  I can access it fully from the Windows 7 machine.  But that's no help, as my /home partition in Ubuntu 10.04 is far too small (around 5 GB) to be of any use, and anyway it would take forever to copy over all the files I want to make available to the Windows 7 machine.

What is so magical about folders in my /home directory?  Why can't I share anything else?  The other folders I want to share all reside on NTFS volumes that are automatically mounted in /media, as specified in my fstab file, during Ubuntu 10.04 starup.

---

### Post by lfpnk0 on 2011-12-30
[FONT=Arial][FONT=monospace]*Ubuntu 10.11 & *[/FONT][I]Samba Server 3.5.11

Could not access Ubuntu share from networked XP SP3 computer, although could access XP share from Ubuntu... 

adding "netbios name = ubuntu" to the [GLOBAL] section of /etc/samba/smb.conf and restarting samba using sudo restart smbd & sudo restart nmbd fixed it for me*.*[/I][/FONT][I][I]

hope this helps someone...
[/I][/I]

---

