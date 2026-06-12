---
title: "Partition Advice - Mythtv and Zoneminder"
date: 2012-04-30
forum: Mythbuntu
---

### Post by km782 on 2012-04-30
Hi, I am somewhat of a Linux novice and am hoping to get some advice for partitioning a new HTPC build.

I will use it for 3 things:
1.) I want to use Mythtv to record and playback TV and ripped DVD's and maybe some music.  
2.) I also want to use the computer to play some emulator games.  
3.) Finally sometime down the line (probably about a year from now) I'll look into buying some cameras so that I can install Zoneminder and use the computer as a home surveillance system.  I'll be using it to record motion only, not continuous video, hopefully saving a lot of disk space.

I won't be using the computer for anything else (no web browsing, word processing, etc.)  I have a 2 TB hard drive and 4 GB of RAM.  I will be installing Mythbuntu 12.04 64 bit.

How is ext4?  I've seen some people post that they don't trust it yet but a lot of the information out there is several years old so I wonder if that has changed now?  Is it ok to use it instead of ext3 for the root partition?

This how I am thinking I will partition the disk:
1.) / - (5 GB?) - ext3 - I'm assuming that I can put both the boot and root in one partition?  Some people have them separate but that seems outdated.  I like being able to make changes/reinstall/upgrade the OS without touching my other data.  Is 5 GB enough?  I have no idea how much space a Mythbuntu install will take up.
2.) /swap (5 GB) - ext3 - I figure I'll give it a little more space than my RAM.  The computer will likely be running all of the time so I won't be putting it to sleep or hibernating.
3.) /home (40 GB) - ext4 - The way I understand it this is where Mythtv will be installed, my emulators and my ROMs for the emulators (these will likely just sit on the disk, I won't be making any changes to them and there are a lot of small files), and eventually Zoneminder.  Does the Mythtv database take up a lot of space?  How much space should I leave for Mythtv, Zoneminder and anything else that is installed with Mythbuntu?
4.) /media (rest of the disk) - XFS - this is where the Mythtv recordings will go, music, and my ripped DVD iso files and I'm assuming my Zoneminder recordings?

Do you have any suggestions?  Is there anything that you would recommend changing?  Thanks for your help!

---

### Post by nickrout on 2012-05-01
> **km782 said:**
> Hi, I am somewhat of a Linux novice and am hoping to get some advice for partitioning a new HTPC build.

I will use it for 3 things:
1.) I want to use Mythtv to record and playback TV and ripped DVD's and maybe some music.  
2.) I also want to use the computer to play some emulator games.  
3.) Finally sometime down the line (probably about a year from now) I'll look into buying some cameras so that I can install Zoneminder and use the computer as a home surveillance system.  I'll be using it to record motion only, not continuous video, hopefully saving a lot of disk space.

I won't be using the computer for anything else (no web browsing, word processing, etc.)  I have a 2 TB hard drive and 4 GB of RAM.  I will be installing Mythbuntu 12.04 64 bit.

How is ext4?  I've seen some people post that they don't trust it yet but a lot of the information out there is several years old so I wonder if that has changed now?  Is it ok to use it instead of ext3 for the root partition?

This how I am thinking I will partition the disk:
1.) / - (5 GB?) - ext3 - I'm assuming that I can put both the boot and root in one partition?  Some people have them separate but that seems outdated.  I like being able to make changes/reinstall/upgrade the OS without touching my other data.  Is 5 GB enough?   no probably not enough, go for 25G > I have no idea how much space a Mythbuntu install will take up.
2.) /swap (5 GB) - ext3 - I figure I'll give it a little more space than my RAM.  The computer will likely be running all of the time so I won't be putting it to sleep or hibernating. you shouldn't need any swap at all with 4G RAM, but if you want some then it doesn't get formatted as ext3 it gets formatted as swap!> 
3.) /home (40 GB) - ext4 - The way I understand it this is where Mythtv will be installed, no, myth gets installed in the normal places, home is not used for anything much.>  my emulators and my ROMs for the emulators (these will likely just sit on the disk, I won't be making any changes to them and there are a lot of small files), although I must admit I don't know where game emulators go for mythgame> and eventually Zoneminder.  I am not sure where zoneminder creates its files, but it isn't in /home. It creates a adtabase in /var/lib/mysql/zm but where the pictures and video files are stored I can't quite figure out!>  Does the Mythtv database take up a lot of space?  no >  How much space should I leave for Mythtv, Zoneminder and anything else that is installed with Mythbuntu?
4.) /media (rest of the disk) - XFS - this is where the Mythtv recordings will go, music, and my ripped DVD iso files and I'm assuming my Zoneminder recordings?

 you will have to change mytht's defaults as it stores it's data by defauly in /var/lib/mythtv, it is best to put it on a separate disk to the OS and change those defaults.> 

Do you have any suggestions?  Is there anything that you would recommend changing?  Thanks for your help!

---

### Post by elliott6 on 2012-05-01
I am no authority, and my setup has its own issues, however, one of the best things I have done (again, personally), is separate the media and OS disks.  If it's not feasible for you, please ignore, but I essentially have one disk dedicated to Mythbuntu (currently a 40GB HDD, but looking to move to a 40GB SSD), and then one disk specifically for all of my media (it's actually a perc5i RAID5 set of 1.5TB disks).  The reason I have done it that way is that if my OS disk dies it can be easily replaced, as well as swapped out if I get the itch.  I started with a one disk setup that was far too small, switching to a slightly larger one disk install.  And then constantly adding media/wanting more storage for said media, I kept having to move things around, which can be a pain.  Finally decided on separating OS and data, and it's been great, especially when I have had to expand the storage space for data.  My setup looks like this (from memory.. not at home at the moment) - 

40GB HDD (again, plenty of space for just OS, and it was something I had lying around):
8GB / (formatted as ext3, but will be ext4 with SSD, and might expand to 10GB or 12GB)
4GB SWAP (gets formatted as SWAP)
rest or ~26GB /home (formatted as xfs)

RAID5:
/media (formatted as XFS with folders for recordings, videos -movies and DVD isos are in this folder-, pictures, music, coverart, and something else I can't remember)

It takes some effort to change all of the folders myth uses to the /media folder, but definitely worth it once it's up and running.  Only problem on the OS drive that comes up size-wise is when recordings are "full", as the logs become quite large with errors, which can stuff up the / partition.  Additionally, for "pushing" access to frontends and others (Windows machines that use the shared media - music and videos), it's easy to identify the "media" folder location than /var/lib/mythtv when I share via NFS.  And be mindful of where you have the "liveTV" folder, as this can quickly use your disk space (sorry.. can't remember the default - think it's /var/lib/mythv as well).

Your size for / might be a little small.  I would expand to at least 10GB, or maybe a touch more, just because downloads/updates get put here, and if you are not diligent in purging, can become a bit stuffy.

Again, 4GB for SWAP should be enough.  I am running 4GBs RAM in mine, with the 4GB SWAP.  The RAM and swap fills up and gets some use, but that's what it's supposed to do (Linux).

/home can be smaller.  With my 40GB setup, it might have 15GB of the 28GB used.

I also don't know about emulators (but will eventually, hopefully), nor zoneminder.  So you will have to adjust accordingly.

Size matters, but more so for recording/media space.  One of my frontends I having running off of a 4GB compactflash card, with media being from the shared backend described above.  The backend needs more, but no need to dedicate a large and fast drive for the OS, hence my suggestion (and nickrout) to separate the two.  

Thanks, and good luck!  (sorry for the length and "rant" in my post.. I babble)

---

### Post by km782 on 2012-05-01
Thanks for the responses.  A lot of people have suggested using two separate disks.  I am planning on trying it out with one disk now and if there are performance issues, I'll run out and grab another drive.

I probably wasn't super clear in my first post.  I'm thinking that I will need 4 partitions:

1.) The first is / (which I will increase the size of)  
2.) The second is swap
3.) On the third I'd like to have everything else except for my media files.  I think this would include /home for settings and /usr for the executable files.  I'm trying to gauge how big to make this partition.
4.) The last partition would use up the rest of the disk with media files (Mythtv recordings, DVD iso's, music, etc.)  I guess this is /var or I can rename it to /media

Does this sound right?  Sorry if these are stupid questions but I feel like the more I read about this the more confused I get.  Am I even able to designate /home and /usr to be on the same partition?  Also, are there OS files stored in these directories and if so am I at risk of data loss when I go to upgrade the OS in the future?

---

### Post by nickrout on 2012-05-01
> **km782 said:**
> Thanks for the responses.  A lot of people have suggested using two separate disks.  I am planning on trying it out with one disk now and if there are performance issues, I'll run out and grab another drive.

I probably wasn't super clear in my first post.  I'm thinking that I will need 4 partitions:

1.) The first is / (which I will increase the size of)  
2.) The second is swap
3.) On the third I'd like to have everything else except for my media files.  I think this would include /home for settings and /usr for the executable files.  I'm trying to gauge how big to make this partition.
4.) The last partition would use up the rest of the disk with media files (Mythtv recordings, DVD iso's, music, etc.)  I guess this is /var or I can rename it to /media

Does this sound right?  Sorry if these are stupid questions but I feel like the more I read about this the more confused I get.  Am I even able to designate /home and /usr to be on the same partition?  Also, are there OS files stored in these directories and if so am I at risk of data loss when I go to upgrade the OS in the future?

Take my word for it:

Disk 1 (40G is sufficient) one partition for / & one for swap if you want it (not sure why you think you need swap with 4G RAM)

Disk 2 one partition for all your media.

---

### Post by elliott6 on 2012-05-02
You sound fine, and weren't as unclear as you think. Nickrout and I, and others, are simply passing along our experience.  The information is overwhelming, and the "use the search" isn't always a helpful response.  Personally, much of my hassle was the constant restructuring as I found what disk setup was best for me to use, finally settling on the one drive for OS (and it can be whatever you have leftover lying around) and a second for the media.  This just keeps it clean.  HOWEVER, to answer your questions: :) 

It would either be 3 or 4 partitions, depending on how you want to store your media.  If leaving default myth settings, it would be 3 partitions, as it stores media to /var/lib, which is what it looks like you are going for.  Therefore - 

1.) The first is / (which I will increase the size of)  
- I use 8.6GB, but like I stated, will increase to at least 12GB.  If you would like extra cushion for other stuff you might install, go for 20GB, or 25GB should be sufficient (I see you plan to use a 2TB drive).  Format to ext3 or default (not sure if default is now ext4).

2.) The second is swap
- I use 4GB, with 4GB RAM.  It "formats" as swap.  So I would recommend the same, which is probably overkill.  System monitor shows 1.7GB (46.2%) of 3.6GB in use; Swap is 114.1MiB (2.4%) of 4.6GB in use.  Whoops, guess I set 5GB for swap.

3.) On the third I'd like to have everything else except for my media files.  I think this would include /home for settings and /usr for the executable files.  I'm trying to gauge how big to make this partition.
- /var/lib is here.  This would be formatted to xfs, and would be the rest of the drive.  Again, default media for myth goes here.  If you wish to change the default directories for media, add the fourth partition and use, perhaps another 20-25GB.  With media separate for me, mine is 24GB, but currently only using 6.6GB (or 27%).

4.) The last partition would use up the rest of the disk with media files (Mythtv recordings, DVD iso's, music, etc.)  I guess this is /var or I can rename it to /media
- /media would be all the rest of the 2TB.  This should be formatted as xfs (or some jfs, as it handles the larger filesizes better, especially when deleting).  For me, I have then created folder within /media - music, mytharchive, mythdvd, mythlogs, mythvideo, pictures, recordings, temp, and videos (contains movies and dvd ISOs).  Then, it's a matter of going through all of the myth setup screens to redirect where things are stored (point to /media/music instead of /var/lib/mythtv/music default for example).  

And yes, OS files are stored in / and configuration stuff too.  I think that's why you get mostly "use separate drives from your media."  And then of course backup!  It's because if something goes wrong with the drive, or you need to change something, you don't have to worry about the data (media) if you require a reinstall, or some other recovery techniques.  However, Linux is pretty good about updates, etc., and unless you are doing a wipe and reinstall, don't worry too much about it.

Good luck, and let us know if you need any additional information.

---

