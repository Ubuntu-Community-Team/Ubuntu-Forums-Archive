---
title: "&quot;Failed to retrieve share list from server&quot;?????????"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by ubuntu1sttimer on 2009-12-16
Keep having trouble to trying connect with Ubuntu to network and shared drives. Doesn't mater if it is any Windows machine or my new D-Link DNS-321 network storage box. Three Windows machines have no problem with the D-Link box but both Ubuntu boxes give this message. Both using 9.10. 

For example, when I try for the fixed IP address of the DNS-123 I get a pop-up error message "Cannot display location "smb:///192.168.1.1", "Failed to retrieve share list from server"

Does anyone know what it means and how to correct it?

---

### Post by Iowan on 2009-12-16
I haven't seen a good "always works" fix for it, though there have been numerous threads.  Best information I've seen suggests a firewall problem, but several of the threads have no firewall active (on either machine).

---

### Post by some-what-Gnu-2-networks on 2009-12-16
Make sure you are trying to connect through a "Windows share" not a " public FTP"

---

### Post by ubuntu1sttimer on 2009-12-16
Yes, have been having this problem for quite some time. Had file sharing working with Dapper (6.04) Did a new install of a new version and have never got Ubuntu file sharing going again. Purchased the DNS-321 in hopes that it might make it easier but did not. All my Windows file sharing is without problems. That is why I am trying to find out what the message is trying to say. Not having file sharing working with Ubuntu greatly limits it's use. In fact, I just purchased a new Windows machine because I needed to be able to move files around. A Ubuntu application will do the work but having to move files with a USB drive just does not get things done for most jobs.

Hope someone will know what the error message means.

---

### Post by ubuntu1sttimer on 2009-12-17
Bump

---

### Post by jeremey on 2009-12-18
Hi, I am having this problem too.  I have my 9.10 desktop in one room connected by ethernet to the wireless router, and a vista laptop in another room connected wirelessly.  I can see the workgroup in my places/network, but double clicking the workgroup gives me this error.  My printer is connected to the laptop and I am trying to share that, as well as files.  I've been playing with it here and there, so if I get something to work I'll let you know!

Jeremey

---

### Post by WSDsmurf on 2009-12-28
I'm having the same/similiar problem... but get this:

I have Ubuntu 9.10 on both a desktop (cat5 connection) and laptop (wifi) to netcomm router.... works fine.

Now moved house, the laptop is now on the cat5 wired connection, the desktop is on the wifi - but the desktop can no longer access the shared folders on the laptop (!!!), with the 'failed to retrieve share list blah blah error message - but it could before. I'm stumped.

---

### Post by ubuntu1sttimer on 2009-12-28
Yes, it just seems that Ubuntu has a problem with sharing files. The interesting problem is that there does not seem to be anyone that can tell us what the error message "Failed to retrieve share list from server" specifically means and what can cause it. There are ideas on how to fix it but not what causes it to be generated. The ideas I have tried have not worked.

I did install NetworkManager in an effort to resolve the problem. Now can see shared directories and drives on the network. But, don't get too excited if you have network printers. I lost all my networked printers. You gain and you loose. 

"I started with a fresh install of 9.04 and upgraded to 9.10. Tthe upgrade hassss caaused aanotherr problem. As you caaan see, 9.10 resets the key repeat speed so there are lots of extra letters shown." (errors between "" marks are uncorrected.)

There seems to be a number of problems with the 9.10 upgrade that have not been addressed.

Oh well, maybe waiting for an new install of 10.4 LTS may solve some of it. In the mean time I am spending alot more time using Vista & 7.

---

### Post by Morbius1 on 2009-12-28
I'm shooting from the hip here but you might try the following. You can always undo it if it doesn't work.

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add to the [global] section the following two lines:
```
client lanman auth = Yes 
lanman auth = Yes 
```Save the file and exit gedit

Back in the terminal type **sudo service samba restart**

Wait a few minutes, and see if you can access the NAS

---

### Post by duncan.rack on 2010-01-11
adding the following lines in the globals section helped
[B]
client lanman auth = Yes
lanman auth = Yes
[/B]
Thanks guys, problem resolved

---

### Post by Iowan on 2010-01-11
> **duncan.rack said:**
> Thanks guys, problem resolvedCongrats - guess I get to throw in this [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") link!

I'm gonna need to remember the **lanman** "trick" - there are a lot of "Failed to retrieve..." threads around.

---

### Post by Baneblade on 2010-02-27
adding those to the global section and restarting samba service hasnt fixed my failed to retrieve message. Anyone else got any other ideas?

---

### Post by aneganov on 2010-03-02
I can't browse windows network at all:
[http://ubuntuforums.org/showthread.php?t=1419660](http://ubuntuforums.org/showthread.php?t=1419660)

Having my Ubuntu laptop and Windows XP SP2 PC in wireless network.

lanman trick didn't help

---

### Post by ubuntu1sttimer on 2010-03-02
I finally got mine going by entering in terminal:

sudo gufw Samba ALLOW anywhere

It then showed up in my firewall rules and Samba works.

I had made some common changes to smb.conf. I had worked on this for some time so not sure just what else I did but the firewall was the last and it worked.

---

### Post by swedski on 2010-04-21
I am having the same problem suddenly after upgrading the firmware on my D-Link DIR 655 router to 131eu.

My network
DIR 655 router (Configuration saved pre-upgrade and re-installed after upgrade)
Netwrok media tank
Sony Vaio Laptop Ubuntu 9.10 (Dual Boot Windows 7)
AMD 5000 Desktop Ubuntu
AMD 5000 XP (Shut off)

When I upgraded my router last night I suddenly could not see my network shares or my network printer.  I recieved that same error "Failed to retrieve share list from server" from both my Ubuntu machines.  I ALWAYS had access to these shares otherwise, the past 3 month with 9.10 and previously from the summer on 9.04.  The XP machine was not turned on.

I have samba installed on both machines and will try the restart when I get home today, but this is a strange problem

---

### Post by ubuntu1sttimer on 2010-04-21
Not an expert on this but the message seems to mean that the machines are not talking to each other. In my case it was the firewall on the Linux machines. Had to tell the firewalls that Samba ports are ok to use.

If you have a "null modem" network cable you could connect two your machines together and see if they talk. On second thought, that might not work for you. My system is static ip. Anyway, from your message it sounds like the only thing you changed is the router so that might be the place to start.

---

### Post by vahnx on 2010-08-26
Adding the two lines then doing a "sudo /etc/rd.d/samba restart" in arch linux worked for me. So how long until those two lines are included by default with samba? Linux is so behind the world when it comes to technology...

---

### Post by Morbius1 on 2010-08-26
> **vahnx said:**
> Adding the two lines then doing a "sudo /etc/rd.d/samba restart" in arch linux worked for me. So how long until those two lines are included by default with samba? [COLOR=Blue]Linux is so behind the world when it comes to technology.[/COLOR]..
Actually you have that the other way around. "lanman" was in the default back when people were playing with the hobbyist OS from microsoft but was removed when when folks migrated to WinNT, Win2K, WinXP, ....

From samba.org:
> This parameter determines whether or not smbclient and other samba client tools will attempt to authenticate itself to servers using the weaker LANMAN password hash. If disabled, only server which support NT password hashes (e.g. Windows NT/2000, Samba, etc... but not Windows 95/98 will be able to be connected from the Samba client.So unless you have Win95, Win98, Whatever Millennium was, or Xandros it's of no use to you. The only reason it worked in this particular case is because the DNS-123 nas is using such an old version of samba.

---

### Post by dagreen0415 on 2010-08-27
Using  Ubuntu 9.1
Message: **Unable to mount location** .....** failed to retrieve share list from serve**r

I can see all shared files on my Ubuntu 9.1 Desktop machine from my Windows Vista Laptop.

I can see the Windows Vista Laptop but no shared files on it from the Ubuntu Desktop.

Help!
Don .....

---

### Post by Charles07 on 2010-10-17
Thanks!

Either this or installing winbind did the trick.

In any event, thanks again.  This community is the best.  Ever. :KS

---

### Post by brad1138 on 2010-10-21
I had tried the ideas on here, but it didn't work, then I opened SPM and noticed "Samba" wasn't even installed. Installed it and all is good.

Why would that not be installed by default?

---

### Post by Krondaj on 2011-05-01
Not sure if my problem is the same.

But i have set up an external hard drive on my ubuntu computer, I set samba (via gui) to share the folders i created.

My mac can see them fine.  but my other ubuntu laptop comes up with the spurious message"Failed to retrieve share list from server"

is this the same as other posters here have reported?  It seems they are talking about windows connectivity issues.  My whole network are two ubuntu computers (soon to be three), and one mac.  Why can the mac and the ubuntu server see each other fine.  whereas my ubuntu laptop can only see my mac laptop.  the ubuntu server cannot see the ubuntu laptop.


HELP!!!!!!!!!!!!!!!

K

---

### Post by pmohankumar on 2011-06-20
[B]Hi,
Where you post this command,
client lanman auth = Yes
lanman auth = Yes

Could you post your smb.conf flie?



[/B]

---

### Post by nerdy_kid on 2011-06-20
make sure your firewall is disabled -- sudo ufw status to see.

---

