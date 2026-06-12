---
title: "Sudo / X Server help"
date: 2006-04-18
forum: Multimedia &amp; Video
---

### Post by Thaeos on 2006-04-18
After installing ubuntu I got the error 'Failed to start the X Server' etc and so I try to run:

"sudo dpkg-reconfigure xserver-xorg"

to set up the vesa thing but i get the error message "unable to lookup ubuntu in gethostbyname()" and I have no clue what this means.

Any help would be appreciated ... I was thinking I should just reinstall but If I don't have to that would be good ...

Also I had the same error with x-server when running the live cd but i got around it by running it in expert mode and stopping it from auto-detecting the video hardware, and telling it to use the nv drivers (or vesa) ... but when installing in expert mode no such option to disable auto-detection of video hardware came up, so yeah.

---

### Post by Sutekh on 2006-04-18
If you did an expert install (not a good idea) you may have issues with using sudo. 

I presume that when you installed you specified a root password?

You can probably get the reconfigure command working by using
```
su <enter the root password>
dpkg-reconfigure xserver-xorg
```
Then you will need to determine how to fix the sudo problem.  I believe it involves editing the /etc/sudoers file, but I have no experience doing this.

---

### Post by Thaeos on 2006-04-19
Well I thought that if you choose the normal installation it overwrites everything on your disk and is pretty much automated ... it has a warning to this effect on the inside of the cardboard cd holder things I got in the mail anyway. As I had a dual boot system running Windows XP and PCLinuxOS I didn't want it to just overwrite everything, but only to replace PCLinuxOS. That's why I chose expert installation as it lets you configure the partitions.

Anyway I reinstalled Ubuntu using expert installation and it produced the same error as expected when trying to start, but this time when running the

"sudo dpkg-reconfigure xserver-xorg"

command it recognised it and seemed to work, but it just didn't do anything. So I logged out and logged in as root and ran 

"dpkg-reconfigure xserver-xorg"

without the "sudo" bit at the front and it worked perfectly, and I am currently writing this in Ubuntu using the nv driver selection. I assume the sudo not working is because there actually is a root account, created in the expert installation. Currently when running programs that require the root account/password as a normal user, the programs don't actually work or even start after entering the password, but if I log out and then log in as root they do work.

I would rather use Ubuntu with the Sudo feature working, and not have to actually log into the root account whenever I need to change something, but as far as I can tell using the normal install will mess up my dual boot system as it will overwrite everything. At least this is the impression I get ... can anybody clarify this for me?

Cheers.

---

### Post by Jason_25 on 2006-04-19
If you choose to reinstall, when the partitioner starts, choose 'manually edit partition table' to choose the partition to install to, making sure none of your other partitions get overwritten.

---

### Post by Thaeos on 2006-04-19
[QUOTE=Jason_25]If you choose to reinstall, when the partitioner starts, choose 'manually edit partition table' to choose the partition to install to, making sure none of your other partitions get overwritten.[/QUOTE]
So this is in the normal install, not expert?

This post is pretty much to say that the x-server error (that is solved by reconfiguring the graphics adapter) could be easily avoided and would save lots of posts that are essentially the same on these forums. All that is needed is for the install to ask the user to configure it rather than detect it automatically, or if the x-server doesn't work after installation then immediately prompt the user to reconfigure.

I had the same error with the x-server not starting when installing PCLinuxOS, but it was no problem as it immediately allowed me to select the correct adapter - either that or during the install (which Ubuntu doesn't allow you to do even in expert mode), I don't remember which it was.

---

### Post by xenmax on 2006-04-19
If you want to fix your expert install to allow sudo access for norman user account, this thread should help:
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)

Some might suggest a re-install in normal mode - that is up to you to decide. I have kept my expert install, but after sudo was fixed for normal user, i only use that.

---

### Post by Thaeos on 2006-04-19
Thanks alot, that got it sorted in no time :)

---

### Post by pedstunite on 2006-05-22
[QUOTE=Thaeos]Thanks alot, that got it sorted in no time :)[/QUOTE]

i had the same problem...just re-installed using normal instead of expert mode, and it fixed lots of problems I had.  However, now I can't boot the graphical user interface.  When I try sudo dpkg-reconfigure xserver.org, it says that xserver.org is not installed and no info is available.

do I have to reinstall (for the 4th time!!), or is there something else I can do to get the graphics working?

---

### Post by Jason_25 on 2006-05-22
Reinstalling won't fix your problems.  Your syntax is wrong first of all.  What is your exact problem?

---

