---
title: "Broadcom BCM4311/11.10/Dell Latitude D620 help"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by Kalantir on 2012-04-27
Ok, so I just installed Ubuntu 11.10 on my laptop and was disappointed to find that I could not connect to the internet with it.  Right now, my only option is to use a wireless connection.  This makes it very difficult to follow any of the instructions I have found for other people who have this same problem.  I can't apt-get anything.  The only reason I have access to the internet right now is because I am booted into Windows.

So, here's what I have done so far.  First, I added the live-cd to the repository list and installed/activated Broadcom STA Wireless Driver.  Unfortunately that didn't seem to do anything.  I rebooted my laptop and still no internet.  Then, I found this thread [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

I rebooted and went back into Ubuntu, followed the instructions and saved the output to all those commands into .txt files.  They are included in the .zip I have uploaded with this post.  If there is no file corresponding to a command listed in that thread, it is because it gave no output.

I really want to make the switch to Ubuntu, but if I can't get my wireless working, I'm going to have to continue using Windows most of the time(I'm an internet junky).

---

### Post by josephmills on 2012-04-27
Please read my post here. 


[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

also please file bug 

[http://www.youtube.com/watch?v=495V7FokwBU](http://www.youtube.com/watch?v=495V7FokwBU)

---

### Post by Kalantir on 2012-04-27
Thank you for the quick response!

So here's what I did:
I followed your instructions and found that my model number is 14e4:4311
Then I scrolled down to the sectioned titled "[B]Installing b43fwcutter with out the internet connection"
[/B]I downloaded the file you provided a link for and unpackaged it in /lib/firmware just like you said
I rebooted, and still don't have internet

Was I supposed to uninstall the Broadcom STA Wireless Driver that I got off the live-cd?

Also, the youtube link you provided seems specific for 12.04 and I am running 11.10 (I also don't know exactly what the bug is.  Is it a problem with the driver? Is it a problem with hardware detection?)

---

### Post by Kalantir on 2012-04-27
I don't know if this helps at all, but Backtrack 5 seems to have working drivers for my wireless device.  Maybe there is some way I can copy the drivers from Backtrack to Ubuntu?

---

### Post by bkratz on 2012-04-28
> **Kalantir said:**
> I don't know if this helps at all, but Backtrack 5 seems to have working drivers for my wireless device.  Maybe there is some way I can copy the drivers from Backtrack to Ubuntu?


Before all that you might want to look here.  [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)  you do need to remove the sta driver in 11.10.  The last part of the page refers to 11.10

---

### Post by Kalantir on 2012-04-28
I managed to get it working by doing a "modprobe -l | grep b43" and then "modprobe b43" after I confirmed it was there.  I'm posting from Ubuntu right now.  It sure is great to use the internet without a script blocker!

Thanks for all the help guys!

---

### Post by bkratz on 2012-04-28
> **Kalantir said:**
> I managed to get it working by doing a "modprobe -l | grep b43" and then "modprobe b43" after I confirmed it was there.  I'm posting from Ubuntu right now.  It sure is great to use the internet without a script blocker!

Thanks for all the help guys!


Glad you solved it!  Enjoy

---

### Post by Kalantir on 2012-04-28
One last thing that is worth noting in case someone else with the same exact problem finds this page...
The modprobe fix only lasts until a reboot is performed.  After a reboot, it reverts back to the Broadcom STA Wireless Driver.  After uninstalling that driver and rebooting it works flawlessly.

---

