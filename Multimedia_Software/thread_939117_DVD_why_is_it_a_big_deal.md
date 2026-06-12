---
title: "DVD why is it a big deal?"
date: 2008-10-05
forum: Multimedia Software
---

### Post by Vertoxic on 2008-10-05
i dont understand why is it so hard to get the DVD player to work lol, anyways i have tried everything guys..

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)  <-(tried to do this)
that did not help, ive tried a few other things as well nothing seems to help..

---

### Post by nowshining on 2008-10-05
legal issues and canonical doesn't want to get sued...altho the founder could afford it... hmmm...

Besides if using totem - it won't play a DVD by default when inserting the disc, sorry and neither choosing the menu item DVD...

Have u tried browsing the disc?? is the disc mounted?? Sometimes a disc won't mount automatically and may need to manually be mounted by double clicking on the icon.. If u have not changed anything the Disc icon should appear on the desktop indicating the disc is mounted...

Alas maybe ur DVD player can't read the disc...

---

### Post by Vertoxic on 2008-10-05
> **nowshining said:**
> legal issues and canonical doesn't want to get sued...altho the founder could afford it... hmmm...

Besides if using totem - it won't play a DVD by default when inserting the disc, sorry and neither choosing the menu item DVD...

Have u tried browsing the disc?? is the disc mounted?? Sometimes a disc won't mount automatically and may need to manually be mounted by double clicking on the icon.. If u have not changed anything the Disc icon should appear on the desktop indicating the disc is mounted...

Alas maybe ur DVD player can't read the disc...
my DVD player is fine brand new laptop it worked good on vista lol, as far as opening the disc and clicking on the icons it opens the DVD and played the FBI warning list and then just stops on the screen, so i know it reads it just wont go any further!

---

### Post by nowshining on 2008-10-05
so u got the w32codecs, and the ubuntu restricted libs, etc.. installed right??

---

### Post by Vertoxic on 2008-10-05
> **nowshining said:**
> so u got the w32codecs, and the ubuntu restricted libs, etc.. installed right??
yes i do i believe so... how do i check to see if they are installed properly?

---

### Post by nowshining on 2008-10-05
look for in synaptic for ```
ubuntu-restricted-extras
``` or in a terminal do ```
sudo apt-get install ubuntu-restricted-extras
```  ur pw won't show as you type it out..

---

### Post by WWSmith36 on 2008-10-05
Install libdvdcss2 and w32 video codecs in Ubuntu 8.04 (Hardy Heron)


Add medibuntu Respository
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

Then, add the GPG Key using the following commands
```
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update

```

For i386 Users install Codecs using the following command

```
sudo apt-get install w32codecs libdvdcss2
```

For amd64 Users install Codecs using the following command

```
sudo apt-get install w64codecs libdvdcss2
```

---

### Post by Vertoxic on 2008-10-05
k im doing all this right now, what player do u guys think i should use? anyone is fine?

---

### Post by Vertoxic on 2008-10-05
ok well thank you all for help me now the DVD wors, but its very pixely what is that it looks horrible in full screen or half, i watching "office space"
anyone what this is maybe a diff DVD player would fix this?

---

### Post by minky311 on 2008-10-05
Try using vlc.

---

### Post by Vertoxic on 2008-10-05
> **minky311 said:**
> Try using vlc.
how do i install "VLC" is it in add/remove ?

---

### Post by minky311 on 2008-10-05
Yes it is. Just search for vlc.

---

### Post by haydnc on 2008-10-05
Hi Vertoxic, I guess you decided not to give up on Ubuntu and install Vista after all. Good on you.

If you run into problems installing VLC from the Add/Remove dialog you should try using Synaptic Package Manager instead. You should be able to 'find' VLC in there and select it to be installed.

---

### Post by Vertoxic on 2008-10-05
> **haydnc said:**
> Hi Vertoxic, I guess you decided not to give up on Ubuntu and install Vista after all. Good on you.

If you run into problems installing VLC from the Add/Remove dialog you should try using Synaptic Package Manager instead. You should be able to 'find' VLC in there and select it to be installed.
hehe thx yah i decided to take a deep breath and do it right, and yes im loving it my wifi works everything alsmost exept this dvd is being werd

wich one of this do i pick guys?

---

### Post by Vertoxic on 2008-10-05
sorry wrong screenshot..

---

### Post by minky311 on 2008-10-05
Install the one that says "vlc".

---

### Post by Vertoxic on 2008-10-05
> **minky311 said:**
> Install the one that says "vlc".
thx just did that and still the same way not any better... maybe i have a problem with my video card? how do i check what GPU drivers im running?

---

### Post by minky311 on 2008-10-05
Try lspci -v in the terminal.
Try this one for a gui
sudo displayconfig-gtk

---

### Post by gandaran on 2008-10-06
> **Vertoxic said:**
> thx just did that and still the same way not any better... maybe i have a problem with my video card? how do i check what GPU drivers im running?
vlc » preferences, change the video output, there are many options there, try each one until you get one that works well, xv or x11
you can also do the same for mplayer

---

