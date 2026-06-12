---
title: "sharing folders over network not possible (KDE)"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by Screwdriver0815 on 2009-08-29
Hi folks,

I have a problem with sharing folders over the network in Kubuntu Jaunty (9.04).

Let me describe:

I have 3 Linux computers over here: 1 Laptop (Ubuntu Jaunty), 1 Desktop (Kubuntu Jaunty with KDE 4.3) and another Desktop with Ubuntu Hardy. 

Both Gnome machines (the Laptop and the Hardy-Desktop) share folders over the newtwork via Samba. I have done it in the usual way: right-click on the folder icon and set option "share this folder"...

I can access these shared folder either from each of the Gnome-machines or from the KDE-machine. No Problem at all.

The problem starts when it comes to sharing a folder on the KDE-machine. I have tried 3 ways:

1. right-click on the folder icon and set option "share..." --> this doesn't work at all

2. editing the /etc/samba/smb.conf file. I did it and after that it worked **once** but only in read-only, despite I have edited the file in this way, that I also can write in this folder. After working once, it never worked again.

3. using the samba configuration frontend kdenetwork-filesharing. When I set up a share in there, I also can see the shared folder from the other computers, but I don't get any access. I get a message (on the gnome machine) that I should type in a password and when I do it, the message comes again... and again, and again... 
Fiddling around in the configuration of the share in KDE does nothing. So it seems to me: no matter what I configure, the result is the same.

does anyone know how to get the share of folders working in KDE 4.3?

BTW: sharing a printer in KDE works fine...

thanks in advance!

Steffen

---

### Post by w00ly on 2009-08-29
I got most of samba working by editing smb.conf
The annoying thing is after setting the [homes] section I cant get home directories to moutn (permission denied). I did get the rest of the system to mount which is ok for now since most of my data is on an external drive on that system. I set the [netlogon] section like this:
> [netlogon]
   comment = Network Logon Service
   path = /
   guest ok = yes
   read only = no
   share modes = no
then mount.cifs //192.168.1.100/netlogon /mnt/htpc -o user=htpc
...now I just have to figure out how to setup credentials so I can do it automatically

---

### Post by moore.bryan on 2009-08-29
Since you're all Linux, why not just use [sshfs]("http://en.wikipedia.org/wiki/SSHFS")?

---

### Post by alphaomegaada on 2009-08-29
I am needing to know how do a new post. I cant find the icon for this. I click New Posts but see nothing for starting a new post

---

### Post by moore.bryan on 2009-08-29
Did you just hijack this thread? :-)

Got to the homepage of the forums, click on the appropriate subcategory for your question, and close to the top left of the new page you'll see *New Thread*. There you go.

---

### Post by w00ly on 2009-08-29
> **moore.bryan said:**
> Since you're all Linux, why not just use [sshfs]("http://en.wikipedia.org/wiki/SSHFS")?
cause every time I come back to linux something's different, such as "what is the best  method for sharing files over LAN" lol..
thanks for the tip though, i'll check it out...never really liked samba

---

### Post by ssri on 2009-08-29
```
sudo apt-get install samba smb4k system-config-samba 
```

Go to applications->settings (and maybe reboot?)

You'll see a nice, small samba gui program there to manage your shares in kubuntu.  So far, so good, as I'm sharing a few directories on a windows network right now.  Right click->share folder, sadly, does not work.

---

### Post by moore.bryan on 2009-08-29
> **w00ly said:**
> cause every time I come back to linux something's different, such as "what is the best  method for sharing files over LAN" lol..
thanks for the tip though, i'll check it out...never really liked samba
I can understand that... sshfs is, relatively, simply and straight-forward. I use it because samba has **never** worked for me... the only downside is the lack of access on any Windows machine I might have to use.

---

### Post by Screwdriver0815 on 2009-08-29
> **moore.bryan said:**
> Since you're all Linux, why not just use [sshfs]("http://en.wikipedia.org/wiki/SSHFS")?

because I want it this way, as described above. But maybe I try it though... Thanks for the tip!

> **ssri said:**
> ```
sudo apt-get install samba smb4k system-config-samba 
```

Go to applications->settings (and maybe reboot?)

You'll see a nice, small samba gui program there to manage your shares in kubuntu.  So far, so good, as I'm sharing a few directories on a windows network right now.  Right click->share folder, sadly, does not work.

this does not work in KDE - I already tried it. The application can not be opened. 
For this I have installed kdenetwork-filesharing, which does basically the same as system-config-samba. But it doesn't work.

---

### Post by ssri on 2009-08-29
> **Screwdriver0815 said:**
> because I want it this way, as described above. But maybe I try it though... Thanks for the tip!



this does not work in KDE - I already tried it. The application can not be opened. 
For this I have installed kdenetwork-filesharing, which does basically the same as system-config-samba. But it doesn't work.

Sorry to hear that, I'm just relating what works for my KDE setup on my laptop, which worked with Intrepid and now Jaunty.

Kubuntu Jaunty
KDE 4.3.0
QT 4.5.2

---

### Post by moore.bryan on 2009-08-29
> **Screwdriver0815 said:**
> because I want it this way, as described above.
Hey, no worries... I just wanted to give you another, possibly better, option.

---

