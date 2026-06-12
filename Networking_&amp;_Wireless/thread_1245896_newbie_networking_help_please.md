---
title: "newbie networking help please??"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by loosie on 2009-08-21
Hi,

I'm brand new to Ubuntu, having just got onto it after a Windows crash. I've had 2 PCs networked successfully until now. One won't boot, so trying Ubuntu to transfer my files & data. Can't work out what's needed to network them tho. Hardware's in place, they are connected thru a modem/router by ethernet. Obviously getting thru to the internet, just not to the other computer.

Can someone give me some instructs on how to set up, pref as a remote desktop, which is what I had going?? Or point me in the direction of relevant instrucs? TIA.

---

### Post by jamest09 on 2009-08-21
Can the machines ping each other?

---

### Post by Iowan on 2009-08-21
Do they both have IP addresses in the same subnet? (They should - if DHCP is working right). If they can **ping** each other, then you may need to set up [Samba]("http://ubuntuforums.org/showthread.php?t=1169149").

---

### Post by loosie on 2009-08-31
Alas, you're speaking a foreign language!:confused: I have no idea if they can 'ping' or how to find out. What's DHCP & how do I find out if they have the same IP & if they're on the same 'subnet'??

What I know... The machines were networked fine when on Windows, remote desktop working. When I set up Ubuntu, I was also able to get to My Documents in the other machine, but for no apparent reason - haven't changed anything - the 'MS Home' network isn't showing up any more. When I go to places/network & click on 'Windows Network' it now says "Unable to mount location. Failed to retrieve share list from server."

I've just installed Samba(which I was sure was already there but I couldn't find it). Have no idea what to do with it tho...

---

### Post by Iowan on 2009-09-01
> **loosie said:**
> Alas, you're speaking a foreign language!:confused:  That can be changed... 
Several commands are easiest from a terminal - although **ping** is also available from System>Administration>Network Tools. The IP address and netmask can be learned by typing **ifconfig -a** in a terminal. 
The "Failed to retrieve share list from server" message reportedly means a firewall (somewhere) is blocking. 
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is another helpful How-To.

---

### Post by cranecreek on 2009-09-01
Here's another option. On the machine that won't boot, copy the files you need to your home directory.
Install scp on both 
Then use scp to transfer the files to the working box or
just burn them to a cd or dvd

---

### Post by loosie on 2009-09-01
Hi, Firstly thank you so much for your patience on my obviously novice, tedious questions!

> Several commands are easiest from a terminal - although **ping** is also available from System>Administration>Network Tools. The IP address and netmask can be learned by typing **ifconfig -a** in a terminal. 
The "Failed to retrieve share list from server" message reportedly means a firewall (somewhere) is blocking. Right, thank you! I have turned off the firewall & can now see my docs in the other computer again.

The ping page in Network Tools needs a network address. The terminal info gave me a whole lot of info, under headings eth0 lo & pan0. I presume the addresses therein are just for this computer? There are also;    HWaddr, inet addr, Bcast,  Mask & inet6 addr under the first 2 headings, just the HWaddr under pan0. Which one(s) of these are the appropriate ones to enter where? If they are just for this computer, how do I find the relevant info on the other Windows machine?

> **cranecreek said:**
> Here's another option. On the machine that won't boot, copy the files you need to your home directory. Install scp on both Then use scp to transfer the files to the working box or just burn them to a cd or dvd

Hi, sorry I didn't update in this thread, that the machine I'm on now is the one that wouldn't boot up.... in Windows. After loading Ubuntu(& since ditching Windows all together) I haven't had a prob with that & have got to my Windows files. At this point, sorting out a remote desktop, to be able to fully access my other (Windows) machine from this one's the only drama(touch wood...). What's scp?

Oh, yes, and the other thing... that I've got 2x Ubuntu loaded, because when I first loaded it, it didn't work too well because of how little the partition was because of Windows taking up so much space... so I deleted Windows & loaded Ubuntu into that big partition... but it won't let me delete the original Ubuntu or change partition size....?? 

There are also a couple of things I've tried doing that tells me I don't have permission for, even tho I'm the sole administrator, user, etc?? So much for touching wood!!

---

### Post by loosie on 2009-09-01
Oh, also I have ensured Samba is installed - it's ticked in the Synoptic package manager anyway - and I could see it in some area under the system tab last week, but I can't find it for the life of me now - where does it hide??

---

### Post by Iowan on 2009-09-02
> **loosie said:**
> There are also a couple of things I've tried doing that tells me I don't have permission for, even tho I'm the sole administrator, user, etc?? So much for touching wood!!For that, there's [sudo]("https://help.ubuntu.com/community/RootSudo"). In brief, for those commands requiring administrative (root) privileges, prefix the command with "sudo" (i.e. **sudo lshw -C network**). Password is your user password.

No one was born a Linux expert - if you're willing to learn, there are those willing to share.

---

### Post by loosie on 2009-09-09
Hi again, I input your instructions into the terminal(**sudo lshw -C network) **but it just came up with; [sudo] password for anya:

---

### Post by Iowan on 2009-09-10
Yup... at that point, you'll need to enter the password for your user (**anya**). It won't echo to the screen as it's being entered - or even display asterisks (*).

---

