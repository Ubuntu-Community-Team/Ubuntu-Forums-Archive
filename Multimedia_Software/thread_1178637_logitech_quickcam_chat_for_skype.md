---
title: "logitech quickcam chat for skype"
date: 2009-06-04
forum: Multimedia Software
---

### Post by oddstuff on 2009-06-04
I read through the related forum posts on this subject but I am still not able to get this webcam working properly with Skype. When I attempt to configure and then test the video in the Skype options, I only see a a green static video. The camera works fine with Cheese and Ekiga. Has anyone managed to get this webcam working properly with Skype and Intrepid? My specific set-up is as follows:

  - [Gnome] Ubuntu release 8.10 (intrepid) with the 2.6.27 kernel
  - Logitech QuickCam chat webcam
  - Skype version 2.0.0.72

---

### Post by Claus7 on 2009-06-04
Hello,

what actually did you try to configure the camera with skype? Since it is working with the other programs you say, then your camera is recognized by ubuntu. So may the famous command:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

might work to you as well.

Regards!

---

### Post by oddstuff on 2009-06-05
Yes ... this command worked! :D I now see video (at least in the test window inside "Options")

Claus7, much appreciated.

So, is there a way to add this PRELOAD command into the launcher in the menu?

---

### Post by d3k4y on 2009-06-12
There is some info on the preload string at [http://hacktivision.com/index.php/2009/06/11/ubuntu-webcam?blog=2]("http://hacktivision.com/index.php/2009/06/11/ubuntu-webcam?blog=2").  Basically, in the launcher, put your export command; webcam app command

---

### Post by spnoe on 2009-11-07
> **d3k4y said:**
> There is some info on the preload string at [http://hacktivision.com/index.php/2009/06/11/ubuntu-webcam?blog=2]("http://hacktivision.com/index.php/2009/06/11/ubuntu-webcam?blog=2").  Basically, in the launcher, put your export command; webcam app command

Could someone inform me how I enter and apply the command as described in this thread in simple terms as I do not understand how I can get the video to work in Skype automaticly. I have tried the command via the terminal and it works with skype but not automaticly.

Help appreciated.
Thanks,
Steve

---

### Post by Jefferythewind on 2009-11-15
Yeah, i am wondering the same thing.

---

### Post by RonaldP3 on 2009-11-16
Same here!

Skype works when running the "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" command in the terminal but when I change the commandline of the starter in my panel from "skype" to "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" I get an error message which says that the file or folder does not exist.

Thanks for the help thusfar!

Ronald

---

### Post by budmaester on 2009-12-04
I am a nube, which config file do you load the cammand and how do I find it?

---

### Post by onetwothreecool on 2009-12-08
i can see only green wave like things. Could someone help me with this? and about the command, i find a file called v4l1compat.so Is that what is needed?

---

### Post by RonaldP3 on 2009-12-16
If you want the webcam to work automatically every time you start skype, below are the steps that worked for me:


[LIST=1]
[*]On your desktop right click and open a new file
[*]Paste ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
``` into the file
[*]Save the file as "SkypeWebcam", and close it.
[*]Right click the new document and make it executable (click properties, and choose the "rights" tab, tick the box to make it executable)
[*]Open a terminal window
[*]Move the new file to a location accessible to everybody by the following command: ```
sudo cp /home/ronald/Desktop/SkypeWebcam /SkypeWebcam
``` **Obs. Change my name into yours! **And I don't run an English version of Ubuntu, so "Desktop" might be spelled "desktop" instead.
[*]Right click on the skype starter, select properties and change the command line to: ```
/SkypeWebcam
```
[*]Now, skype should run with webcam automatically when clicked
[*]You can delete the "Skypewebcam" file on your desktop
[/LIST]
If you don't have a skype starter, you can make one by selecting the skype icon in the Applications 'list' and right click it to make a starter

---

### Post by sa-mejia on 2010-01-24
A quite simpler solution is the following:

Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Santiago.

P.D. The tip was taken from [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by hari1986 on 2011-02-01
Alternatively, you can edit the ~/.bashrc file

add

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

at the end of the file.

$source .bashrc

and skype will work without writing the particular command again and again

---

