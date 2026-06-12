---
title: "[SOLVED] Mythbuntu crashes unexpected"
date: 2008-11-20
forum: Mythbuntu
---

### Post by jonwestin on 2008-11-20
Hello,

I recently installed Mythbuntu on a HTPC I bought, and it has been working great, but the last week ive had unexpected crashes. I thought it might have something to do with Deluge, since our router is misbehaving but it seems thats not the case..
And I have no idea where to start searching for whats causing it, so any advice is welcome. What logs should I look at and where are they? :) Im not a total noob but right now I feel like one. 

Cheers
Jon

Edit: This is the HTPC: [http://ggsdata.se/pcmoder/pcdator2.php](http://ggsdata.se/pcmoder/pcdator2.php)
GSS-data Enlight. No information in English tho, ill post specs when I get home from work :)

---

### Post by jonwestin on 2008-11-20
AMD Athlon64 X2 4800+ 2.5GHz 
ASUS MicroATX M2N-VM 
Geforce 7050PV
2048MB Ram DDR2 800

---

### Post by dmfrey on 2008-11-20
Can you describe a little more...what you are doing when it crashes?  Are you watching a recording or a video, listening to music, etc.  Is it just Mythbuntu that crashes or is does your machine power off?  Please be as specific as possible.

What capture devices do you have setup?


The logs are located in /var/log/mythtv.  There are logs for both the frontend and backend.  Check both and look for any exceptions.

---

### Post by jonwestin on 2008-11-20
> **dmfrey said:**
> Can you describe a little more...what you are doing when it crashes?  Are you watching a recording or a video, listening to music, etc.  Is it just Mythbuntu that crashes or is does your machine power off?  Please be as specific as possible.

What capture devices do you have setup?


The logs are located in /var/log/mythtv.  There are logs for both the frontend and backend.  Check both and look for any exceptions.

Thanks for your reply. At first it just crashed when I was watching videos but recently I had a crash while VNCing. The computer freezes entirely and I have power it off to restart. 

Ill check the logs when I get back home.

---

### Post by jonwestin on 2008-11-28
Im afraid this might have to do with overheating. The comp is placed next to the TV and plenty of space around and above but i dunno.. the chasi fan wasnt installed, apparently. 

and ive been transfering a lot of files lately, and last time i got some weird error while copying through the network. some of the files in dir wasnt complete so i tried replacing them but the same error, which has nothing to do with permissions. i then tried removing them, both through the filemanager and in terminal with sudo rm and then the FM or terminal just hangs. i cant even list the dir in terminal. 

next time i booted up mythbuntu performed the file check and stopped at 30% or so and froze. hard drive error? how do i check that and is there anything i can do to fix it?

any answer is very welcome :)

jon

---

### Post by canoemoose on 2008-11-28
> **jonwestin said:**
> Im afraid this might have to do with overheating. The comp is placed next to the TV and plenty of space around and above but i dunno.. the chasi fan wasnt installed, apparently. 

and ive been transfering a lot of files lately, and last time i got some weird error while copying through the network. some of the files in dir wasnt complete so i tried replacing them but the same error, which has nothing to do with permissions. i then tried removing them, both through the filemanager and in terminal with sudo rm and then the FM or terminal just hangs. i cant even list the dir in terminal. 

next time i booted up mythbuntu performed the file check and stopped at 30% or so and froze. hard drive error? how do i check that and is there anything i can do to fix it?

any answer is very welcome :)

jon
I had the same problems with a normal Ubuntu install when my hard drive was knackered.  Sounds to me like the machine overheated because the fan wasn't installed properly, this cooked (literally) the hard drive which is now corrupted.  If you have access to another hard drive you could try that as a test, but imho it's new hard drive time.  Sorry to be the bearer of bad news!!

---

### Post by jonwestin on 2008-11-28
> **canoemoose said:**
> I had the same problems with a normal Ubuntu install when my hard drive was knackered.  Sounds to me like the machine overheated because the fan wasn't installed properly, this cooked (literally) the hard drive which is now corrupted.  If you have access to another hard drive you could try that as a test, but imho it's new hard drive time.  Sorry to be the bearer of bad news!!

thanks for your reply, even though its bad news. 

i also tried reinstall mythbuntu and the install seemed to run ok but when i rebooted i got grub error 15, and ive tried every way of restoring grub but same frikkin error. 

crap. the disk shouldnt overheat that easily but well well.. is there any way to check it?

edit: when i was running the livecd for restoring grub i could mount the disk, both partitions. but i have no idea where to check for errors.

---

### Post by canoemoose on 2008-11-28
Um.  It ought be possible to run fsck on the partitions from the LiveCD if they are not mounted.  If your problem is the same as mine was, fsck will return multiple problems with your drive, which it will fix, but next time yuo run it things will be broken again.

---

### Post by jonwestin on 2008-11-29
> **canoemoose said:**
> Um.  It ought be possible to run fsck on the partitions from the LiveCD if they are not mounted.  If your problem is the same as mine was, fsck will return multiple problems with your drive, which it will fix, but next time yuo run it things will be broken again.

hm, i ran the fsck and it seemed to fix the problem cause the files i tried to delete earlier were gone and i could mount and access the disk without any problems.. thing is i now cant install mythbuntu (or any other dist) cause the grub wont install.. any ideas?

---

### Post by canoemoose on 2008-11-29
> **jonwestin said:**
> hm, i ran the fsck and it seemed to fix the problem cause the files i tried to delete earlier were gone and i could mount and access the disk without any problems.. thing is i now cant install mythbuntu (or any other dist) cause the grub wont install.. any ideas?
Sorry, no ideas.  Could be a bad sector on the drive I suppose. Hang on, that's an idea!  Try partitioning off the first bit of the drive and then try installing mythbuntu/whatever on the rest of it.

---

### Post by jonwestin on 2008-11-30
> **canoemoose said:**
> Sorry, no ideas.  Could be a bad sector on the drive I suppose. Hang on, that's an idea!  Try partitioning off the first bit of the drive and then try installing mythbuntu/whatever on the rest of it.

ah. seems like the mbr is messed up or something. tried three different install cds and nothing works, also tried to remove the partition and make a new one but no luck. is there anyway of fixing the mbr or whatever it is? :(

---

### Post by jonwestin on 2008-12-01
i've now tried the Super grub CD and it still wont install.. have no idea what to do next so ill guess ill just order a new drive and send in the old one to the company that sold it.

edit: i just found the solution!

> 1. Boot to an available Linux prompt (live CD? Terminal.)
2. Make sure you are root or sudo your commands.
3. (sudo) mkdir /mnt/temp
4. (sudo) mount /dev/hdx (or sdx) /mnt/temp
5. (sudo) grub-install /dev/hdx &#8211;root-directory=/mnt/temp/
That allows GRUB to access the device, yet it will store its settings and components where you want them, on your linux partition. Hope this helps.

(Found this here: [http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/), thanks Richard Clark)

Then do the grub -> find -> root -> setup thing
and then chroot into the dir you mounted (/mnt/temp) and run update-grub.

Should work..

---

### Post by jonwestin on 2008-12-01
hm nevermind, i got dumped to the Busybox shell so as far as i can tell, that means something went kinda wrong..


edit again: solved that by changing the menu.lst, was set to hda1 in the kernelthingy, should be sda2. all good!

---

### Post by canoemoose on 2008-12-02
Well done!!
If it's only the MBR then you should be sorted!!  Otherwise, just keep an eye on it to see if it starts going stange again.

---

