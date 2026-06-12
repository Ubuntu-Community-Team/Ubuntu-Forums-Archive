---
title: "graphics driver probs on inspiron 1525"
date: 2013-02-22
forum: Multimedia Software
---

### Post by rexmundi243 on 2013-02-22
My Dell inspiron 1525 has a problem that I don't understand, help appreciated, I'm sure it is simple to you lot...

I know that my 1525 has NVIDEA graphics on it(I have previously had XP and Vista on it, so have the windows nvidea drivers), the same that is on my other Dell machine (optiplex) , and on that one I was able to install the nvidea X server.
But when I try to do the same on my 1525 I get a warning box pop up that says:

"You do not appear to be using the NVIDEA X driver.
Please edit your X configuration file (just run 'nvidea-xconfig'
as root), and restart the X server"

that doesn't mean a lot to me, I'm guessing it is a command line thing.... not got round to that yet, so please help...

How do I do the above?
Rex

Rex Mundi

---

### Post by Yellow Pasque on 2013-02-22
Please give output of:
```
lspci | grep -i VGA
```

---

### Post by Bucky Ball on 2013-02-22
*Thread moved to **Multimedia & Video**.*

---

### Post by rexmundi243 on 2013-02-22
> **Temüjin said:**
> Please give output of:
```
lspci | grep -i VGA
```

sorry, I don't know what you mean, where and how do I type that in?

I really am that ignorant, so please bear with me...

Rex

---

### Post by Yellow Pasque on 2013-02-22
In the terminal Ctlr+Alt+T

---

### Post by rexmundi243 on 2013-02-22
Thankyou.
It returns with:
00:02.0 VGA compatible controller: Intel corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

---

### Post by rexmundi243 on 2013-02-22
which means it is not nvidea... hmm, my memory must be faulty.

---

### Post by rexmundi243 on 2013-02-22
which is very confusing, because when I go into my ubunto software centre, under system, search for nvidia shows the following:
NVIDEA binary Xorg driver development files
nvidea-current-dev

and further down, 
Tool of configuring the nvidea graphics driver
nvidia-settings

I didn't put these on, the one I (mistakenly) tried to install that produced my original enquiry message, that is further down the list, so that means that when I originally installed ubuntu on this machine (2 days ago for the first time) then it was that install process that selected the nvidia driver...

sorry, I keep spelling nvidia wrong...

so I think that means I need an intel driver, is that correct?

---

### Post by Yellow Pasque on 2013-02-22
Intel driver is already installed by default. You just need to remove the nvidia packages.

> I didn't put these on
They are dependencies of the nvidia, so you indirectly installed them (Ubuntu does not come with prpropietary video drivers installed).

---

### Post by rexmundi243 on 2013-02-22
and to add further to my confusion, in my software centre under system, I search for intel, and I find the following installed on my system:

Intel-gpu-tools
xserver-xorg-video-intel
libdrm-intel1
libva1
libva-a11-1


that is me well confused now, if my "current" driver is nvidea but my graphics is intel...

---

### Post by rexmundi243 on 2013-02-22
> **Temüjin said:**
> Intel driver is already installed by default. You just need to remove the nvidia packages.


They are dependencies of the nvidia, so you indirectly installed them (Ubuntu does not come with prpropietary video drivers installed).

I guess I must have done...

anyway, I did as you suggested and just removed all the nvidia stuff, although there is one that I am not sure of:

xserver-xorg-video-nouveau

I think I read somewhere that is something to do with nvidia, can I safely remove that one too?

So far, removing three nvidia ones have not caused a problem, so thanks for that tip.

Rex

---

### Post by rexmundi243 on 2013-02-22
Thanks so far Temujin, I hope my silly questions don't annoy you, but the thing that started all this for me was after I installed ubuntu on the inspiron the first time two days ago, I looked in 'system settings/details' and for graphics it just says "Unknown"... and as I am lending the inspiron to a friend I wanted it right, hence my mistaken effort to install nvidia.

But it is no different with my dell desktop, that also shows graphics as unknown, why is this? How can the system not know what graphics system is on there?

Rex

---

### Post by Yellow Pasque on 2013-02-22
nouveau package can be uninstalled, but it doesn't interfere with other open-source drivers (like intel), so best to leave it alone..

> graphics it just says "Unknown"...
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)
```
sudo apt-get mesa-utils
```

---

### Post by rexmundi243 on 2013-02-23
> **Temüjin said:**
> nouveau package can be uninstalled, but it doesn't interfere with other open-source drivers (like intel), so best to leave it alone..


[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)
```
sudo apt-get mesa-utils
```

that returns:

E: Invalid operation mesa-utils

and gives me another question, why E: above?

And, why in two fresh installations of Ubuntu do both of them say "graphics unknown".... I will check my probook soon, that has a dual boot installation, I will see what that says.

---

### Post by Yellow Pasque on 2013-02-23
Note to self: more proofreading needed.
```
sudo apt-get install mesa-utils
```

> And, why in two fresh installations of Ubuntu do both of them say "graphics unknown".... 
Did you even read the bug report? You must have mesa-utils installed to fix "graphics unknown" display.

---

### Post by rexmundi243 on 2013-02-23
> **Temüjin said:**
> Note to self: more proofreading needed.
```
sudo apt-get install mesa-utils
```


Did you even read the bug report? You must have mesa-utils installed to fix "graphics unknown" display.

Note to self: must read what I was advised to read.

Thanks, will do that now.
Rex

---

### Post by rexmundi243 on 2013-02-23
Thank you very much Temujin, that has fixed my problem, and I have learnt something too, a double bonus.

That is my optiplex fixed, now to do the same on my other machines.

Rex

---

### Post by rexmundi243 on 2013-02-23
I thought that had solved all my probd...
It has on my optiplex, now it shows the graphics driver, but NOt on my inspiron, I installed mesa-utils, and now it just shows nothing for graphics, whereas before it was unknown.

Should I try and reinstall the intel driver?
edit:
not that I uninstalled it, it is showing as installed....

---

### Post by rexmundi243 on 2013-02-23
Problem now solved by reinstalling ubuntu from scratch then installing mesa-utils

Thank you

---

