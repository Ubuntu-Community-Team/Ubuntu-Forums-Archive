---
title: "VLC interface too big in 18.04"
date: 2018-04-28
forum: Multimedia Software
---

### Post by Cheltspy on 2018-04-28
Just installed 18.04 but VLC interface is too big and can't be made any smaller than quarter of the screen.

In Screen display settings the monitor is reported as 7" yet it is 42".

Other apps appear okay.

---

### Post by Autodave on 2018-04-28
What graphics card do you have in there? Did you install a driver for it? If so, what driver and where did you get it from?

---

### Post by Cheltspy on 2018-04-28
Intel N3700 (i915 chipset) never needed to install any driver for it.

---

### Post by Cheltspy on 2018-04-28
Fixed by adding a file called  gnome-qt.sh in /etc/profile.d

with this inside.

export QT_AUTO_SCREEN_SCALE_FACTOR=0

---

### Post by jadaube2 on 2018-05-15
+1 - had the same problem with my tv-box computer after I upgraded from 17.10 to 18.04. worked for both the gnome and xubuntu desktops.

---

### Post by wyliecoyoteuk on 2018-06-08
I had the same problem, that solved it, thankyou very much

---

### Post by noah31 on 2018-06-26
Thanks a ton, saved me a headache.

---

### Post by scouser73 on 2018-07-16
> **Cheltspy said:**
> Fixed by adding a file called  gnome-qt.sh in /etc/profile.d

with this inside.

export QT_AUTO_SCREEN_SCALE_FACTOR=0

Cheers, your solution worked perfectly for me, all I needed to do afterwards was restart the PC and VLC appeared normally.

---

### Post by darkdragon-001 on 2018-09-13
I created a [bug report]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1792167"). Please also mark it as affecting you and add your system specs so that this issue gets solved soon!

---

### Post by eagleestar on 2019-02-10
1. open a terminal and type: 
sudo -H /bin/bash

2. Type your password. 

3. navigate to the etc/profile.d folder by typing: 
cd /etc/profile.d

4. Open the text editor and type the following: 
[COLOR=#000000][I]export QT_AUTO_SCREEN_SCALE_FACTOR=0

[/I][/COLOR]Now save the file to the desktop as gnome-qt.sh 
Close the text editor. 

5. Back in the terminal type the following, where USER is your own user name. Press enter when done. 
[COLOR=#000000]
[/COLOR]sudo cp '/home/USER/Desktop/gnome-qt.sh' /etc/profile.d
You can even drag the file into the terminal after sudo cp .

What this will do is copy your file from the desktop into the profile.d folder. 

6. Now you can close the terminal. Delete the desktop file if you want. 

7. Restart the computer and VLC should look normal.

---

