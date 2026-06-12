---
title: "WTF is wrong with Samba?!"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2011-12-12
Ever since I adopted Ubuntu in 2007, I've had virtual tug-o-war with Samba.  One release of Ubuntu will have a working Samba, the next two don't.  Samba will work one day, then updates break it.  Why do broken Samba packages get pushed to the repos in the first place, and why don't the devs fix them?  Samba is by far the most frustrating part of using Linux.
I'm fully aware of how to configure and use Samba.  My complaint is that a perfectly working network one day becomes inoperable the next because so called "upgraded packages" break functionality entirely.
[SIZE="4"]
**A suggestion:**[/SIZE] replace samba with sftp or nfs as the "native" network browsing in Linux.  Why should I be made to suffer errors that read "Could not connect to Windows Network" on a network that only has Linux computers, and why is this the DEFAULT behavior?  When I open "Network" in Nautilus/thunar/dolphin, it should display all types of shares not just Windows shares.

---

### Post by akavir on 2011-12-12
I just came to the Ubuntu forums wondering if samba was as much of an issue in 11.10 as it is in Linux Mint 12 that I'm using.  I have 3 linux mint computer running on my network and they save and load all their files from a TB NAS.  The last 2 versions of Mint have had samba working seamlessly out of the box.  But I go and install 12, (which by the way works amazing other than Samba.)  I've been pawing around various tutorials and posted on the Mint forums a weeks ago, with no answers, I was hoping to get some insight here in the Ubuntu forums to see if this is an upstream bug?  The weirdest part, on my HTPC I access movies and music off the NAS through XBMC, and it does read the smb share and loads my media library, but I have no access through the file browser no matter what things I do with samba settings.  I went to Mint because the I like the ability to use the wide range of ubuntu repos without dealing with the direction Ubuntu is heading as a desktop.  But I guess I still have to deal with the breakages.  Seriously though, how can you mess up something as basic and necessary as samba?

---

### Post by redmk2 on 2011-12-12
> **N00b-un-2 said:**
> Ever since I adopted Ubuntu in 2007, I've had virtual tug-o-war with Samba.  One release of Ubuntu will have a working Samba, the next two don't.  Samba will work one day, then updates break it.  Why do broken Samba packages get pushed to the repos in the first place, and why don't the devs fix them?  Samba is by far the most frustrating part of using Linux.
I'm fully aware of how to configure and use Samba.  My complaint is that a perfectly working network one day becomes inoperable the next because so called "upgraded packages" break functionality entirely.
I have not had the same experience as you.  All of my Samba shares work fine and have so since Ubuntu 7.10 (Gutsy Gibbon).  I have both  updated the OS and installed fresh on numerous hosts.  I have never had an update create a problem with Samba.  I have used the same configuration (smb.conf) on all of my installs.  The only differences are the share definitions.  I don't see any breakage and the package maintainer has not mentioned any difficulties either.> 
[SIZE="4"]
**A suggestion:**[/SIZE] replace samba with sftp or nfs as the "native" network browsing in Linux. 
Define "native network browsing".  :-)> 
 Why should I be made to suffer errors that read "Could not connect to Windows Network" on a network that only has Linux computers, and why is this the DEFAULT behavior? 
If you setup Samba correctly you would not have to suffer through anything.  The term "Windows Network" is just that: a term for a network that supports (SMB/CIFS).  I'm not sure what you mean by "this the DEFAULT behavior".  SMB/CIFS is no more the default than NFS or SSH.  The only default I know of is that a Samba client is installed by default.> 
 When I open "Network" in Nautilus/thunar/dolphin, it should display all types of shares not just Windows shares.
Neither SSH (sFTP) or NFS have "browsable shares" from a file manager.  NFS shares (exports) are mounted to the local file file system transparently and sFTP must be used in a SSH session.

My suggestion is to use whatever works for your situation.  If you have problems ask for help here.

---

### Post by redmk2 on 2011-12-12
> **akavir said:**
> ... Seriously though, how can you f**k up something as basic and necessary as samba?
Ahhhhh...the network configuration can be culprit, not necessarily a specific Samba problem per se.

---

### Post by N00b-un-2 on 2011-12-12
What I mean by default is use something aside from samba in dynamically browsable shares (what you see when you open "network" in you file manager of choice).  We should not be using a windows based solution for Linux when there are a half dozen alternatives, most of which being FAR more secure.  What I mean by "native" is what is seen when you open the network dialog in Nautilus/thunar/dolphin.
Samba >>IS<< set up properly on my computers.  It works fine when I configure it, and then installing new samba packages breaks my ability to browse network shares.  I've been using the same smb.conf since the days of 8.04 and when it works it works.  But updates often break things.  My proof is that installing samba from a fresh install and copying my smb.conf (and configuring my shares per each computer accordingly) results in working Samba browsing.  downloading the updated packages  breaks samba browsing.  Reverting to the old packages fixes samba browsing.  Seems pretty straight forward to me.

---

### Post by N00b-un-2 on 2011-12-12
> Neither SSH (sFTP) or NFS have "browsable shares" from a file manager. NFS shares (exports) are mounted to the local file file system transparently and sFTP must be used in a SSH session.

when samba breaks, I can still access samba shares in the same manner as sftp, eg; typing smb://user@192.168.X.X or sftp://user@192.168.X.X in the location bar, then entering my username and password.  The difference is, SFTP never tells me "access denied" when I type in a proper user name and password.  Samba has always been fidgety about permissions in my experience.  sometimes just refreshing a window will change "Access Denied" to a browsable share.

In terms of security I'd say its a toss up between sftp and NFS.  NFS is great because you can specify exactly who gets to access the shares.  SFTP is great because it's very secure and yet allows you access to more than just a folder containing "Music" or "Photos".  I just want zero configuration networking.  Time to buy a mac maybe?  

out of curiosity, could you post your smb.conf so I can compare your configuration to mine?

---

### Post by Morbius1 on 2011-12-12
> when samba breaks, I can still access samba shares in the same manner as  sftp, eg; typing smb://user@192.168.X.X or sftp://user@192.168.X.X in  the location bar, then entering my username and password.Then samba isn't broke.

What does appear to be broken is name resolution. That's a different problem. 
> NFS is great because you can specify exactly who gets to access the sharesI don't want to start an NFS - Samba war but I can create a samba share that is accessible to only one user and only if that user is accessing that share from a specific machine.

---

### Post by N00b-un-2 on 2011-12-12
well then name resolution is what breaks CONSTANTLY on samba.  I've never lost the ability to manually open a samba share, but dynamically accessed network browsing is what sets Samba apart from sftp or nfs.  i don't want to start a samba/nfs war either as they both have their uses.  But if dynamic network browsing doesn't work, Samba is effectively broken and has no advantage over any other method of file sharing.  This is a fairly simplistic view of things but that's the gist of it.  If I click on windows network and I get an error message saying "Could not retrieve shares list from server" or "Could not open Windows Network" or "Access Denied" then Samba is effectively broken.  Especially when it worked properly the day before.

---

