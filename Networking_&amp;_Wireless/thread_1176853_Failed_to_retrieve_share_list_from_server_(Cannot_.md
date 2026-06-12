---
title: "Failed to retrieve share list from server (Cannot access Windows workgroup)"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by mc51299 on 2009-06-02
I have two small and unrelated home based windows networks, each having several Windows XP computers on it but one having some Vista computers and one having no Vista computers. Both have a Buffalo Tech TeraStation NAS.  My Ubuntu 9.04 PC (clean new install) sees the Windows network at both locations and the Windows workgroups that exist on both.  And, on the Windows network that has no Vista PCs, my Ubuntu PC can access the Windows network AND the computers on that network, including the NAS (although after the upgrade to 9.04 it takes several attempts/retries to get them to mount). BUT, my Ubuntu PC cannot access any of the computers on the network that has some Vista PCs, not even the XP PCs, and gives an error "Failed to retrieve share list from server".  The reason I mention that one network includes some Vista PCs and one does not is that this is the ONLY difference between them that I can think of. Does anyone have any idea what is going on?  Thanks!

---

### Post by superprash2003 on 2009-06-03
are the machines able to ping each other?? try this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by dmizer on 2009-06-03
Please see the 6th link in my sig.

---

### Post by mc51299 on 2009-06-03
Thanks Superprash2003 - Yes, I can ping the other computers and I can even see the NAS shares using the smb://x.x.x.x approach, but can't open any of them.  I should be able to find them by name going through Places->Network->Windows Network->'Workgroup Name' as this works on one network but not the other.

And thanks Dmizer - I had seen your post before, but I've done none of this and yet it (Places->Network->Windows Network->'Workgroup Name') works on one network but not the other virtually identical one - the only difference between the networks is the specific router and the fact that one network has a couple of Vista PCs in addition to the XP PCs.  I've now also tried all 4 of your steps with no effect unfortunately.

So still no resolution I'm afraid.

---

### Post by dmizer on 2009-06-03
If you are able, I would suggest testing the trouble network with all the Vista computers disconnected (or turned off). If you are then able to gain access to the XP and NAS shares, you will need to look into possible Vista configuration problems.

Edit:
Also of note, I've found many references which state that (although it is possible) by default, Vista prevents you from sharing entire drives.

---

### Post by mc51299 on 2009-06-03
OK dmizer - I am not sharing entire drives on Vista BUT I turned off the two Vista computers and then the Places->Network->Windows Network->'Workgroup Name' approach DID start working as with the other network that had no Vista PCs. Then it stopped again when the Vista PCs were turned back on. So it is definitely just the presence of the two Vista PCs that is mucking up the works. (Interestingly, the two Vista PCs were seen under their workgroup name even when they were off - probably some kind of memory from previous attempts even). What now then?!?!

---

### Post by dmizer on 2009-06-03
Well, this is probably a Vista configuration issue, but just to be sure, please post the contents of your /etc/samba/smb.conf

---

### Post by mc51299 on 2009-06-03
Well Dmizer, Samba is not installed, so this file is the default file installed with Ubuntu. Everything appears essentially commented out. Since it is so long, I just added .txt to the file name and attached it here. What do you think?  (Did the file get attached?)

---

### Post by mc51299 on 2009-06-03
Sorry - here is the smb.conf file properly attached to this post.

---

### Post by dmizer on 2009-06-03
Not everything is commented out.

I have a small edit suggestion that may make a difference. Please open the smb.conf file for editing:
```
gksudo gedit /etc/samba/smb.conf
```
And add netbios name = <your computer name> just below "workgroup = WORKGROUP" like so:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = [COLOR="Red"]computer-name[/COLOR]
```
Replace [COLOR="Red"]computer-name[/COLOR] with whatever your Ubuntu computer is named (everything after the "@" symbol on the command line).

For example, here's my CLI prompt:
```
dmizer@[COLOR="Red"]shinkansen[/COLOR]:~$
```
And here's my smb.conf file:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = [COLOR="Red"]shinkansen[/COLOR]
```

Also, scroll down a bit and remove the ";" from in front of this line:
```
;   name resolve order = lmhosts host wins bcast
```

Once you've made those two edits, save the file and either restart samba or reboot. Then try to access the Vista shares again.

---

### Post by mc51299 on 2009-06-06
OK dmizer, I've made the change but no effect is evident for the Places->Network->'Worgroup Name' approach. For the other approach, smb://xxx.xxx.xxx.xxx, it did actually work once, but only once for a protected share amd never since. One thing I have noticed is that using the smb://xxx.xxx.xxx.xxx approach, I can always access shares that are not user/password restricted, but on that shares that are, nothing happens - no access, no request for user name or password, and no error message (except for the one time).

---

### Post by mc51299 on 2009-06-06
OK, at this moment the smb://xxx.xxx.xxx.xxx approach IS working. So there appears no rhyme or reason to when it does or doesn't. But the Places->Network->Windows Network->'Workgroup Name' approach still never works on the affected network.

---

### Post by dmizer on 2009-06-06
What is the output of:
```
smbtree
```

---

### Post by mc51299 on 2009-06-07
smbtree as a command causes the system to ask me for my password, then, after inputting that, returns nothing. I have maybe found a pattern though (which may or may not have already existed prior to the last two changes you suggested). It appears that if I try the Places->Network->Windows Network->'Workgroup Name' approach first, even though it fails, and then then try the smb://xxx.xxx.xxx.xxx approach that I CAN gain access to the protected shares. If this pattern is correct, and not my imagination, does it make any sense?

---

### Post by dmizer on 2009-06-07
> **mc51299 said:**
> smbtree as a command causes the system to ask me for my password, then, after inputting that, returns nothing. I have maybe found a pattern though (which may or may not have already existed prior to the last two changes you suggested). It appears that if I try the Places->Network->Windows Network->'Workgroup Name' approach first, even though it fails, and then then try the smb://xxx.xxx.xxx.xxx approach that I CAN gain access to the protected shares. If this pattern is correct, and not my imagination, does it make any sense?

Does smb://computername work? In other words, can you get there with the netbios name instead of the IP address?

---

### Post by mc51299 on 2009-06-23
Yes, using the name instead of the numeric address seems to work. But I have found another clue maybe - the problems seem to start when one of the Vista PCs actually logs onto or even just tries to log onto the file server with specific user name/password access.

---

### Post by dmizer on 2009-07-01
Do you have password protected shares on the Vista machines?

---

### Post by smarks on 2009-09-17
> **mc51299 said:**
> Sorry - here is the smb.conf file properly attached to this post.

Hey man thanks for this smb.conf file. I have been looking all over for a solution. yours was very helpful.

---

### Post by Visserys on 2009-09-20
[CENTER]Hi guys, for various reasons, mainly I wanted to play savage 2 and my ati card didnt have opengl 2.0 support Im using ubuntu 8.04. 
Everything is working ok except I cannot connect to windows shares. If I wait about five minutes I can browse "workgroup" and see the computers, but I cannot open them. It says failed to retrieve share list from server. I have everything samba installed and tried pyneighbourhood, in which i can actually see the "folders" that should be shared on the computer Im trying to access, but again I cannot access anything.
What should I do haha.... Im a noobie:confused:
[/CENTER]

---

### Post by Visserys on 2009-09-20
> **Visserys said:**
> [CENTER]Hi guys, for various reasons, mainly I wanted to play savage 2 and my ati card didnt have opengl 2.0 support Im using ubuntu 8.04. 
Everything is working ok except I cannot connect to windows shares. If I wait about five minutes I can browse "workgroup" and see the computers, but I cannot open them. It says failed to retrieve share list from server. I have everything samba installed and tried pyneighbourhood, in which i can actually see the "folders" that should be shared on the computer Im trying to access, but again I cannot access anything.
What should I do haha.... Im a noobie:confused:
[/CENTER]

  
Output from smbtree command:

shaun@holly-lappy:~$ smbtree
Password: 
WORKGROUP
    \\SHAUN-LAPPY            
timeout connecting to 61.110.21.165:445
timeout connecting to 61.110.21.165:139
cli_start_connection: failed to connect to SHAUN-LAPPY<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\HOLLY-LAPPY            holly-lappy server (Samba, Ubuntu)
        \\HOLLY-LAPPY\IPC$               IPC Service (holly-lappy server (Samba, Ubuntu))
        \\HOLLY-LAPPY\print$             Printer Drivers

---

### Post by dmizer on 2009-09-20
> **Visserys said:**
> Output from smbtree command:

shaun@holly-lappy:~$ smbtree
Password: 
WORKGROUP
    \\SHAUN-LAPPY            
timeout connecting to 61.110.21.165:445
timeout connecting to 61.110.21.165:139
cli_start_connection: failed to connect to SHAUN-LAPPY<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\HOLLY-LAPPY            holly-lappy server (Samba, Ubuntu)
        \\HOLLY-LAPPY\IPC$               IPC Service (holly-lappy server (Samba, Ubuntu))
        \\HOLLY-LAPPY\print$             Printer Drivers

Check for, and disable any firewalls, both on the Ubuntu machine and on the shaun-lappy machine.

---

### Post by wired99 on 2009-09-20
Thank you thank you thank you.
I had a similar thread running but no one was able to help me.
This link help me to connect my computers. thank you again.

[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Visserys on 2009-09-20
[CENTER]> **dmizer said:**
> Check for, and disable any firewalls, both on the Ubuntu machine and on the shaun-lappy machine.


Ok So I tested by completely turning off the firewall on my Win 7 machine and it still didn't work. Im not really sure how to turn the firewall off on my Ubuntu 8.10 machine, but I looked around and didn't see anything installed.

Thanks.
[/CENTER]

---

### Post by xanmalone on 2009-09-23
I'm guessing he means the default ufw.

Basically, open a terminal window and enter the following:

sudo ufw disable
--

That disabled the basic Firewall Ubuntu has, or you could call it a frontend for the iptables.

When you're done you should enable it by typing:

sudo ufw enable

--

If that's the cause of your problems, i'm sure someone here will help you configure your system to allow local shares to be accessed.

Personally my network sharing folders stopped working after upgrading to 9.04. So i have to use the smb:// approach in Nautilus

---

### Post by Fhernd on 2010-02-19
Hi!

I have the same problem... I applied the recommendations from **dmizer**, but the problem persists.

So long!

---

### Post by dmizer on 2010-02-19
Those of you having this problem on Vista Win7 shares after applying the fixes outlined in the 6th link in my sig, please try this possible fix: [http://ubuntuforums.org/showpost.php?p=8848476&postcount=344](http://ubuntuforums.org/showpost.php?p=8848476&postcount=344)

---

