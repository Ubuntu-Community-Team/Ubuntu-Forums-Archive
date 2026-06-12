---
title: "How to File Share in Ubuntu 10.04 Easily and using GUI's only"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by WolfRage on 2010-06-05
[COLOR=blue]**How to File Share in Ubuntu 10.04 Easily and using GUI's only.**[/COLOR]
 
[COLOR=red]Disclaimer: Sharing files in this way is not secure; so please make sure you only do this on a private network that has been properly secured. Otherwise any user on the network can access and modify your shared files; you have been warned![/COLOR]
 
**1.** "Applications" menu ->"Ubuntu Software Center" -> in the search box type "Samba" then install "Samba". (Because even though you enabled file share and tried to share the files 10.04 seems to not actually install "Samba". Plus this installs the "Samba" GUI.)
**2. This step was removed to prevent confusion.**
**3.** "System" menu -> "Administration" -> "Samba". Enter your password. In the GUI that opens up choose "Preferences" menu -> "Server Settings" then the "Security" tab change the authentication mode to share and the guest account to your user name account. This prevents permission problems later on.
**4.** Choose the "Add a Samba Share"; the green plus icon; browse to the directory you wish to share. Place a check mark in "Writable" and "Visible". Then on the "Access" tab choose "Allow access to everyone". 
**5.** Press OK; now your should be able to see the share from the other computers just choose "Places" menu -> "Network" then either the computer name if it shows up or select "Windows Network" -> "WORKGROUP" -> Computer Name then the Shared folder.
 
> 
**2.** Share the selected folder via natuilus, right-click on the folder and choose "Sharing Options" or "Properties" -> "Sharing" Tab. This may be an unnecessary step but at least we know Nautilus has applied the proper permissions for us; on the pop-up choose "Automatically Update Permissions".
I hope that this helps as many of you as possible. If anyone has any updates please let me know. I am glad to see that this can finally be done all using GUI's now but it still should be as simple as sharing the folder with the "Sharing Options" selection in Nautilus. There is still work to be done on this in Ubuntu.
I am going to jump on Launch Pad and look for all of the bugs that I can find related to these issues and see if I can contribute what I have learned and maybe I can try to organize some of the bugs to get a collective fix in the works. I will post back any updates.
**Please If you used my method please note this is not the way it is supposed to be done in 10.04 so you are affected by the bug. Please go to this bug and be counted.** [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

---

### Post by Paddy Landau on 2010-06-05
This didn't work for me, until I made a certain change to the Samba file in *all* of the computers.

If you have the same problem as I did, try the following.

[LIST=1]
[*]Edit the Samba file. The easiest way is to press Alt-F2 and enter [FONT=Courier New]gksu gedit /etc/samba/smb.conf[/FONT]
[*]Scroll down to where you see the [FONT=Courier New][global][/FONT] section (probably at the end of the file).
[*]Anywhere under there, add the following two lines:
[FONT=Courier New]name resolve order = bcast host lmhosts wins
os level = 33[/FONT]
[*]Double-check that you've typed it right. Save. Reboot.
[/LIST]

---

### Post by matt-fender on 2010-06-06
I ****ing love you, i will have your babies :d:d:d:d

---

### Post by AfrikaDietmar on 2010-06-07
Hello WolfRage,

Just installed Ubuntu 10.04, and with this tutorial plus the GUI it is really great and practical to setup a sharing folder. I did it step by step and it worked.

> **5.** Press OK; now your should be able to see the share from the  other computers just choose "Places" menu -> "Network" then either  the computer name if it shows up or select "Windows Network" ->  "WORKGROUP" -> Computer Name then the Shared folder.


I edited the smb.conf file with 
sudo gedit /etc/samba/smb.conf

And inputed the name of the windows work group, it appears there.

Is there also a different way by using the GUI to set the name of the workgroup ?

> [COLOR=Red]
Disclaimer: Sharing files in this way is not secure; so please make sure  you only do this on a private network that has been properly secured.  Otherwise any user on the network can access and modify your shared  files; you have been warned![/COLOR]

1. I have a network, or in other words a simple workgroup with shared folders and I would like to make it as such, that for other users, when they want to access the shared folder, they need to input a password.

2. Then in that folder, i will have some folders that i would also like to protect or only give access to specific people with password protection, or make it accessible only to certain users. Any idea how todo this ?

---

### Post by Paddy Landau on 2010-06-07
> **AfrikaDietmar said:**
> Is there also a different way by using the GUI to set the name of the workgroup ?
System > Administration > Samba > Preferences > Server Settings > Basic > Workgroup.

---

### Post by AfrikaDietmar on 2010-06-07
Hi Paddy,

thanks! 

When usind the GUI my ubuntu was crashing a lot.

I did the following in terminal:
got myself root status with: sudo su
  	 	 	 	 	 	  [B]and then rm -r /etc/samba
[/B]thought it would remove samba and then i can reinstall it from the software centre.

Well after that i had some more problems. Function apt -get install samba wasn't working.
I then tried again installation from the software centre, there i got some error messages because it was having some issues with the missing smb.conf, but the error message suggested a fix by copying it and give the exact line i had to input in terminal.
That somehow solved the problem and i was able to instal GUI and SMB/CIF file.

I did reboot and GUI is working and i managed to make it show a folder in the windows network. 

But what is missing now is when i right click on a folder, there are no "Sharing Options"... Any idea how to make that reappear again ?

---

### Post by AfrikaDietmar on 2010-06-07
Problem got solved by re installing Nautilus.

---

### Post by Morbius1 on 2010-06-07
I don't usually comment on someone else's HowTo because I think that's just rude but in this case what your are suggesting can actually cause one method to interfere with another.

There are two completely different methods of using samba to share files and you're using both on the same target:

_**Nautilus-share**_
> **2.** Share the selected folder via natuilus, right-click on the  folder and choose "Sharing Options" or "Properties" -> "Sharing" Tab. It's share definitions are located in : **/var/lib/samba/usershares.**

_**Classic-shares**_
> **3.** "System" menu -> "Administration" -> "Samba". It's share definitions are located in: [B]/etc/samba/smb.conf

[/B]It's best to use one method or the other. Both can be used but you need to keep track of what method you're using with what share because you don't want to use both methods on the same target directory. It appears you're only using Nautilus-share to change the permissions of the target ( which is one of it's advantages over Classic-share ), but that can easy be done by using Nautilus > Right Click > Properties > Permissions.

> **3.** "System" menu -> "Administration" -> "Samba". Enter your  password. In the GUI that opens up choose "Preferences" menu ->  "Server Settings" then the "Security" tab change the authentication mode  to share and the guest account to your user name account. This prevents  permission problems later on.Share level security has been deprecated and hasn't been used since the Regan administration. There are other ways to prevent the "permissions problems" you refer to ( I'm guessing you mean the "nobody" owner for files that are sent from that remote guest ) than setting the guest to you.

> I am glad to see that this can finally be done all using GUI's now but  it still should be as simple as sharing the folder with the "Sharing  Options" selection in Nautilus. There is still work to be done on this  in Ubuntu.Ya lost me on on this one. Had you stuck with nautilus-share to the end your HowTo would have looked like this:

Open Nautilus
Right Click on a folder you own
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete files..", and "Guest Access"
Select "Create Share"
It will ask you if you want to modify permissions - you do

You just created a public share using nautilus alone.

I would urge you to remove item two. Then your post will be about Classic-share alone and that will minimize confusion. What you don't want is someone eventually using nautilus-share to create an authenticated share and using Classic-share to create a guest share on the same target.

---

### Post by Paddy Landau on 2010-06-08
> **AfrikaDietmar said:**
> I did the following in terminal:
got myself root status with: sudo su
                                 [B]and then rm -r /etc/samba
[/B]thought it would remove samba and then i can reinstall it from the software centre.
OK, some explanation is needed.

[LIST=1]
[*]You never should have to become root with [FONT=Courier New]sudo su[/FONT]. Instead just issue the command with sudo:
[FONT=Courier New] sudo rm -r /etc/samba[/FONT]
It's safer that way.
[*]When you delete a configuration directory (which is what you did), you're not uninstalling anything. You're only deleting the configuration files for that package.
[*]Synaptic keeps track of all installed packages *and their dependencies*, so *always install and uninstall using Synaptic.* If you delete a program's directory, Synaptic won't know about it, so can't keep track of the required dependencies.
[*]The correct way to remove (uninstall) Samba or any other package is through Synaptic using any one of the following three methods.
[LIST]
[*]Ubuntu Software Manager.
[*]System > Administration > Synaptic Package Manager. If you "Mark for Removal", it removes the package; if you "Mark for Complete Removal", it both removes it and (supposedly) removes the configuration files.
[*]Remove (uninstall) Samba from the terminal (same as "Mark for Removal"):
[FONT=Courier New] sudo apt-get remove samba[/FONT]
Remove samba and its configuration files (same as "Mark for Complete Removal"):
[FONT=Courier New] sudo apt-get purge samba[/FONT]
[/LIST]
 
[/LIST]
 > **AfrikaDietmar said:**
> Well after that i had some more problems. Function apt -get install samba wasn't working.
The above explanation will let you understand why you couldn't install; Synaptic had it noted as installed (which it was -- you'd simply deleted the configuration).

As you got it working by reinstalling Nautilus, I'm guessing that Synaptic added whatever dependencies were missing. Enjoy.

---

### Post by AfrikaDietmar on 2010-06-08
@Morbius1

ok, that makes more sense to me now concerning classic and nautilus share.

@Paddy
thanks for this step by step way to handle that, that gives me a whole new perception how things are structured. 

By the way, whenever from synaptic, the installation wasn't working, there was an error message that was so kind to say which command line to apply in the terminal in order to copy the smb.conf file, it copied it from somewhere. After that it kind of worked.

It wasn't really necessary that i install Nautilus. I installed it because i found it strange that no emblem was showing on the folder when i shared it through the SAMBA GUI. So i thought something was missing. But thanks to the explanation of Morbius i have no understood that Nautilus and Samba are 2 different things. I have removed the nautlis shared option and did it with Samba GUI and added manually an emblem to the shared folder to identify it.

I recently tried to restart samba in the terminal with 
sudo /etc/init.d/samba restart
it didn't work.

I checked in synaptic file manager and it looks like its still there...
Should i completely remove the package and reinstall ?

---

### Post by Morbius1 on 2010-06-08
> I recently tried to restart samba in the terminal with 
sudo /etc/init.d/samba restart
it didn't work.
For reasons known only to our Ubuntu overlords the "samba" service that has worked so well for so long has been replaced with it's component daemons. So in 10.04 and beyond you need to issue the following two commands to reproduce what one command did before:

```
sudo service smbd restart
sudo service nmbd restart
```[COLOR=Blue]EDIT: Actually it's more complicated than that. [/COLOR]Before if the "samba service" was not running and you did a "sudo service samba restart" it would start it. But no more. 

So if smbd is not running you have to issue a :
```
 sudo service smbd start
```If smbd is running you can restart it with a:
```
sudo service smbd restart
```

---

### Post by WolfRage on 2010-06-09
@ **AfrikaDietmar -** I am sorry to hear you are having such troubles. But unfortunately when you mix terminal with the GUI you run some risk; if you are unsure what a command will do. To repair damge to a specific installation and using a GUI I found synaptic to be most helpful. If you open synaptic and search for the broken application you can right click and choose re-install; which should fix the problem.
 
@ **Morbius1 -** I appreciate your comments and insight. However I did try to follow the nautilus approach all of the way through, but it appears I am one of the many users that sharing through nautilus does not seem to actually work. Trust me I tried, yes I read the manual; the guide; and the wiki, but all to no avial. I do not blame Ubuntu it may be my exotic computer hardware that is causing the problems, but I had the same issue in 9.10. When I set up sharing in 9.10 I had the ownership issues of "nobody". 
So taking the extra step of using nautilus to set the permissions seemed logical at the time. Perhaps not needed with the setup in the Samba GUI. 
However I would like to point out that nautilus share is not actually using Samba it is using Apache; but don't take my word for it. 
[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766)

---

### Post by Paddy Landau on 2010-06-09
> **WolfRage said:**
> I do not blame Ubuntu it may be my exotic computer hardware that is causing the problems...
There does seem to be a problem with the Ubuntu method. I have four different computers that gave this problem with fresh installations of Ubuntu and Xubuntu 10.04, despite following the official instructions precisely.

The main point is that we've found the solution. :)

---

### Post by WolfRage on 2010-06-09
**@ Paddy** - Exactly; and I know I am happy that I can once again share my files!
 
**@ matt-fender** - Glad it worked for you! Thanks for the offer but my wife has already decided that she will be having my babies. 
 
**@ Morbius1 -** I removed step two from the How-To. Thanks for the help!

---

### Post by Morbius1 on 2010-06-09
> However I would like to point out that nautilus share is not actually  using Samba it is using Apache; but don't take my word for it. You're confusing Nautilus-share with "Personal File Sharing".

Personal File Sharing ( which is not Samba ) requires the following packages to be installed:
[B]Apache2.2.bin
libapache2-mod-dnssd[/B]

  Nautilus-share ( in Samba it's called usershare ) has been part of Samba for years.
[COLOR=Blue]EDIT: just to be clear[/COLOR], "Personal File Sharing" is enabled from a menu item. Nautilus-share is enabled from Nautilus-itself. In fact when you first use it it will install Samba if it's not already installed.

[COLOR=Blue]EDIT2[/COLOR]: The first attachment is Personal File Sharing, the second is Nautilus-share :

---

### Post by WolfRage on 2010-06-09
Actually that is probably the biggest problem of all. There are so many ways to share files and not a one of them is like the others. I know it is a Linux way of life to have amny ways to tackle the same problem, but for Ubuntu to provide two totally different options by default is definitely confusing.
It also seems that some ways work for some people but other ways work for others; further adding to the confusion.

---

### Post by Morbius1 on 2010-06-09
> I know it is a Linux way of life to have amny ways to tackle the same  problem, but for Ubuntu to provide two totally different options by  default is definitely confusing.On this we agree. There is very little documentation on "personal File Sharing" or Nautilus-share. There are no warnings about nautilus-share and Classic share interaction. People like me who were brought up using Classic-share don't even know that Nautilus-share is available until they start to use by accident.

---

### Post by AfrikaDietmar on 2010-06-10
OK.

So far as making the sharing work among WIN & UBUNTU with the details above, it works fine. 

But then if you want to issue user rights to folders, that is also password protect them, it gets more complicated. I even messed up my FSTAB by following one tutorial, so at the moment one PC is down. I have downloaded the new 10.04 iso file, but when i burn it on CD in windows, the CD just doesn't work on boot up... Filesystem issues ? hmm. (I actually did a cd overburn.) 

What i found out to somehow make folders have user rights and passwords you need to get ACL working, even when you install it, you need to make an entry in FSTAB, thats where i messed up.

Maybe someone can help me out ?
I followed this tutorial which is my thread here:

[http://ubuntuforums.org/showthread.php?t=1505579](http://ubuntuforums.org/showthread.php?t=1505579)

And thats my thread where I'm trying to figure out how to be able to boot ubuntu again, maybe anyone of you guys knows what todo ?

[http://ubuntuforums.org/showthread.php?t=1505320](http://ubuntuforums.org/showthread.php?t=1505320)

As you can see, i'm really new to ubuntu, but i really want to learn how things work, chatting with you guys has really teached me a lot and in addition to this, its fun to. ):P

---

### Post by Morbius1 on 2010-06-10
> What i found out to somehow make folders have user rights and passwords  you need to get ACL working, even when you install it, you need to make  an entry in FSTAB, thats where i messed up.That is incorrect. The youtube HowTo you referenced ( although technically correct ) is totally unnecessary. Samba can do this by itself.

Rather than hjack this thread any more than I have please see my post here: [http://ubuntuforums.org/showthread.php?p=9439699#post9439699](http://ubuntuforums.org/showthread.php?p=9439699#post9439699)

---

### Post by Paddy Landau on 2010-06-11
Bug filed for those who have to fiddle with /etc/smb.conf.

If it affects you, feel free to vote for it.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

---

### Post by d3v1150m471c on 2010-06-11
nice tutorial. *bookmarks page*

---

### Post by Garthhh on 2010-06-11
> **Paddy Landau said:**
> Bug filed for those who have to fiddle with /etc/smb.conf.

If it affects you, feel free to vote for it.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

Thanks for the bug report
please do vote:KS

---

### Post by Garthhh on 2010-06-15
There are also some other related threads:
Paddy Landau's thread
[http://ubuntuforums.org/showthread.php?t=1491092](http://ubuntuforums.org/showthread.php?t=1491092)
with a work around

Wolfrage's better solution:
[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

A bug [please subscribe]:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

My thread from a couple of weeks ago:
[http://ubuntuforums.org/showthread.php?t=1491180](http://ubuntuforums.org/showthread.php?t=1491180)

The community of developers has spent many hours developing this  capability, too bad it doesn't work, without a bunch of fiddling around  on the command line:confused:
If you are reading this & would like to be able to share files with a  couple of mouse clicks, post a comment on the threads & especially  the bug

---

### Post by VastOne on 2010-06-17
> **Paddy Landau said:**
> There does seem to be a problem with the Ubuntu method. I have four different computers that gave this problem with fresh installations of Ubuntu and Xubuntu 10.04, despite following the official instructions precisely.

The main point is that we've found the solution. :)

This makes me laugh and puke at the same time...

In following your thread Paddy, I have been all over the map trying to get Samba to run between two Lucid machines and I am completely disgusted with how ridiculous it just to get a simple share setup. In earlier installs, I simply right clicked in Nautilus and I was on my way. But with kernel testing and new installs.... we are where we are...

I have both smb configs exact, yet I can only see one machine in the network from each machine.  I really do not care to even go any further than that. It is setup right, it should work very very simple.

Gonna just blow away the samba and go with ssh or NFS...

I apologize for jumping into your thread and the fantastic work you have done, but as you have said in this message, this problem roars it's head on any different install, ranging form 0 issues to totally dead and it makes no sense at all....

It is just a simple network share between two machines...And I cannot tell you how angry I am right now that it is like sawing off my arm to get it to work....I think I'd rather have my arm  :confused:

To clarify, the share is there...just not showing up in the Network.  I can connect to it by go to a location in Nautilus and the old smb://xxx.xxx.xxx.xxx/share name

It just should not be this hard and I did join the bug list...End of a long day and rant, and again, please accept my apologies.

---

### Post by Garthhh on 2010-06-17
> **VastOne said:**
> This makes me laugh and puke at the same time...

In following your thread Paddy, I have been all over the map trying to get Samba to run between two Lucid machines and I am completely disgusted with how ridiculous it just to get a simple share setup. In earlier installs, I simply right clicked in Nautilus and I was on my way. But with kernel testing and new installs.... we are where we are...

I have both smb configs exact, yet I can only see one machine in the network from each machine.  I really do not care to even go any further than that. It is setup right, it should work very very simple.

Gonna just blow away the samba and go with ssh or NFS...

I apologize for jumping into your thread and the fantastic work you have done, but as you have said in this message, this problem roars it's head on any different install, ranging form 0 issues to totally dead and it makes no sense at all....

It is just a simple network share between two machines...And I cannot tell you how angry I am right now that it is like sawing off my arm to get it to work....I think I'd rather have my arm  :confused:

To clarify, the share is there...just not showing up in the Network.  I can connect to it by go to a location in Nautilus and the old smb://xxx.xxx.xxx.xxx/share name

It just should not be this hard and I did join the bug list...End of a long day and rant, and again, please accept my apologies.

there is certainly no reason to apologize
this is a situation where the squeaky wheel gets the grease
Squeeeeeeeeeeeeeeeeeeeeeeeeeeel

the whole situation reminds me of all the Bullshine I was going through with my wife's vista machine before I installed a dualboot about a month ago. [she is totally happy & asked me why we hadn't done it sooner].  fiddling around with permissions & naming, bahh I just want to be able share a few documents & pictures.
this should not be a big deal
I'll stick to emailing doc to myself & webalbums for now

---

### Post by VastOne on 2010-06-17
> **Garthhh said:**
> there is certainly no reason to apologize
this is a situation where the squeaky wheel gets the grease
Squeeeeeeeeeeeeeeeeeeeeeeeeeeel

the whole situation reminds me of all the Bullshine I was going through with my wife's vista machine before I installed a dualboot about a month ago. [she is totally happy & asked me why we hadn't done it sooner].  fiddling around with permissions & naming, bahh I just want to be able share a few documents & pictures.
this should not be a big deal
I'll stick to emailing doc to myself & webalbums for now

+1 :guitar:

I ended up setting up NFS is 5 minutes and that I knew I could do all day long...It's just that connecting an in house network drive, same credentials everywhere, should be a walk on the beach...

The only thing that really bothers me is how disparate it is to so many different users...

Maybe the great folks who develop such apps will hear these squeaky wheels and grab some WD40 and get this on a smoother track.

---

### Post by Garthhh on 2010-06-18
> **VastOne said:**
> +1 :guitar:

I ended up setting up NFS is 5 minutes and that I knew I could do all day long...It's just that connecting an in house network drive, same credentials everywhere, should be a walk on the beach...

The only thing that really bothers me is how disparate it is to so many different users...

Maybe the great folks who develop such apps will hear these squeaky wheels and grab some WD40 and get this on a smoother track.

I was doing a search to try & figure out what 
NFS means
found this 
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)
which seems to be a fair bit more complex than a right click or so

& found this thread

[http://ubuntuforums.org/showthread.php?p=9477045#post9477045](http://ubuntuforums.org/showthread.php?p=9477045#post9477045)

I added the list I posted earlier

---

### Post by N3RVE on 2010-06-20
Very informative. Thank You.

---

### Post by stinger30au on 2010-06-20
share files on your network very easy with a app called "giver"

sudo apt-get install giver

or install "giver" via the ubuntu software centre

gui driven, designed for lan use, no setup needed

magic bit of gear

---

### Post by sturmey on 2010-06-21
You failed to mention one VERY vital point. When you install Samba, you have to find "system-config-samba" which is the GUI for Samba. If you don't install this then you can't find System>Administration>Samba

Still having problems allowing access to the files and directories inside the share.

---

### Post by VastOne on 2010-06-21
> **stinger30au said:**
> share files on your network very easy with a app called "giver"

sudo apt-get install giver

or install "giver" via the ubuntu software centre

gui driven, designed for lan use, no setup needed

magic bit of gear

Hey stinger,

I used giver when it first came out and had totally forgotten about it...

Thanks for the reminder and it is a very cool app.

---

### Post by WolfRage on 2010-06-23
Please make sure you guys are posting as affected against the bug so they can see just how many are affected. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

---

### Post by dvdragon on 2010-06-24
Thank you so much. This really helped.

---

### Post by anung524 on 2010-08-21
Thank you WolfRage! :):):)

I made file sharing work from your step by step tutorial on the first post.
But instead i unchecked the "Writable" checkbox, so nobody can access and modify my shared files.

once again THANKS!! I've been trying to fix this issue for months.. :D:D:D

---

### Post by F W Adams on 2010-08-22
Well done Wolfrage, I got a file share working easily from your post #1. Also Morbius post #8 useful. But having so many ways of doing things in ubuntu, especially as default is so confusing, it creates lots of posts under google with people confusing all sorts of things. Only one method is needed, one that works, much less work overall for everyone including the delelopers. It's taken me hours to sort out, and to get a very basic framework understood.

-------------

Useful hint: if anyone want to share a hidden file it doesn't seem to possible using post #1. I just edited /etc/samba/smb.conf by copying the entry at the end and then editing it to make the new entry and it worked fine.

---

### Post by Jimmy9pints on 2010-12-22
I just had to log in to say thank you very much to the original poster, and thank you to whomever made the Samba GUI. 

I just had to change the permissions 755 in the folders I wanted to finish the job. Everything was good after that. 

By the way, I used ```
sudo chmod -R 755 /path/to/file
``` to get that to work.

I can tell you I've struggled with file sharing (whether FTP, Samba or whatever) for years. I am so glad to get a human-useable GUI finally.

---

### Post by dojida on 2011-01-08
I know this thread is solved but I just wanted to say thanks for the great, easy to follow Howto. I managed to get Vista to talk to Karmic at last.

---

### Post by LinuxUser2341 on 2011-01-08
[s]Using Ubuntu server 10.10 with Ubuntu Desktop installed.
I'm having a problem with step 3.
**3.** "System" menu -> "Administration" -> "Samba". Enter your password.

Samba asks for administrative password, I tried my password three times but I get [Failed to run system-config-samba as user root].

Any suggestions?[/s]

I got it. Just had to reset the administrative password i suppose, as I never gave it one.

sudo passwd root
 [COLOR=red]your password[/COLOR]
 [COLOR=blue]desired root-password[/COLOR]
 [COLOR=blue]retype the desired root-password[/COLOR]

---

### Post by u2nTu on 2011-01-31
This thread comes up high in the search rank and file sharing is SO much  easier in 10.10, a little help for those who come here as I did:

To access files on Windows machines from Ubuntu (10.10), just click  'Places' | 'Connect to Server', pick 'Windows share', enter the name of  the Windows machine (In XP: 'Control Panel' | 'System' | see 'Computer  Name' tab) in 'Server' and click 'Connect'.

To share Ubuntu files is even easier. Click 'Places' |   'Home', right-click the folder to be shared and pick Sharing Options, then 'Share this folder' and any options.

Hats off to the devs for making file sharing unbelievably easy.

Side note (other than semi-hijacking the thread, sorry #-o ) -- Love the  CLI, but Ubuntu has eliminated so much of the need ... why does anyone  run Windows anymore? I'm about to uninstall XP from my last laptop and  be done with Microsoft. Goodbye. ):P

---

### Post by Paddy Landau on 2011-02-01
> **u2nTu said:**
> why does anyone  run Windows anymore?
It comes with most new computers (in the UK, you can get only Windows or Mac computers; I have found no alternative). And a few programs work only on Windows.

---

### Post by Garthhh on 2011-02-01
> **Paddy Landau said:**
> It comes with most new computers (in the UK, you can get only Windows or Mac computers; I have found no alternative). And a few programs work only on Windows.

The newest version of [Virtual Box]("http://www.virtualbox.org/") is very usable 
a fully updated xp box can be built & saved as an appliance, which cuts down on the work when similar installations are needed 
For me it is some sites just don't work without IE..

---

### Post by federal_topone on 2011-02-09
thankyou for the tips... i will try first






[MY BLOG]("http://syahmei.blogspot.com")
Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by critin on 2011-06-15
Wolfrage's better solution Is the one that worked for me.  'Personal File Sharing' would not become enabled no matter which instruction I followed.  I was finally able to network two XP Professionals, an XP Home and an Ubuntu,  I now see all four comp's on each box freely with no constrictions nor passwords needed.

I thought Samba was already installed because there were a few references to some files, but when I searched, it wasn't there.  
I followed the steps exactly (except for the Nautilus) and it just works!

File sharing did not work in this newly installed ubuntu 10.4 for me.

BTW--I like Windows XP.  Vista requires too many authorizations.  This ubuntu pops up the authentication to continue and/or the 'unlock' box every few minutes even though I've disabled screensaver, and I'm looking for the 'turn off' tutorial I saw the other day.  I hope I wasn't dreaming because no one is going to mess with my files,  XP  has no 'required' restrictions, and I will enjoy ubuntu just as much someday.  I like both even though it isn't PC to admit it.

Thanks for the informative tutorial!

---

### Post by Paddy Landau on 2011-06-16
> **critin said:**
> This ubuntu pops up the authentication to continue and/or the 'unlock' box every few minutes even though I've disabled screensaver, and I'm looking for the 'turn off' tutorial I saw the other day.
I'm not sure why you are receiving that authentication box all the time. Does it pop up at random times? Try this:
System > Preferences > Screensaver > uncheck Lock screen when screensaver is active.

> **critin said:**
> I like both even though it isn't PC to admit it.There's nothing un-PC about it. If you like both, then you like both. It's an entirely personal opinion, and no one here should try to change your mind.

---

### Post by critin on 2011-06-16
Yes, the first thing I always do is uncheck the screensaver lock box.  When I'm updating the screen still locks, or when I'm reading--I've even increased the time to no avail.  lol  

Re Windows:  I like windows XP only because I know it well.  I had to reinstall a while back and the security updates and other 'strongly recommended' updates took almost 20 gigs of space.  I don't like their license policy of not being able to put MY PAID FOR OS on any mach I choose to.  I do not intend to replace it when technology leaves it behind as  MS no longer supports it.

 I'm on a mission to learn linux just as well and have it on all my machines.  I like the idea of freedom to choose and appreciate all the hard work others do. I make it a point to learn at least one new thing a day and it's surely not boring.  lol

critin

---

### Post by Paddy Landau on 2011-06-16
> **critin said:**
> I'm on a mission to learn linux just as well and have it on all my machines.
That's doable, unless you have need of a specific program that is supported only on Windows and Wine doesn't run.

> **critin said:**
> I make it a point to learn at least one new thing a day and it's surely not boring.
That's for sure!

---

### Post by Fartingbob on 2011-07-06
Ok, im hoping you guys can help me.
Installed 10.04 32bit on my fileserver which is directly connected (ethernet) to my win7x64 machine. Fresh install, updated everything and then disconnected the internet from fileserver. followed the guide here and its not working.

Windows says there is a connection but with no network access from its network and sharing center. If i try to browse network from 'my computer' i cant see ubuntu at all. Ubuntu can see "windows network" in the network menu, but when i click on it it says unable to mount connection. But it can still see its there.

I tried setting up samba on a laptop a few days ago to make sure my win7 system would see it and everything worked fine. I would browse the selected folders on the ubuntu laptop from windows. Did exactly the same thing on the fileserver and nothing.

Guesses? Not that good at linux, so if im having to go to the terminal or edit config files then be gentle.

Everything is physically hooked up right and i did exactly the same thing as i did on the laptop tester a few days ago.

---

### Post by BLTicklemonster on 2011-09-09
Every time I think Ubuntu really is ready for the real world, they issue an update that totally whacks my networking. It's like, every time I do an update, I cross my fingers and pray I have networking when it's done. 

We do photography, and we now have no way to share back and forth so we can work on stuff. 

Whoppie.

Dear Canonical, Please pay attention to what you're doing.

---

### Post by Morbius1 on 2011-09-10
It would be helpful if you described the errors you are getting or at least post the output of the following command so others can help you:
```
smbtree
```*Note: I would recommend for times like this where some form of file sharing is absolutely necessary that users download one or both of the following applications:*

**Dukto** : [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list)
**Transfer on Lan**: [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list)

Nothing fancy with these. It simply allows MachineA to push a file to MachineB. Tranfser on Lan requires java and Dukto does not. No installation ( it's simply unpacked ) or setup is required. Every machine has to have the application.

---

### Post by BLTicklemonster on 2011-09-18
```
WORKGROUP
	\\VICKI-PC       		
	\\BILL-GF6100-M754		bill-GF6100-M754 server (Samba, Ubuntu)
		\\BILL-GF6100-M754\public         	
		\\BILL-GF6100-M754\music          	
		\\BILL-GF6100-M754\print$         	Printer Drivers
		\\BILL-GF6100-M754\IPC$           	IPC Service (bill-GF6100-M754 server (Samba, Ubuntu))
MSHOME
	\\VICKI          		vicki-desktop server (Samba, Ubuntu)
		\\VICKI\public         	
		\\VICKI\photos         	
		\\VICKI\photo resume   	
		\\VICKI\link to photos 	
		\\VICKI\ye olde maps   	
		\\VICKI\prom           	
		\\VICKI\IPC$           	IPC Service (vicki-desktop server (Samba, Ubuntu))
		\\VICKI\print$         	Printer Drivers

```

Looks grand, doesn't it?

But no one can access anyone else since the upgrades.

I'll try either of those files, it'd be nice to be able to have confidence in my file sharing capabilities. (my wife's computer is about to run out of space, so she needs to be able to dump some photos soon!)

---

### Post by Morbius1 on 2011-09-18
The biggest problem is the name of BILL-GF6100-M754. It's 16 characters long. It can only be 15 characters long. You can fix that for samba purposes within samba itself:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
``` Add the following line to the [global] section right under the "workgroup" line so you can find it later:
```
netbios name = bill-M754
```Save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and try it again.

---

### Post by BLTicklemonster on 2011-09-19
> **Morbius1 said:**
> The biggest problem is the name of BILL-GF6100-M754. It's 16 characters long. It can only be 15 characters long. You can fix that for samba purposes within samba itself:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
``` Add the following line to the [global] section right under the "workgroup" line so you can find it later:
```
netbios name = bill-M754
```Save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and try it again.

How funny. Ubuntu named my computer while I was setting it up. 
One would think the folks who made Ubuntu wouldn't let something like this slide by, wouldn't one?

Thanks, I'll give it a shot.

---

### Post by BLTicklemonster on 2011-09-19
Thank you, Morbius 1, that did the trick. But why did Ubuntu share files just fine with that name when I'd just installed 11.04? Bah, who cares, I just got networking back, and I'm transferring photos again. Thank you, thank you, thank you.

---

### Post by BLTicklemonster on 2011-10-01
Correction:
I just got around to trying to hit this computer from another one, and it could not get in.

Turns out my domain had been changed from MSHOME to WORKGROUP. 

What's up with that? Why would an upgrade do that? I'd made sure we were all MSHOME when I installed 11.04 so that we were all on the same page. 

Oh well, I changed it back, and we're going great now. I don't know why I didn't see that earlier.

---

### Post by Morbius1 on 2011-10-01
What's even more odd is why it mattered. 

I have on my home lan 4 separate workgroups and I can see and access them all.

---

### Post by Garthhh on 2011-10-02
I still get tangled up with permissions on documents,anything that OO opens
I can see the files, I can open the files, I can make a copy of the files, but I can't edit or delete 
I gave up & just work as a remote desktop & email anything I need to print to myself

sharing is still an ongoing bug, that no one seems to want to fix
it should be easy & all inclusive, instead of defaulting to restrictive...

---

### Post by BLTicklemonster on 2011-10-02
Seems like every time I get everything working here, an upgrade comes along and strands all the computers.

I agree, networking should be a priority. Not "edit this file, edit that file, do this, do that. Hey, if you can do it in terminal in 42 easy steps, you can do it in a gui once. I wish I knew how to create GUIs. I played with borland years ago just enough to see how simple it was to "if you know the routine", create a program to perform all the steps for you. I wish I knew how to do that. It'd make my life a lot more simple.

---

### Post by Paddy Landau on 2011-10-02
May I suggest, whenever you hit a Samba problem, [report a bug]("https://help.ubuntu.com/community/ReportingBugs") (or, if already reported, vote for it).

Samba is a major bugbear. Admittedly it's not Linux's fault; Samba is trying to work with Windows instead of Windows trying to work with everyone, but hey it needs fixing.

---

### Post by BLTicklemonster on 2011-10-03
When I first got in to Ubuntu, I was in to reporting bugs, but honest to God, that's the most confusing mess I've ever seen. I don't see how they have any plans to make enough sense out of that place to even fix bugs, much less track progress.

---

### Post by Garthhh on 2011-10-03
> **Paddy Landau said:**
> May I suggest, whenever you hit a Samba problem, [report a bug]("https://help.ubuntu.com/community/ReportingBugs") (or, if already reported, vote for it).

Samba is a major bugbear. Admittedly it's not Linux's fault; Samba is trying to work with Windows instead of Windows trying to work with everyone, but hey it needs fixing.

Paddy, I'm only running linux machines & don't have any windows machines directly on my network, [though I do have some virtual machines]. I'd be happy if I could share between them
I'll give it all another try when the LTS comes around

I have filed bugs with samba & OO, it doesn't seem to be of much concern, I haven't tried with tried with Libre Office yet

I'm not very happy with the attitude by the powers that be, Unity is the last in a long line of unilateral decisions by Mark Shuttleworth.  It's his goat rodeo [he pays the bills] so he can do what he wants

I'm looking at 
[http://www.mageia.org/en/](http://www.mageia.org/en/)
which is a similar situation to OO/LO
the parent stopped supporting the distro cut the devs loose who went for a community based thing,
it's still early

---

### Post by Morbius1 on 2011-10-03
Given the size an complexity of Samba it's remarkable how bug free it is. 97% of the the support posts on this forum has to do with browsing the network for samba shares by name which isn't a Samba issue at all but a network issue ( name services ). It may appear to be a samba issue because samba can be used to to work around it and sometimes fix it.
> I have filed bugs with samba & OO, it doesn't seem to be of much concernDid you file the bug reports with Samba and OpenOffice or with Ubuntu. If you made it with Ubuntu the best you could have expected was for them to pass it along to Samba and OO themselves. 
>  I can see the files, I can open the files, I can make a copy of the files, but I can't edit or delete That sounds like a Linux file permissions issue not a Samba issue.
>          I still get tangled up with permissions on 
documents,anything that OO opens[COLOR=Blue]**nobrl**[/COLOR]

Did a quick search on the forum ( different problem same solution ) to show you an example of how nobrl is used: [http://ubuntuforums.org/showthread.php?t=1477983](http://ubuntuforums.org/showthread.php?t=1477983)

---

### Post by Garthhh on 2011-10-04
> **Morbius1 said:**
> Given the size an complexity of Samba it's remarkable how bug free it is. 97% of the the support posts on this forum has to do with browsing the network for samba shares by name which isn't a Samba issue at all but a network issue ( name services ). It may appear to be a samba issue because samba can be used to to work around it and sometimes fix it.
Did you file the bug reports with Samba and OpenOffice or with Ubuntu. If you made it with Ubuntu the best you could have expected was for them to pass it along to Samba and OO themselves. 
That sounds like a Linux file permissions issue not a Samba issue.
[COLOR=Blue]**nobrl**[/COLOR]

Did a quick search on the forum ( different problem same solution ) to show you an example of how nobrl is used: [http://ubuntuforums.org/showthread.php?t=1477983](http://ubuntuforums.org/showthread.php?t=1477983)

I filed a bug with OO, not sure about samba, it's been a year or so

I can open a copy of whatever document, but that sort of defeats one of my primary goals for shares, which is to be able to do some housekeeping on the other computers on my network & not having multiple versions of the same document scattered about


the fix looks doable, but certainly takes us beyond the premise of this thread [using GUI's only]
which gets us into won the battle, but lost the war territory
the war being shares that work in furtherance of a nice open source OS that is user friendly

The buck stops with the OS, which should tie all the loose ends up to form a cohesive package
I find it odd that what amounts to a beta is the default choice for download on the Ubun home page
it should be the LTS
little things do matter when it comes to marketing...

Sorry
<rant off>

Thanks for the solution
It's always good to leave a few breadcrumbs for anyone looking for answers...:D:D

---

### Post by BLTicklemonster on 2011-10-11
How typical. 

My wife did an update today, and when it was done it asked her to reboot.

Now I can't see her shares any more, and she can't get on the network at all. Some error about dbus or something.

Arrrrgh.

---

### Post by Garthhh on 2011-10-11
I noticed early on that many times if I saved a bookmark for a share, I would get an error when I tried to use it
going to places>network>windows network> workgroup
worked nearly everytime,
even still I occasionally have to do a restart after an error
no matter which way I try to access

---

### Post by Paddy Landau on 2011-10-13
I have just reinstalled four computers and their shares worked perfectly. All are 11.04, either Ubuntu or Lubuntu.

This is what I did:

**1.** Install Samba (of course).

**2.** Back up /etc/samba/smb.conf.

**3.** Replace /etc/samba/smb.conf with the following code. Change WORKGROUP to your workgroup name, YOURPATH to the path to the public folder (e.g. /public), and COMMENT to a suitable description (e.g. *Alice's Shares*).
```
[global]
    workgroup = **WORKGROUP**
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = **COMMENT**
    path = **YOURPATH**
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes
```**4.** Reboot all four computers.

I hope that helps.

---

### Post by Morbius1 on 2011-10-13
[1] The [global] section of the above smb.conf is the default configuration so there's no need to create a new smb.conf.

[2] If I follow your steps exactly it won't work because you are missing a step.

You created a public share at "YOURPATH" that allows write access but you didn't adjust the Linux file permissions to accommodate "other" ( corresponding to an anonymous remote user ) to write to the directory. So you will need a step 5:

**5.** Change permissions on the shared directory:
```
sudo chmod 0777 YOURPATH
```

---

### Post by Paddy Landau on 2011-10-13
@Morbius1: Thanks for adding that clarification. You are correct; that is exactly what I did!

---

### Post by capscrew on 2011-10-13
> **Morbius1 said:**
> [1] The [global] section of the above smb.conf is the default configuration so there's no need to create a new smb.conf.

[2] If I follow your steps exactly it won't work because you are missing a step.

You created a public share at "YOURPATH" that allows write access but you didn't adjust the Linux file permissions to accommodate "other" ( corresponding to an anonymous remote user ) to write to the directory. So you will need a step 5:

**5.** Change permissions on the shared directory:
```
sudo chmod 0777 YOURPATH
```

@Morbius1,

I'm not to keen on providing world write and execute permissions (777) on guest enabled shares.  The way I handle it is to create a system user (not a mortal user) named *smbguest*.  This user added to the _group_ I also created named ***smbusers***.  I also set the umask to 002 so the default permissions at creation time is 775 for directories and 664 for files.  

After changing the guest user from *nobody *to *smbguest* in the the smb.conf file, I now longer have to change file permissions on any file or directory on the system and there are no world writable files anywhere on the system.

The only place that I change file permissions is to remove group write permissions on the [homes] shares.

This is admittedly a complex notion and not for everyone.  It involves some work to set up, but once in place offers better security and less administration when setting up future shares.

Food for thought...

---

### Post by Garthhh on 2011-10-13
> **Paddy Landau said:**
> @Morbius1: Thanks for adding that clarification. You are correct; that is exactly what I did!

once again easy & GUI are out the proverbial window

---

### Post by Steve54 on 2011-10-26
Hopefully I will be able to try this out later today as I'd had no success with samba. If it works ok, how do I add multiple shared folders or can I just add the top level folder eg. /media/ to share everything below it?
 
I know the obvious answer is just to try and see what happens, unfortunately being new at this I wouldn't have a clue if it didn't work if it was as simple as a missing '/' or totally barking up the wrong tree.

---

### Post by Morbius1 on 2011-10-26
Although it's never mentioned in this HowTo you will be using a package called **system-config-samba**. That utility will allow you to browse to as many folders as you want and share them individually.

I would caution against sharing /media in it's entirety however. If this is a dual boot for example and you have not mounted the Windows OS someplace else it will mount to /media automatically when selected in Nautilus and you will then inadvertently allow access to everyone on the lan.

---

### Post by Paddy Landau on 2011-10-26
> **Steve54 said:**
> ... how do I add multiple shared folders...
> **Morbius1 said:**
> I would caution against sharing /media in it's entirety...
Morbius is correct.

You can create a new folder (I have created /public on my computers) and share that. Everything under that folder will be shared.

Be aware that when you add a file or folder there on the host computer without using the network, it is saved with the usual permissions, whereas when you save with the network, it is saved with read-write access to all.

---

### Post by Steve54 on 2011-10-26
Thanks for the replies. The machine is basically running as a large NAS, it only has Ubuntu Server 10.4 installed on a CF card. All of the HDDs are for data (media files) only. Currently the Ubuntu mount point for the various drives/folders is eg. /media/TV1, /media/TV2, /media/music, etc.
 
The current situation is that from the media server I can see and copy from my windows PC but not the other way round, I can live with this but last night I found out that my stand-alone media player couldn't access the files on the media server ("No Shared Folders Found"), so basically I need to be able to *share the data files with the media player. Although it is connected to the router I don't think the system has to be really that secure as it's only an internal home network, ideally I don't want to have to mess around with user names and passwords every time I access a shared folder (I'm not even sure if the media player has the ability to do that anyway).
 
If it's of any importance or help to what I need the system is running totally headless. I'm the only one with an account to login to Ubuntu and all other access is through either a DLNA server (PS3 mediaserver) or through the media player.
 
Thank you for your time in reading this.

---

### Post by Paddy Landau on 2011-10-26
@Steve54: I have Windows and Ubuntu, and they all connect to each other easily. The method is as described in [post 65]("http://ubuntuforums.org/showthread.php?p=11336624#post11336624") and [post 66]("http://ubuntuforums.org/showthread.php?p=11336867#post11336867"). Ensure that you have named the workgroup on all your computers (both Windows and Ubuntu) the same, and that each computer has a distinct computer name.

---

### Post by Steve54 on 2011-10-26
Ok, thank you. I will give it a try when I get home tonight.

---

### Post by Morbius1 on 2011-10-26
Based only on your descriptions in your posts this may not be a Samba problem at all.

> Currently the Ubuntu mount point for the various drives/folders is eg. /media/TV1, /media/TV2, /media/music, etc.> I found out that my stand-alone media player couldn't access the files on the media server ("No Shared Folders Found")Those 2 statements begs to have some questions answered:

[1] How are you mounting them? If you are mounting them in fstab then post it to the forum:
```
cat /etc/fstab
```[2] What are the permissions of those mounts? The following command will tell us that:
```
ls -al /media
```[3] Finally, how have you set up your shares? The following command will tell us that:
```
testparm -s
```

---

### Post by Steve54 on 2011-10-26
Here's the output of the three sections you asked for.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=e30eec19-8fe3-4ec1-a5f0-79f101a21fde /               ext2    noatime,discard,data=writeback,errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=e7dd6647-5b29-4054-8f61-9b884df301a4 /home           ext2    defaults        0       2
UUID=1d351a76-43c7-4149-af1a-761dfe15acc1  /media/Films  ext4  defaults  0  0
UUID=a55b6676-b8cc-4baf-b4e9-bff020c795ba  /media/Horror  ext4  defaults  0  0
UUID=bdb92db3-fe75-4a27-9f7a-856557ff4188  /media/TV1  ext4  defaults  0  0

tmp     /tmp            tmpfs   noexec,nosuid,rw,size=8192k   0     0

vartmp  /var/tmp        tmpfs   noexec,nosuid,rw,size=1024k   0     0

varlog  /var/log        tmpfs   noexec,nosuid,rw,size=8192k   0     0



drwxr-xr-x  9 root root 4096 2011-10-17 19:11 .
drwxr-xr-x 22 root root 4096 2011-10-17 18:28 ..
drwxr-xr-x  2 root root 4096 2011-10-17 19:10 external1
drwxr-xr-x  2 root root 4096 2011-10-17 19:11 external2
drwxrwxrwx  4 root root 4096 2011-10-16 17:41 Films
drwxrwxrwx  4 root root 4096 2011-10-17 18:34 Horror
drwxrwxrwx  4 root root 4096 2011-10-21 17:44 TV1


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Films]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Films]
    path = /media/Films

---

### Post by Morbius1 on 2011-10-26
I was wrong it is a Samba problem.

> ideally I don't want to have to mess around with user names and  passwords every time I access a shared folder (I'm not even sure if the  media player has the ability to do that anyway).Your Linux permissions on /media/Films will allow remote guest access but your share definition will not:
> [Films]
    path = /media/Films     You need to add a line to that definition to allow guest access so that it looks like this:
> [Films]
     path = /media/Films
[COLOR=Blue]**guest ok = Yes**[/COLOR]
 Then restart samba:
```
sudo service smbd restart
```Wait a few minutes because the network has a fit when you restart samba and things need to settle down and then try accessing it again.

If you still have a problem post the output of these commands:
```
hostname
smbtree
```

---

### Post by Steve54 on 2011-10-26
Thanks for your help, unfortunately it's back to the drawing board as Ubuntu has fallen over. It hasn't restarted post a reboot via vnc. Now I've got to faff around with a monitor etc to find out what's going on now.
 
I've found the problem but I don't know how to fix it so I might have to reinstall it. It's some sort of problem with mounting the filesystem, It seems to have lost my home directory.

---

### Post by Steve54 on 2011-10-27
I have managed to get sharing sorted as far as my Windows PC is concerned but the media player still reports 'No Shared Folder'

---

### Post by Morbius1 on 2011-10-27
Since I don't know how your media server works it's hard to figure out what's going on here. I did do a search on all this and found something on the WDTV Live forums - I don't know if it's applicable to you.

Given your specific media server does the following make any sense:
> I got my WDTV Live today, and wanted to report my success with setting  it up with with my NAS which has Samba shares and runs on Fedora 11. I  initially could not get the shares to be seen on the WDTV. I had set  auto login to ON when I set it up I then realised the correct order was  to Clear the login info and then login first through the network share  on the Video menu with auto login on the Network setting menu OFF. The  when you get to see the shares go back to the setting menu and turn auto  login on. This seems to have worked consistently with multiple reboots  and menu hops.
Sorry, what experience I have is limited to the normal Windows, Mac, and Linux sort of lans.

---

### Post by Steve54 on 2011-10-27
No worries I'm grateful for the help you have given me as I'm heading in the right direction now.
 
 
It was too late last night when I eventually got it up and running to play around and see what's going on. I am just confused for now as to why the Ubuntu server and the Windows PC (XP) can now read and write to one another and the media player can see both but only access the files on the Windows PC. So to my poor little mind there is still something different in the way samba presents the shares/files than Windows does natively.
 
 
 
I will have a look on the WDTV forums.
 
PS Just looked on the WDTV site and there is also a suggestion of starting/checking that nmbd is running. I have seen that elsewhere that with the newer Ubuntus restarting the samba service no longer starts nmbd. Could be worth a look.

---

### Post by disnominal on 2011-12-24
Thank you very much!
These instructions have quite helpful!!

---

### Post by BLTicklemonster on 2012-03-17
You guys rock, by the way.

---

