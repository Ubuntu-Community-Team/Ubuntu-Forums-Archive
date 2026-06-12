---
title: "Accidentally uninstalled nvidia.  Won't let me reinstall."
date: 2009-02-09
forum: Multimedia Software
---

### Post by missbliss on 2009-02-09
I downloaded Envy for some reason I can't remember and when I opened it I somehow managed to check "uninstall nvidia driver" and click apply.  (I was a couple drinks in.......)

But, now it gives me this error message when I try to install:

> There was an error in the installation process. You can see the log file /var/log/envy-installer.log

When I plug that in to the terminal I get:

```
skhills@skhills-laptop:~$ /var/log/envy-installer.log
python: can't open file 'pulse.py': [Errno 2] No such file or directory
/var/log/envy-installer.log: line 2: root@skhills-laptop:/usr/share/envy#: No such file or directory
/var/log/envy-installer.log: line 3: ENVY: command not found
skhills@skhills-laptop:~$ 


```

Any help?

---

### Post by ibutho on 2009-02-09
To view the log file, you are supposed to do something like
```
less /var/log/envy-installer.log
```

---

### Post by missbliss on 2009-02-10
> **ibutho said:**
> To view the log file, you are supposed to do something like
```
less /var/log/envy-installer.log
```

Ah, thanks you.  Here's what I got that time:

```
python pulse.py ati 
root@skhills-laptop:/usr/share/envy# python pulse.py ati
ENVY ERROR: ATI card not found
/var/log/envy-installer.log (END) 


```

---

### Post by norwoods on 2009-02-10
it appears that you told envy to install an ati driver which is not an nvidia driver, select an nvidia driver in envy or do something else.
i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

---

### Post by missbliss on 2009-02-10
Quick question:  Would reinstalling Ubuntu fix this problem??  (I'm kind of having a hard time installing the driver.)  I've downloaded some packages, but am a little lost after that.

---

### Post by norwoods on 2009-02-10
reinstalling Ubuntu would probably leave you about where you are now, without the nvidia driver.

---

### Post by missbliss on 2009-02-10
> **norwoods said:**
> reinstalling Ubuntu would probably leave you about where you are now, without the nvidia driver.
Alright, thanks. Time to do a bit more research.   I guess what I'm confused about is this:

After I've obtained the packages, what do I do?  lol.

---

### Post by norwoods on 2009-02-10
start System--Administration--Synaptic Package Manager

start Settings--repositories

on the Third-Party Software tab, add the source for intrepid from 
[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

download the key from 
[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa) 
into a file with any name

on the Authentication tab, add the previous file with Import Key File

close Software Sources

search for 180.27

mark all files with 180.27 under Latest Version for installation

Apply

start System--Administration--Hardware Drivers

activate the version 180 driver

start Applications--Accessories--Terminal

in the Terminal, type gksu nvidia-settings

configure the Xorg.conf file

---

### Post by avrilrox on 2009-02-10
> **missbliss said:**
> Quick question:  Would reinstalling Ubuntu fix this problem??  (I'm kind of having a hard time installing the driver.)  I've downloaded some packages, but am a little lost after that.

Actually, reinstalling Ubuntu **could** help.

I remember myself reinstalling Ubuntu after messing with the wrong ATI drivers. Ati drivers truly are a pain in the a$$.

After you reinstall Ubuntu, it will search for adequate drivers. Make sure you install those Ubuntu recommend or everything could go wrong. I'm currently using Nvidia and it's a lot easier. Go into Configuration -> Hardware Drivers and activate Nvidia drivers. It will download them and install them. As easy as that.

---

### Post by missbliss on 2009-02-11
Crap, I seemed to have dug myself deeper, here.  

```
skhills@skhills-laptop:~$ sudo apt-get update
E: Malformed line 54 in source list /etc/apt/sources.list (URI parse)
skhills@skhills-laptop:~$ sudo apt-get install -f
E: Malformed line 54 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
skhills@skhills-laptop:~$ 

```

This is an error code I'm getting for a lot of inputs I'm plugging in to the terminal.  :-/

---

### Post by norwoods on 2009-02-11
repair or delete line 54 in the file /etc/apt/sources.list

---

