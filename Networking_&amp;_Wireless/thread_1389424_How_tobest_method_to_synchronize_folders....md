---
title: "How to/best method to synchronize folders..."
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by lucasreece on 2010-01-24
Hi.. I posted the following to the Mint forums but no solutions for me yet so hopefully someone can help on the Ubuntu forums please.......


I'm relatively new to Linux so I do hope this is not a stupid question and am looking to the community for some advice.

Due to recent releases of Ubuntu/Kubuntu/Mint/Mint KDE, I'm pretty near ready to take the plunge full time into Linux on my main desktop machine. Just one thing stopping me though at the moment... folder synchronization.

I have the following setup:
1) Desktop machine running Mint KDE or Gnome hard wired to a Netgear DG834GT router.
2) Archived files stored on a dedicated partition mounted as /home/lucas/archive.
3) Laptop running Windows 7 also hard wired to the router.
4) Shared folder on the Windows 7 laptop called "Archive" on a dedicated "Data" partition.

What I would like to do is synchronize the folder specified in 2 above to the shared folder specified in 4 above.

Can anyone help me how to get started with this please?


In Windows I use SyncBackPro to synchronize folders. Is there anything similar in Linux?
Many thanks.

---

### Post by John Bean on 2010-01-24
I use rsync. There's a nice friendly GUI frontend for it called Grsync in the repositories.

---

### Post by ubername on 2010-01-24
Do you want two separate archives?

Why not just point ubuntu at your windows archive?

---

### Post by lucasreece on 2010-01-24
Yes 2 separate archives. I want to synchronize the folder on my Linux box with a folder on the Windows laptop.

How can I use GRsync to do this. I've looked at it recently but how do I get access to the windows box from within Linux?

Thanks.

---

### Post by n45w73 on 2010-01-24
I use Toucan available on all platform and on stand alone USB key !   works great.

of course u have to have public folder on ur machines on ur network :-)




> **lucasreece said:**
> Yes 2 separate archives. I want to synchronize the folder on my Linux box with a folder on the Windows laptop.

How can I use GRsync to do this. I've looked at it recently but how do I get access to the windows box from within Linux?

Thanks.

---

### Post by brucewagner on 2010-01-26
I'm planning to do something very similar.  

I want my local "Home" folder to synch to my "Ubuntu One" folder automatically. 

Are there any special issues using Grsynch to synch a folder with a folder inside the "Ubuntu One" folder?

---

### Post by brucewagner on 2010-01-26
Actually,  I should revise my question. 

After more research, I'm thinking of using DropBox instead of Ubuntu One ( more stable, more mature, more features, all three platforms )....

Are there any issues with using rsynch / grsynch with DropBox.....  to synch my Home folder on Ubuntu Mint 8 with a folder inside my DropBox called "Home"...?

(......which, I believe, should be the Default for ALL Ubuntu installations.)

---

### Post by duruttye on 2010-03-05
Hey!

Any news on this?

It would be great to have a REAL TIME synchronization between my folder and the Dropbox folder. I use Conduit now, but I always have to resolve conflicts, and synchronize folders, it doesn't do it automatically.

---

### Post by brucewagner on 2010-03-05
It's simple. 

Put all your folders and your documents and everything INSIDE of the DropBox folder. 

Everything is automatically synchronized immediately.  Slick!

In fact, I store EVERYTHING inside of the Public folder,inside of the DropBox folder.  This way EVERY file and document I have... has its own URL in case I want to share it with a friend. Cool!  :)

---

### Post by tg3793 on 2011-03-08
The problem that I've had with dropbox is a Linux only problem. I have a symlink in my dropbox that points to a very large external hard drive. For the sake of organization I need that symlink there but I do NOT want all of that data from my 500 gig external drive to be uploaded to dropbox.

Dropbox in this case is 'too' efficient. It follows the symlink and wants to recursively backup many many gigs there. I didn't have that problem when I was using Windows only. Dropbox doesn't follow Windows shortcuts :-)

---

