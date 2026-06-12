---
title: "Ubuntu not booting, problems with nvidia graphics card"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jackhynes on 2011-04-08
After a 10.10 update-manager -d upgrade I can't boot to the desktop without failsafex.

Firstly the grub screen will not always appear. Sometimes it just shows the purple screen which is followed by and hangs at a black screen with a flashing hyphen. If you try to bring up a terminal, artifacts appear all over the screen. A ctrl+alt+del reboots the computer and sometimes the grub screen will appear.

Selecting the first option in grub creates a boot as described above. Removing quiet splash makes no difference. If you boot in recovery mode you can get to the desktop by selecting 'boot in failsafex' then clicking OK on the low graphics mode dialog, then selecting restart X. This gives you the log in screen.

At the desktop it shows classic Ubuntu (despite selecting Ubuntu at the login screen). Compiz will not run giving the following error message:
```
$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
Cannot register the panel shell: there is already one running.

```
When opening nvidia X server settings it says:
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

If I try to restart X the computer hangs at a black screen, which is also what happens if I log out.

On an unrelated note software-centre has been removed and won't install, citing:
```
$ sudo apt-get install software-center
[sudo] password for jack: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 software-center : Depends: python-webkit but it is not going to be installed
                   Depends: ubuntu-sso-client (>= 0.99.6) but it is not going to be installed
E: Broken packages

```

I am using an nvidia GTS 240 graphics card. Anyone know how I can log in normally?

---

### Post by ronacc on 2011-04-08
you also need to remove  vt.handoff=7  and change set gfxpayload=$linux_gfx_mode   to    set gfxpayload=text
edit:   and when you get to login select ubuntu classic no effects

---

### Post by jackhynes on 2011-04-08
> **ronacc said:**
> you also need to remove  vt.handoff=7  and change set gfxpayload=$linux_gfx_mode   to    set gfxpayload=text
Okay this got me to a terminal screen but I couldn't get a graphical interface. I tried ctrl+alt+F7 and 'gdm start'.

> **ronacc said:**
> edit:   and when you get to login select ubuntu classic no effects
This gives me the exact same desktop as logging in with the Ubuntu option selected.

---

### Post by ronacc on 2011-04-08
Oh I thought you couldn't get a desktop at all . Go to system>administration>additional drivers and see if there is an nvidia driver showing , if so install it , if not check your software sources and make sure they are pointed at natty .

unity won't run without compiz and compiz won't run with the failsafe driver .

---

### Post by jackhynes on 2011-04-08
Yeah the nvidia driver said it was installed and activated. I removed and reinstalled it. I'll see what happens after the restart.

The software sources all point to natty, they were changed automatically by the update-manager -d upgrade.

---

### Post by jackhynes on 2011-04-08
Alright everything works great now. It was just a faulty nvidia driver. Can't believe I didn't think of that first!!

Thanks for the help ronacc!

---

### Post by ronacc on 2011-04-08
probably your old nvidia driver from maverick was still there .

---

