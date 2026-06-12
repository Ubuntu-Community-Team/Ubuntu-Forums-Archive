---
title: "failed to mount windows server"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by mastergoomba on 2010-03-21
i'm trying to connect to the other computers on the network in my house, but, when i try to view the main file folders it tells me "unable to mount location: failed to mount windows share" i've looked everywhere i can think of and have done everything they've told me to do, and i still can't get it to work. what am i doing wrong??

---

### Post by km0r3 on 2010-03-21
> **mastergoomba said:**
> i'm trying to connect to the other computers on the network in my house, but, when i try to view the main file folders it tells me "unable to mount location: failed to mount windows share" i've looked everywhere i can think of and have done everything they've told me to do, and i still can't get it to work. what am i doing wrong??

Do you have Samba installed?

*Where exactly* have you looked?

Try using Nautilus, the standard GNOME File Manager. Browse the other Windows Share computer by typing smb://<Ip_address> in the search bar, where <Ip_address> is a valid IP Address, of course.

[RIGHT][SIZE=5]Be more descriptive.[/SIZE]

Read your own message yourself from a 3rd person view, and then ask yourself if he really described his problem in a manner that he can be effectively helped.
[/RIGHT]


**Questions?** Ask.

---

### Post by johnson.d on 2010-03-22
You can try mounting the windows server through command line, which may be helpful in troubleshooting further as gives the more accurate error output. You can use the following command to mount the Windows share:

$ sudo mount -t cifs //<ip-address>/<share> /<mount-point> -o user=<user-id>

---

### Post by dmizer on 2010-03-22
This is most likely a firewall problem. See the 6th link in my sig for more possible solutions.

---

### Post by mastergoomba on 2010-03-24
km0r3- basically what i've done is just input the error message into google and followed what looked relevent. i do have samba installed, but, the other computers in the house are running windows 7 and i ubunto 9.10.

Johnson- i tried using the command line and all it gave me was information on mounting.

dmizer- it's not a firewall thing, i don't have one installed. the other computers see me and pull stuff out of folders i've set to share. and i can see the other computers on mine, i just can't mount the drive in order to explore and copy stuff like music onto my hard drive. i tried using your networking stuff and it's messed up my computer, i have to reinstall ubuntu.

---

### Post by dmizer on 2010-03-24
> **mastergoomba said:**
> i tried using your networking stuff and it's messed up my computer, i have to reinstall ubuntu.

You shouldn't have to reinstall after making changes. If it's really that bad, then you could use a live CD to undo the changes you made.

---

### Post by mastergoomba on 2010-03-24
so, i think i spoke to soon... i went into the package manager and checked out the firewall packages and saw ufw installed. is it safe to uninstall that??

---

### Post by dmizer on 2010-03-24
> **mastergoomba said:**
> so, i think i spoke to soon... i went into the package manager and checked out the firewall packages and saw ufw installed. is it safe to uninstall that??

Well, you can but usually it's not necessary and certainly not recommended. All you have to do is make sure it's disabled. You can run this command to be sure:
```
sudo ufw disable
```

---

### Post by mastergoomba on 2010-03-27
okay, it's disabled. but, when i go to drop files onto my computer from one of the windows machines it says destination folder access denied.... any insight?

---

### Post by mastergoomba on 2010-03-29
??

---

### Post by dmizer on 2010-03-29
> **mastergoomba said:**
> okay, it's disabled. but, when i go to drop files onto my computer from one of the windows machines it says destination folder access denied.... any insight?

This is the opposite of the problem you describe in the first post. Are you able to access the Windows machines from Ubuntu now that the firewall is disabled? If so, then this problem is resolved, and you should open a new thread to help you solve the problem of being able to access Ubuntu from Windows.

---

### Post by mastergoomba on 2010-04-05
nope, i can't access anything from either machine.

---

### Post by dmizer on 2010-04-05
> **mastergoomba said:**
> nope, i can't access anything from either machine.
I believe I have misunderstood then. Earlier you said this:

> **mastergoomba said:**
> the other computers see me and pull stuff out of folders i've set to share.
So I assumed that there was no problem with Windows seeing Ubuntu, and that the problem was only with Ubuntu accessing Windows.

If you follow everything in the 6th link of my sig, you should be able to access Windows. Earlier you indicated that these changes prevented your computer from booting. I have had other people report this as well, and the problem is usually related to WINS. Try all of the edits I suggest with the exception of installing winbind.

---

