---
title: "system logs out on video playback"
date: 2011-04-29
forum: Multimedia Software
---

### Post by wjb361 on 2011-04-29
hi i just updated to 11.04 and now my system logs out every time i play a video file plz help me out this never happened to me b4

---

### Post by wjb361 on 2011-04-29
plz help i have been using ubuntu for a year now this never happened

---

### Post by briankachelman on 2011-04-29
I am having the same problem.  I have tried VLC Mplayer and others.  When I try to maximize or hit any menu button my system logs out.  Any help here would be nice.  I'm having to dual boot for now and use xubuntu 10.10 for any vid playback, just cause it is light.

---

### Post by Ventricle on 2011-04-30
having the same problem,hope this gets solved soon

---

### Post by princeofmugs on 2011-05-01
same problem - updated from 10.04 to 10.10 nutty narwhal... and now video is broken.  using any media player, i can open a video file, plays briefly, then logs me out.  happens automatically if i try to do anything like go fullscreen or use a menu.
driving me batty - as this pc is mostly being used for video watching for kids!  should i downgrade back to 10.04, or is there a fix about?

using a via embedded mb, not sure of the video chipset exactly...

---

### Post by Natalio on 2011-05-01
I'm having the same problem! Googled it up a little bit but came up with nothing. Any suggestions?

---

### Post by kai_kan on 2011-05-02
Had this problem since the Natty upgrade, too, but it miraculously fixed itself. Still can't watch videos fullscreen with VLC (I can with MPlayer), but I just get a black screen without a sign out. 

Have we anything else in common? I've an ATI graphics card.

---

### Post by princeofmugs on 2011-05-03
i ran the upgrade manager today in the hopes of a fix, but no such luck.  both Mplayer and VLC are failing, as soon as i try to touch a menu or go fullscreen...
think it might be time to downgrade....

---

### Post by RangoTheClown on 2011-05-03
I'm having the same problem and this is rather annoying.

---

### Post by tails29 on 2011-05-04
My brother has the same problem, when i installed Ubuntu 10.10 on his PC and it's continued into 11.04 but my pc is ok. strange gremlins are afoot lol.

---

### Post by confusedubuntite on 2011-05-04
Me too. Fine on 10.10, I did a clean install of 11.04 and it crashes back to the login sreen every time I move/resize a video. Graphics card is an integrated S3/VIA Unichrome KM400, so its not an ATI bug.
 
My GUI is 'Ubuntu classic' which I assume is Gnome as it looks pretty much the same as 10.10.
 
Help!

---

### Post by jayantpd on 2011-05-05
The same problem here. I rebooted the system and login with failsafeX option (with low graphics), and the video played without logging out.
It seems the problem is with integrated S3/VIA Unichrome KM400 Graphic card, as on my system.
However, myself a newbie, and less knowledge of ubuntu, just use graphical version, and very happy with it.
Should i fall back to ubuntu 10.10 .....

---

### Post by confusedubuntite on 2011-05-05
I don't think it's the S3 KM400, as someone earlier said they had the same problem with an ATI card.
 
However I have given up and gone back to a nice stable 10.10!

---

### Post by tails29 on 2011-05-05
surely there has to be a simple solution to this problem

---

### Post by Yellow Pasque on 2011-05-05
You might want to look at ~/.xsession-errors to see what the deal is.

---

### Post by jayantpd on 2011-05-05
Don't know how much i am correct, but, resolved the problem changing the output video driver to x11 in the following manner:
1. smplayer: Options --> Preferances--> Video --> Output Driver --> x11(slow)
2. vlc: Tools --> Preferences --> Video --> UNCHECKED Accelerated Video Output
Now the Videos are playing on FULL-SCREEN without logging off.

I did not find a way to configure Totem movie player but one can disable the default output that is causing the problem as a workaround by doing the following.

1. Right click "Applications" on the top panel.
2. Select "Edit Menus"
3. Select "Preferences" under the Menu section on the left side.
4. Select "Multimedia Systems Selector" on the right side.
5. Click close.
6. On the panel, click "System", "Preferences" and then "Multimedia Systems Selector".
7. Click the "Video" tab.
8. From the "Plugin" dropdown, select "X Window System (No XV)"
9. Click close.

Logoff and then login.

Enjoy Fullscreen video in Totem and other players and Firefox. :-)

---

### Post by sevic33 on 2011-05-12
thanks jayantpd,work for me on vlc player :)

---

### Post by firekage on 2012-06-22
Sorry for refreshing but i have similar problem using nvidia binary drivers. As soon as i run smplayer by clicking on it Ubuntu logs out and i'm at login screen. I can play movies trough terminal in smplayer but not by clicking on it.

I don't understand because funny thing is that i used, for an example, 280.13 drivers from nVidia while standard ubuntu drivers with the same number but installed via sudo apt-get install nvidia-current works fine! This happens on all nvidia binary drivers under Ubuntu 11.10 with GTX260.

Can somebody help me? I can't run smplayer and switch something in it because as soon as i run it than Ubuntu logs out. Also, i tried to run Unity in 2d with this drivers but as soon as i clicked for anything than Ubuntu also logs out.

---

