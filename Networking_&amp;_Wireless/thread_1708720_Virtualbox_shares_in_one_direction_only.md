---
title: "Virtualbox shares in one direction only?"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by zeezee22 on 2011-03-17
Hi.

I have been pouring over pages from some days over this one and come to my end.

I have Meekat Guest, Xp host on Virtualbox; set up for folder share on virtual networking.

Xp can see Linux shared folder, can withdraw to itself, yet cannot deposit to shared folder; error received "Disk write protected or in use"

Linux access to 'workgroup' - xp machine is seen yet when clicked on returns the error of

"Unable to mount location - failed to obtain share list from server"

smb call from Host returns "Connection to STENCILCUP failed (Error NT_STATUS_UNSUCCESSFUL"

Does anyone have an idea of what I can do next?

Thx in advance,

Zz22

---

### Post by dmizer on 2011-03-17
Why not just use the Virtualbox built in file sharing capability instead of having to mess with samba?

You'll have to add the guest additions, but that's easy enough. Then just use the Virtualbox manager to select the folder you want to share.

---

### Post by zeezee22 on 2011-03-17
Thanx for the guidance. 

What I did was to delete the shared folder in Samba and registered the folder with VBox (while guest was closed). Opened guest>network connections>folders still there (including shared guest to host) yet when I click on host folder it asks me for a username and pass, to which none of my ubuntu combinations fit. Is there somewhere I can set this up? 

Also, how does ubuntu access the shared folder via Vbox? To my logic; Xp runs in Vbox; Vbox manages shared folder; all well and good. Yet do I fish inside Vbox to access XP->Ubuntu shares? When I was there, I didn't notice where that event would take place.

zZ22

---

### Post by dmizer on 2011-03-17
Are you trying to share a Windows folder, or a Maverick directory? If you are trying to share a Windows folder, then you should look closely at the Windows folder permissions. Also, due to size limits, overhead, speed, and general disk wear and tear, I recomend against sharing files from a virtual guest. Your Windows host has direct access to the hard drive, so you should keep shared files there.

Once the guest tools are installed, you can mount the shared directory like so (where "share" is the name of the share in VirtualBox shared folders list, and /mount/point is an empty directory on your Maverick box):
```
mount -t vboxsf share /mount/point
```

Also, make sure that the shared directory access is marked as "full" if you need it to be writeable.

---

### Post by zeezee22 on 2011-03-18
Yea, I hear you on guest to host shares; basically the reason I am doing this is that I'm looking for a solution to my Photoshop and Illustrator dependency and, this working with VBox has been my latest attempt.

I've pretty much had my hands removed since moving over to Linux as far as artwork goes and, lumbering thru gimp and Inkscape is going to take me a long time (that I haven't got), to master them to the level that I have got to with these Adobe products. I'm totally disinterested in putting Xp online, where many of my images will end up (via email/gallery) - it's the performance of MS online that really brings out the worst in OS's and has firmly convinced me to keep MS a good arms reach from the important things in my cyberlife.

My only other remedy to this desire is to start looking for decent tutorials on the Linux equivalents and, as time is passing on this Adobe exercise without a solution, I am starting to consider beginning to my training anyway, despite the fact that initial explorations of these programs show that they are not quite up to the tasks that I have in mind.

Hmmm....

---

### Post by zeezee22 on 2011-03-18
Oh, and to answer your questions; I am looking to bring a file or image off the net (Meerkat), transfer it  via VBox (Xp), work it (adobe), transfer it back (Meerkat) and send it out.

Since I made the full-blooded switch from MS about 2 weeks ago, I have followed online tuts for manual install of CS5 in Meerkat (no avail), running portable versions of CS3 (for only CS3 versions appear to work, except for PS and IL) and now I'm scratching for a solution via VBox.

I'm not adverse to doing file transfers via USB and, altho my technical skills in linux are growing everyday, I still haven't got so far as having Windoze recognizing the USB ports, yet, tho' I realize I may have to get to that bridge, seeing as I do use wide format printing equipment in a large part of my process.

I'll do what you suggest and let you know how it goes. Any other suggestions are welcome.

Many thanx,

Zz22

---

### Post by zeezee22 on 2011-03-18
I did the command you suggest and the reply is:

mount: only root can do that

I suspect there is something missing in my approach?

---

### Post by dmizer on 2011-03-19
Humm, I think I need to clarify something.

> **zeezee22 said:**
> I have Meekat Guest, Xp host on Virtualbox; set up for folder share on virtual networking.
This indicates that the primary OS on your computer is Windows, and that Maverick is only running in VirtualBox.

> **zeezee22 said:**
> Oh, and to answer your questions; I am looking to bring a file or image off the net (Meerkat), transfer it  via VBox (Xp), work it (adobe), transfer it back (Meerkat) and send it out.

But this sounds like you have it the other way around, with Ubuntu as your primary OS and Windows running in VirtualBox.

Could you please clarify this? Then I can offer some more options.

---

### Post by zeezee22 on 2011-03-20
Big whoops! Yes, my bad - I'm Ubuntu at heart, Windoze is guest.

I was on windows yesterday and adobe phoned home for an update. A laughed to myself thinking "well, you can try...!" and, to my total surprise, it did!
I hadn't set anything up any internet; tho' for the time being I can at least email to myself.

That's not the answer I was hoping for, but it's a way out of the one-way box I was in. 

If you have further ideas on direct shares, thank you in advance.

---

### Post by dmizer on 2011-03-20
What is the path of the directory you're trying to share? Can you post the ls -la results from that directory?

---

### Post by JKyleOKC on 2011-03-20
The surprise you got with the Adobe update was because a vbox VM defaults at creation time to having a NAT network adapter, allowing it direct access to the internet but not directly to its host system. You can change this when the VM is powered off, to use a bridged adapter instead, and then it will go through the host's network connection but will have its own IP address, and can communicate with the rest of your LAN.

However the solution you are looking for is what vbox calls "Shared Folders." I'm using version 3.12, not the current version 4, so the terminology may have changed slightly, but I can click on the little folder icon at the bottom right of the vbox window to open the shared folders management dialog, and from there can define directories on the host to be shared with the guest. An alternative way to get to the same dialog is to click the "Devices" entry of the menu bar at the top of the window, and select "Shared Folders" from the pulldown.

As dmizer has said, you need to check "full" if you don't want the shared folder to be read-only, and you also need to specify that it's a permanent share if you want it to be that through any re-boots of the VM.

Running XP in a VM is an excellent way to solve your problem. I'm doing it to maintain a number of Windows programs I've written using Delphi, and to run my data recovery programs for databases that use Pervasive's Btrieve/MKDE engines...

---

### Post by zeezee22 on 2011-03-27
Thanx for your input guys. I forget if I mentioned that I've been away for a week at trade school doing exams and such (ew). That's all for now (yay).

Dmizer - I don't know how to do what you ask. Instructions?

JkyleOKC - welcome to the thread and thx for your input. I will review my Vbox settings as you suggest.

---

### Post by dmizer on 2011-03-27
> **zeezee22 said:**
> Dmizer - I don't know how to do what you ask. Instructions?

Open a terminal
Use the "cd" command to change directories like so (be sure to use the full path):
```
cd /home/dmizer/shared
```

Once you're in your shared directory, use the "ls" command to show the permissions like so:
```
ls -la
```

---

