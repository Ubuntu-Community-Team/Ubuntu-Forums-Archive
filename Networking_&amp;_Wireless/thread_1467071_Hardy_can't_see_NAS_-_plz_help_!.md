---
title: "Hardy can't see NAS - plz help !"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by dik23 on 2010-04-30
Hi, I thought I'd finally ask for help. I have been at this for a couple of weeks.

I have a machine here running Hardy. I use it as a slave and normally access it with NX which is why I have stuck with the LTS release. I want to update to Lucid but I think it's wise to get this sorted out first.

I have had a folder on my Linkstation NAS mounted in fstab for getting on for 2 years, until recently when I discovered that if I reset the machine I'd end up with a desktop with a constant waiting cursor. I commented out the line in fstab and the cursor's back to normal.

If I go to Places > Network it shows the Linkstation along with the share on the linux box and a share on a XP machine I use for gaming. The NAS comes with 2 shared folders by default: share (where my files are) and info (instructions etc). I can open info and look at what's stored in the folders there but I can't open or copy anything. I get a "Connection timed out". I can't even open the share folder and get the same error if I try although it does mount both folders with icons on my desktop which I can unmount. If I try to do this too much nautilus crashes. Every machine on the network can view the share on Hardy, as long as the correct password is used.

Now I can do anything I like with these folders if I use my XP machine, my misses laptop that runs Karmic, my netbook, my XBOX that runs XBMC and the Hardy machine if I boot from LiveCD so it's not an issue with the NAS, network or hardware. It has to be an issue with the install of Hardy.

I can ping the NAS but if I put the LAN 192.168.2.4 into a browser I can't see the page it should show although it does qualify the address with a /cgi-bin/top.cgi. The browser sits there "forever" saying it's waiting. This page can be viewed from every other machine.

If I mount the folder using "sudo mount -t cifs //192.168.2.4/share /mnt/linkstation -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777" it mounts with no error output but I can't view anything still.

I use Firestarter to edit IPTables and 137-139 and 445 are open. This has worked for almost 2yrs. 

"wins" is referenced in the hosts line of /etc/nsswitch.conf

winbind is installed (needed for WINE)

Some errors that "might be connected" and keep popping up in /var/log/ are :

nsswitch/idmap_tdb.c:idmap_tdb_alloc_init(397)   ## 397 and 750 are displayed alternatively 
idmap uid range missing or invalid
idmap will be unable to map foreign SIDs

nsswitch/winbindd_passdb.c:sid_to_name(130)
Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend

syslog:
CIFS VFS: server not responding
CIFS VFS: No response for cmd 50 mid 5002  ## the last number changes

I also get :

CIFS VFS: Send error in SETFSUnixInfo = -11

When I Google "SETFSUnixInfo = -11" I almost get a googlewack, there's 3 results. One isn't in English and another is from a post I made asking about it ! Not very helpful. There's plenty of references to SETFSUnixInfo = -5 but no -11 and I'm not qualified to know if the -11 is relevant.

I am attaching a txt file with the content of smbtree, smb.conf, smbclient -L linkstation, findsmb and sudo iptables -L

I am half tempted to just update to Lucid but can't help feeling as if that could just compound my problems. Thanks in advance for any help

---

### Post by dik23 on 2010-05-30
Ok - upgraded to Lucid now and have same problem

I'm finding this especially confusing because other machines can see the share on the Lucid box and the Lucid Box can see a share on a XP box, whilst everything apart from my Lucid box can see the NAS.



Also tried 

sudo mount.cifs //192.168.2.4/share /mnt/linkstation -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

with no luck, syslog still giving me 

CIFS VFS: No response for cmd 50 mid NNN
CIFS VFS: Send error in SETFSUnixInfo = -11


Anybody ??

---

### Post by Iowan on 2010-05-30
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help - if you haven't already seen it...

---

### Post by dik23 on 2010-05-30
Yeah, seen that quite a lot recently

Something I have just noticed is if I do a 

sudo /etc/init.d/samba restart

I get

sudo: /etc/init.d/samba: command not found

I have been using the new way :

sudo service smbd restart
sudo service nmbd restart

---

### Post by dik23 on 2010-05-30
Just noticed something else 

As I mentioned I have a shared drive on lucid

I can access it from multiple locations but I've just right click > share and it's telling me it's not shared ?!

Edit: I can mount it, but not under the name it's already mounted under, and unmount it and the share keeps working ?!
Edit2: Ok, if I do a sudo nautilus I can see it's shared - odd that it doesn't show up to the user

---

### Post by Iowan on 2010-05-31
A [similiar]("http://ubuntuforums.org/showthread.php?p=9383607") thread - now solved. Dunno if it's similar enough to help...

---

### Post by dik23 on 2010-06-01
Ok - got it working now after much grief

The NAS has an option to adjust ethernet frame size (Jumbo Frames).

It seems my lucid box didn't like that - which is odd seeming as none of the other machines in the house have had any issues at all.

At least it's working, thanks for all advice given, much appreciated

---

