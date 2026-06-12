---
title: "MythTV Shutdown Button"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by wjston on 2007-02-01
I am relatively new to Linux and MythTV. I started playing with both back in the early spring because I was interested in Ubuntu as an alternative operating system to Windows. I came across a post explaining MythTV and quickly became quite intrigued with the idea of controlling what to watch on tv and being able to pause/record live tv. After months of tinkering and reinstalling, I can happily say I have two systems that are working quite well. Both systems are frontend/backend configurations.

One issue that I spent many hours researching was the ability to shut down my PVR from within MythTV. From everything that I could find using Google, it is not possible to shutdown a combined frontend/backend myth box unless one returns to the Ubuntu desktop. For the last month, I have successfully been shutting down my Ubuntu system with a "Shutdown" button that I configured in Myth's mainmenu. For anyone interested in setting up their systems to do the same I am including the steps that enabled the shutdown button to finally control my Myth pvr. As I previously mentioned, I am relatively new to linux and I am not sure whether there will be any long term problems that might arise from shutting down the computer from within MythTV - I only know that I haven't had any problems to date.

[COLOR="Blue"]Adding the Shutdown button:[/COLOR] [COLOR="Black"](it is always good to backup the original file just in case things don't end up the way they should).
As myth user: 
**$ cp /usr/share/mythtv/mainmenu.xml /usr/share/mythtv/mainmenu.xml.backup** 
**$ sudo nano /usr/share/mythtv/mainmenu.xml**[/COLOR]
[COLOR="Blue"]Add the following to the end of mainmenu.xml[/COLOR]
[B][COLOR="Black"]<button>
<type>MENU_UTILITIES_SETUP</type>
<text>Shutdown</text>
<action>EXEC ~/.mythtv/mythscript/shutdown.sh</action>
</button>[/COLOR][/B]

</mythmenu>

[COLOR="Blue"]Create mythscript directory.[/COLOR]
**[COLOR="Black"]$ mkdir ~/.mythtv/mythscript[/COLOR]**

[COLOR="Blue"]Create shutdown script.[/COLOR]
[COLOR="Black"]**$ sudo nano ~/.mythtv/mythscript/shutdown.sh**[/COLOR]
[COLOR="DimGray"]# ! /bin/bash

# This script will be used to shutdown the computer
# from within MythTV when the myth user selects
# the Shutdown button located on the mainmenu

# This script created on Jan 04 2007

# Shutdown
sudo /sbin/shutdown -h now

exit[/COLOR]

[COLOR="Blue"]Save and exit

Now we need to create a new group called "shutdown"
As Root:[/COLOR]
[COLOR="Black"][B]# groupadd shutdown
# nano /etc/group
Add "mythtv" (without quotes) to end of shutdown group[/B][/COLOR]

Then
As Root: **# visudo**
Add: **%shutdown ALL= NOPASSWD: /sbin/halt, /sbin/shutdown**

[COLOR="Blue"]## Make Script More Secure[/COLOR]
**$ sudo chgrp shutdown ~/.mythtv/mythscript/shutdown.sh**

[COLOR="Blue"]Make the script executable only for the group "shutdown"[/COLOR]
**$ sudo chmod g+x ~/.mythtv/mythscript/shutdown.sh**

[COLOR="Black"]If everything went well, you should be able to shutdown your system using the shutdown button from within MythTV. I hope this helps those individuals who have been looking to control their pvr's shutdown ablility using a remote. I hope I haven't forgotten any steps as this was over a month ago that I set this up. 

ENJOY[/COLOR]

---

### Post by josesanders on 2007-02-01
I don't want to shut down my box from within MythTV, but does anyone know if it is possible to modify this to eject DVDs from within MythTV?  As it is, the Eject Media command in MythDVD doesn't seem to do anything, and neither does the eject button on the DVD rom.  Therefore, the only way that I know of to get the thing out is to go get my mouse from my other computer, plug it into my MythTV box, and right click on the DVD and select Eject.  This is very tedious.

I'd give it a shot, but it seems to me that if it were easy, then the command that is already there would work.

---

### Post by wjston on 2007-02-01
> **josesanders said:**
> I don't want to shut down my box from within MythTV, but does anyone know if it is possible to modify this to eject DVDs from within MythTV? 
It's not necessary.
 > **josesanders said:**
> As it is, the Eject Media command in MythDVD doesn't seem to do anything, and neither does the eject button on the DVD rom.  Therefore, the only way that I know of to get the thing out is to go get my mouse from my other computer, plug it into my MythTV box, and right click on the DVD and select Eject.  This is very tedious.

I'd give it a shot, but it seems to me that if it were easy, then the command that is already there would work.

Check to see if mythtv has been added as a user in the group cdrom.
As myth user: **$ sudo nano /etc/group**

Add [COLOR="Red"]mythtv[/COLOR] to the end of the line that starts with - cdrom:x:24:haldaemon[COLOR="Red"], mythtv[/COLOR]

[COLOR="Black"]This gives MythTV permissions to control the cd/dvd drive.[/COLOR]

Also, you may want to go into (Ubuntu Desktop) **System>Preferences>Removable Drives and Media>Storage** and uncheck **Burn a CD or DVD when a blank disc is inserted** so that applications are not launched when you insert a disc - it can get very annoying having applications launch when you are in MythTV and you don't have a mouse nearby.

The only issues I have with the **Eject media** button is that I get a message box that states unable to eject disc even when it has just ejected it. I press OK, it disappears and then I press OK again and the drawer closes.

Hope this helps!

---

### Post by josesanders on 2007-02-01
I already added the mythtv user to the cdrom line, and all of the other lines where the original user is.  I'll post this as a new thread, since it's off the subject from your original post.

---

### Post by fletcherthunder on 2007-03-05
hey, thanks for the how-to!  i was just looking for this, i'm new to mythtv, and surprised that it doesn't have a shutdown function built-in.

---

### Post by wjston on 2007-03-05
> **fletcherthunder said:**
> hey, thanks for the how-to!  i was just looking for this, i'm new to mythtv, and surprised that it doesn't have a shutdown function built-in.

Apparently, if you have seperate Frontend/Backend systems, this is or can be enabled. I had a system with MythDora on it and it comes with this already set up. It took me a while to figure out how to do this without Ubuntu reporting a "Kernel Panic." I hope everything works for you.

---

### Post by Blutack on 2008-02-04
You can just change this line:
> <button>
<type>MENU_UTILITIES_SETUP</type>
<text>Shutdown</text>
<action>EXEC ~/.mythtv/mythscript/shutdown.sh</action>
</button>

To read

> <button>
<type>MENU_UTILITIES_SETUP</type>
<text>Shutdown</text>
<action>EXEC sudo shutdown -h now</action>
</button>

And add your user to the sudoers file
> 
user ALL= NOPASSWD: /sbin/shutdown


Works for me, hopefully just as secure.  If someone compromises your user account they can shutdown either way, whether you use a script or not - either way you are in the shutdown group and so can run it from the command line.

---

