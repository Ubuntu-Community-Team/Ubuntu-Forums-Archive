---
title: "No ATI Control"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by fool on 2006-11-19
I installed the latest ATI drivers, and it seems as though they all run fine. I don't have the control panel. The icon is installed on the Applications > Accessories menu but whenever I click I get "Could not launch menu item" "Failed to execute child process "/usr/bin/fireglcontrolpanel" (No such file or directory)".

I have run a file search for "fireglcontrolpanel" and it appears that I don't have it. I have tried "fireglcontrolpanel" in a terminal but get "bash: /usr/bin/fireglcontrolpanel: No such file or directory".
I followed the instructions at the [Unoffical ATI Linux Driver Wiki]("http://wiki.cchtml.com/") 

I get:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6174 (8.31.5)

so it looks as though everything installed fine

---

### Post by fool on 2006-11-19
Found out the file does exist, but it still won't open. Same error message. Any help would be greatly appreciated

---

### Post by HansHarz on 2006-12-02
I got the same problem with a radeon 9600. did you found anything that will help ?
HansHarz

---

### Post by tylerjames on 2006-12-14
currently experiencing the same problem... but my fglrxinfo returns

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

i used the official ATI graphical installer for my mobile radeon x1400

---

### Post by jzlharvey on 2007-02-05
I am having the same issue.
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---

### Post by hmaldonado on 2007-02-12
Hi there

I had the same problem after installing the ATI drivers:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

Using the 'file' command I realised the following:

dusty$ file /usr/bin/fireglcontrolpanel
/usr/bin/fireglcontrolpanel: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.3, dynamically linked (uses shared libs), for GNU/Linux 2.4.3, stripped

As you can see it is a 32-bit application and probably you are running amd64. To be able to run it you have to install the following packages:

sudo apt-get install ia32-libs ia32-libs-gtk

You must also install the dependencies for these packages. Once they have all been installed you will be able to run the ATI Control Panel.

Hazael

---

### Post by madcowbcs on 2007-03-18
I get the same problems with my 9800.  I run the 32 bit version on my P4.  I alien-ed the rpm the ati had.  How do I find out if I need dependencies?   Does it matter what order I install them in?  Every time I install a package I find layers upon layers of dependencies that need to be done by hand.  Is there an easier way?

---

### Post by res1uqtp on 2007-05-02
> **hmaldonado said:**
> 
You must also install the dependencies for these packages. Once they have all been installed you will be able to run the ATI Control Panel.

Hazael

I'm a newbie so bare with me here. How to you install dependencies for this package? What am I looking for? Thanks in advance for the help.

---

