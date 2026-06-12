---
title: "Vnc"
date: 2007-10-05
forum: Mythbuntu
---

### Post by p$y on 2007-10-05
Hi,

I've enabled the VNC support and entered a password, but I always get a authentification error. I am sure I've entered the right password. With Ubuntu's remote desktop enabled it worked. Have I to add the port or something else?

---

### Post by p$y on 2007-10-05
ok, entered the same password with vnc4passwd and now it just works :lolflag:

---

### Post by superm1 on 2007-10-05
> **p$y said:**
> Hi,

I've enabled the VNC support and entered a password, but I always get a authentification error. I am sure I've entered the right password. With Ubuntu's remote desktop enabled it worked. Have I to add the port or something else?
Okay as a quick comparison,

Can you generate a password using vncpasswd by hand, and do a diff on that file versus the one in /root/.vnc/passwd?

It's possible the vnc password generation got broken for us in some regard.

Did you create your password during ubquity installation, or during mythbuntu control centre?

---

### Post by p$y on 2007-10-06
I don't know if I entered a password during the installation, I think it was later during the mythbuntu control centre. Sorry I don't know hoh to compare the files, I think you would be faster to do this ;-)

---

### Post by superm1 on 2007-10-06
> **p$y said:**
> I don't know if I entered a password during the installation, I think it was later during the mythbuntu control centre. Sorry I don't know hoh to compare the files, I think you would be faster to do this ;-)
Okay its possible the control centre has this function broken then.  (Hope not :))

We are doing one last upload for it later today.  If you can remove /root/.vnc/passwd, and try to do it once more?

---

### Post by superm1 on 2007-10-06
> **superm1 said:**
> Okay its possible the control centre has this function broken then.  (Hope not :))

We are doing one last upload for it later today.  If you can remove /root/.vnc/passwd, and try to do it once more?

Well I looked a little closer at the code and caught the bug.  In the upcoming upload (0.8-0ubuntu1) this is fixed.

Thanks for pointing it out!

---

### Post by Lytspeed on 2007-11-03
Hi,

Is it possible that this bug is still around?  I tried enabling remote control with a password under the Control Centre, and I'm not able to control my Mythbuntu box remotely.  When I check back in the Control Centre, the remote control entry is again set to "disabled."

If I start a vino-session or x11vnc session, I can control the box remotely.  I would like to have remote control start up automatically so I can run the box headless (or at least with just a TV connected.)

Thanks in advance for any help.

Stace

---

### Post by Lytspeed on 2007-11-03
Okay, I solved part of my own problem.  When I would try to enable VNC Service in Control Centre, I would get a small update screen, and then Control Centre would disappear.

By going to the terminal and entering "vnc4server", I discovered that the app wasn't installed, and that the installer was asking for the Mythbuntu Gutsy CD.  After putting that in and allowing the instlall to finish, Control Centre shows the VNC Service as enabled, but I still can't connect to it.

I've tried the following, where [IP] is my Mythbuntu box's IP address:

[IP]
[IP]:0
[IP]:1
[IP]::5900
[IP]::5901

:confused:

Any ideas?

Thanks,
Stace

---

### Post by Lytspeed on 2007-11-03
Hello again,

I know it's bad form to reply to my own posts, but I don't want to make anyone retrace my steps.

Here's where I am so far.  If I exit Control Centre, open a terminal, and perform "sudo apt-get install vnc4server", then supply the CD for it to install from, everything appears to install fine.  If I do "netstat -l", it shows that my box is listening on port 5900, just like it's supposed to.  I switch to my XP box, connect to my IP address (with no parameters), and I get a beautiful representation of my current Mythbuntu screen, which is exactly what I want.

However, if I restart the computer, the vnc4server job that's running doesn't hold, not surprisingly, and if I try to start it by running "vnc4server" from the command line, it doesn't start the same.  It starts on port 5901, and when I connect to [IP]::5901, I get an ugly grey X server screen, and that's not what I want.

Control Centre does recognize that vnc4server exists now, and allows me to disable (i.e. uninstall) it, but will not enable (i.e. reinstall) it correctly.

So, currently, the only way for me to get the desktop VNC connection that I want is to disable/uninstall vnc4server using Control Centre, then manually install vnc4server from CD, and it's configured correctly upon install.  Then, as long as I don't turn off the Mythbuntu box, I can connect from my PC.

Someone please tell me what I'm missing.  There has to be a better solution than this to let me access the :0 screen from my inferior XP box!

Stace

---

### Post by superm1 on 2007-11-04
> **Lytspeed said:**
> Hello again,

I know it's bad form to reply to my own posts, but I don't want to make anyone retrace my steps.

Here's where I am so far.  If I exit Control Centre, open a terminal, and perform "sudo apt-get install vnc4server", then supply the CD for it to install from, everything appears to install fine.  If I do "netstat -l", it shows that my box is listening on port 5900, just like it's supposed to.  I switch to my XP box, connect to my IP address (with no parameters), and I get a beautiful representation of my current Mythbuntu screen, which is exactly what I want.

However, if I restart the computer, the vnc4server job that's running doesn't hold, not surprisingly, and if I try to start it by running "vnc4server" from the command line, it doesn't start the same.  It starts on port 5901, and when I connect to [IP]::5901, I get an ugly grey X server screen, and that's not what I want.

Control Centre does recognize that vnc4server exists now, and allows me to disable (i.e. uninstall) it, but will not enable (i.e. reinstall) it correctly.

So, currently, the only way for me to get the desktop VNC connection that I want is to disable/uninstall vnc4server using Control Centre, then manually install vnc4server from CD, and it's configured correctly upon install.  Then, as long as I don't turn off the Mythbuntu box, I can connect from my PC.

Someone please tell me what I'm missing.  There has to be a better solution than this to let me access the :0 screen from my inferior XP box!

Stace

There is a bug in the control centre that it wants to install everything from CD (like apt) but doesn't tell you.  If you put the CD in the drive before you install it, it should work properly.

---

### Post by mungewell on 2007-11-06
> **Lytspeed said:**
> Hello again,

Someone please tell me what I'm missing.  There has to be a better solution than this to let me access the :0 screen from my inferior XP box!


Check that the vnc module is being loaded when X starts... should say so in the /var/log/Xorg.0.log

---
(II) LoadModule: "vnc"
(II) Loading /usr/lib/xorg/modules/extensions//libvnc.so
(II) Module vnc: vendor="RealVNC Ltd"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension VNC
---

Also check that the /etc/X11/xorg.conf file contains the appropriate vncpassword file. Should be something like

---
Section "Screen"
	Identifier	"Dummy Screen"
	Device		"Dummy GFX Card"
	Monitor		"Dummy Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	Option		"PasswordFile" "/root/.vnc/passwd"
EndSection
---

Good luck,
Munge.

---

