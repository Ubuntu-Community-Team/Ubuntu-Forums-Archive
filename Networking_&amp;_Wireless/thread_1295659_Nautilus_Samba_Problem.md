---
title: "Nautilus Samba Problem"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by szale9001 on 2009-10-19
I recently upgraded to Karmic and have stumbled across an interesting problem. The computer that shares the printers in the house (runs Windows 7) cannot be accessed by my computer. When double clicking on the computer name in the Nautilus Networking window, I get the "Failed to retrieve share list from server" error. Same if I try and connect via smb://IP. This is a problem since I can't connect to the shared printers because the SMB Browser in the printer connect dialog must be trying to connect the same way because when I click the arrow next to the computer name, nothing happens. Reason I suggest this may be a nautilus problem is because the output of smbtree can see all of the shares on that computer! More over I installed Jaunty in a VM and it can access the root and shares through Nautilus just fine. None of the existing solutions I have searched up have helped. Is anyone else experiencing this/able to offer assistance? Thanks

---

### Post by carnagex420x on 2009-10-19
I have had allot of odd issues with Win7. My Win7 box does not appear in my workgroup even with network discovery on. I also had an issue with a print server, it seemed that the print server was the local master and was using non-standard samba ports. I made my linux box the local master and set it up so it wins all the elections. I can navigate to my win7 box with smb:// but no icon is given.
I dont think this is a nautilus problem, i think you are getting the server list from the local master browser. Check your firewalls and change your local master browser. Also keep in mine there is an election that takes place and you need to wait a little bit for everything to register.

---

### Post by szale9001 on 2009-10-20
How come accessing the samba root works fine in Jaunty though? 
(Also on a side note, I have compared smb.conf files from both, they are exactly the same and the smbtree command prints out all of the correct shares in both karmic and jaunty.) 
I seem to receive this error only when attempting to access the samba root in Karmic's Nautilus.

---

### Post by carnagex420x on 2009-10-21
did u try mounting the samba share from the command line?

To view samba shares:
```
smbclient -L <host>
```

Thats the easiest way to tell if the problem is Nautilus.

---

### Post by dmizer on 2009-10-21
> **szale9001 said:**
> I get the "Failed to retrieve share list from server" error.

This error is almost always related to a firewall problem. The firewall may be interfering on either the Windows side or the Ubuntu side. Please see the 6th link in my sig.

---

### Post by szale9001 on 2009-10-22
> **carnagex420x said:**
> did u try mounting the samba share from the command line?

To view samba shares:
```
smbclient -L <host>
```

Thats the easiest way to tell if the problem is Nautilus.

Interesting, i did the smbclient -L command on karmic and my Jaunty VM. The Karmic computer threw a 'Error returning browse list: NT_STATUS_NOT_SUPPORTED' error where the Jaunty VM listed the shares fine. 

I know what you are saying dmizer, but why would it work on the Jaunty VM (the VM runs on my karmic machine) if it was a firewall issue. This is odd though, so I suppose it isn't Nautilus, what then?

---

### Post by carnagex420x on 2009-10-22
check your samba log to see who won the election. The reason you could get a list from one and not the other would be because one probably is the local master browser and has the server list, while the other is trying to receive it from the LMB and cant throwing you an error.

---

### Post by dmizer on 2009-10-22
> **szale9001 said:**
> I know what you are saying dmizer, but why would it work on the Jaunty VM (the VM runs on my karmic machine) if it was a firewall issue. This is odd though, so I suppose it isn't Nautilus, what then?

Because if you're using a bridged network connection, the Jaunty VM doesn't ever go through the Karmic firewall.

To find the cause of your problem in your Karmic machine, you should take a look at the steps in the 6th link in my sig. If none of that stuff works for you, then post back and we'll go from there.

---

### Post by szale9001 on 2009-10-23
Ok, i tried the suggestions in your sig dmizer, no go unfortunately. I have tried all of those on separate occasions. More recently after rereading the post I tried disabling ufw alltogether and rebooting, this had no effect. Also if I run sudo iptables -L with ufw *enabled*, it looks exactly like the disabled firewall output on pastebin. 

Carnage, where can I locate those logs, I found a few winbind logs in /var/log/samba but I found those to have no relevance as there was very little in them at it all pertained to winbind cache and such.

If it helps some, smbclient -L CompName produces this output

```

user@computer $: smbclient -L CompName
Enter user's password: 
Domain=[COMPNAME] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
Domain=[COMPNAME] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------


```

The computer is set with password protected sharing disabled.

---

### Post by carnagex420x on 2009-10-23
if you try to access a share on a win7 box you need a password no matter what, I tried, so you might as well turn it on. but as far as your log, in you smb.conf file change log level to 2 and this should give you info on the elections. I missed that this was on a VM on the same box, which makes me think that is your problem. I havent had good luck sharing shares on a guest VM with a bridged network to the host. I think this is because, even though the VM interface has a separate MAC it still interfaces with the host interface and possibly confilcts.
- I use VMware BTW.

---

### Post by dmizer on 2009-10-23
> **carnagex420x said:**
> if you try to access a share on a win7 box you need a password no matter what, I tried, so you might as well turn it on. but as far as your log, in you smb.conf file change log level to 2 and this should give you info on the elections. I missed that this was on a VM on the same box, which makes me think that is your problem. I havent had good luck sharing shares on a guest VM with a bridged network to the host. I think this is because, even though the VM interface has a separate MAC it still interfaces with the host interface and possibly confilcts.
- I use VMware BTW.

I just had catastrophic failure on my vmware server, otherwise I'd test this myself but, I suspect that you don't need to do this. You may be successful by adding the Ubuntu username to the Win7 server.

---

### Post by carnagex420x on 2009-10-24
If you are trying to access a share on a win7 box from Ubuntu you do need to log in. Even if password protected shares are off. But you don't have to take my word for it, just try it.

---

### Post by Aero-Z on 2009-10-24
> **carnagex420x said:**
> If you are trying to access a share on a win7 box from Ubuntu you do need to log in. Even if password protected shares are off. But you don't have to take my word for it, just try it.
Hmm, log in? Maybe I don't get something right now, but how you do it? :)

---

### Post by carnagex420x on 2009-10-24
you are prompted for credentials wen you try to access a share win7 box from ubuntu.

---

### Post by 3ashlar on 2009-10-31
I have the same problem.

I have 4 machines on my network - a desktop running Ubuntu 9.10, a laptop running Ubuntu 9.10, a netbook running Ubuntu 9.04 and a desktop running Windows 7 Home.

I can browse Windows 7 shares from the machine running Ubuntu 9.04 but can't from the machines running 9.10.  (I could from these machines  when they were at 9.04 before they were upgraded to 9.10).

The output from smbtree on both the 9.04 and 9.10 machines is the same and shows the shared files on Windows 7.

The output from smbclient -L <host> on 9.10 returns NT_STATUS_NOT_SUPPORTED

If, in Nautilus, I enter SMB://<win 7 host> on 9.10 I get "Failed to retrieve share list from server"  However, if I enter SMB://<win 7 host>/<shared file>/ I can access the files on the windows 7 machine from the 9.10 machines.

---

### Post by szale9001 on 2009-10-31
> **3ashlar said:**
> I have the same problem.

I have 4 machines on my network - a desktop running Ubuntu 9.10, a laptop running Ubuntu 9.10, a netbook running Ubuntu 9.04 and a desktop running Windows 7 Home.

I can browse Windows 7 shares from the machine running Ubuntu 9.04 but can't from the machines running 9.10.  (I could from these machines  when they were at 9.04 before they were upgraded to 9.10).

The output from smbtree on both the 9.04 and 9.10 machines is the same and shows the shared files on Windows 7.

The output from smbclient -L <host> on 9.10 returns NT_STATUS_NOT_SUPPORTED

If, in Nautilus, I enter SMB://<win 7 host> on 9.10 I get "Failed to retrieve share list from server"  However, if I enter SMB://<win 7 host>/<shared file>/ I can access the files on the windows 7 machine from the 9.10 machines.

Exactly, I can access if I know the share name to. While normally that would suffice, it becomes much more difficult when trying to access shared printers. Its Much easier to browse for them...
Just not sure where to go from here.  My Win7 box IS configured to have password sharing *disabled*.
It seems like a regression since Jaunty doesn't seem to have this problem. Does anyone know if this happens with Vista as well?

---

### Post by Sigma47 on 2009-11-01
I'm in a similar pickle here: running "smbclient -L host/CompName" yield (Error NT_STATUS_UNSUCCESSFUL)/(Error NT_STATUS_BAD_NETWORK_NAME), however I can access the shares using "Places>Connect to Server" I can access the shares by IP/share_name. My smbtree out doesn't recognize any of the other comps though...argghhhh!

---

### Post by zuke on 2009-11-01
Same issue, it worked fine for me till I ran the windows media player 12 streaming stuff. Now I cannot access my windows 7 box shares, tho after uninstalling the wmp crap I can at least see the box

---

### Post by carnagex420x on 2009-11-01
The most important question I can ask is which box is your local master browser? Id suggest even using Wireshark just to get a lil better idea of whats going on.

---

### Post by accipter on 2009-11-01
It appears that I have the same problem with 9.10.  I can browse a share if I know the name, but can I browse to an unknown share with Nautilus.

---

### Post by cowlip1 on 2009-11-01
> **accipter said:**
> It appears that I have the same problem with 9.10.  I can browse a share if I know the name, but can I browse to an unknown share with Nautilus.

OMG you're right, this works!  You can do this anonymously.

But whenever I try and get a listing of shares from the Windows 7 computer... "Error returning browse list: NT_STATUS_NOT_SUPPORTED"

Printing using CUPS also fails with "Session Startup Failed: NT_STATUS_LOGON_FAILURE"

Seems very pervasive!  Just upgraded to Karmic, yet everything samba-related on Jaunty and Intrepid was perfect.

---

### Post by 3ashlar on 2009-11-02
> **carnagex420x said:**
> The most important question I can ask is which box is your local master browser? Id suggest even using Wireshark just to get a lil better idea of whats going on.
 
My Master Browser is the Windows 7 machine.  This machine is always on and acts as my file server.

---

### Post by danwood76 on 2009-11-03
Ok I am having this same problem.

The only live CD I have is for 8.10 and that works with my Windows 7 machine perfecty.

So I downloaded the latest samba source and compiled it, guess what?
smbclient now works and going to smb://{WINDOWS 7 MACHINE NAME} allows me to view the shares on that machine.

So I assume this is a regreassion as to a configuration issue as the old config files still work with the newer version of samba.

---

### Post by Redsandro on 2009-11-03
I have the same after updating Xubuntu from 9.04 to 9.10. I don't know what to do because I've tried a lot.

```
sander@MCRED:~$ smbclient -L //redsandro
Enter sander's password: 
Anonymous login successful
Domain=[REDNET] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
Anonymous login successful
Domain=[REDNET] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Server               Comment
	---------            -------
	REDSANDRO            
	RUBLLTOP             

	Workgroup            Master
	---------            -------
	REDNET               REDSANDRO
sander@MCRED:~$ 

```

---

### Post by carnagex420x on 2009-11-04
So my next question is which version are you running. Its possible its a bug or just a depreciated version.

---

### Post by danwood76 on 2009-11-04
The current version of samba in Karmic is 3.4.0

I installed version 3.4.3 and browsing to smb://COMPUTERNAME works aswell as smbclient although the integration with nautilus doesnt work fully due to the different version libs. You still cannot just browse the network but it still works better than the default version IMO.

---

### Post by abraxxa on 2009-11-04
I can browse the net on my fresh 9.10 installation but also have the problem that shares can't be listed.

---

### Post by szale9001 on 2009-11-04
> **danwood76 said:**
> Ok I am having this same problem.

The only live CD I have is for 8.10 and that works with my Windows 7 machine perfecty.

So I downloaded the latest samba source and compiled it, guess what?
smbclient now works and going to smb://{WINDOWS 7 MACHINE NAME} allows me to view the shares on that machine.

So I assume this is a regreassion as to a configuration issue as the old config files still work with the newer version of samba.

Is there a ppa somewhere that can upgrade all of samba to the latest version? I just find it highly unlikely that a new version of samba will be pushed in karmic's life time. (Hope im wrong though)

---

### Post by Redsandro on 2009-11-04
Also looking to update samba. It's crazy if they wouldn't update Buntu 9.10 with the new version though. Would they cripple their software used by millions of people for 6 months? Idiots.

Can anyone tell me what fails due to lib problems if you install Samba 3.4.3?

Alternative is Gigolo, it mounts samba shares just fine even though anything else using samba doesn't work.

---

### Post by Sigma47 on 2009-11-04
I finally got my network browsing in Nautilus. You must have to reboot for a domain change to take effect. Prior to rebooting I was able to direct to pc's on my home network using smb///IP/share, but I still had the default samba workgroup and couldn't figure it out. So, I rebooted for an unrelated purpose and voila. FYI for anyone so careless and unBuntu as me.

---

### Post by Redsandro on 2009-11-04
Reboot is not a fix for Xubuntu, so I'm still interested in upgrading samba!

I guess it's probably a bad idea to use **deb [http://www.samba.org/samba/ftp/Binary_Packages/Debian](http://www.samba.org/samba/ftp/Binary_Packages/Debian) sarge samba** for this?
-edit-
Nevermind, that's old anyway!

---

### Post by lakerssuperman on 2009-11-04
I was having trouble seeing my shares.  I would look under problem #3 in this thread.  You have to uncomment a line in your smb.conf file and rearrange the ordering of that line.  Once I did that I could see all my computers and shares.

[http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba+browsing]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba+browsing")

Change this:
";   name resolve order = lmhosts host wins bcast"

To this:
"name resolve order = lmhosts wins bcast host"

And then issue:
'sudo /etc/init.d/samba restart' from a terminal

---

### Post by Redsandro on 2009-11-04
Hey thanks for pointing this out. This is a half fix.
It fixes my sharing between (x)ubuntu machines and Windows <= Vista, but for Windows 7 RTM you still need samba 3.4.3.

[SIZE="5"]If you don't have Windows 7 in your network, I suggest you try what he said! :D[/SIZE]

---

### Post by dmizer on 2009-11-06
> **Redsandro said:**
> Hey thanks for pointing this out. This is a half fix.
It fixes my sharing between (x)ubuntu machines and Windows <= Vista, but for Windows 7 RTM you still need samba 3.4.3.

[SIZE="5"]If you don't have Windows 7 in your network, I suggest you try what he said! :D[/SIZE]

Those of you having problems with Win7, please try adding the following options to your [global] stanza in /etc/samba/smb.conf:
```
domain master = no
local master = no
preferred master = no
os level = 0
```
Restart samba or reboot after making this change. See if that improves things.

Edit:
Please **ONLY** use this configuration if you are using Samba for file sharing between Ubuntu and Windows, not if you are using Samba for sharing files between Linux boxes.

---

### Post by Redsandro on 2009-11-06
Doesn't this configuration make samba fail when the Windows 7 machine is off and only Ubuntu machines are in the network? They all ignore the master election.

---

### Post by dmizer on 2009-11-06
> **Redsandro said:**
> Doesn't this configuration make samba fail when the Windows 7 machine is off and only Ubuntu machines are in the network? They all ignore the master election.

Yes, this is a potential problem with the above configuration. I will edit my post accordingly. Thank you.

---

### Post by Redsandro on 2009-11-06
Thanks. So my six computer network remains a puzzle:

1x Win 7
1x Win Vista
1x Win XP Pro
1x Ubuntu
2x Xubuntu

Most of the time two *buntu machines and the Windows 7 machine are on, but not always.

---

### Post by carnagex420x on 2009-11-07
so has this been identified as a problem with older samba versions? is upgrading samba the answer here? beside user specific configurations...

---

### Post by Redsandro on 2009-11-07
Not a problem with older versions.
And according to this:
[http://samba.org/samba/history/samba-3.4.3.html](http://samba.org/samba/history/samba-3.4.3.html)
not a problem with newer versions in conjunction with Win7 either.

> Major enhancements in Samba 3.4.3 include:

   o Fix trust relationships to windows 2008 (2008 r2) (bug #6711).
   o Fix file corruption using smbclient with NT4 server (bug #6606).
   o Fix Windows 7 share access (which defaults to NTLMv2) (bug #6680).

---

### Post by dmizer on 2009-11-07
> **Redsandro said:**
> Thanks. So my six computer network remains a puzzle:

1x Win 7
1x Win Vista
1x Win XP Pro
1x Ubuntu
2x Xubuntu

Most of the time two *buntu machines and the Windows 7 machine are on, but not always.

Use NFS to share between the Ubuntu machines, and Samba to share between the Ubuntu machines and the Windows machine. For a quick, easy NFS howto, please see the 4th link in my sig.

---

### Post by Redsandro on 2009-11-07
Thanks :)

---

### Post by arryo on 2009-11-11
I'm not sure If i'm doing correctly about compiling samba-3.4.3, I downloaded the tar file, /confige, make, and make install (like the guided from samba website). But when i check the version of smbclient, it's still saying i'm using version 3.4.0. Hence, I still have problem with smbclient - L mywin7machine

error: NT_STATUS_NOT_SUPPORTED

Could someone tell me how to fix the problem

Thank you very much

---

### Post by szale9001 on 2009-11-14
looks like the problem has been fixed in the latest batch of updates...

---

