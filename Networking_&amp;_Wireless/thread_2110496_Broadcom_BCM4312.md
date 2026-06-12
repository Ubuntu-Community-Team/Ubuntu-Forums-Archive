---
title: "Broadcom BCM4312"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by AntegRal on 2013-01-30
HELLO everybody ):P
i've got Dell VOstro 1510 laptop and i've just installed kubuntu 12.04 but i have a great problem: :D
my wireless is off when i am in kbuntu and no network is available
i guess i should install some drivers for it but i don't know how to do that
i have searched whole internet (o.O) but i couldn't find any thing...
PLEASE HELP ME!

---

### Post by ahallubuntu on 2013-01-30
Open a terminal (search for "terminal" and open that) and type:

```
lspci | grep -i broadcom
```

I refurbished a 1510 about a year ago and am pretty sure the wireless card I removed to install an Intel 5100 wireless card was originally one of the troublesome Boardcom wireless cards that often cause new users trouble.  The above command should tell us which one - then someone can give you the commands to type to get it working.

Any chance you can connect with an ethernet cable temporarily?  I seemed to recall Ubuntu had an "Additional Driver" for that wireless card as well - maybe you need to be online to download it...

---

### Post by Hodevah on 2013-01-30
Hello AntegRal:  :)

I won't be able to aid you much as I am also a new beginner in using Linux but I can tell you that one of the things that you need to do is to post the information that is set up in this 'how to' here>[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

The information that you post from there will serve to provide some valuable information to the one's that can help you. The people here are very helpful and will likely also ask you for that supporting information.

---

### Post by AntegRal on 2013-01-30
ahallubuntu and  Hodevah! thank you both!

> **ahallubuntu said:**
> Open a terminal (search for "terminal" and open that) and type:

```
lspci | grep -i broadcom
```


thit is the result:
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
 
what should i do now please?

> **ahallubuntu said:**
> 
Any chance you can connect with an ethernet cable temporarily? 

yes! i'm now connected with an ethernet cable.

---

### Post by ahallubuntu on 2013-01-30
This worked for someone else using your card in a Dell:

[http://ubuntuforums.org/showthread.php?t=2100005](http://ubuntuforums.org/showthread.php?t=2100005)

Try opening a terminal again and typing these commands:

```
sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by AntegRal on 2013-01-30
> **ahallubuntu said:**
> 
[http://ubuntuforums.org/showthread.php?t=2100005](http://ubuntuforums.org/showthread.php?t=2100005)

Try opening a terminal again and typing these commands:

```
sudo dpkg-reconfigure bcmwl-kernel-source

```

thank you but..
this is the result:

Package `bcmwl-kernel-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: bcmwl-kernel-source is not installed

:(

---

### Post by ahallubuntu on 2013-01-30
Hmm.  Maybe try this first:

```
sudo apt-get update
sudo apt-get install dkms
```

then try the previous two lines again.

---

### Post by ahallubuntu on 2013-01-30
Oops!  Wait, I missed this in the original post.  So do this:

```
sudo apt-get update
sudo apt-get install linux-headers-generic bcmwl-kernel-source
```

And then if it still does not work, try the reconfigure lines previous.

---

### Post by AntegRal on 2013-01-30
it didn't work dear ahallubuntu! :(
i downloaded updates and entered the codes, but:
[IMG]http://s2.picofile.com/file/7639524515/snapshot1.png[/IMG]
it made my wireless completely diasbled( wireless tab is diabled now)
[IMG]http://s2.picofile.com/file/7639524729/snapshot2.png[/IMG]

---

### Post by ahallubuntu on 2013-01-30
I'm so sorry this has been difficult for you!  I'll leave this to someone else.  I get rid of these troublesome Broadcom wireless cards almost first thing, but I realize that's not practical for everyone!

---

### Post by AntegRal on 2013-01-31
thank you by the way ;)
so i have a new problem: i missed my wireless driver i guess! :)
what should i do now????

---

### Post by coldraven on 2013-01-31
I'm running Kubuntu 12.04 and I have the Broadcom BCM4311 wifi card. It works fine and I did not have to do anything.
I think that if the wifi was switched off when you installed the drivers are not loaded.
Can you see if it is switched on?  My laptop has a blue LED that shows that the wifi is on.

---

