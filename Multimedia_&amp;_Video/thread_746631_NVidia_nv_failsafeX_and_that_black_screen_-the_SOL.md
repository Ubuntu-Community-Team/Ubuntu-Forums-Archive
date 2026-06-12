---
title: "NVidia nv failsafeX and that black screen -the SOLUTION"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by otchie1 on 2008-04-05
Two days this has taken, outstanding way to waste my time. I even formatted my Feisty and installed Heron to try to get out of this.

NVidia GeForce7600GS with HannsG 1440x900 LCD panel conected via VGA cable& DVI->VGA adapter (that isn't important BTW, the card doesn't have a VGA out, just two DVIs).

Nvidia 169.12

This refers to you if you can boot just fine using 'nv' in the xorg.conf but whenever you use 'nvidia' you get a black screen.

I tried the rstricted drivers thingy, manual installation, nvidia-settings auto update & envy....turns out it doesn't matter which method you use, just get nvidia somehow.

So, either use nv or drop into recovery mode. I use recovery so I 'vi' but you could just as easily use gedit in an nv environment

First thing DISABLE THE FAILSAFE BULLETPROOFX NONSENSE - all that does is run X from a failsafe xorg.conf_failsafe that is no help to you at all.
Open up the file /etc/gdm/gdm.conf as root,

```
sudo vi /etc/gdm/gdm.conf
```

and comment out (add #) the line,

```
FailSafeXServer=/etc/gdm/failsafeXServer
```

Now if you make a typo in your xorg.conf you'll get a really useful output from X telling where it chokes......why would you NOT want that?

Second job is to edit your xorg.conf. As root,

```
sudo vi /etc/X11/xorg.conf
```

Scroll down through the file and see if there is an 'xinemera' or 'twinview' junk in there. If there is and you don't have two monitors then either nvidia-settings or maybe Ubuntu itself added stuff you didn't ask for. Make very sure that Section "ServerLayout" there isn't pointing X to something called Screen0 when you want it to go to Screen.

My money is on a snaffu from Nvidia as a new version of nvidia-setting came out last month and I never had this trouble before.

Read it carefully..ServerLayout references a Screen.....Screen names a Device & a Monitor...make sure they are all accurate and haven't been changed.

Lastly, the magic, in the Device section that references the graphics card that you are using (the one with 'nvidia', add the line,

```
Option "ConnectedMonitor" "CRT"
```

I know, you have a DPF but all I can say is that without the above line your nvidia graphics card will decide that nothing is connected and you'll have a black screen.

I can reliably comment out that line and reproduce the blackscreen everytime...uncommenting it lets me boot.

---

