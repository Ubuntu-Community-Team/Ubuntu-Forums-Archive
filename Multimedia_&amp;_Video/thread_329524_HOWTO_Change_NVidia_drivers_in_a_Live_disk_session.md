---
title: "HOWTO Change NVidia drivers in a Live disk session."
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by CyberCod on 2007-01-01
For people having graphical artifacts and errors in Live disk sessions due to non-compatible NVidia drivers, preventing them from installing.  For this to work, you must have dhcp enabled broadband plugged into the computer at the time, so that the live session will be able to access repositories via the internet.


	If you only have one PC, you'll need to write or print these instructions out for reference during the process.


	Boot up into Live CD desktop.  Once there, press
```
Ctrl+Alt+F5
``` 
It will give you a login prompt.  Put in ubuntu for the username and there is no password on the live disk.  Once you're logged in it  should look like ubuntu@ubuntu$ or something like that.



At this point type 
```
sudo apt-get install mined
```
and wait for it to install.

(yes i know the LiveCD comes with a command line text editor, but this one is easy to use for new people)


next step will be to type in 
```
mined /etc/apt/sources.list
```


You're gonna look for the sources that end in "restricted" and remove the # in front of them.  And then you'll need to save the file and exit mined.


Then you'll want to type in
```
sudo apt-get update
```
and wait for the repositories to refresh themselves.

Then you're gonna type in
```
sudo apt-get install nvidia-glx
```

Once that is finished, you'll type in
```
sudo nvidia-glx-config enable
```


At this point you should be able to hit CTRL+ALT+F7 and get graphical interface back up with the new drivers.  If you still have artifacts, try pressing Ctrl+Alt+Backspace to restart the GUI session.

Once you are at this point you should be able to install like normal... 

If you reboot before installing, you'll have to do all of this over again next time you load up the live disk.  


Hope this helps.


Good luck.

---

