---
title: "Mythbuntu Backend ?'s"
date: 2010-04-01
forum: Mythbuntu
---

### Post by x2aws on 2010-04-01
Hi all.  I have been starting to do a complete Myth-setup (2 frontends, 1 master backend) and have a few ?'s.

I just finished up my backend install, did all my HDD's as ext4.  I have the OS on a OCZ vertex 30GB (no swap due to the 4GB of RAM) and the remainder 5 Hitachi 2TB drives as /videoX (where they would  be 1,2,3,4,5).  I go through the whole install (TAKES forever to format these drives) and I enter the Myth-Setup screen.  I setup my HD-PVR and HD-Homerun, SD data, etc.  I go to storage directories and enter default to add in my Hitachi's.  I enter in the path (/videoX) and add all 5.  When I go to exit, it tells me that /videoX (1-5) are not valid directories.  I think to mysel, "well maybe they were not mounted properly or I don't really have them setup right.  I delete all of them and exit thinking I can go back and add them in.

Upon restart (which I have it set to "auto log in") it dumps me to a CLI.  I thought that maybe we would have a GUI, but for a backend I guess not.  The screen flashes about 20-30 times and finally dumps me at a command prompt asking me for a user name/ password.  I enter it in, thinking maybe there was an issue.  I go to root to look to see if my mount points for my 2TB drives are there, and 1-5 are there.  

I kill the backend, and try to enter mythtv-setup. It errors out telling me a problem with X.  So I take it there isn't a GUI with the backend.

So ?'s are:
1.) how to enter setup if there isn't a GUI supplied.
2.) Why were my storage directories invalid if they are actually there?
3.) Why did the screen flash like crazy after reboot?
4.) Why didn't it auto log me in?
5.) Is there a better way t setup my 5 2TB drives??


Thanks in advance to any that have gotten this far, and a BIGGER thanks for those that have answers!!

---

### Post by 4dognight on 2010-04-01
1. It does use a XFCE desktop by default. My guess is your having problems with your xorg.conf file. What type of video card do you have? Also, look in /var/log/ for the xorg log file for errors. The backend setup is in the system menu once you get you desktop working.

2.can you show us the output from a df command, and your /etc/fstab

3.prob due to video card config as above

4.not sure , prob again video problem

5. 10 TB is a lot of disk. Only other solution is to maybe create a raid5 or raid10 array for redundancy. My guess is your ripping dvds. It is gonna take lots of time to rip em, and you might not want to spend the time again if you have a drive failure.

---

### Post by ian dobson on 2010-04-01
Hi,

I have a large RAID5 array (4 * 2Tb wd drives). If one drive dies the RAID array can handle it (add a now one and add to array). I also have 2*2Tb wd 4Kb drives in a RAID1 stripe for backups, if I delete a file by mistake/the file system screws up.

This makes it alot easier to handle all my data rather than having it split over different drives. I currently have about 1.7Tb in my mythtv recordings.

With regards to your problems

1) Have a look at your xorg log file in /var/log for your grahical frontend problem.

2) Check the access rights for the mount points (videoX) maybe your mythtv user doesn't have the rights to access the directory.

3) Show us a copy of your df command and maybe a ls -o for the directory above your videoX directories.

Regards
Ian Dobson

---

### Post by klc5555 on 2010-04-01
Not sure about the graphics issue, but when you set up your storage drive mountpoints, you may have left them set to root, and not writable by other accounts, including mythtv. 

Usually the storage directories will be set owner "mythtv", group "mythtv", permissions at 775. They should probably also be mounted somewhere in the usual path for mythtv storage (in mythbuntu), i.e. /var/lib/mythtv/videoX 

4dognight is right, 10T is a lot of storage at first, but the recordings/videos/rips you save will sneak up on you. After a couple of years, I find 8T across a couple of backends not unreasonable, and have an extra 2T drive sitting in a drawer which I expect I'll need to add for storage by the end of the summer.

---

### Post by x2aws on 2010-04-01
1.) I thought there was a GUI. I was thinking why they wouldn't include one by default..  I am using a Nvidia 9500 using HDMI out for the moment until I retire the box to its final destination and SSH from there.

2.) I can as soon as I get home.

3.) Thought so

4.) Thought so.

5.) No DVD ripping, only High Def recording, and future proof.  I told the wife that once I do this, I WILL NOT touch it again (hardware wise).  She hates when I fiddle with things.

Thanks for the help!!

---

### Post by x2aws on 2010-04-01
> **ian dobson said:**
> Hi,

I have a large RAID5 array (4 * 2Tb wd drives). If one drive dies the RAID array can handle it (add a now one and add to array). I also have 2*2Tb wd 4Kb drives in a RAID1 stripe for backups, if I delete a file by mistake/the file system screws up.

This makes it alot easier to handle all my data rather than having it split over different drives. I currently have about 1.7Tb in my mythtv recordings.

With regards to your problems

1) Have a look at your xorg log file in /var/log for your grahical frontend problem.

2) Check the access rights for the mount points (videoX) maybe your mythtv user doesn't have the rights to access the directory.

3) Show us a copy of your df command and maybe a ls -o for the directory above your videoX directories.

Regards
Ian Dobson

Ian,

I noticed last night the dir's were root/root with a DXWR, so I changed them to 777 to give FULL rights, but didn't change the user/group.  I am unsure of what user groups Mythbuntu has and also does it create a mythtv user, or does it use the user I created?!?!?!??!?

With the lack of Documentation this is a little harder  ;)  but still doable  :)


Sean

---

### Post by ian dobson on 2010-04-01
Hi,

OK, on my box the mythtv user is "mythtv", I'm not running mythbuntu, rather ubuntu with the myth-backend packages installed.

If you do a cat /etc/passwd you'll see all the users known by the system. I'm not sure if mythbuntu uses the "default" user (the one created during install) for the mythtv-backend process or mythtv.

Regards
Ian Dobson

---

### Post by 4dognight on 2010-04-01
> **x2aws said:**
> 1.) I thought there was a GUI. I was thinking why they wouldn't include one by default..  I am using a Nvidia 9500 using HDMI out for the moment until I retire the box to its final destination and SSH from there.

2.) I can as soon as I get home.

3.) Thought so

4.) Thought so.

5.) No DVD ripping, only High Def recording, and future proof.  I told the wife that once I do this, I WILL NOT touch it again (hardware wise).  She hates when I fiddle with things.

Thanks for the help!!

Maybe try just using the Dsub out for the moment. This way you can exclude HDMI for now. I also assume you loaded the nvidia driver.

Unless you keep everything you record, you wont come close to 10 TB. I have 1.5TB , but just record,watch and then delete shows, in HD. I dont even use half of my 1.5TB.

---

### Post by x2aws on 2010-04-01
> **4dognight said:**
> Maybe try just using the Dsub out for the moment. This way you can exclude HDMI for now. I also assume you loaded the nvidia driver.

Unless you keep everything you record, you wont come close to 10 TB. I have 1.5TB , but just record,watch and then delete shows, in HD. I dont even use half of my 1.5TB.


Gotcha.. I'll see if I can find the DVI-VGA adapter so I can go directly to my TV.  And speaking on the HDD's, I record a TON of movies, plus I already bought/installed them..  The wife would have my head if I told her they weren't needed  ;)

---

### Post by x2aws on 2010-04-02
::SNIP::
 
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

 
Heres what I got.  Using the VGA cable, the screen still flashes like crazy for about 5-10 seconds, and dumps me to a CLI.
 
Any ideas??

---

### Post by pootle1 on 2010-04-02
first thing is to sort out x, the rest should then not be too hard.

Which version of Ubuntu / myth are you using? and is it 32 bit 64 bit.  Which media did you actually install from?

Which nvidia drivers did you install and how did you do it?  

If you do rebuild, I suggest leaving out all the extra discs during the initial build, then you can pick them up again once the basics is up and working.

If this machine is a backend only, you could leave out the nvidia drivers and just use the ones that come with ubuntu - lower performance and no vdpau, but that won't matter on a backend.

---

