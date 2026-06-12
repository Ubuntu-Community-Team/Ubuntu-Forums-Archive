---
title: "why can't I attach / find my network drive NAS from firefox etc"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by mral4000 on 2010-02-09
Ive been having this issue for ages
annoys me a lot!

It's completely inconsistent; sometimes I am able to locate the network drive - other times not!  Its definately online and connected and can be seen by evolution mail for example.

all im trying to do is download a file and select the save location as a folder within the network drive.  where does it go to and why can't I just browse to it like on ermmm Win***s?  I used to have this problem continuously when using webmail.

It also appears that linux doesnt remember things too well - this other operating system i used to use would remember where Id saved something so in scenarios where Im downloading multiple .pdfs for example - I wouldnt have to repeatedly navigate to the same folder.....

---

### Post by ugm6hr on 2010-02-09
It should remember drive locations.

If not, it is generally because the drive isn't currently "mounted" - this is perhaps why your drives keep disappearing.

What type of NAS / file system / network etc do you sue?  It would be helpful to have more detail regarding your setup to try and help.

---

### Post by mral4000 on 2010-02-09
hey ugm6hr

its just a small WD Netcenter

gotta be honest - I've still got a lot to learn on Linux.  does it need to be permanently mounted?  Should it not just show it up once it's plugged it it?  Is there a way of forcing it to remember it?

i assume its formatted as NTFS still.  Its plugged into a netgear switch which in turn goes intot he little 4 port wifi router that the net co sent.

cheers

---

### Post by ugm6hr on 2010-02-10
I use XFCE rather than Gnome now, so can't remember exactly how Nautilus (Gnome File Manager) manages network drives.

If you want to ensure you have control over them, try installing Gigolo:
```
sudo apt-get install gigolo
```

It's pretty self-explanatory, and allows absolute control over SMB (i.e. Windows shares) netowrk drives, which I suspect yours is.

---

### Post by mral4000 on 2010-02-11
heyup - yerr this sounds like some good info!  I'll give it a bash - so what's the deal then - u type the code into the synaptic package manager and it grabs it and you mark it for DL?
im such a linux novice :)

---

