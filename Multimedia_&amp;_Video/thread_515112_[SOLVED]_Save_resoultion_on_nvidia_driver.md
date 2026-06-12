---
title: "[SOLVED] Save resoultion on nvidia driver"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by idanool on 2007-08-01
Hello!

I installed restricted nvidia (gf 7600GS) driver on my ubuntu 7.04.
I changed the resolution from 640x480 to 1280x1024, and also "save to X configuration file". but each time I restart my machine it returns to 640x480 with 2 black bars (like wide screen resolution on a regular screen).
so I need to change the resolution manually each time I restart.
how can I change the resolution permanently ?

another strange thing is that once in a few restarts when I try to change the resolution I get  a messed up picture of my desktop (some fragments of the desktop on a black background) for a few seconds, then I get a black screen, that only the cursor is visible. then I can't do anything but reboot.

thanks in advance.

---

### Post by wolfen69 on 2007-08-01
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gsiliceo on 2007-08-01
You can make a script like i did using xrandr, just go to System Preferences
First open console and type 
```
xrandr
```
, it will display all the modes that your driver support, wrote down the number of the mode that you want, for example i get a list and the mode i want is
```
*0   1024 x 768    ( 321mm x 240mm )  *60   87   85   75   70 
```
In my example i can type 
```
xrandr -s 0 
```
to get my screen to 1024 x 768, or
```
xrandr -s 0 -r 85
```
where 85 is the refresh frequency.

Once you know the command to get your screen to the resolution/frequency you need to make this command automatically executed when you log in. To do this go to System - Preferences - Sessions and click New, Name: screen set (or something) and command, "xrandr -s 0 -s 85"  or whatever your command looks like.

Thats how i solved it, im sure there is a way to get your resolution and refresh freq using xorg.conf but i havent been able to do it.

---

### Post by tseliot on 2007-08-02
> **idanool said:**
> so I need to change the resolution manually each time I restart.
how can I change the resolution permanently ?


Type:
```
sudo nvidia-settings
```

set the resolution and save your settings

---

### Post by poji on 2007-08-02
hello

loving ubuntu!!

i did a clean install of ff got everything running just right :)
then i noticed that in restricted drivers manager said that:-
NVIDIA accelerated graphics driver    Not in use.
so
i checked the enable box, and it installed them.
when rebooted it got so far then the screen went blank, it had turned the off the screan bulbs on my laptop.

did dpkg-reconfigure xserver-xorg
used the vesa option and just filled in the rest as normal/default settings.
rebooted and it all works again. But, i tryed a GL screansaver and it didn't work, wer'as it was working, if a bit slow, before the glx drivers where updated.

tryed looking in the synaptic and it returned no results at all. tryed sudo apt-get install nvidia-glx, to try and find an older version to overwrite the newer.
and got:-
nvidia-glx is already the newest verson.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
so
how do i revert back to the original glx driver that was installed with the install package that i downloaded?

is it a matter of being more specific of the the driver version? 

hope someone has the answer, as i don't really want to have to start all over again, again. as the same happened on ee before, but just wanted to have the latest version, so overwrote it before trying to resolve it.

poji

---

### Post by idanool on 2007-08-03
thanks!
the problem was that I ran nvidia-settings via the menu shortcut, so it wasn't under su.
so when I tried to save the xorg.conf it didn't actually saved it, and it didn't give any error.
when I run it with sudo it was saved successfully.

---

### Post by tseliot on 2007-08-03
> **poji said:**
> hello

loving ubuntu!!

i did a clean install of ff got everything running just right :)
then i noticed that in restricted drivers manager said that:-
NVIDIA accelerated graphics driver    Not in use.
so
i checked the enable box, and it installed them.
when rebooted it got so far then the screen went blank, it had turned the off the screan bulbs on my laptop.

did dpkg-reconfigure xserver-xorg
used the vesa option and just filled in the rest as normal/default settings.
rebooted and it all works again. But, i tryed a GL screansaver and it didn't work, wer'as it was working, if a bit slow, before the glx drivers where updated.

tryed looking in the synaptic and it returned no results at all. tryed sudo apt-get install nvidia-glx, to try and find an older version to overwrite the newer.
and got:-
nvidia-glx is already the newest verson.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
so
how do i revert back to the original glx driver that was installed with the install package that i downloaded?

is it a matter of being more specific of the the driver version? 

hope someone has the answer, as i don't really want to have to start all over again, again. as the same happened on ee before, but just wanted to have the latest version, so overwrote it before trying to resolve it.

poji
What's the model of your graphic card?

---

### Post by poji on 2007-08-03
the device manager tells me it is a NV17 [GeForce4 420 Go 32M]

---

### Post by Uber Nooblett on 2007-08-03
> **tseliot said:**
> Type:
```
sudo nvidia-settings
```

set the resolution and save your settings

this worked for me :)

Just open a console, type:

gksudo nvidia-settings 

and then save, and no more issues :)

---

### Post by gsiliceo on 2007-08-05
> **Uber Nooblett said:**
> this worked for me :)

Just open a console, type:

gksudo nvidia-settings 

and then save, and no more issues :)

It didnt worked for me, i tried this and the nvidia-settings was saving a faulty xorg.conf because i couldnt boot anymore and had to do a dpkg-reconfigure xserver-xorg, thats why i used xrandr to change my settings at gnome startup.

using. NvidiaFx5200

---

### Post by Gary.M on 2007-08-07
OK, I've been suffering this too...

Freshly re-installed Kubuntu. Installed Envy and used that to install the Nvidia driver.

No matter what although I set 1280 x 960 at 85Hz when I reboot, I get 1280 x 960 at 60Hz.

Sudo nvidia-settings doesn't stick.

Doesn't seem to matter what is in xorg.conf the 60Hz one is what I get.

Then I read this message...

[http://ubuntuforums.org/showthread.php?t=518708](http://ubuntuforums.org/showthread.php?t=518708)

So I set what I want with nvidia-settings. Go into systems settings - monitor. Chose the refresh rate there that gives me 85Hz (it shows options of 50Hz and 55Hz, and the 50Hz one gives me 85Hz (the 55Hz one gives me 60Hz actual) go figure!. Anyway I settle for the 50Hz option which at least delivers what I want. Save, exit system settings. Logout, re-start X-server. Login... ta-da... I have 85Hz as I want.

Something is screwed up in Kde.

I like Linux, but gee, Windows makes this stuff so much easier. And remembers...

---

### Post by Brandon.Viking on 2007-08-10
This one has been getting me a little frustrated too.
I have everything in the config file as it should be ... also recreated via the nvidia-settings utility a dozen times ... everytime I reboot the settings do not stay.
I get the resolution ok ... but the refresh rate is 65 instead of 75Hz like I want it.
I know the files are right ... something about this nvidia-settings I dont like.

How do I make it stick?
<continues to hack away> 

BTW, options like xrandr in the sessions is not a configuration hack its a work around.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Gary.M on 2007-08-10
You're right where I was a few days ago. See my above post. Either in Gnome or KDE go into the regular system settings and screen res setup. Play with those controls (the refresh one) and see which setting gives you the refresh rate you've been trying to set. It won't report correctly though, so go by what the monitor actually is getting. Save that one. It seems that from then on Nvidia settings will be able to assert control. At least in KDE it worked for me. This is one of those things that is overlooked by the Win XP knockers... at least in XP you can just set this stuff logically... but then we will be accused of not using the Open Source driver....

---

