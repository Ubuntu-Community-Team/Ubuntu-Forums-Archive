---
title: "clean install no wireless"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by searayman on 2009-05-26
I just did a clean install of 9.04 and I do not have any wireless. I am running a dell ups m1530

---

### Post by RedSingularity on 2009-05-27
Post the output of "lspci" from the terminal.

---

### Post by superprash2003 on 2009-05-27
also output of **lshw -C network**

---

### Post by searayman on 2009-05-27
> **superprash2003 said:**
> also output of **lshw -C network**

That gave me nothing

---

### Post by superprash2003 on 2009-05-27
i doubt that.. thats supposed to give you an output..

---

### Post by searayman on 2009-05-27
> **superprash2003 said:**
> i doubt that.. thats supposed to give you an output..

Well before I did a clean install it gave me a output

---

### Post by The Toxic Mite on 2009-05-27
Try again. I think they are forgetting that you just **copy and paste** the output of that command.

Like I said, just try again :)

---

### Post by irv on 2009-05-27
I have a dell 1525 and I have a wireless network problem and the only way I got it to work was Ndiswraper. Here is a howto for installing it.
[URL="http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper"]
http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper[/URL]

Some one else is having the same problem. Here is another thread:
[http://ubuntuforums.org/showthread.php?p=7353077]("http://ubuntuforums.org/showthread.php?p=7353077")

---

### Post by The Toxic Mite on 2009-05-27
> **irv said:**
> I have a dell 1525 and I have a wireless network problem and the only way I got it to work was Ndiswraper. Here is a howto for installing it.
[URL="http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper"]
http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper[/URL]

Some one else is having the same problem. Here is another thread:
[http://ubuntuforums.org/showthread.php?p=7353077](http://ubuntuforums.org/showthread.php?p=7353077)


What wireless card did you have? ;)

I would like to know what he has before we give him a solution, but thanks for chipping in :P:D

---

### Post by irv on 2009-05-27
> **The Toxic Mite said:**
> What wireless card did you have? ;)

I would like to know what he has before we give him a solution, but thanks for chipping in :P:D

My wireless is WLAN Mini Card 154

---

### Post by searayman on 2009-05-27
> **superprash2003 said:**
> i doubt that.. thats supposed to give you an output..

ok so my bad, you were right I do get an output:

[http://pastebin.ca/1436456](http://pastebin.ca/1436456)

---

### Post by searayman on 2009-05-27
> **Shadow121 said:**
> Post the output of "lspci" from the terminal.

here are the results of lspci

[http://pastebin.ca/1436459](http://pastebin.ca/1436459)

---

### Post by Ayuthia on 2009-05-27
Have you tried the information in my post for your other similar thread:
[http://ubuntuforums.org/showpost.php?p=7354456&postcount=11](http://ubuntuforums.org/showpost.php?p=7354456&postcount=11)

---

### Post by searayman on 2009-05-27
> **Ayuthia said:**
> Have you tried the information in my post for your other similar thread:
[http://ubuntuforums.org/showpost.php?p=7354456&postcount=11](http://ubuntuforums.org/showpost.php?p=7354456&postcount=11)

ok just tried that, and it doesn't look like it reported back anything:

mike@mike-laptop:~$ sudo modprobe -r b43 ssb wl
[sudo] password for mike: 
mike@mike-laptop:~$ sudo modprobe wl
mike@mike-laptop:~$ sudo ifconfig eth1 up
mike@mike-laptop:~$ sudo ifconfig eth1 up
mike@mike-laptop:~$ 
mike@mike-laptop:~$

---

### Post by searayman on 2009-05-27
> **searayman said:**
> ok just tried that, and it doesn't look like it reported back anything:

mike@mike-laptop:~$ sudo modprobe -r b43 ssb wl
[sudo] password for mike: 
mike@mike-laptop:~$ sudo modprobe wl
mike@mike-laptop:~$ sudo ifconfig eth1 up
mike@mike-laptop:~$ sudo ifconfig eth1 up
mike@mike-laptop:~$ 
mike@mike-laptop:~$

scratch what I just said, this worked. I didnt look in wireless network to see if it found any networks and after performing this it found wireless thanks.

---

### Post by irv on 2009-05-27
On my old laptop I installed the wicd network manager and I have no problems with wireless and I love the way it just works. I don't care where I go it always finds the wireless connections in the area I am in. Now that I have been using it for sometime now, I will never go back to using The Network Administration Tool

---

### Post by searayman on 2009-05-27
> **searayman said:**
> scratch what I just said, this worked. I didnt look in wireless network to see if it found any networks and after performing this it found wireless thanks.

ok so this all worked but when i restart it ddoes not hold. I have to run those commands all over to get back onto the wireless.

---

### Post by irv on 2009-05-27
> **searayman said:**
> ok so this all worked but when i restart it ddoes not hold. I have to run those commands all over to get back onto the wireless.

Why don't you just run it in the startup applications. 
[ATTACH]115345[/ATTACH]

---

### Post by Ayuthia on 2009-05-27
You can add it there or you can add it to the /etc/rc.local:
```
gksu gedit /etc/rc.local
```Just add it before the 'exit 0' line:
```
modprobe -r b43 ssb wl
modprobe wl
ifconfig eth1 up
```

Or you can try blacklisting b43 and ssb:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by unix1adm on 2009-05-27
I have the same issue with an IBM R51. My netowrking was fine then I did the upgrade and now its not. see my thread.. any help you can give is appreciated. Sorry for hijacikng this one.. 

[http://ubuntuforums.org/showthread.php?t=1171395](http://ubuntuforums.org/showthread.php?t=1171395)

---

