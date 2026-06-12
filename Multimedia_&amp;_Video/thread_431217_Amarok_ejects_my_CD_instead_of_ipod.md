---
title: "Amarok ejects my CD instead of ipod"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by hatstand on 2007-05-02
Hi all, 

been to loads of the threads on ipods, kubuntu and Amarok, but this seems to be a new one.

I plug in my ipod. It appears on desktop and Amarok auto opens. I have transferred songs both back and forth. No problem and great app. 

However, when I want to eject the ipod, the right click button on the desktop icon won't let me: it says the ipod is busy. I am supposing that Amarok is still connected to it.

So I press "disconnect" in Amarok, the ipod disappears from the devices panel, but the CD drive opens.

back on the desktop, I can still access the ipod as an USB device, but there is no option to eject or "safely remove".

I'm guessing that I have to do something to Amarok to make it stop thinking my ipod lives in the CD drive.

Any ideas?

---

### Post by jonfenton on 2007-05-03
I had the same problem but unfortunately I could not find a solution. Still at least I get some exercise closing it.

---

### Post by hatstand on 2007-05-04
NOt a very useful, reply, but at least it was humourous, so, thanks!:)

---

### Post by 13thfloor on 2007-05-30
I found some help here.  [[COLOR="Blue"]http://brendonmosher.com/node/149[/COLOR]]("http://brendonmosher.com/node/149")

But it didn't quite work for me.  I ended up making a simple script based on knowing where the device was mounted instead of trying to find it with the script.  Put the script wherever you want and make it executable - I went with the original [COLOR="DarkRed"]/home/<user>/bin/amarok_eject[/COLOR] suggestion.  My iPod is auto-mounted at [COLOR="DarkRed"]/dev/sde2[/COLOR], yours may vary - make sure to change it in the script.  And I'm using KDE, not sure if that matters, maybe try 'gnome-eject' as in the original or just 'eject' instead of 'kdeeject'.  Just running the command doesn't seem to work, for some reason it does as a script.  It now is removed from the system and continues to charge.


```
#!/bin/sh
# amarok_eject

kdeeject -q /dev/sde2 && umount /dev/sde2
```

And then in the Configure window under post-disconnect command - make sure to use the proper directory

```
bash /home/[COLOR="DarkRed"]<user>[/COLOR]/bin/amarok_eject %m
```

I hope someone finds this useful.

---

### Post by tgm4883 on 2007-08-15
> **13thfloor said:**
> I found some help here.  [[COLOR="Blue"]http://brendonmosher.com/node/149[/COLOR]]("http://brendonmosher.com/node/149")

But it didn't quite work for me.  I ended up making a simple script based on knowing where the device was mounted instead of trying to find it with the script.  Put the script wherever you want and make it executable - I went with the original [COLOR="DarkRed"]/home/<user>/bin/amarok_eject[/COLOR] suggestion.  My iPod is auto-mounted at [COLOR="DarkRed"]/dev/sde2[/COLOR], yours may vary - make sure to change it in the script.  And I'm using KDE, not sure if that matters, maybe try 'gnome-eject' as in the original or just 'eject' instead of 'kdeeject'.  Just running the command doesn't seem to work, for some reason it does as a script.  It now is removed from the system and continues to charge.


```
#!/bin/sh
# amarok_eject

kdeeject -q /dev/sde2 && umount /dev/sde2
```

And then in the Configure window under post-disconnect command - make sure to use the proper directory

```
bash /home/[COLOR="DarkRed"]<user>[/COLOR]/bin/amarok_eject %m
```



I hope someone finds this useful.

Hmm, well this almost worked for me using gnome.  I altered it a little, and amarok does disconnect the ipod (disconnects it in gnome too) but says that it failed (even though it succeeded)

Here is my amarok_eject file
```
#!/bin/sh
# amarok_eject
gnome-eject -e -n -d /dev/sdf2
```


:EDIT:

I just fixed it, I removed the -n from my amarok_eject command and it now works great.  No error.  -n is the switch for no dialogs in gnome-eject.  I guess amarok needs the dialogs to know it disconnected correctly.  The ipod is auto detected in amarok, not manually configured.

Here is my amarok_eject file (/home/thomas/.scripts/amarok_eject)
```

#!/bin/sh
# amarok_eject
gnome-eject -e -d /dev/sdf2
```

and here is my post-disconnect command in amarok
```
/home/thomas/.scripts/amarok_eject
```

---

### Post by Auslegung on 2007-11-04
That sounds like it fixes the problem I'm having, the trouble is I'm a complete noob and don't know where to type 

#!/bin/sh
# amarok_eject
gnome-eject -e -d /dev/sdf2

Could someone please give me a step-by-step on doing exactly what tgm4883 said to do?  One other thing: there is no /home/<username>/bin file, though I suspect I create that file and that's where I type the above script, I'm not sure.

---

### Post by 13thfloor on 2007-11-04
> **Auslegung said:**
> That sounds like it fixes the problem I'm having, the trouble is I'm a complete noob and don't know where to type 

#!/bin/sh
# amarok_eject
gnome-eject -e -d /dev/sdf2

Could someone please give me a step-by-step on doing exactly what tgm4883 said to do?  One other thing: there is no /home/<username>/bin file, though I suspect I create that file and that's where I type the above script, I'm not sure.

1)  You type that part in the text editor of your choice - kate, gedit, etc.
2)  Save the file with a name like amarok_eject or similar - just use something that is easy for you to remember what the file does.  And you can save it anywhere you want to.  Most users will generally use their home folder or another directory within it.
3)  Make the file executable and place the script's location (including the filename itself) in the post-disconnect command text box as shown in the other comments.  For help with making a file executable try this link, [http://www.cyberciti.biz/faq/how-do-i-make-a-linux-or-freebsd-file-an-executable-file/]("http://www.cyberciti.biz/faq/how-do-i-make-a-linux-or-freebsd-file-an-executable-file/")
4)  Ask for more help if you need it, but hopefully this helps you out.

---

### Post by Auslegung on 2007-11-04
AWESOME! Thanks, you helped a lot, plus I learned a little about chmod.  Gotta love the Ubuntu community

---

### Post by BarneyRubble on 2007-11-12
tgm4883's script worked perfectly for me. Thanks a lot feller !

---

### Post by mtabholt on 2007-11-18
In the "Configure Media Device" window, under "Post-disconnect command", type:

kdeeject %m

Click OK to close this window.

%d is looking to unmount the device ( /dev/sdx ), where %m is looking to unmount the mount point.

If your /etc/fstab has allowed user to mount / unmount, then this will work fine:

/dev/sda2       /media/ipod vfat users,rw,noauto 0 0

---

### Post by iammeagain on 2007-12-27
I took the ```
gnome-eject -e -d /dev/sdf2
``` and then in Amarok went to Settings >> Configure Amarok >> Media Devices  
Then clicked on Configure Device Settings (the three little gears next to my ipod's configuration)
The pasted the command under Post-disconnect command
ejects by just clicking the disconnect button now.

EDIT: Gnome said unsafe removal once, although it doesn't seem to be doing it again. Just a heads up.

---

### Post by raycosm on 2007-12-31
> **mtabholt said:**
> In the "Configure Media Device" window, under "Post-disconnect command", type:

kdeeject %m

Click OK to close this window.

%d is looking to unmount the device ( /dev/sdx ), where %m is looking to unmount the mount point.

If your /etc/fstab has allowed user to mount / unmount, then this will work fine:

/dev/sda2       /media/ipod vfat users,rw,noauto 0 0

Hmm, not sure what anything meant cause I'm a noob, but kdeeject %m worked perfectly. (Using KDE, obviously)

Thanks

---

### Post by abhiroopb on 2008-05-13
So I finally managed to get amarok configured properly to use the iPod.

1. used this guide here to set it up so that my 80gb black classic iPod can be used ([http://ohioloco.ubuntuforums.org/sho...d.php?t=658523](http://ohioloco.ubuntuforums.org/sho...d.php?t=658523)).

2. I can connect it on amarok, I transfer music and then I update the artwork.

3. When I click disconnect (my post disconnect command is umount %d && eject %d - found it on amarok website I think) it disconnects and I can see the iPod ejecting.

4. I can browse my music without any issue including seeing the artwork.

PROBLEM:

5. When I plug the iPod back into the computer, nothing happens, absoloutely nothing.

6. Checking fdisk -l, I can see where the iPod is, and I mount it manually, I then have to delete the iPod_Control folder (actually I only have to delete the iTunes folder, but the database gets screwed up so it makes sense to delete everything), unmount the iPod and then do a hard eject (as I can't see any other way to eject the iPod properly).

7. Connect it to amarok and it connects fine, asks if I want initialize the database (as I have obviously deleted it).


This problem ONLY seems to occur if I actually add songs to the iPod. If I were to connect the iPod and then disconnect it (without adding any songs), upon reconnection it would appear fine.

This is obviously VERY annoying, as it means I can add songs once, and then have to delete everything in order to add it again!!!

Help please!

(started a new thread as my problem is slightly different: [http://ubuntuforums.org/showthread.php?p=4950066#post4950066](http://ubuntuforums.org/showthread.php?p=4950066#post4950066))

---

### Post by 13thfloor on 2008-05-13
What version of HAL are you using?

One problem I had was with HAL, and I had to downgrade to the version for Feisty to make usb devices mounts properly.

I haven't tried Kubuntu 8.04 yet...

---

### Post by abhiroopb on 2008-05-13
Not sure about HAL and I'm on gutsy

---

### Post by 13thfloor on 2008-05-13
I'm on Gusty as well and I had to downgrade to the Feisty version of HAL to get usb devices to work properly.

Your problem sounds similar to mine.  I would be able to connect the first time but subsequent connections would not work.  I can't remember what thread I found the info on, but it fixed my usb mounting problem.

---

### Post by abhiroopb on 2008-05-13
Thanks a lot for the link. I'm going to hold of using that for a while. I'd like to see if this is an iPod/amarok related bug, as it seems to be that. It sometimes works and sometimes doesn't! Basically I got it to eject properly (at least it seemed to be properly!) And then it connected. I transfered my library fine, but then it doesn't connect again! I personally don't think its a usb issue, so I'll give it a while and then try it out.

---

### Post by abhiroopb on 2008-05-15
I am begining to suspect your solution might be the answer here. My iPod sometimes connects and it sometimes does not. VERY random with no clear logical pattern as to why it is doing so. What would downgrading hal potentially do to my system? And also how would this affect my system when I decide to upgrade to hardy?

---

### Post by abhiroopb on 2008-05-15
How do I downgrade? I tried double clicking the deb and it said that a later version was installed (duh!) and when I tried to remove the current hal from synaptic way too many other important packaes was going to be uninstalled (e.g. network manager!).

---

### Post by 13thfloor on 2008-05-15
To downgrade:

1) Find the .deb file and right click on it.
2) Go to "Open With" and when it expands select KPackage - hopefully you have it installed
3) When KPackage opens select Install at the bottom
4) A new window opens and there is a checkbox to "Allow Downgrade"
5) Install it.

The only downside I have is the constant icon in the taskbar letting me know there is an updated package.

I haven't tried upgrading to Hardy yet, but I don't think it will be an issue.  Typically you upgrade all software to the latest version so hopefully the bugs have been worked out of HAL in the new version.  Otherwise I'll be putting the Feisty version right back in.

---

### Post by bushwacker on 2008-05-28
Works great here w/ 8.04 on my Dell e1505 with the latest 8GB Ipod Nano. Now all I have to do is figure out how to get amarok to actually download/set album cover images... :\

---

### Post by abhiroopb on 2008-05-28
Depending on how many songs you have I suggest you spend a bit of time and MANUALLY copy every single album cover to their folder. In the long run this is much better, as it will be the right album cover, AND it isn't dependent on Amarok.

---

### Post by creasar on 2008-05-28
Hi, I certainly agree with you. Your advice is really very helpful for us.
Thanks a lot!

---

