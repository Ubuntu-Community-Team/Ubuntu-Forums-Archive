---
title: "problems, tried to fix the 1440x900... now all i get is a terminal screen"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by lord_jagganath on 2007-10-10
HELP... I must have done something stupid to my /etc/X11/xorg.conf file... as now it just boots to a terminal ( as if using an old dos interface), and no gui in sight... gui error...or some thing like that

---

### Post by nzadLithium on 2007-10-10
can you post your contents of /etc/X11/xorg.conf?

---

### Post by lord_jagganath on 2007-10-10
ok i will try... it involves a helluva writing on my part...hhehe

thanks for your help (in advance) though...

ok here it iswhen i first start off. it reachesa terminal screen where it asks me to logon ( juggernaut@login~$ : )
afterwhich it goes to a blue/red screen "Failed to start x server"
select yes to find out error
Data inco0mplete
Problem parsing config file
Error parsing config file
fatal server error

no screens found                 "f
 select ok

Detailed error
(WW) xf86CloseConsole:KD_SETMODE failed : bad file description
xf86CloseConsole:VT_getmode Failed :  bad file description
xf86 OpenConsole:VT_getstart failed:  bad file description

and then i login,
when it is at juggernaut@juggernaut-desktop~$ inputting /etc/X11/xorg.conf does little/nothing it says it is a file error...

---

### Post by nzadLithium on 2007-10-10
you need to do sudo nano /etc/X11/xorg.conf

while in nano u use ctrl + the key to use the shorcuts listed at the bottom.

also are you using a nvidia or ati based graphics card?

they both have programs that can write your xorg.conf for you.

If your using an ati or nvidia card dont bother writing up the xorg.conf just tell me which you have and if you already installed the propriety drivers.

If your using any other graphics card then you'll still need to get me the contents of your xorg.conf

---

### Post by nzadLithium on 2007-10-10
oh and im not going to be on again till tomorrow but i have this thread bookmarked so ill check it then.

---

### Post by lord_jagganath on 2007-10-10
using an ati card... and the proprietry drivers haven't been installed ( rather never did need it.... earlier though...when i still had a crt monitor..)

---

### Post by nzadLithium on 2007-10-10
I just thought of another more easy way to do :idea:

run 

sudo dpkg-reconfigure xserver-xorg

answer all the questions it asks you and it should re-setup your xserver :biggrin:

When it asks for the driver since you werent using the propriety before chances are you were using 'vesa'

---

### Post by lord_jagganath on 2007-10-11
thanks for all the help!!
i got it!!!

---

### Post by mbgm8ndb on 2007-10-17
Thanks nzadLithium, this was a very big help!!


> **nzadLithium said:**
> I just thought of another more easy way to do :idea:

run 

sudo dpkg-reconfigure xserver-xorg

answer all the questions it asks you and it should re-setup your xserver :biggrin:

When it asks for the driver since you werent using the propriety before chances are you were using 'vesa'

---

