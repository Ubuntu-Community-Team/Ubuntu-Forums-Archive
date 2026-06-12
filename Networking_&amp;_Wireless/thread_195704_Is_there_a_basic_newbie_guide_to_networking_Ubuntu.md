---
title: "Is there a basic newbie guide to networking Ubuntu?"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by LinuxAtLast on 2006-06-13
I have got two computers with Ubuntu on, one attached to my home network and one to my work network. At home I have peer to peer with three other machines, all running Win XP. At work I have my ubuntu machine attached to a network with a windows 2000 server running a domain. I have worked out that samba is the key, but whenever I start reading the posts etc about samba I am rapidly lost :( 

Can anyone point me to a really basic guide to attaching an Ubuntu machine to a network with windows computers on it so that I can share files and printers?

Cheers

---

### Post by Nikusan on 2006-06-13
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) Might be a good starting point

---

### Post by RudolfMDLT on 2006-06-13
Hi there!

You say on a domain? Never done one of those, but see if this helps:

First - make sure all the PC's are on the same Domain: System => Administration => shared folders. Share a folder, highlight it in the menu and click General windows settings. Here you change the domain to be the same as the Win2000 machine's and disable Wins server.

Then share files on all the PC's. In windows, don't use the wizard - just enable file sharing.

Then you have to add users to the Ubuntu machine so that the windows PC's can access it.
First you have to add users to the Unbuntu PC user list:
SYSTEM=>ADMINISTRATION=>USERS AND GROUPS.
Add a user for every pc that you have.


Now you need to add the users to Samba:
This is done in the terminal:

1) sudo smbpasswd -e yourname (you're user name)
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username (kitchenpc)
(the usernames of your network users)
4)Type and retype their passwords

You have to redo step 1 and 2 every terminal session - so first add all the users to the users and groups list and then do the Terminal part where you only have to repeat steps 3 and 4 for every user added.

Now when the login pops up from the XP/2000 side you can just login and everything should work fine!

After doing all of the above, go to the terminal and type "smbtree" and see if you can see all the computers on your network.

For more, see this how to:

[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

Cheers, hope this easier to understand, any troubles, check back here and we'll see what we can do!

PS: sharing printers on the Ubuntu side, you may need to adit samba's config file, but first lets get the network up and running.

---

### Post by LinuxAtLast on 2006-06-13
[QUOTE=RudolfMDLT]
Then you have to add users to the Ubuntu machine so that the windows PC's can access it.
First you have to add users to the Unbuntu PC user list:
SYSTEM=>ADMINISTRATION=>USERS AND GROUPS.
Add a user for every pc that you have.


Now you need to add the users to Samba:
This is done in the terminal:

1) sudo smbpasswd -e yourname (you're user name)
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username (kitchenpc)
(the usernames of your network users)
4)Type and retype their passwords

You have to redo step 1 and 2 every terminal session - so first add all the users to the users and groups list and then do the Terminal part where you only have to repeat steps 3 and 4 for every user added.

[/QUOTE]

Sorry, here is where I show just how "newb" I am:

When adding a user for each pc is that making the pc a user or adding one of the users that exists on the windows pc?

In steps 1 and 2 above are these my current Unbuntu username and password or different ones. (eg my Ubuntu login is "user" and "Password", is that what I put in?)

Sorry to be dim and thanks for the help!

Cheers

---

### Post by RudolfMDLT on 2006-06-14
Sorry I'm only getting back to you now! I was writing my Mid-Year exams, my last one. It's now 1 in the morning this side of the globe so you should be getting up soon! :)

If you have 1 Ubuntu machine named ubuntu, 2 MS machines named games and family respectively. In ubuntu under SYSTEM=>ADMINISTRATION=>USERS AND GROUPS, you would add a user called games and a user called family. Then in the terminal, you add the exact same users you created, games, family.

I recently posted on how to get my ATI card to work and asked people not to just tell me to copy and paste, but explain what i am copying and pasting.

1) sudo smbpasswd -e yourname (you're user name)
This is the user name you are currently logged in as, you need to log into samba as well to gain access.
> 
rudolf@rudolf:~$ sudo smbpasswd -e rudolf
New SMB password: Although happens when you type here, just type, it is happening.
Retype new SMB password:
Enabled user rudolf.

3)sudo smbpasswd -a XP username (kitchenpc)
Over here you add the users from your Ubuntu machine's user list to the Samba list, i.e. games and family. This enables the XP users to log into samba. 
4)Type and retype their passwords

Hope this sorts you!

And don't call yourself dim! I'll link you to my first post on the forum and you'll see dim!-It was also on Samba! we're here to help! Please post back as soon as possible if you need any help at all!

Cheers!

---

### Post by Aggienator on 2006-06-15
Thanks RudolfMDLT, all becomes clear! (I'm really LinuxAtLast, but logged in at work, hence different name!). If your exam answers are as clear as this you'll get top grades :KS !

Best Wishes!

---

### Post by beameup on 2006-06-20
I've been having trouble with my wifes XP machine accessing my Linux machine, so I followed these steps. It worked but the XP machine sees my whole Home folder and I only have 1 folder shared which is /home/beameup/downloads. 
So I removed the user from users and groups but I don't know how to remove it from Samba. Or is there something else I missed? All I want is a folder to share across the network both ways. I could already see and access the Windows machines fine.
It was working but something changed a few weeks before the final release.

Edit: I found the commands by typing smbpasswd ?    It's sudo smbpasswd -d username to disable and sudo smbpasswd -x username to delete

---

### Post by sandpaperback on 2006-06-22
Thanks for the post Rudolf!  

I was having a tough time getting my Xbox to connect to the shares.  Once I figured out which usernames you were talking about (did read the entire thread... doh!) everything went great.

---

