---
title: "Can't get past login screen after ATI update"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by johannix on 2008-02-22
My current status is that I cannot get to my desktop. What happens is the login screen comes I submit my username/password and then it loops back to the login screen after going to the terminal for a couple seconds.

Before this problem I had updated my ATI driver following 'Method 2' from this WIKI: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

I'm running Gutsy and have an ATI Radeon 600 card and was trying to update to the Catalyst 8.2 driver.

After the driver installation everything installed without error.


Bit stuck...

---

### Post by steefjeqv on 2008-02-22
Hi,

I remember having a similar problem after upgrading the ATI driver.

The ATI installer had changed the rights/owner of one file to root, thus disabling the possibility to login.

I can't remember the exact file though.
Do you have any error messages when you log in ?

Greetings,
Steven

---

### Post by johannix on 2008-02-22
I viewed /var/log/messages after logging in and saw that the last messages were calls to fglrx, but I didn't notice any errors.

I am able to login in safe mode, which uses the Mesa drivers, so now it's really a straightforward ATI problem (I think).


To give proper info about when my system started going crazy, I must tell you that it started when I upgraded from Feisty to Gutsy. I've been ignoring the problem and starting up with my older Kernel (which for some reason seemed to still work) until a couple days ago when my sound and video stopped behaving.

---

### Post by johannix on 2008-02-24
Boy-oh-boy. So the past couple days has been quite the challenge getting things back to normal, but I have learned a lot about how the video card settings work in Linux...

So what it took to get things going is first off to go to the terminal using ctl-alt-F1 once the machine started up and messing with /etc/X11/xorg.conf a bit. The commands that were the most useful were:

Remove old versions of fglrx (ATI drivers):
```
dkms status
sudo dkms remove -m fglrx -v <version> --all
```

Put things back to normal:
```
sudo apt-get install xserver-xgl
```

Then I went through the "method 2" instructions on this site: [ATI 8.2 Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

