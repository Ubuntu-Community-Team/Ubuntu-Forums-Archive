---
title: "[SOLVED] Help with lirc and  Hauppauge remote"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by pjman on 2007-02-10
I'm trying to get lirc working with my  Hauppauge remote that came with my [WINTV-PVR-150 104]("http://www.newegg.com/product/product.asp?item=N82E16815116625"). I've followed two different guides:

[One]("https://help.ubuntu.com/community/Install_Lirc_Edgy")
[Two]("http://doc.gwos.org/index.php/Lirc")

It's not working for me and I'm looking for help troubleshooting the issue. I'm running Edgy with 2.6.17-10-generic. 

To save a couple of potential questions:

[LIST]I made sure to use the third party repositories in the first guide to make sure the Packages >= 0.8.0-9.[/LIST]

[LIST]I have followed the steps in guide two where you have to "Disable ir_common" because of the new remote control "feature" in kernel 2.6.17. In fact I've tried both using the ir-common.ko provided by the author of the guide (hexion) and also compiling my own following the instructions; boy did that take a long time :shock:[/LIST]

Am I correct that this remote should use i2c? What are my next steps for troubleshooting?

---

### Post by basketcase on 2007-02-10
> **pjman said:**
> I'm trying to get lirc working with my  Hauppauge remote that came with my [WINTV-PVR-150 104]("http://www.newegg.com/product/product.asp?item=N82E16815116625"). I've followed two different guides:

[One]("https://help.ubuntu.com/community/Install_Lirc_Edgy")
[Two]("http://doc.gwos.org/index.php/Lirc")

It's not working for me and I'm looking for help troubleshooting the issue. I'm running Edgy with 2.6.17-10-generic. 

To save a couple of potential questions:[LIST]
[*]I made sure to use the third party repositories in the first guide to make sure the Packages >= 0.8.0-9.[/LIST][LIST]
[*]I have followed the steps in guide two where you have to "Disable ir_common" because of the new remote control "feature" in kernel 2.6.17. In fact I've tried both using the ir-common.ko provided by the author of the guide (hexion) and also compiling my own following the instructions; boy did that take a long time :shock:[/LIST]Am I correct that this remote should use i2c? What are my next steps for troubleshooting?


sudo /etc/init.d/lirc start

What is your output? 

then irw

Press buttons on your remote..see anything?  I'm dealing with a very similar problem in Dapper with my PVR-350.

I just fixed mine....
In the first link you have LIRC in Edgy, there is a command irrecord.  I had to record my own remote.  But after I did that, and followed the guide, it's working!

---

### Post by pjman on 2007-02-10
> **basketcase said:**
> sudo /etc/init.d/lirc start

What is your output? 

when I do 'sudo /etc/init.d/lirc restart' I get:

Stopping lirc daemon: lircmd lircd.
Starting lirc daemon: lircd.

> **basketcase said:**
> 
then irw

This one is odd. I'm supposed to get a blank line and it's supposed to appear to "lock up" so it can return some values when I press a button on the remote. I got the blank line when I followed the first guide. Now with the second guide irw closes and brings me right back to a new line command prompt.

```

~$ irw
~$
```

> **basketcase said:**
> 
I just fixed mine....
In the first link you have LIRC in Edgy, there is a command irrecord.  I had to record my own remote.  But after I did that, and followed the guide, it's working!

I'll try that and report what happens.

---

### Post by pjman on 2007-02-11
After running 'sudo irrecord -d /dev/lirc0 lircd.conf' I'm asked to press enter. I press enter and then it says to "Hold down an arbitrary button". I do this and after about 5 seconds this comes up:

irrecord: gap not found, can't continue

Any ideas?

---

### Post by basketcase on 2007-02-11
I was too far away from my receiver.  I had to be about 6" or so from it.  Also, check to make sure batteries are good.  

Basically it's just not seeing the remote.

---

### Post by pjman on 2007-02-11
I changed batteries and still no go. Is there any way to tell if it's a bad remote or something with a driver on my system?

---

### Post by pjman on 2007-02-11
One other thing I notice, as I plug in the IR receiver cable into the back of my PVR-150 card the red receiver at the end of the cable lights up red. This happens only when the cable is plugged in halfway. Should it be lighted up when it's fully plugged in?

***EDIT***

I also thought this info might help...

When I run dmesg | grep lirc

I get
```
[17179608.456000] lirc_dev: IR Remote Control driver registered, at major 61
[17179608.460000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179608.656000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179608.656000] lirc_dev: lirc_register_plugin: sample_rate: 10
```

---

### Post by pjman on 2007-02-12
After much searching I got the remote working!! Although a reboot breaks it again... Hopefully someone can help with that.

Here are the steps. 

```
sudo lircd -n
```
gives me
```
lircd: lircd(hauppauge) ready
```

I then type irw in a new terminal

The below text shows up in the previous terminal with 'sudo lircd -n'
```
lircd: accepted new client on /dev/lircd
lircd: could not get file information for /dev/lirc
lircd: default_init(): No such file or directory
lircd: caught signal
Terminated
```

It's not seeing /dev/lirc. If I create a symbolic link from /dev/lirc to /dev/lirc0

```
sudo ln -s /dev/lirc0 /dev/lirc
```

everything works until I reboot. 

Can someone tell me why /dev/lirc wasn't created in the first place? How can I get the symbolic link to stay after a reboot?

Thanks!

---

### Post by pjman on 2007-02-13
Does anyone know why /dev/lirc is not being created with the install of lirc? How can I make the symbolic link stay after a reboot?

Thanks!

---

### Post by L_V on 2007-03-15
> **pjman said:**
> Does anyone know why /dev/lirc is not being created with the install of lirc? How can I make the symbolic link stay after a reboot?
No answer on that one ?

---

### Post by electronikjunkie on 2007-03-15
you could just create a startup script to issue the commands you issued after boot and put it in /etc/init.d

also check out this link. there's an example of a script you can use on one of those pages.

[http://www.ubuntuforums.org/showthread.php?t=163496](http://www.ubuntuforums.org/showthread.php?t=163496)

---

### Post by L_V on 2007-03-16
Thanks for the link.
I think I will need at least one more week to try to make lirc correctly work.

I could not imagine it was so complex to install a so simple IR serial receiver under linux.
Something should definitively be made to improve this because not sure everybody can spend at least 2 weeks to make it work.

---

### Post by mrming on 2007-06-27
To create the symbolic link on startup create a startup script containing:

sudo ln -s /dev/lirc0 /dev/lirc

There's a guide to creating a startup script here:
[http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/)

hth :)

---

