---
title: "Failed to retrieve share list from server"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by kwalters on 2010-07-24
Trying to share files between Ubuntu 10.04 machines has become a continuing nightmare; it has been going on ever since the launch of 10.04.

I have worked my way through every post and howto I can find in this forum, but without success.

I have 3 machines in my home network; 2 are on wired connections and one on wireless.  Each machine dual boots Ubuntu 10.04 and Win XP.

When all machines are in XP, everything is fine.  When all machines are in Ubuntu, the reverse is the case.  On some I can see the other machines; on others I can only see "Windows network". In all cases, clicking on any of the icons that emerge from Places>Network, I get the "failed to mount....failed to retrieve share list from server."

Along the way, I have changed /etc/samba/smb.conf so often that I have now done a clean reinstall of Ubuntu on each machine and a clean installation of Samba. The problem remains.

I have a few specific questions, the answers to which might just lead me in new directions

1.   In the smb.conf file, should the "Netbios name" entry be the name of the machine itself or the name of the Ubuntu machine that you wish to be the server.?


2.   Should there be a different entry for WINS support yes/no for server and clients?

3.   Many of the howtos take you to /etc/init.d/samba to start and stop samba; but that folder is not present on any of my installations.  Is that OK?  Do those instructions only apply to earlier versions?
4    I am totally at a loss over the WINS server entry, and what w,x,y,z are meant to be replaced with

IF anyone could answer the above questions, that would be a great help

Thanks

KW

---

### Post by Iowan on 2010-07-24
Working on another "Failed to retrieve share list..." thread, but a couple of answers for you:
1. The name of the machine itself. Primarily, the smb.conf file is used to configure the machine as a server (but see item 3).

2. The client wouldn't need it ("no"), the server might - but only one/network.

3. Samba client come pre-installed, but the server will need to be added. After installation, that option may be there.

4. That would be the IP address of the WINS server - that option isn't used if the machine itself is set up as the WINS server (item 2). 

Although not a Samba Setup How-To, [this]("http://ubuntuforums.org/showthread.php?t=1169149") might be helpful.

---

### Post by kwalters on 2010-07-24
Many thanks for that prompt respone, Iowan.

I am going back to put wins support to no on every machine except the one I want as server.  Also, on that machine (the server), I will not enter the wins server, but will put its IP address on all the others. Presumably (from what you say) I could delete the hostname entry on all except the designated server.

Will let you know when I have played around for a bit.

By the way, I did try the GUI system for Samba Configuration as I normally avoid terminal operations like the plague.  However I challenge anyone to change the Samba password from whatever the default is using that GUI
Thanks again

KW

---

### Post by Iowan on 2010-07-24
> **kwalters said:**
> Presumably (from what you say) I could delete the hostname entry on all except the designated server. I'd leave it - it won't hurt anything.

Don't be surprised if more knowledgeable folks come along with better information. My Samba knowledge is deteriorating as Samba changes.

By the way, in the past (back when I kinda understood Samba) I had better luck with the "Connect to Server" option.

---

### Post by kwalters on 2010-07-30
I think it is worth recording what happened after I tried IOWAN's suggestion.

Firstly, I got 2 of the 3 Ubuntu machines to share files, but the third would not do anything,   I  decided that I had mucked about with the configuration so much that I might as well do a clean reinstall of 10.04 and start again.

After a clean reinstall of the original 10.04 ISO cd I found Samba ready installed with the package but had to make the file sharing work by installing the apache2-bin files and the libapache2-mod-dnssd (or whatever they are called)  Immediately all 3 machines could browse each other and actually move files in each direction,   Perfect, I thought;  problem solved.  I had not touched any SMB.conf file from start to finish.

Then Update manager reminded me I needed updates,  I installed the 243 files it identified.  I was conscious of reading that it was updates that seemed to be causing the problem.  So I was pleasantly surprised when my networking continued to work perfectly after the update,

HOWEVER, tonight, the first boot up on the recalcitrant machine since the update, I was back exactly where we all started.  The dreaded message about could not retrieve share information appeared on every machine that I tried to network with.  I think I have now proved conclusively that the updates are behind the problem; but which of my 243 files was the culprit is beyond my expertise,  I tried going back to kernel 21, the original, but that achieved nothing;  whatever the update did has stuck.
  
I am now clean out of ideas.  I have devoted innumerable hours to reading this forum and its HOWTOs and trying out their suggestions; but my Ubuntu machines cannot network with each other.  When even one of them is working Windows XP, everything seems to work; but with Ubuntu alone I am back to having no networking.

I see from this forum that the problem persists for other people  - even people who appear far more expert than I.  I submit it is about time that the official Ubuntu team got to grips with this problem and organised a patch  - and organised a way of advertising it.  I think that, as a minimum, this topic deserves a sticky at the top of this forum.

Interestingly, I had just changed from having Win XP as the default in Grub to haing UBUNTU.  I am now reverting to Win XP as the default.  I so not propose to waste any more time ploughing through this forum every night in the hope of a solution.  If a proper solution is found, I should be grateful for an email on [email]keithwalters2002@yahoo.co.uk[/email] to let me know


KW

---

### Post by redmk2 on 2010-07-30
> **kwalters said:**
> I think it is worth recording what happened after I tried IOWAN's suggestion.

Firstly, I got 2 of the 3 Ubuntu machines to share files, but the third would not do anything,   I  decided that I had mucked about with the configuration so much that I might as well do a clean reinstall of 10.04 and start again.

After a clean reinstall of the original 10.04 ISO cd I found Samba ready installed with the package but had to make the file sharing work by installing the apache2-bin files and the libapache2-mod-dnssd (or whatever they are called)  Immediately all 3 machines could browse each other and actually move files in each direction,   Perfect, I thought;  problem solved.  I had not touched any SMB.conf file from start to finish.
The files you mentioned ([COLOR="Red"]**installing the apache2-bin files and the libapache2-mod-dnssd (or whatever they are called)**[/COLOR]) have nothing to do with Samba.  It is unfortunate that Ubuntu dev's have chosen to name "Personal Sharing" as such.  This causes no end to users who don't know the difference between the two types of shares that can be created (e.g Samba or Personal). > 


... my Ubuntu machines cannot network with each other.  When even one of them is working Windows XP, everything seems to work; but with Ubuntu alone I am back to having no networking.
The XP host runs the Microsoft equivalent of Samba.  XP knows nothing about "personal shares" on Ubuntu.  I believe that this is called Web-DAV, But I'm no Microsoft expert. > 

I see from this forum that the problem persists for other people  - even people who appear far more expert than I.  I submit it is about time that the official Ubuntu team got to grips with this problem and organised a patch  - and organised a way of advertising it.  I think that, as a minimum, this topic deserves a sticky at the top of this forum.
Samba works fine for me.  I think you just need to understand the difference in the two types of sharing.

---

