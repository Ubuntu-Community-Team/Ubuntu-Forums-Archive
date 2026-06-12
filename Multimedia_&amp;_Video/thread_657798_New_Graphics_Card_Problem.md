---
title: "New Graphics Card Problem"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by snofrandy on 2008-01-03
I recently upgraded my graphics card from an 8600GTS to an 8800GT.  Now, when I log into Ubuntu (Gutsy GIbbon), I get the following error:
[CENTER]
Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to vew the X server output to diagnose the problem?[/CENTER]

When I press Yes, at the bototm, it says "Fatal server error: no screens found" and the (EE) is No devices detected.

Then it shows "The X server is now disabled.  Restart GDM when it is configured properly.

Need help please.  I am relatively new to Linux.  Thanks!!

---

### Post by RawMustard on 2008-01-04
That's weird, both those cards should use the same nvidia driver.  Did you have the restricted drivers installed?

It sound like maybe your BUS ID might have changed with the new card.  If you have the nvidia drivers installed, what does "nvidia-xconfig --query-gpu-info" say your BUS ID is?  and is it the same as your /etc/X11/xorg.conf file?

Can you do that at the prompt after login in to your computer?

---

### Post by Lostincyberspace on 2008-01-04
Re install the driver it can be done through envy which is in the repository's.

---

### Post by snofrandy on 2008-01-04
> **RawMustard said:**
> That's weird, both those cards should use the same nvidia driver.  Did you have the restricted drivers installed?

It sound like maybe your BUS ID might have changed with the new card.  If you have the nvidia drivers installed, what does "nvidia-xconfig --query-gpu-info" say your BUS ID is?  and is it the same as your /etc/X11/xorg.conf file?

Can you do that at the prompt after login in to your computer?


It says:

NVIDIA: could not open the device file /dev/nvidiact1 (No such device or address).

ERROR: Unable to query GPU information



when i try to sudo gedit xorg.conf or sudo edit xorg.conf, it says:
cannot open display:

---

### Post by snofrandy on 2008-01-04
> **Lostincyberspace said:**
> Re install the driver it can be done through envy which is in the repository's.

how do i do that?

---

### Post by Sef on 2008-01-04
Here's a way to hopefully fix your problem via Applications > Accessories > Terminal:

(From overdrank's [post]("http://ubuntuforums.org/showthread.php?t=645527&highlight=xorg").  It worked for me.  Mostly just put in the defaults.)

> Well I would start with backing up the xorg
To copy Xorg
Code:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

To restore backup
Code:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Then you can use the command
Code:

```
sudo dpkg-reconfigure xserver-xorg
```



---

### Post by snofrandy on 2008-01-04
hello.  i did the sudo dpkg-reconfigure xserver-xorg and still came out the same.  I can't log into the GUI of Ubuntu.

If this helps, i have the Ubuntu Studio edition :confused:

---

### Post by shimrodmimir on 2008-01-05
I had the same probem, and solved it with this solution:

[http://ubuntuforums.org/showthread.php?t=657035](http://ubuntuforums.org/showthread.php?t=657035)

---

