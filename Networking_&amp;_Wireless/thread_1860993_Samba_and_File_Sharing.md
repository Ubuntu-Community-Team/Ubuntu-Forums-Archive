---
title: "Samba and File Sharing"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by DaimyoKirby on 2011-10-15
Hi there. I believe this would be the forum for this, but I beg you pardon if it isn't.

I recently ran into some complications that require me to reinstall Xubuntu, but I have files on my computer, with nowhere to go. I want to connect my computer to my router/modem with an ethernet cable, and transfer them across my local(home) network to another computer, so I can get them later after reinstalling.

I was directed towards something called Samba, but I don't really know what it is, or how to get it started.

So basically, can someone direct me towards a very user-friendly how-to thread/site, or explain to me here how to get started?

Also, if it makes a difference, I'm currently running off a startup disk, since I don't have access to an actual installation.

---

### Post by cryptictalk on 2011-10-15
Hi,

You can try doing something like this:

    sudo apt-get install samba

(That will install both the samba server and the samba client)

Then use a command like this:

    nautilus smb://<IP Address Of Windows Machine>/c$


After that you maybe prompted for a user name and password, enter the details of an account that has Administrator rights.

PS.  nautilus is a GNOME application, I do not know the equivalent in KDE

Hope that helps! :)

---

### Post by DaimyoKirby on 2011-10-15
Ok, so I installed samba that way, and then had to install nautilus, but then when I did the command, a popup window appeared:
[IMG]http://i.imgur.com/cJmySl.png[/IMG]

What do I do now?
Do I put in my password, or the username and password for the computer I'm trying to connect with?

---

### Post by DaimyoKirby on 2011-10-15
Bump...

---

### Post by capscrew on 2011-10-15
> **DaimyoKirby said:**
> Ok, so I installed samba that way, and then had to install nautilus, but then when I did the command, a popup window appeared:
[IMG]http://i.imgur.com/cJmySl.png[/IMG]

What do I do now?
Do I put in my password, or the username and password for the computer I'm trying to connect with?

I would think you should use the user/pass of a user on the Windows machine.  Try all combinations and see what happens.

I assume you are  using a LiveCD and at the present you are logged in as the user *ubuntu* and windows has no idea who that is.  In addition you are trying to open an admin share.  Do you have another share further down the tree?

---

### Post by DaimyoKirby on 2011-10-15
I tried my laptop's name (ubuntu) and password, a logged-in account on the pc's username and password, and neither worked.
What do you mean by *another share*? Is that a folder or something that is sharing between the two computers?

Also, as a side note, I was using samba, and I managed to have the folder show up on my laptop, under network, and it also shows up my pc. The only problem is now permissions. I can drop a file into the folder (*public on ubuntu*), but I don't have the permissions to open the file in the folder, move/copy it from the folder, and my pc can't drop files into the folder or open the files.

So how would I change the permissions?

---

### Post by capscrew on 2011-10-15
> **DaimyoKirby said:**
> What do you mean by *another share*? Is that a folder or something that is sharing between the two computers?

Both Windows and Samba *share folders of files*.  The folder that you are trying to enter is the root of the file (C$) system and is for administrators only.  If you share another folder (say one in your home directory) you will have easier permissions. > 

Also, as a side note, I was using samba, and I managed to have the folder show up on my laptop, under network, and it also shows up my pc. The only problem is now permissions. I can drop a file into the folder (*public on ubuntu*), but I don't have the permissions to open the file in the folder, move/copy it from the folder, and my pc can't drop files into the folder or open the files.

So how would I change the permissions?

How did you create the share?

can you post the output from the terminal of this```
testparm -s
```

---

