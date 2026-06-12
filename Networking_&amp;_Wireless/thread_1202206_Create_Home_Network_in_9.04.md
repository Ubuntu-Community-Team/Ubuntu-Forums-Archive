---
title: "Create Home Network in 9.04"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by jose187 on 2009-07-02
Hi,

I have a laptop and a desktop both running Ubuntu 9.04. The desktop contains all the files i want to access through my laptop. 

The laptop is connected to the internet via wireless, and the desktop through a wired network.

I have tried to make the laptop access the desktop files, but haven't been able to do it. I've installed NFS, and then did some other things i didn't understand....

can somebody help me please...

Thanks in advance.

---

### Post by K.Y.A on 2009-07-02
Here is now it works. install nfs-kernel-server via apt on both computers.

```
sudo apt-get install nfs-kernel-server
```


Now, on the desktop, add this line of code to the file /etc/exports. To do this, run:

```
sudo gedit /etc/exports
```

and add the following code to the file, on a new line:

```
/home/USERNAME 192.168.1.1/24(rw,no_root_squash,async)

```

Change USERNAME to what your username is on the desktop.

Now, run this:
```

sudo /etc/init.d/nfs-kernel-server restart
```

Which will restart NFS.

Now, on the laptop, make a folder in your home directory called NFS.

then run this:


```
sudo mount XXX.XXX.XXX.XXX:/home/USERNAME ~/NFS
```

REPLACE XXX.XXX.XXX.XXX with the desktop's ip address and replace USERNAME with the username of the username on your desktop.

And you're done! Just navigate to the desktop folder on your laptop and you will be able to view your files on your desktop!

---

### Post by jose187 on 2009-07-02
THANK YOU!!!!!!!!

That has worked a treat!!!!

One last question. How can i unmount it?
It keeps saying i need to be root...what can i do now?

---

### Post by K.Y.A on 2009-07-02
> **jose187 said:**
> THANK YOU!!!!!!!!

That has worked a treat!!!!

One last question. How can i unmount it?
It keeps saying i need to be root...what can i do now?

Since you mounted it via terminal as root, you have to unmount it via terminal as root.

Just:

```
sudo umount ~/NFS
```

---

### Post by K.Y.A on 2009-07-02
> **jose187 said:**
> THANK YOU!!!!!!!!

That has worked a treat!!!!

One last question. How can i unmount it?
It keeps saying i need to be root...what can i do now?

I'm glad I made you happy:D

You can do many things with Linux, you just gotta learn how. :)

---

