---
title: "Samba network share mounting"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by Mooseknuckle on 2010-10-08
Hello.   I have 2 Ubuntu machines: a desktop in my bedroom, and a laptop.

I have my music shared on my desktop machine, and can access it through the network menu item in the nautilus manager, but I want the files from the share to be mounted on the disk so I can access it through the commandline.

If I right-click the shared folder in Nautilus, it says its location is smb://rob/music

If I do:

mount -t smbfs //rob/music /mnt/music, it tells me that it cant locate rob.

So I try "ping rob" and that doesn't work.

I can't make a hosts entry for rob which happens at this moment to be 192.168.0.8, because my router assigns different IP addresses to various machines at different times, and I cant seem to find a way to make static maps from MAC address to ip address.

So, how come nautilus can see my samba share on the machine "rob", but the mount commands cannot?

Thanks for any help!

---

### Post by luvshines on 2010-10-08
Maybe you can try 
```
mount -t cifs //rob/<share> <mount-path> -vvv
```
to see what is going being the scenes.

Though I am sure there are network settings available for IP switching cases. I can't recall it now, OOM(out of memory) :D

---

### Post by Mooseknuckle on 2010-10-08
Mount cannot resolve the address for 'rob' ...

Exact error text: 

mount error: could not resolve address for rob: No address associated with hostname
No ip address specified and hostname not found


keep in mind nautilus's network tab can see these shares just fine as smb://rob/music, etc

---

### Post by Morbius1 on 2010-10-08
I'm having a hard time understanding this problem:
>  So, how come nautilus can see my samba share on the machine "rob", but the mount commands cannot?But this I can help with:
> but I want the files from the share to be mounted on the disk so I can access it through the commandline.When you connect to the share thorough Nautilus it already is mounted. It's just in a peculiar place:

> /home/your-user-name/.gvfs/music on robIt's in a hidden directory ".gvfs" and has spaces in the directory name which complicates things a bit but it is mounted. See if you can find it there.

---

### Post by capscrew on 2010-10-08
> **Mooseknuckle said:**
> Mount cannot resolve the address for 'rob' ...

Exact error text: 

mount error: could not resolve address for rob: No address associated with hostname
No ip address specified and hostname not found


keep in mind nautilus's network tab can see these shares just fine as smb://rob/music, etc

The //rob/ part is a NetBIOS name.  There is no need for static IP addresses, although it is nice to have.

What do you get with ```
sudo smbtree
```

---

### Post by Mooseknuckle on 2010-10-08
smbtree output:

WORKGROUP
	\\ROB    		rob server (Samba, Ubuntu)
		\\ROB\music          	
		\\ROB\pics           	
		\\ROB\video          	
		\\ROB\IPC$           	IPC Service (rob server (Samba, Ubuntu))
		\\ROB\print$         	Printer Drivers
	\\AIMEE-LAPTOP   		aimee-laptop server (Samba, Ubuntu)
		\\AIMEE-LAPTOP\IPC$           	IPC Service (aimee-laptop server (Samba, Ubuntu))
		\\AIMEE-LAPTOP\print$         	Printer Drivers

---

### Post by capscrew on 2010-10-08
> **Mooseknuckle said:**
> smbtree output:

WORKGROUP
	\\ROB    		rob server (Samba, Ubuntu)
		\\ROB\music          	
		\\ROB\pics           	
		\\ROB\video          	
		\\ROB\IPC$           	IPC Service (rob server (Samba, Ubuntu))
		\\ROB\print$         	Printer Drivers
	\\AIMEE-LAPTOP   		aimee-laptop server (Samba, Ubuntu)
		\\AIMEE-LAPTOP\IPC$           	IPC Service (aimee-laptop server (Samba, Ubuntu))
		\\AIMEE-LAPTOP\print$         	Printer Drivers

I assume you are doing this from AIMEE-LAPTOP is this correct?

What is the output of this (bracket the output with [ code] [/code])```
smbclient -L rob
```

---

### Post by holiday on 2010-10-08
> **Mooseknuckle said:**
> Mount cannot resolve the address for 'rob' ...

Exact error text: 

mount error: could not resolve address for rob: No address associated with hostname
No ip address specified and hostname not found


keep in mind nautilus's network tab can see these shares just fine as smb://rob/music, etc

Have you tried substituting rob's IP address for "rob" so like:

smb://192.168.2.5/music

Using your real IP address instead of my imaginary one.

---

### Post by effn10 on 2012-10-27
Hi,
I come on this thread open for 2 years, since actually I have the same problem - and it is not solved here.
I do not know how to mount my remote drive via command lines. I tried the following code:
```
sudo mount -t smbfs smb://bthub3/usb1 /mnt/WD
```
and I get the following output:
```
Mounting cifs URL not implemented yet. Attempt to mount smb://bthub3/usb1
No ip address specified and hostname not found

```

Can somebody help?

Thanks in advance,
effn10

---

### Post by effn10 on 2012-10-27
OK, replying to myself.

By chance, I tried the easiest thing I could think of:
```
nautilus smb://bthub3/usb1
```
...and it works!
Nautilus opens a window with //bthub3/usb1 mounted.

---

### Post by wildmanne39 on 2012-10-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

