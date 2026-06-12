---
title: "Web Cam bios not saving"
date: 2010-02-17
forum: Multimedia Software
---

### Post by squigglytail on 2010-02-17
I've got an Asus Eee 1005 running Eeebuntu. I can't seem to get the web cam to enable in the bios. I can go into the bios and change the status to Enabled, then I hit F10 to save and exit. Then allow the computer to start up. When I go into Cheese to test the camera it says that the Web Cam is not found. I shutdown the computer and go back into the bios and the Web Cam is disabled again! Any ideas why it is not saving my status change in the bios?


I just followed these instructions found here: [http://wiki.eeeuser.com/howto:controlcamera](http://wiki.eeeuser.com/howto:controlcamera)

 [Open a terminal window]("http://wiki.eeeuser.com/howto:openaterminal") and run the following commands: 
 sudo bash
cd /usr/bin
wget [http://berkus.madfire.net/eeecamtray.gz](http://berkus.madfire.net/eeecamtray.gz)
gunzip eeecamtray.gz
chmod +x eeecamtray
./eeecamtray   At this point, a small camera icon should appear in your task tray. (*if you running in Ubuntu instead of the default Xandros, it will require installing a library, see below*)  The icon in the task tray will either show up as green for enabled or red for disabled. To make sure everything works, right-click on the icon and select either Enable camera or Disable camera a few times. You should see messages in the terminal window similar to the lines below. 



===


When I go to the icon to enable the camera, my terminal says: Trying to read camera status. **failed to open control file

---

### Post by no2498 on 2010-02-17
stay out of the bios

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button

get programs ( cheese and wxcam )

get an load ( gstreamer ) if you need to

1 of the 2 programs will see your cam

---

