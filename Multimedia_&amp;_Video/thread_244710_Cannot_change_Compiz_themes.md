---
title: "Cannot change Compiz themes"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by Clark Nova on 2006-08-26
I've finally managed to install Compiz and Xgl on my system (yay me!) but I cannot get any themes that I download for Compiz to work. I open "CGWD Themer" from System > Preferences and I have imported the themes that I downloaded from Gnome-Look.org but when I click on them nothing happens. There is no button to "apply" the theme either so I'm a bit puzzled why it's not working.

Can anybody tell me what I'm doing wrong?](*,) 

Thanks

---

### Post by Clark Nova on 2006-08-26
Ok, perhaps this is my problem:

> simon@simon-desktop:~$ sudo apt-get install cgwd-themes
Reading package lists... Done
Building dependency tree... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  cgwd: Depends: compiz-plugins (>= 0.2) but it is not going to be installedor
                 compiz-vanilla but it is not going to be installed
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins (>= 0.6) but it is not going to be installed
  compiz-gnome: Depends: compiz (= 0.0.2-4ubuntu2) but 0.0.13.40-0ubuntu1 is to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
simon@simon-desktop:~$






I don't have all of the packages installed correctly? What do I need to do to get this working?

Thanks](*,)

---

### Post by lozenge on 2006-08-26
> **Clark Nova said:**
> I've finally managed to install Compiz and Xgl on my system (yay me!) but I cannot get any themes that I download for Compiz to work. I open "CGWD Themer" from System > Preferences and I have imported the themes that I downloaded from Gnome-Look.org but when I click on them nothing happens. There is no button to "apply" the theme either so I'm a bit puzzled why it's not working.

Can anybody tell me what I'm doing wrong?](*,) 

Thanks

I have the same problem. I have no idea how to apply the themes.

---

### Post by BOBSONATOR on 2006-08-26
Wow this is so funny, im having the same exact problem.

Are we related?

---

### Post by h00s on 2006-08-26
Ok, first things first.

You need to have xgl/compiz installed from beerorkid.com/compiz.info repositories, not ubuntu.
To update compiz from this sources, add this to your /etc/apt/sources.list
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```
Then, in terminal type:```

sudo apt-get update
sudo apt-get upgrade
```
After that done, you have to modify your compiz startup file from this:
```
#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator &
compiz --replace gconf &
```
to this:
```

#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```
Short explanation: you must have cgwd running (instead of gnome-window-decorator) to be able to change themes with cgwd-themer. But, to be able run cgwd you must have installed latest version of compiz/xgl.

---

### Post by BOBSONATOR on 2006-08-26
> **h00s said:**
> 
```

#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```


Whenever i use that command, insted of the other, i get no borders on my windows.

---

### Post by h00s on 2006-08-27
> **BOBSONATOR said:**
> Whenever i use that command, insted of the other, i get no borders on my windows.
Make sure that you have all plugins listen in gconf-editor under apps -> compiz -> general -> allscreens -> options -> active_plugins in this order:
```

gconf, decoration, transset, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus

```

---

### Post by Clark Nova on 2006-08-27
> **h00s said:**
> Ok, first things first.

You need to have xgl/compiz installed from beerorkid.com/compiz.info repositories, not ubuntu.
To update compiz from this sources, add this to your /etc/apt/sources.list
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```
Then, in terminal type:```

sudo apt-get update
sudo apt-get upgrade
```
After that done, you have to modify your compiz startup file from this:
```
#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator &
compiz --replace gconf &
```
to this:
```

#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```
Short explanation: you must have cgwd running (instead of gnome-window-decorator) to be able to change themes with cgwd-themer. But, to be able run cgwd you must have installed latest version of compiz/xgl.

Great, thanks very much! I just need to know where I can find my Compiz startup file so I can edit it now. Can anybody tell me the path to this file?

Thanks:D

---

### Post by h00s on 2006-08-27
> **Clark Nova said:**
> Great, thanks very much! I just need to know where I can find my Compiz startup file so I can edit it now. Can anybody tell me the path to this file?

Most often way of running compiz is to define it in session startup programs.
Go to menu System -> Preferences -> Sessions and select startup programs.
There should be some programs listed like those:
```

update-notifier
gnome-power-manager
gnome-volume-manager --sm-disable
**/usr/bin/startcompiz**

```
Now you see that you must modify /usr/bin/startcompiz file to be able run cgwd.
Note: maybe you dont have a script that run compiz, instead gnome-window-decorator/cgwd is running direct from 'startup programs'. That's not good. Better solution is to create a custom script (like /usr/bin/startcompiz) with this contents:
```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```
I hope this help :)

---

### Post by Clark Nova on 2006-08-28
> **h00s said:**
> Most often way of running compiz is to define it in session startup programs.
Go to menu System -> Preferences -> Sessions and select startup programs.
There should be some programs listed like those:
```

update-notifier
gnome-power-manager
gnome-volume-manager --sm-disable
**/usr/bin/startcompiz**

```
Now you see that you must modify /usr/bin/startcompiz file to be able run cgwd.
Note: maybe you dont have a script that run compiz, instead gnome-window-decorator/cgwd is running direct from 'startup programs'. That's not good. Better solution is to create a custom script (like /usr/bin/startcompiz) with this contents:
```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```
I hope this help :)


Thanks h00s, I have done as you said and created a custom script and placed it in my startup programs list. It has not worked however and I am still unable to change my Compiz themes. 

I do not have Compiz start automatically when I log in, instead I need to open a terminal and type "thefuture" to run it. Here is a link to the guide that I followed to get Compiz installed:

[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=thefuture]("http://www.ubuntuforums.org/showthread.php?t=131267&highlight=thefuture")

If you or anybody else could help me a bit further with this I would be really grateful :)

---

### Post by h00s on 2006-08-28
It probably didn't work because you did not chmod script to be able to run it.

Never mind, do this:
Open terminal and type:
```

sudo gedit /usr/bin/thefuture

```
Now in that file, change this:
```

gnome-window-decorator &

```
to this:
```

cgwd &

```
Run 'thefuture'.
Now it must work :-D

---

### Post by Clark Nova on 2006-08-28
Thank you so much! All is now working perfectly

:KS :KS :KS :KS :KS

---

### Post by h00s on 2006-08-28
You're welcome! :grin:

Take care,
h00s

---

### Post by Altur on 2006-08-30
Ok, I'm pretty new to Linux, I just got Compiz working on my system (fresh install) and I followed some of the instructions in this thread so I could apply themes for the fancy graphics.  I think I changed something I wasn't supposed to and altered the "thefuture" file (located in the /usr/bin folder).
Is there any way I can get someone to post the original version of the file?

Specificly, I have no bar at the top with my three buttons, and can't move any of the windows or change to another workspace.


Like I said, I'm new to linux and am slowly picking up on the command-line, but I really don't have a clue, so if there is something I can do to fix this, I wouldn't have any idea how to do it.

---

### Post by h00s on 2006-08-30
Ok, here is what you need to do:
Open terminal and type:
```

sudo gedit /usr/bin/thefuture

```
delete content and paste this in it:
```

#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator &
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

---

### Post by waldorf on 2006-08-30
I'm a bit confused.

h00s, you suggested two different things for  /usr/bin/startcompiz

#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator &
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &


and


#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &


Which one should I be using?

Thanks for taking the time to answer all these questions

---

### Post by h00s on 2006-08-30
The first one is for use when the xgl/compiz is installed from ubuntu repositories.
If xgl/compiz is installed from quinn's repository, then there's cgwd available and then you should use second script.

cgwd must be used if you want change compiz themes but it's only available thru quinn's repository, not official ubuntu.

I hope this help.

---

### Post by Altur on 2006-08-30
Thanks so much h00s, hopefully that will fix my problem, if not I can always just wipe the disk (I hope not...)

---

### Post by PriceChild on 2006-08-30
I don't use a startup script anymore... thefuture has been deleted.

If you get gnome-compiz-manager installed, you have a little cube in your notification bar to turn compiz on and off. Simple :)

It also installs a nice manager for compiz.

If you install cgwd, cgwd-themes and even cgwd-themes-extra then you will be able to use its theme manager (remember to log out and in again, starting compiz using the cube) and themes will work :)

Pricey

---

### Post by beetlejelly on 2006-09-02
hmmm... I am having the same problem. I have the little red cube icon and I have all the themes listed there but when I click on one the theme doesn't change. In my start-up list I have "/usr/bin/compiz-start," not "/usr/bin/startcompiz."

I cant find the tutorial I used to actually get cgwd working, but I know I didn't use "thefuture" method... am I making any sense?

---

### Post by DrPestilence on 2006-09-02
Yay! Im half way there, After using, second script, I have one applyed that I was looking at before a reboot... but I still cant cahnge them lol.

---

### Post by DrPestilence on 2006-09-02
Ohkay Ignore my lat post, I think it is working the way its suposed to, but it looks like a combination between compiz and the gnome teme i was using prior, is that normal? (and how does one get the truglass ththemes to go?)

Thank you in advance for taking the time, I am a total linux newb, but rreeaallyy want to learn.

---

### Post by wislon on 2006-09-03
I've been banging my head on this for several days, I can't believe the solution was that simple! I was looking in all the wrong places!

Thanks h00s! :)

---

