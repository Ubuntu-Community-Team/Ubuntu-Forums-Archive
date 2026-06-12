---
title: "HOWTO Slingbox Ubuntu 13.04"
date: 2013-06-01
forum: Multimedia Software
---

### Post by majerus on 2013-06-01
I had some troubles getting information on how to watch my slingbox on ubuntu. I was unable to get any support from Slingbox as they only support windows, android, and apple platforms. Here is how I got it to work.


1) Create a slingbox.htm file with ```
<iframe src="http://slingplayer.slingbox.com/embedded/slingplayer.php" frameborder="0" width="1440" height="900"></iframe>
``` as the contents

2)   Create a new shell script that will reference the .htm file you just created.

I created slingbox.sh in /home/USERNAME/Documents 

```

#!/bin/bash
xdg-open /home/USERNAME/Desktop/Slingbox.htm &
```

Make the .sh script executable by right clicking on it, selecting permissions tab, then select "allow executing file as a program"


2) Now create a .png file and save it to the same directory. I just googled for the slingbox logo and captured it with shutter. "Sudo apt-get install shutter" (this is a cool program)


3) Create a "slingbox.desktop" file under /user/share/applications

                      Terminal : ```
sudo touch /usr/share/applications/slingbox.desktop
```
                      Change permissions terminal : ```
sudo chmod a+x /usr/share/applications/slingbox.desktop
```

        OR 

                   GUI : Navigate to /usr/share/applications 
                                Create new text document named slingbox.desktop
                                 Right click change permissions as mentioned earlier


4) Add the following text to the slingbox.desktop file

```

[Desktop Entry]Version=1.0
Name=Slingbox
Exec=/home/USERNAME/Documents/slingbox.sh
Terminal=false
Icon=/home/USERNAME/Documents/slingbox.png
Type=Application

```


*REMEMBER TO MODIFY YOUR PATH TO YOUR USERNAME*

Reboot and you should now have a slingbox icon on your unity search, and should launch with your default web browser.


Here is a pic 


[[IMG]http://i1345.photobucket.com/albums/p677/majerus1/slingboxforumexample_zps1e6cb734.jpg[/IMG]]("http://s1345.photobucket.com/user/majerus1/media/slingboxforumexample_zps1e6cb734.jpg.html")

---

### Post by rinaldomerlo on 2013-06-21
Or just use the slingbox facebook app.

---

### Post by majerus on 2013-06-30
Had no idea that there was a facebook app. Good to know. I think understanding how to create an icon for unity is cool in general.

---

