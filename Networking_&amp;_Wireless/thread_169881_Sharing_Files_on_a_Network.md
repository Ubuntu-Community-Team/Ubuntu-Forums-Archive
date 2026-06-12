---
title: "Sharing Files on a Network"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by kleenex88h on 2006-05-03
I'm having a problem sharing files on my network.  I can't access any other computers on my network.  It doesn't matter what computer I use, I just can't access the shared files.  Whenever I try I'm asked for a username and password to access the computers, but no matter what I enter I can't login.  I have 3 computers on the network (win98 wired, win2k wireless, ubuntu breezy wired) using a wireless router.  I have no problem accessing the router or the internet from any of the computers, and I can access all the computers using a VNC service.  I just can't get at the files.  AARGH!  Any help would be **greatly **appreciated.

kleenex88h
Jeremy Courliss

---

### Post by Iowan on 2006-05-03
I presume the files are on the Breezy box?
Samba is running?
Usernames exist in Linux and Samba - or share set for **guest OK = yes**?

---

### Post by kleenex88h on 2006-05-03
[QUOTE=Iowan]I presume the files are on the Breezy box?
Samba is running?
Usernames exist in Linux and Samba - or share set for **guest OK = yes**?[/QUOTE]

Files are all over the place, basically some on every computer, but I'm using the Breezy box all the time now so I'm more concerned with accessing/transfering the files from the windows boxes.

Yes Samba is running (it automatically installed when I set up the shared folder).

I only have one username on each computer - can I login w/ that username or do I need to set up different ones?

I'm not sure on the **share set **stuff.  I don't even know where I can edit that.

BTW, I've been using ubuntu for about a week now, so I don't quite know all the inner workings yet.  Learning something new every day.

Thanks,
kleenex88h
Jeremy Courliss - Proud linux user for one week and counting!

---

### Post by Iowan on 2006-05-03
Are the Windows boxes set up to share files/directories? Even without logging onto my "network" from my w98 machine, I was able to set up a shared directory and view it from this Breezy box.  I didn't try putting a file into the directory to see if I could open it from Breezy, though.

---

### Post by CameronCalver on 2006-05-04
Hey kleenex88h i have no idea even where to start i have to ubuntu computers one of them is the internet box and the other one i wanna share internet how do i even do that i have a ethenet card in both and a blue cable going to a hub lol what do i do next can you give me a easy step to step

---

### Post by kleenex88h on 2006-05-04
[QUOTE=Iowan]Are the Windows boxes set up to share files/directories? [/QUOTE]

Yes, they are set up to share.  I actually kind of got the sharing to work.  I disabled the shared folder on the Breezy box and it stopped asking me for a login for the network, so I can now access the files on the windows boxes.  However, this means I can't share the files on the Breezy box.  Not a huge deal, but It would sure be easier to share files on a network than to use a USB drive.

thanks,
kleenex88h
Jeremy Courliss - **not** a Linux wiz  :rolleyes:

---

### Post by Iowan on 2006-05-05
Sharing from Breezy -> Windows will (probably) require having a Samba Server on the Breezy box.  You said Samba is running - is it the server or the client (smb or smbclient)?  If the server, you'll probably need to edit the /etc/smb.conf file.  There is information buried in [here]("http://www.howtoforge.com/samba_setup_ubuntu_5.10"), but it's kinda overkill for your application.

---

### Post by dschulz on 2006-05-05
try installing openssh-server package. then in nautilus you can just login in the remote box by entering "scp://user@remotebox" in nautilus or "fish://user@remotebox" in konqueror...

---

### Post by CameronCalver on 2006-05-05
Hey i wanna make a shared folder how do i start i have that open ssh thing so i go on to nautilus then what

---

