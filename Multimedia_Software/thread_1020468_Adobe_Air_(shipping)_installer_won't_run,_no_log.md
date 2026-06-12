---
title: "Adobe Air (shipping) installer won't run, no log"
date: 2008-12-24
forum: Multimedia Software
---

### Post by secdroid on 2008-12-24
Posted similar on Adobe's Air user-to-user forum.  No response.

Trying to install shipping version of Air for Linux on 32 bit Ubuntu 8.10 (Intrepid Ibex) with Gnome. Placed .bin file in home directory, added a+x permissions to .bin, created empty .airinstall.log (with a+w permissions) in home, sudo su (plus pw -- now running as root), ./AdobeAIRInstaller.bin in a terminal (with home as current dir).

What happens is that cursor disappears for 20-30 seconds, there is a blink in the terminal window, and then the cursor comes back. There is an extremely brief appearance of *something* small on the desktop and then it is gone.  No message in the terminal and the airinstall.log is 0 length. No content in /opt. Tried removing .bin suffix and same result.

root@asrock-intrepid:/home/testuser# whoami
root
root@asrock-intrepid:/home/testuser# ls -l .airinstall.log
-rw-rw-rw- 1 root root 0 2008-12-23 15:58 .airinstall.log
root@asrock-intrepid:/home/testuser# ls -l AdobeAIRInstaller.bin
-rwxr-xr-x 1 root root 13553300 2008-12-23 16:04 AdobeAIRInstaller.bin
root@asrock-intrepid:/home/testuser# ./AdobeAIRInstaller.bin
root@asrock-intrepid:/home/testuser# ls -l .airinstall.log
-rw-rw-rw- 1 root root 0 2008-12-23 15:58 .airinstall.log 

FWIW, processor is AMD Duron, but should run anything a PIII can...

Any suggestions on how to troubleshoot? 

***

Is it my imagination or are Ubuntu upgrades more problemmatic than fresh installs?  My 8.10 upgrade is much less solid than my 8.04.1 clean install on the same hardware.  The consensus of the reviews of 8.10 are quite positive, so my experiences don't seem typical.

---

### Post by albandy on 2008-12-24
Don't do sudo su, it's possible that the installer can't locate your display.

I've installed it this way:
chmod 755 AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin

and disable the visual effects (Some java applications don't work well with them enabled)

---

### Post by liquidfunk on 2008-12-24
All I did was right click, "Allow Executing File As Program", then just double clicked it. 

 I'm running on Fedora though :)

---

### Post by secdroid on 2008-12-24
Thanks for the replies, albandy and liquidfunk.

Tried albandy's suggestion and got exactly the same result -- no installer app GUI and zero length .airinstall.log.

What you both said tracks with the posts I've googled.  In fact, I haven't seen any other posts with a problem like mine.  When permission is set correctly, there doesn't seem to be any problem invoking the Adobe Air installer on any supported distro.  I'm just "lucky."  :rolleyes:

I'm kind of disappointed that the installer will run and die without any message, return code, or log entry.  Really makes troubleshooting challenging.

---

### Post by secdroid on 2008-12-24
Did a bit of testing.  Fresh 8.10 install on a test partition of the same box, using Alternate-I386.  Update all and reboot.  Tried install of Adobe Air on this partition and got exactly the same result.  I give up.

FWIW, I also tested for a Firefox glitch that I had with my regular (dist upgraded) 8.10 partition.  Not present in the test partition.

Suspect that Upgrade is not always a safe option.  Googled that point and found a number of folks who have had issues with Ubuntu and Debian upgrade installs.

What I've learned from 8.10 --
[LIST]
[*]Don't upgrade the distro; do a fresh install
[*]8.10 works well for many, but definitely not for all (forum posts & blogs)
[*]Never use the desktop CD to install, due to video detect issues (me and many others; still need to edit xorg.conf)
[*]Alternate CD installations are better, but still quite bloated (YMMV)
[*]Time to learn how to do minimal Gnome installs manually
[/LIST]

---

### Post by brundlelinux on 2008-12-25
I was having similar issues as Secdroid getting AIR installed so I could use Tweetdeck.  It would *look* like it was giving me the EULA screen for about a nanosecond and then fatal crash.

I used Albandy's suggestion and did the chmod and it worked perfectly.  I'm using Ubuntu Ibex, FWIW.

As a sidenote off-thread... I too had issues with doing the distro update from 8.04 to 8.10.  It was more buggy than a New Orleans night in July.  From a clean install, slick as can be.  

Just my two cents.

---

### Post by xc3RnbFO8P on 2008-12-25
Here is another howto.([http://www.sizlopedia.com/2008/04/06/how-to-install-adobe-air-on-ubuntu/](http://www.sizlopedia.com/2008/04/06/how-to-install-adobe-air-on-ubuntu/))
> Adobe Technologies released the Linux version of Adobe AIR some weeks ago which brings web applications
and widgets to your desktop. Installing new applications on a Linux distribution is always a mystery for newbies so here is a guide that teaches you how to install Adobe AIR on Ubuntu.

   1. Open the Terminal
   2. Download the file from here using the wget command:
     wget [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)
   3. The name of the file is adobeair_linux_a1_033108.bin
   4. Save the file in the Home folder (Places > Home Folder)
   5. Run this command:
      chmod +x adobeair_linux_a1_033108.bin
   6. Now run this command:
      sudo ./adobeair_linux_a1_033108.bin

The normal installer will open, install it. From now whenever you download a .air file, just double click it and it will be installed.

---

