---
title: "SAMBA Resource Intensive?"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by mcman56 on 2011-11-08
Is SAMBA resource intensive....as in...would it be a bad idea to load on an old laptop?

---

### Post by capscrew on 2011-11-08
> **mcman56 said:**
> Is SAMBA resource intensive....as in...would it be a bad idea to load on an old laptop?

Not at all.  I run a Samba server on an old Dell P3 with 512MB of RAM.

---

### Post by papibe on 2011-11-08
Not really.

Are you also going to use the laptop as a desktop? How old is it?

If you are going to have several clients accessing intensively the shares, then the local desktop experience won't be the best. However as a server would be just fine.

BTW, I have a 512Mb RAM Pentium4 serving Samba shares and NFS to XBMC (movies and music), and it works perfectly.

Regrads,

---

### Post by capscrew on 2011-11-08
> **papibe said:**
> Not really.


I have to disagree here.  The question was about Samba not desktops or GUI's.  There are literally millions of Samba installs running on light resources (CPU).  They are the NAS boxes that WD, Samsung et al sell everyday.

---

### Post by mcman56 on 2011-11-08
I sort of use it like a desk top.  It is a a Compaq/ HP Something Notebook from about 2004 with 1 G of ram.
 
I would just like to be able to pull files from a Windows system on the network.

---

### Post by capscrew on 2011-11-08
> **mcman56 said:**
> I sort of use it like a desk top.  It is a a Compaq/ HP Something Notebook from about 2004 with 1 G of ram.
 
I would just like to be able to pull files from a Windows system on the network.

Does it have Ubuntu on it already?  If so, it already can browse Windows shares (as a client).  Without knowing specifically the CPU is it's hard to tell, but my suspicion is that should work just fine.

---

### Post by JayKay3OOO on 2011-11-08
nah, I've run a samba file server on an athlon xp and that clocks in around 2GHZ single core.

File serving is really all about the hard drive speed and the network connection speed because this is essentially what causes a file server to go slow as it's not a particularly complex operation for the computer to complete as it does not need to display and render files.

If you have a lot of people connecting to it while you are trying to work then of course your computer is going to go slow because the hard drive is having data copied from it so it's just like having a constant file transfer going on and if u've ever tried to do more than 6 or 7 at a time then the drive gets bogged down and OS operation becomes slow.

SSD does use a little more CPU than HDD, but not much extra.

The point being that you can have the fastest CPU in the world and then kill the performance with a slow drive.

---

### Post by mcman56 on 2011-11-08
> **capscrew said:**
> Does it have Ubuntu on it already? If so, it already can browse Windows shares (as a client). Without knowing specifically the CPU is it's hard to tell, but my suspicion is that should work just fine.
 
 
It is currently running Ubuntu.  How do I browse the Windows system hard drive?  I thought SAMBA was needed to pull things from a network.

---

### Post by capscrew on 2011-11-08
> **mcman56 said:**
> It is currently running Ubuntu.  How do I browse the Windows system hard drive?  I thought SAMBA was needed to pull things from a network.
You can't browse a local Windows hard drive.  I'll bet you are dual booting.  You will have to mount the drive to a mount point, say /mnt/win. This has nothing to do with Samba at all.

If you have a *Windows share* on a remote host (another computer) you can browse for that, but that is very different from a local partition that happens to have Windows formatting and data on it.

---

### Post by mcman56 on 2011-11-08
I think I'm getting more confused.  The laptop is Ubuntu only. It is not a dual boot.  I want to pull files from the hard drive of another PC.  This other PC is on the wireless network running Windows Vista.  Are you saying I do not need SAMBA?  If so, what do I need to do?  Thanks

---

### Post by capscrew on 2011-11-08
> **mcman56 said:**
> I think I'm getting more confused.  The laptop is Ubuntu only. It is not a dual boot.  I want to pull files from the hard drive of another PC.  This other PC is on the wireless network running Windows Vista.  Are you saying I do not need SAMBA?  If so, what do I need to do?  Thanks

Hold on there.  So there are 2 machines.  When you said *"How do I browse the Windows system hard drive? " *  I assumed that this was a local partition and that you were dual booting.

Since you have a second machine then you do have to use Samba and the other machine must share the directory before you can see it and move files.  The both machines must be on the same LAN (Local Area Network) for Samba to work).

Is the wireless network the same for both machines?  Are any directories shared on the Windows machine?

I have 2 laptops running Windows Vista that I have shared directories.  I run Ubuntu Desktop with Samba.  All machines can see all the shares.

---

### Post by mcman56 on 2011-11-09
Both machines are on a wireless network.  They currently access a wireless printer on that network. 

[LIST]
[*] I shared one directory on the Windows system.  (Do I need to do something else on the windows side?)
[*]I found some directions stating all I needed was the smbfs plug in so I loaded that.
[*]From there the directions get very detailed with lots of commands in a terminal.
[*]I'm a beginner and did not get it to work.
[/LIST]
So....what is the easiest way for a beginner to set this up?  Is there a SAMBA guide for idiots?  This is just at home so I don't need all of the security stuff.  Both computers boot up without passwords.

Thanks

---

