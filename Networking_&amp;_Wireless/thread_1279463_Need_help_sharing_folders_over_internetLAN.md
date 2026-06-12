---
title: "Need help sharing folders over internet/LAN"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by Thanh-BKK on 2009-09-30
Hello.

I have a major poblem. Boss told me that he wants to go paperless - no problem. However my machines don't play along!

Situation: 24 machines via several switches on a router, each one has it's own static true internet IP (leased line!) and the internet stuff works perfectly. 22 of the machines run Ubuntu 9.04 Jaunty, two run Windows XP. A workgroup is set up as well, all machines are member of that workgroup.

The two Windows machines can happily see each other's "shared folder" and they also happily use the one printer that is physically connected to one of them. 

However NONE of the Ubuntu-machines sees either Windows machine (or any of the other Ubuntu machines), and neither Windows machine sees ANY of the Ubuntu machines!! Looks like all my Ubuntu boxes are deaf-mute, and now i need to get them to talk and listen.

Samba and smb-client are installed on each of them, a folder that is supposedly shared (with read/write access for other users) is on the desktop and such folder is also on the Windows machines. All Ubuntus are on the correct workgroup as per smbconf but - nothing works.

How can i get it done..? Been googling for hours, found no solution. 

(at my home near-identical setup - 2x Ubuntu, 1x Windows XP and it works perfectly, the difference being that those three are on an actual LAN, not on true internet IP's)

And one more - if my project is possible at all (it works with Windows so should work with Ubuntu, too...) i need to do one more thing - the "shared folder" has to be on a removable drive, i.e. a flash drive. At home i shared an entire NTFS volume on one of my Ubuntu boxes with no problems, however that is not a removable device. How exactly can i share a removable device, or at least a folder on one, in Ubuntu? And is it possible to restrict access to such folder/device to just one IP, i.e. 22 employee workstations, one (Windows!) admin station and admin (and ONLY admin!) can place files into each employee's flash drive, while each employee can place files into a folder on admin's machine. 

I have two days to get this going... if not i'll have to go Bluetooth which would be a nightmare.

Many thanks in advance for any advice/hints/tips/tricks.

Kind regards.....

Thanh

---

### Post by nevarDeath on 2009-09-30
I am by no means an expert, but when faced with a network problem, the first thing I do is make sure the computers can ping. I know this sounds so stupid simple, but ti's usually a great place to start. Have you tried to ping the XP computers from the ubuntu ones? I don't know jack about samba, but also have you checked the firewalls on the windows boxes? You said they were all connected with switches, if there is a router in there, I would check for a firewall there too, or forwarded ports? Is firestarter on the ubuntu machines? Maybe some firewall issues there? This is the simple stuff you should verify first IMHO.

---

### Post by gordintoronto on 2009-09-30
First, tell your boss that two days is not reasonable.

"You can convince a fool to commit to an unreasonable deadline, but there is nothing in the world you can do to make him meet it."

I suggest you set up one real domain server with private and public shares on it.  Forget the flash drive nonsense.  Each workstation does not need to have a shared folder; a whole network can do very nicely with one public shared folder, maybe with folders within it for different kinds of files.

If admin needs to send files to users, do it as email attachments.

---

### Post by Thanh-BKK on 2009-09-30
Hi :)

Well you are certainly more of an expert than me :) As to "ping" - i know how to do that from DOS or a DOS-prompt on a Windows-box but how do i ping on Ubuntu..?? 

Firestarter? Sorry, i am hearing that the first time, really.

The Windows boxes only run the Windows built-in firewall and i don't think there is an issue with it, after all the Windows boxes happily talk to each other. It's the Ubuntu boxes that are deaf-mute (as those can't see each other either) but they all have internet so the network connection/switches/router are fine. 

The router neither requires to forward ports nor is there a firewall. All ports are open/forwarded and all sorts of communication can pass through. It's a leased line with 32 true internet IP's, it goes modem -> router -> big switch -> VoIP boxes, few computers, more switches -> more VoIP boxes, more computers. 

What i have done so far is what i did at home - downloaded/installed Samba, smbclient and system-config-samba, created a shared folder on each machine, made sure they are all on the same workgroup and hoped it would then work because at home it DOES. At the office it does NOT. The only difference is the fact that at the office they have internet IP's while at home they have LAN IP's. 

(can i add a second, static LAN, IP..??? I remember from the leased line provider we also have a set of LAN IP's..... as many as Internet IP's in fact, but can i give one machine two IP's at once..?)

Kind regards.....

Thanh

---

### Post by ghostborg on 2009-09-30
[http://ubuntuforums.org/showthread.php?t=1165234]("http://ubuntuforums.org/showthread.php?t=1165234")

---

### Post by Thanh-BKK on 2009-09-30
> **gordintoronto said:**
> First, tell your boss that two days is not reasonable.

"You can convince a fool to commit to an unreasonable deadline, but there is nothing in the world you can do to make him meet it."

I suggest you set up one real domain server with private and public shares on it.  Forget the flash drive nonsense.  Each workstation does not need to have a shared folder; a whole network can do very nicely with one public shared folder, maybe with folders within it for different kinds of files.

If admin needs to send files to users, do it as email attachments.

Hello.

The problem is - i am the admin. My job is to get the company's e-mail and provide the attachments to the employees. So far it was done by printing them and saving them on my machine (Windows, because all happens on a PGP encrypted drive - and there's no PGP for Linux). Now we already changed to flash drives - instead of printing i put the attachments on the employee's flash drives. Still have to walk around to collect and distribute the flash drives, however the guys need their data when they go home as some work from home, too. 

I was thinking of a file server - however i don't know how to set one up or how to run one, i am a hardware guy who can build machines but when it comes to software i am pretty much lost. 

So all i need is my shared folders on flash drives and first of all the Ubuntu machines to be able to talk to the admin machine. The boss is the one who pays the salary soe he shall not be questioned, if he wants it done it needs to get done (and heck i make 4 times the average salary in this country so i better get it done). And i do NOT put Windows back on those machines even though there it would work right away - it took me long enough to convince the boss to try Linux and once he saw one working and liked it i did all the others too.

Best regards....

Thanh

---

### Post by nevarDeath on 2009-09-30
I too am a hardware guy. I do tech support for extended warranties and that's my job is to determine hardware failure all day long. Ping works the same in linux as it does in windows except you have to stop it with ctrl-c or it just keeps pinging forever.

If you haven't heard of firestarter, then don't worry, it's not your problem. It's a front end GUI that configures the linux built-in firewall for you.

One thing I have learned is to never underestimate windows firewall. as simple as it is, I've seen it do some crazy things. It won't take 10 minutes to disable that firewall and try to ping it from a few of your linux computers. Judging by the info you've provided I too doubt it's a low-level connection problem, but if the basics aren't covered then you can't expect the more complex things to work either.

This tops my skill level in your situation, but at my job I always regret it when I don't check the simple things first.

---

### Post by rafttrip on 2009-10-01
Hello

I have a similar problem.

I have 3 PC I am trying to share a folder. 1 Ubuntu desktop 1 Ubuntu laptop on wireless and 1 Windows desktop.

At the moment I can't share any thing; however the Win PC can see the shared folder on the laptop but cannot access it. 

The laptop can see both computers but cannot access ether PC. it says can not mount the share for the Ubuntu desktop. It asks for user name and password for the windows machine but I haven't setup any thing like that on the Windows machine?

I have shared files before with this setup but the laptop was using Mint7 at the time.

Any help would be appreciated.:)

Update:
I am now able to see Ubuntu laptop and Windows desktop under Places>Network>Windows Network>WORKGROUP

I connected to the laptop using 'Connect To Server'

On the laptop both desktops show up but still getting the 'Unable to mount location: Failed to retrieve share list from server' error message. I am however able to share files using the 'Connect To Server' method. https:

//help.ubuntu.com/community/SettingUpSamba 

"Alternate : From the menu at the top select "Location" -> "Connect to a server". In the "Service type" pull down select "Windows share". Enter the server ip address in the "Server:" box and the share name in the "Share:" box. Click "Connect" and then "Connect" again on the second dialog box (no need for a password)."

This is an acceptable workaround for now but would be better if it worked the way it should.

If any one can help it would be greatly appreciated.

---

