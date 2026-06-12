---
title: "video driver for rv280 radeon 9200 se ati"
date: 2008-07-01
forum: Multimedia Software
---

### Post by broekskw on 2008-07-01
ok have been trying to get my correct driver for this card installed, have tried many guides all with not luck,some guides the commands do not work at all, last on i tried was the envy guide but now my video display on logon is in low graphic mode, can try to select the correct drive but with no luck, how do you uninstall envy, i have both envy and envyng?????

stupid me for trying to get this working:confused:

---

### Post by Melcar on 2008-07-01
The [radeon]("http://www.x.org/wiki/radeon") driver is really your only choice.  It's already included in the Ubuntu kernel so there is no need to install it, other than do some modifications to xorg.conf.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by broekskw on 2008-07-01
great and thanks will take a look but i think i tried this some time before with no luck, will this take envy of my system, as all i have is a low res screen:popcorn:

---

### Post by broekskw on 2008-07-01
still having problems, tried envyng again and keep getting this error

any thought anyone, please help:popcorn:

---

### Post by Melcar on 2008-07-01
The ATI driver (fglrx) does not support the card, so Envy will always give you problems.  Best to uninstall it.

Reconfigure X:

```
sudo dpkg-reconfigure xserver-xorg
```

When that's done edit xorg.conf:

> sudo gedit /etc/X11/xorg.conf

#Modify your Device section

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelMethod"   "XAA"
EndSection



Reboot

---

### Post by broekskw on 2008-07-01
thanks Melcar will try your way, one more question, how do you uninstall envy

tried under applications envy then uninstall with no luck,:popcorn:

---

### Post by Melcar on 2008-07-01
If you installed with Synaptic, just remove the package.

---

### Post by broekskw on 2008-07-01
no downloaded from this site and then ran the program

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

so still have no idea as to uninstall, this thing making my day very lousy :confused:

everything on my deck top and firefox is one size only and every time i minimize something i lose it, like its on a nothers screen that i can not see:confused::confused::confused:

so have to keep this one open all the time

---

### Post by broekskw on 2008-07-01
great news, some how do not know how but rebooted in recovery mode and ran some rhings on the menu from there and got my old settings back, so now good to go

so how do i see if my driver is installed (Ubuntu Hardy Heron 8.04]without screwing things up


thanks all
:popcorn:

---

### Post by Melcar on 2008-07-01
Synaptic should list it since it was a .deb package you installed.  Just search for Envy and something should pop up.  Either way, the program itself will not harm your system, so leaving it installed should be fine (even if you can't use it).
Also, when you edit your xorg.conf, you may need to add in your screen resolution under the "Screen" section, similar to this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection
```

---

### Post by Melcar on 2008-07-01
To see what driver the card is using, run "glxinfo" from the terminal.  In your case (using the radeon driver) it should say something about Mesa.  You can also run from a terminal

```
sudo lshw -C video
```

... and check what driver/module is listed.

---

### Post by broekskw on 2008-07-01
thanks Melcar will check that out, have one more question

i have onboard video and a ati card, the ati is the main one but i think the onboard one is also there because every time i minimize any screen it goes to the  rh side of my screen that i can not see, how do i check if the on board video is also there and how do i switch from one to the other? or delete the onboard one


thanks

---

### Post by Melcar on 2008-07-01
Usually one disables the onboard video in the BIOS.  Reboot your PC and enter the BIOS setup menu (how to get in depends on your board, but its usually the del key) and find the option to disable the onboard video.

---

### Post by markbuntu on 2008-07-02
If you installed the driver with envy, you can use envy to remove it. Then get the radeon driver with Synaptic. It is really important to disable the onboard video card in the bios if you are not using it.

---

### Post by broekskw on 2008-07-03
thanks again for your reply, checked 2 times in my bios and can not find my on board video controller to disable it.
in my ubuntu setup is there a comand to see if 2 displays are active

thanks again:popcorn:

---

### Post by broekskw on 2008-07-03
ok double check on the back of my motherboard and also the manual for this board, and i do not have on board video, so how come then every time i minimize my web page, or terminal page or anything it disappears, like it goes to the other screen and know way of getting them back,when this happens (all the time) i boot out of ubuntu and back into window to check out the web(window xp:confused::confused:)

hope some one has a solution to this problem:popcorn:

---

### Post by broekskw on 2008-07-03
help :popcorn:

---

### Post by OM NOM NOM on 2010-03-16
> **Melcar said:**
> The ATI driver (fglrx) does not support the card, so Envy will always give you problems. Best to uninstall it.
 
Reconfigure X:
 
```
sudo dpkg-reconfigure xserver-xorg
```
 
When that's done edit xorg.conf:
 
 
 
Reboot
 
Meclar - Realizing this post is about five years old, just wanted thank you as this worked PERFECTLy for an old P4 test box I had with a 9200 SE. So..Thanks!

---

