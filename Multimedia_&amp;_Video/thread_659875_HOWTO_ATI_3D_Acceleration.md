---
title: "HOWTO: ATI 3D Acceleration"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by jaz.spb on 2008-01-06
Tested on ATI Radeon X700 and ATI Mobility Radeon X1400. It sould work on many ATI video cards.
[SIZE="5"]
**[COLOR="Red"]WARNING! If the restricted driver manager is  working properly, use it, but not this howto![/COLOR]**[/SIZE]

**1. Make sure that you have the following packages installed:**

kernel-sources  (linux-kernel-devel)
gcc
libgcc
glibc
glibc-devel
glib2
glib2-devel
cpp
g++
libstdc++
libstdc++-devel

**2. Create directory /ati**

    ```
mkdir /ati
```

**3. Dowlnload driver for your video card from [COLOR="Red"][http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)[/COLOR]**

[B]
4. Run commands:[/B]

[I][B]
make file executable:[/B][/I]


```
 chmod +x your_driver_file_name.run
```

***launching installation:***

    ```
  ./your_driver_file_name.run
```

It  will start  a GUI guide:
[LIST]
[*]Select Install Driver and click Continue.
[*]Click I Agree to the ATI License Agreement.
[*]Select Automatic and click Continue.
[*]Click Exit(OK) to close the Installer.
[/LIST]
[B]
5. The driver has been installed, lets configure the driver:[/B]

```
aticonfig --initial
```
[B]
7. Now, restart  the xserver (Ctr+Alt+Backspace)[/B]
[B]
8.  If your screen resolution is right, install this package   [COLOR="Red"]xorg-driver-fglrx[/COLOR] [/B]  .
[B]
9.  Restart the xserver (Ctr+Alt+Backspace)[/B]
[B]
9. Run this command to test your card:
[/B]

     ```
 glxgears
```
It opens a window with a gears. Wait for approximately 10 seconds and close window. In your terminal window you can see something like that:
```
7972 frames in 5.0 seconds = 1594.231 FPS
```
the more FPS, the better.


**Thats all for installation drivers. Now, you can use special visual effects.**

---

### Post by archivator on 2008-01-06
I wouldn't install the driver this way as uninstalling it would be a very difficult and time-consuming task.
Instead, I suggest people follow [this](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) guide. I've been using it for several different releases of fglrx and I haven't had any troubles.

---

### Post by jaz.spb on 2008-01-06
haha, 
1. why I should uninstall the driver?
2. lets people to choose the way

---

### Post by erfahren on 2008-01-06
> **jaz.spb said:**
> haha, 
1. why I should uninstall the driver?
2. lets people to choose the way
because newbies may come across this and install the driver this way, then have problems with it and need to revert the changes. The other guide makes .debs which are easily uninstallable.

You made it a "HowTo" in the subject line, not "this is what worked for you" type thing.

Many forum members here are already in an ongoing battle trying to prevent new users who don't know any better from telling others to install using ATI's installer.

Also, the fglrx driver included with Gutsy is stable and can be activated with a couple clicks.

---

### Post by jaz.spb on 2008-01-06
**erfahren ** "Restricted driver manager" does not work on many laptops with ATI video card(I have check it). I don't know why. But it is a fact. 
I suggested method. which always brings to result.
In actual fact I wanted to write HOWTO only for ATI Mobility Radeon X1400.
Installing drivers for it is possible only by my method. Then, I have tested my howto on other ATI cards, all was very good and I decided to name my post "HOWTO: ATI 3D Acceleration".
Well, I wouldn't argue about it, I have changed the topic of the post.
But I don't agree with you. I am absolutely sure that ATI Mobility Radeon X1400 on Dell Inspiron 6400 may not be configured by other method.
Installing the drivers from repository is not do the job.

---

### Post by jaz.spb on 2008-01-07
well, I'll change my post. I'll add this "WARNING! If the restricted driver manager is working properly, use it, but not this howto!"

---

### Post by erfahren on 2008-01-07
All I was thinking is that maybe just a note saying this is the way to install the new ATI driver using its installer and it's an alternative to the Unofficial ATI Linux Driver Wiki at: 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
... and the way you describe may yield better results for some cards.

To be honest here, you probably know more about this than I do. All I'm really going by is what I've seen on this forum and my personal experience in regards to the fglrx driver. I do know that what works for some versions of cards doesn't always work for others (I think it depends on the chipset as well, that's where I'm at a complete loss).

So I think it's important to be able to revert any changes made in case it doesn't work for some reason. That's why the guide to create the .debs to install is recommended, the changes can be easily undone. (There's actually a policy that the guides marked as HowTos in the "Tips & Tutorials" subforum include instructions on how to revert any changes made.)

The other thing is, what happens when there is a kernel update? Will having the driver installed that way cause any problems? (Again, you probably know more about than I.)

You asked why you should uninstall it, and said let users choose which way. Well, some new user who comes across this may need to uninstall it, and no alternative was given. A new user may figure that this is the way it always should be done.

I do know that the ATI driver has improved (so it's own installer probably has as well). Some of the older versions released (that were newer than what's in the Gutsy repos), were problematic and the installer didn't support all the cards (from what I understood). Maybe my information is just outdated.


I guess the main thing here (and why I get so adamant about this), is that so many new users with ATI cards who try out Ubuntu immediately go to activate the desktop effects, and when they can't, they post on the forums asking why (even though there are hundreds of threads about that same issue). Before anyone is able to post saying that all they really need to do is install XGL to try them out, there are numerous replies telling them to install the newest driver, which didn't always lead to good results.

(To put that cynically, there'll be some thread that's 20 posts long, spanning a couple days, just because some guy wants to spin a cube around awhile like he saw on youtube. It gets a little annoying. ) 

Finally, for new users, going out and immediatelly installing the newest driver is really a carry-over of the Windows mentality. That isn't always recommended with Linux. 

So anyway, that's all I'm really trying to say.

---

### Post by Bablefish on 2008-01-07
Take this as a warning to any Ubuntu user who just happens to have an ATI card in their machine. It seems the only new drivers for the card are for a 64 bit cpu. If you think I am kidding just go to the ATI site and run a check for the Linux driver for your card. If you find it is the same driver for the 32 and 64 odds are they are for 64 bit only. Dispite what it says. And if you still insist on installing it, I promise not only will Xserver crash, but your xorg file will vanish without a trace. It took me 2 months to get my Ubuntu laptop working fine after I crashed it.

---

### Post by jaz.spb on 2008-01-07
I have typed the warning. It marked by red color. This warning will help users to choose the way. I think the more howtos the better because all ATI video cards are really different and unpredictable. Eventually, one of howtos will bring users to the wishful result. I'm sorry for my mistake. I had named my post "ATI 3D Acceleration". Well I have improved. And now the name of my post is true. 
I suppose that the "Restricted driver manager" is not working on some localisations of ubuntu, for example on the Russian locale. But it's not all problems. Something breaks in ubuntu configs, when ubuntu is installing on the notebooks with ATI Mobility Radeon X1400". 
I tried to install 2 versions of kernel(I supposed that kernel may be a real cause of problems with "Restricted driver manager" too.) but the result was identically. 
I ask for respect. I'm not a housewife. Please, don't make me an idiot.

---

### Post by Dragon5000 on 2008-05-25
Hey jaz,
Thanks a bunch! I followed your instructions, and I was finally able to open Warsow!!! However, I must say I get higher FPSs on 'glxgears' with the default Ubuntu driver...Anyways, the reason why I wanted to install the damn ATI driver was so I could play 3D games/FPS games (which did not load at all with fglrx). Granted I'm new at this, and probably I'm doing something wrong, but what I did was to install a new instance of Ubuntu 7.10 and test the installation on that. 
Thanks again dude!
:guitar:

---

### Post by Dragon5000 on 2008-05-25
Well, let me take it back...It worked fine on a Gutsy 32 install. I've tried it on my main Gutsy 64, and I've screwed everything up. I thought that by copying my xorg.conf and paste the content back in if this happened would have fixed it, but it didn't. So here I go again, banging my head against the wall because i f@ked up!

---

