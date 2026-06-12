---
title: "NVIDIA proprietary driver wont save after reboot on Biostar 7050 board"
date: 2007-11-21
forum: Mythbuntu
---

### Post by jdkoola on 2007-11-21
Equipment:
Biostar TForce 7050 Board
AMD 4000+ X2 Brisbane
OCZ Plat Rev 2, 2 GB
Belkin Wireless-G PCI
ADS Tech TV Tuner


I just installed Mythbuntu 7.10 on this setup, and it wouldn't boot off the live CD unless I used "safe graphics mode."  Fine, whatever.  So I finished installation, and then I downloaded and installed the most recent NVIDIA drivers from their website.  Everything went great.  I was able to use all the new resolutions and such.  However, when I restarted the computer I was back to square one--It popped up with an error message saying that it couldn't recognize my video card or monitor and I had to boot using "Low graphics mode."  I checked the Proprietary Driver Manager and it had the NVIDIA proprietary drivers checked already, so I unchecked and rechecked which caused it download the drivers again (this time automatically instead of me manually doing it).  I once again restarted the computer and once again it gave me the same "Can't recognize Video Card/Monitor" error.

Any insight would be appreciated.

---

### Post by superm1 on 2007-11-21
> **jdkoola said:**
> Equipment:
Biostar TForce 7050 Board
AMD 4000+ X2 Brisbane
OCZ Plat Rev 2, 2 GB
Belkin Wireless-G PCI
ADS Tech TV Tuner


I just installed Mythbuntu 7.10 on this setup, and it wouldn't boot off the live CD unless I used "safe graphics mode."  Fine, whatever.  So I finished installation, and then I downloaded and installed the most recent NVIDIA drivers from their website.  Everything went great.  I was able to use all the new resolutions and such.  However, when I restarted the computer I was back to square one--It popped up with an error message saying that it couldn't recognize my video card or monitor and I had to boot using "Low graphics mode."  I checked the Proprietary Driver Manager and it had the NVIDIA proprietary drivers checked already, so I unchecked and rechecked which caused it download the drivers again (this time automatically instead of me manually doing it).  I once again restarted the computer and once again it gave me the same "Can't recognize Video Card/Monitor" error.

Any insight would be appreciated.
Well for starters why'd you manually install the driver?  The automatic installation is there to avoid odd configuration issues that might arise from manually doing it....

---

### Post by jdkoola on 2007-11-21
Perhaps manually installing the NVIDIA drivers was a bad idea, I wouldn't know.  I wanted the latest NVIDIA drivers which were released just a couple days ago.

---

### Post by superm1 on 2007-11-21
Well if you aren't that far invested into this setup yet, I say reinstall and let the automatic installation handle things.  It will be a lot easier than trying to debug this imo.

---

### Post by subramanya1983 on 2008-03-11
i am also facing the same issue. actually, i tried installing nvidia drivers automatically.. in spite of that, i was not able to set the visual effects to "Extra". then i tried downloading and installing the driver. it worked for the first time but failed to save the settings after a restart.   i need to keep installing nvidia everytime i log in (in case i need to enjoy effects like cube, skydome etc)

---

### Post by jdkoola on 2008-03-14
hi I ended up reinstalling and simply let mythbuntu install the driver automatically; however, I didn't try turning on any extra special effects.

---

### Post by volkswagner on 2008-03-17
I was going through this at the same time.  Trying to do it without a reinstall since I had logged many hours configuring my box.

Here is what I did and my thread.  I am not sure If this will work for others.  I hope my difficult time can benefit others, before they pull all their hair out as I did.  :lolflag:


[http://ubuntuforums.org/showthread.php?t=711591]("http://ubuntuforums.org/showthread.php?t=711591")



I will try to remember all the steps I took to get my restricted drivers back.

Here is what I did, I am not sure if all or any of the following are required.

I used Envy to remove the drivers so If you don't have it installed, install it now. Don't run Envy though.

I also disabled all autostart programs(settings>autostart programs>deselect all

at the local machine (pc with driver you want to remove), stop X-server

Code:

sudo /etc/init.d/gdm stop

Create an SSH session from another machine on the LAN (this may not be required, I was not able to get a console on my machine with X-server stopped). Don't enable forward -X.

Code:

ssh username@ip

Change directory to /

Code:

cd /

Run Envy in text mode

Code:

envy -t

choose choice 6 "Clean the installation of any Nvidia drivers" (ATI choices avail also)

Code:

6

Follow an remaining steps

Restart

Code:

8


At the local machine if running in low graphics mode>select continue

Open mythbuntu control centre from the applications menu.

Go to restricted drivers, check box for enable

Restart X-server (this may need to be done on a remote machine as I did)

Code:

sudo /etc/init.d/gdm restart

Open Mythbuntu-control-centre to see if under restricted driver manager you can open Nvidia settings. If you can set your screen resolution.

If can or can't a sytem restart may be necessary.

You should have joy with restricted drivers. Don't forget to enable the autostart programs

Restart again to see if it all stayed

I hope I did not forget anything. After my one hundredth try I started to keep a log of my steps. Got tired of that after another 10-20 tries. I finally discovered these steps around try number 150

---

