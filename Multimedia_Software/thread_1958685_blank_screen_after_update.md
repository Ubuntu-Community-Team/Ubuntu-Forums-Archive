---
title: "blank screen after update"
date: 2012-04-14
forum: Multimedia Software
---

### Post by wvff525 on 2012-04-14
Hi everyone, I'm new to the forum and new to ubuntu as well. Last night the update manager had 2 updates and I installed them. Unfortunatly I didn't pay attention to what the updates were but I think they were for the graphics card. I restarted the computer after the updates and noticed the icons and side bar was missing and the computer was really slow. I did some reading and decided to remove the drivers using this command from terminal "sudo apt-get purge nvidia*". This solved my problem and everything worked as normal except for a game I play wouldn't load. I then went to the driver updates and activated the nividia binary xorg driver for GeForce series 6 or newer cards. After rebooting all I get after the bios is a black screen. I'm not sure how to solve this problem. I was reading about recovery and holding the shift key during boot, but this did nothing for me. My system specs: amd fx quad core with 8 Gb ram and a gigabyte M68MT-S2 motherboard integrated  with the nvidia GeForce 7025/ NForce 630a chipset. I am running Ubuntu 11.10.  Any help would be greatly appreciated.

---

### Post by rhss6-2011 on 2012-04-14
When you are at the blank screen press CTRL+ALT+F1 for a terminal login. Then login using your user (lowercase - don't forget) and press enter - Linux will then ask you to enter your password.
Do that (even if it doesn't show any stars or anything) press enter and you'll login.

After you've done that:

sudo apt-get install ubuntu-desktop

Assuming your desktop is gone this will re-install it...

Cheers

---

### Post by kc1di on 2012-04-14
hi do what rhss6-2011 says except instead of ubuntu-desktop install the following driver  xserver-xorg-video-nouveau

reboot that should get you back to a desktop.  Then we will go from there to restore resolutions etc.

---

### Post by wvff525 on 2012-04-14
ok sorry, I should have clarified the black screen a little better. The monitor is not getting any input from the graphics card at all. After it goes through the bios it goes black like in standby mode. I did try the ctrl+ alt+ f1...but it did nothing. I have a pendrive with ubuntu 11.10 installed on it and I'm currently running on that. i can mount my file system on the hard drive and see all the files. Is there any way to run the terminal and switch it to my hard drive file system so the sudo commands are working on them instead of what is on my pendrive?

---

### Post by kc1di on 2012-04-14
> **wvff525 said:**
> ok sorry, I should have clarified the black screen a little better. The monitor is not getting any input from the graphics card at all. After it goes through the bios it goes black like in standby mode. I did try the ctrl+ alt+ f1...but it did nothing. I have a pendrive with ubuntu 11.10 installed on it and I'm currently running on that. i can mount my file system on the hard drive and see all the files. Is there any way to run the terminal and switch it to my hard drive file system so the sudo commands are working on them instead of what is on my pendrive?
At this point I would use the usb drive to save any important files you may want to save them reinstall.

---

### Post by wvff525 on 2012-04-14
I was afraid of that. I just tried to reinstall from the usb and keep all my files and settings and it didn't work.:( I can do a clean install but I'm going to loose around 20gb of music and 30 to 40 gb of game files. I just don't have a way to back up that much data. My largest usb is 8gb. I think I should invest in an external hard drive. 
Which graphic driver should I install for my system? There was a list of 6 or 7 of them. I installed the one that said for geforce series 6 or newer.

---

### Post by Dscottmc7 on 2012-04-15
Had the same problem. I used the Live CD to backup all of my files to another drive...shutdown , turned that drive OFF.  Booted with Live CD (**Precise 12.4**).
I had manually partitioned the drive brilliantly (read, "stupidly") so I chose to "use the entire disk" and reformat.
Shutdown, then connected all HDDs and rebooted.
Everything worked like clockwork until I decided to install the AMD/ATI Proprietary Drivers.  --***CRASH***--bit time![http://ubuntuforums.org/images/icons/icon13.gif](http://ubuntuforums.org/images/icons/icon13.gif)
If anyone has this problem, I found that I (?) could not install the Prop drivers...so the following:
Ctr>Alt>"t" to terminal if in X mode or root if command line.

$ sudo jockey -e
(or sudo jockey -l) to list the recognized drivers.  In my case:
"none" so I rebooted to the Recovery Menu. 
Enable "Network" (scroll down and enter.) if you don't go back click "Ctr-d".

Scroll to "Root"
code:
$ rm xorg.conf
$ apt-get install fglrx
reboot
Once both screens are live go to "Settings" and click on "Display"
You see both of your displays.  

Click "ON" for each.  Two (2) things to note:
 1.  Check the **resolution** for each one.  Normally you'll want this to be the same setting for each monitor.  However I have a 1920x1200 ("24" DIV) and a 1920x1080 (23" HDMI) so I have each monitor configured to its **maximum resolution**.  Be careful, however, with that setup as when you drag a folder/file from the larger screen to the lessor it can get "stuck" (bothersome...but if so, just double click to get it back).
2. I chose my Left (Acer) Monitor for my "Launcher Placement."  This gives a full wide screen display and the icons only show on the far left (Acer) ...Hope this helps.  Me?  I'm smiling!
[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

### Post by kc1di on 2012-04-15
> **wvff525 said:**
> I was afraid of that. I just tried to reinstall from the usb and keep all my files and settings and it didn't work.:( I can do a clean install but I'm going to loose around 20gb of music and 30 to 40 gb of game files. I just don't have a way to back up that much data. My largest usb is 8gb. I think I should invest in an external hard drive. 
Which graphic driver should I install for my system? There was a list of 6 or 7 of them. I installed the one that said for geforce series 6 or newer.
with your card Nvidia current should work OK also the open source drivers should work. 
After install if the system does not automatically offer you the Additional drivers set up go to System tool additional drivers and it should find your card and offer you Nvidia current as an option.
(Note before re-install I would partion my HD. so you have a seperate /home partition that way if you ever need to re-install again you won't have to loose all your data. 
you can follow the guide on this page to set up your /home Partition.
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")
Note: Ubuntu One makes a good place to back up some files that way there always available. I also use Dropbox for some.

---

### Post by wvff525 on 2012-04-15
I tried making a new partition before the clean install and moving my data to that partition while I was still running off the usb drive. It created the partition but said I didn't have permission to move my files. I got frustrated and just did the clean install. 
I still have driver issues with my card....after the clean install it comes up fine running the nvidia generic driver. When I go to additional drivers and install one and reboot it comes up again with the black screen. The first driver I tried was the nvidia-current, which was recommended....it didn't work. After another clean install I tried the nvidia-current-updates....same issue. This is clean install #3 I'm on currently and I'm almost afraid to try again...lol. The only ones left are nvidia-96 or nvidia-173 or going directly to Nvidia website and downloading their driver. I'm thinking real hard about the latter one.

---

