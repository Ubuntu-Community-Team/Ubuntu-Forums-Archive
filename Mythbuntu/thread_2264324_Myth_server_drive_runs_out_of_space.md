---
title: "Myth server drive runs out of space"
date: 2015-02-06
forum: Mythbuntu
---

### Post by hollywoodpete on 2015-02-06
I have set up the mythbuntu server 14.04 on a headless server 3 times.  The hard drive is 240Gb. After about a week of viewing live TV and recording a few shows, the hard  drive runs out of space and then freezes. I was under the impression  that the recorded shows would auto-delete before this happens. I have  re-installed each time. What am I doing wrong? Is the drive not large  enough? Is there a way to export the files to a NAS with more drive space?

---

### Post by Lester_Burnham on 2015-02-07
> **hollywoodpete said:**
> I have set up the mythbuntu server 14.04 on a headless server 3 times.  The hard drive is 240Gb. After about a week of viewing live TV and recording a few shows, the hard  drive runs out of space and then freezes. I was under the impression  that the recorded shows would auto-delete before this happens. I have  re-installed each time.
It all depends I suppose, on how full the drive is before you watch live TV. Do you have auto expire set for all recording rules?

> What am I doing wrong?
You're probably best adding another drive or partition and create /mythtv/recordings folders then, symlinking it to /var/lib/mythtv/recordings.
Or just change recording location in the backend to /mythtv/recordings.
All of the above methods will protect the root partition from filling up.

> Is the drive not large  enough?
Not really. SD quality here is about 1.5 GB/hr. HD is about 3GB/hr

> Is there a way to export the files to a NAS with more drive space?
You could mount a NAS location in your fstab and record to that.

Lester

---

### Post by hollywoodpete on 2015-02-07
Thanks for the reply. Mythbuntu  is the only progam on the drive. I start with about 224 gb free. I guess the best answer is to add another drive. I have a Dell PowerEdge 860 server and the specs say the motherboard will support up to 1.5 TB. Im not sure if that means 2 x 750 gb or 2 x 1.5 TB. I'm thinking about getting a 3 TB drive and hoping for the best.

If the default setting for recording is auto expire, that is what I am doing. If I have to add that setting, it hasn't been done nor do I know how to do it.

Is it too late to partition the disc? I guess I should have partitioned the disc prior to installing Muthbuntu with a root partition aroun 30 GB for the OS and the rest for media.

---

### Post by Lester_Burnham on 2015-02-08
Hi,
You can probably only shrink it now via a live cd because it's mounted with the OS. Best to just add another drive. 

Auto expire is by default. If you use mythweb, you'll see it at the bottom when you set a recording. Some people change settings to keep everything and then wonder why it grinds to a halt. Defaults are good :)

How much live TV do you watch?

I'll look at the power edge specs.

Lester

Edit. Hard to find anything concrete. Do you have a 1tb drive you can try? That's normally all I use.

---

### Post by khPWXxF on 2015-02-08
I’ll add to what Lester has said:
 
1. You don’t say where you are and the type of recordings you make.  Lester has given an Australian rule of thumb;  in the UK it uses about 2GB/hour for standard definition.  That would give you about 100 hours with your disk which sounds a lot to be burned up in a week.   In US I think it’s somewhat greedier on space.
 
2.  You can check on your partitions regularly with df.  Use du to find out where the space has gone.  The frontend list of recordings gives space used too.
 
3. Splitting /var/lib/mythtv (or /var) from the rest is always stated as good practice.
 
4.  You say that your backend is ‘headless’.  How are you watching recordings?  If on an Android or ipad frontend then watch out for big HLS files which get left lying around and are not expired automatically.   Mythtv or xbmc/kodi frontend should be okay though.
 
5.  A second drive for recordings is always recommended as it separates your heavy database traffic from your recordings.  I originally started with a single 500GB drive (SATA 2) which worked well though.
 
6.  If you do get a second drive then you have a number of backup and resilience options.  Emergency root and swap partitions together with database backups to the big drive in case of primary failure;  maintaining a copy of recent recordings to a partition on your smaller disk in case of big disk failure.
 
7.  1.5TB sounds an odd limit – not a power of 2.  Your system is listed here under generation 9.
[http://en.wikipedia.org/wiki/List_of_Dell_PowerEdge_Servers](http://en.wikipedia.org/wiki/List_of_Dell_PowerEdge_Servers)
I wonder if that was the biggest capacity available then because various documents give different sizes.  I’ve heard of problems at 4TB but not at 1.5.
 
Phil

---

### Post by hollywoodpete on 2015-02-08
You guys are great. I am in the US. I checked a couple of files and in High def a one hour show is about 5 gb. I had previously been deleting shows with MythWeb. I decided to just let the auto expire take over. It obviously didn't work as well as I expected. We mostly watch live tv but at some point I would like to schedule every show we like and watch them at our convenience.

I am using Kodi as the front-ends. I had been using XBMC for years and my wife has finally gotten comfortable with the interface. I am trying to play with the myth frontend but at this point,  getting my wife to switch is not going to happen. I use MythWeb to schedule and delete all recordings.

I know the hard drive question is a little off the topic. I picked up some info[ here]("http://en.community.dell.com/techcenter/extras/w/wiki/2837.hdd-support-for-2-5tb-3tb-drives-and-beyond"). I have a couple of extra hard drives laying around so that wont be an issue. The server form factor only has room for one more drive so I really want to pop in the largest drive possible. I have always been impressed by the ability for Linux to handle massive drives but I think the BIOS or controller may be an issue in this server. I will put in a 2 TB drive and hope for the best

Thanks again for the help. I may need a little more help after the new drive goes in.

And as long as I'm asking hardware questions, would it be worth the expense of increasing my RAM from 4 gb to 8 gb as long as I have the server open? 4 gb is ~$70 US . Would there be any benefit in 8gb?

---

### Post by khPWXxF on 2015-02-08
A few points on the graph for you:

My initial setup, a combined FE/BE on a dual core AMD system, had 2GB and nothing allocated to graphics.   A single SATA 500GB disk.  Ran fine, but I erred on the side of caution before allocating RAM to graphics.

I now run it with 4GB but 512MB of that is allocated to nvidia graphics with VDPAU.  It has 2 disks - root on one, /var/lib/mythtv on the other.  It runs fine recording half a dozen programs simultaneously plus playback.   I have never seen swap used.

Note it's not doing anything else apart from Mythtv.

Phil

---

### Post by hollywoodpete on 2015-02-12
You guys were great with the help but I need to ask for a little hand-holding. I installed a 2TB drive and have it formatted to ext3 to auto-mount on media. 

I have decided to "[COLOR=#000000]**Or just change recording location in the backend to /mythtv/recordings.**"  
I'm just not sure how to do that step. Can it be done through MythWeb or do I need to do it through the backend setup?[/COLOR]

---

### Post by Lester_Burnham on 2015-02-12
Hi,
Are you using an external 2tb drive (USB) or internal on SATA?
First I would format it as ext4. Either way above, add the drive to your /etc/fstab to mount at boot.

Create the folder to mount it into
```
sudo mkdir /mythtv
sudo chmod 777 /mythtv
```
Run this below to find the 2tb drive's UUID to add to fstab.
```
sudo blkid
```
Move the cursor down to the bottom and add the two lines below to your fstab, substituting your UUID. Use gedit if you have it installed.
```
sudo nano /etc/fstab
```
> # /mythtv
UUID=11e3e2a4-52d4-4234-9349-24c749636ee5 /mythtv         ext4    defaults        0       2
Save and close, then run
```
sudo mount -a
```
Make sure there's no errors.

To mount the drive to the new location.
```
sudo mkdir /mythtv/recordings
cd /mythtv
sudo chown mythtv:mythtv /recordings
```
Now go to the backend and change the recording location.
Lester

---

### Post by hollywoodpete on 2015-02-12
Thanks for the quick reply. I opened the server and installed a new internal SATA drive and upgraded the Memory to 8GB. I will reformat to EXT4. Will the previous instructions above succeed in  "[COLOR=#000000]3.** Splitting /var/lib/mythtv (or /var) from the rest is always stated as good practice". ?**

[/COLOR]

---

### Post by Lester_Burnham on 2015-02-12
Hi,
Hopefully Phil will be around soon to help you out, as I need to go out.
Plus I need to think/read up on a bit for the best way to do it.
Lester

---

### Post by hollywoodpete on 2015-02-12
Thanks Lester,
I wish I knew a good place to "read more" I know just enough to be dangerous.

I did follow your code and the disk is mounting at /mythtv/. I went to Storage Groups and changed default from /var/lib/mythtv/recordings to /mythtv/recordings. I did the same thing with the livetv group. That is not the answer.

---

### Post by Lester_Burnham on 2015-02-12
No. Probably because all the old recordings/live TV/streaming files are still in the old location. I would've waited for more info.

---

### Post by hollywoodpete on 2015-02-12
No problem. I try to safely tinker but it doesn't always workout that way. Sometimes it actually works. I will chill

---

### Post by Lester_Burnham on 2015-02-13
Hi,

You probably need to move the whole /var accross. But you could probably copy all the folders across from /var/lib/mythtv/ into you're newly created /mythtv and symlink each folder back to /var/lib/mythtv/.
It's by no means really correct, but it should keep all the paths relative to where they should be and still work.

1. Copy everything in /var/lib/mythtv/ to /mythtv/
2. Rename all folders in /var/lib/mythtv/ to banners.bak etc.
3. Symlink all folders from /mythtv/ back to /var/lib/mythtv/ (you can also restore the recording path you changed earlier)
```
sudo ln -s /mythtv/banners /var/lib/mythtv/banners
sudo ln -s /mythtv/coverart /var/lib/mythtv/coverart
sudo ln -s /mythtv/fanart /var/lib/mythtv/fanart
sudo ln -s /mythtv/livetv /var/lib/mythtv/livetv
sudo ln -s /mythtv/recordings /var/lib/mythtv/recordings
sudo ln -s /mythtv/streaming /var/lib/mythtv/streaming
sudo ln -s /mythtv/videos /var/lib/mythtv/videos
sudo ln -s /mythtv/bare-client /var/lib/mythtv/bare-client
sudo ln -s /mythtv/db_backups /var/lib/mythtv/db_backups
sudo ln -s /mythtv/screenshots /var/lib/mythtv/screenshots
sudo ln -s /mythtv/trailers /var/lib/mythtv/trailers
```

Restart the PC and do some testing with fronted etc. before deleting the renamed folders
Maybe also go into backend-setup > General>Page 3 and check "Follow Symbolic links when deleting files"

Hopefully someone chimes in with a "cleaner" method of doing things. 

Lester

---

### Post by khPWXxF on 2015-02-13
You should already be able to access your new disk as /var/lib/mythtv if you have set up fstab as advised by Lester.
   
  In order to move contents of /var/lib/mythtv from the 'old' to the 'new' disk I would:
   
  1. Take a backup copy of fstab and temporarily comment out the mythtv line in the live one.
  2.  Reboot.  This will allow you to see recordings etc under /var/lib/mythtv on the old disk, but the new disk will not be visible.
  3.  Close down backend and  frontend.  Change the name of /var/lib/mythtv eg
   
  cd /var/lib
  sudo mv mythtv mythtvold
   
  4.  Re-allow the line in fstab (or copy from your backup).
  5. Reboot.
  6. Stop frontend and  backend.
   
  You will now see both folders:  an empty mythtv on the new disk, and a full mythtvold on the old.
   
  7.  Copy contents of old to new.   I think this should do it:
  sudo cp –v –r –f  /var/lib/mythtvold/* /var/lib/mythtv/
   
  8.  Reboot and test.
  9.  If all is well, empty mythtvold
   
  Good luck!
  Phil

---

### Post by hollywoodpete on 2015-02-13
Sorry to be a pest but I am confused about this line
3.  Close down backend and  frontend.**  Change the name of /var/lib/mythtv eg**
I should be able to handle the rest fine.
Thanks


mythuser@homer:~$ sudo cp &#8211;v &#8211;r &#8211;f /var/lib/mythtvold/* /var/lib/mythtv/
[sudo] password for mythuser: 
cp: target &#8216;/var/lib/mythtv/&#8217; is not a directory
mythuser@homer:~$

There is a folder named /mythtv/ that contains 2 folders lost+found and recordings and is 1.9TB in size
/var/lib/mythold has all of the folders (banners, bare-client, etc)
there does not appear to be a folder named /var/lib/mythtv

My naive self tells me I am mounting the drive in the wrong place and it needs to mount at /var/lib/mythtv instead of just /mythtv/

---

### Post by Lester_Burnham on 2015-02-13
Sorry to butt in.
You'll need to change the mount point we made earlier in fstab to point to /var/lib/mythtv for this. I think Phil misread this part.

Comment it out in fstab, then run a sudo mount -a to unmount it. Modify it after you unmounted it.
```
# /mythtv
UUID=11e3e2a4-52d4-4234-9349-24c749636ee5 /var/lib/mythtv ext4 defaults 0 2
```

Basically with Phil's method, you are doing some substitution. Moving the files out of the way, so you can mount the new drive to the correct location. Probably a sudo mount -a again would save a reboot, then copy it all back into /var/lib/mythtv

Phil will be back to confirm.

Lester

---

### Post by hollywoodpete on 2015-02-13
Well, I might be closer. In /var/lib/ I have multiple folders including /var/lib/mythtv which contains lost+found and recordings and is 1.9 TB in size. There is also a folder /var/lib/mythtvold that contains the correct folders that I need to move.

mythuser@homer:~$ sudo cp &#8211;v &#8211;r &#8211;f /var/lib/mythtvold/* /var/lib/mythtv/
[sudo] password for mythuser: 
cp: cannot stat &#8216;&#8211;v&#8217;: No such file or directory
cp: cannot stat &#8216;&#8211;r&#8217;: No such file or directory
cp: cannot stat &#8216;&#8211;f&#8217;: No such file or directory
cp: omitting directory &#8216;/var/lib/mythtvold/banners&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/bare-client&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/coverart&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/db_backups&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/fanart&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/livetv&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/recordings&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/screenshots&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/streaming&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/trailers&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/videos&#8217;

And just for information in case it is helpful, this is a backend server only. There is no frontend installed

I'm not sure if logs will help but here [URL="http://pastebin.com/et7K9mH2"]http://pastebin.com/et7K9mH2


[/URL]

---

### Post by hollywoodpete on 2015-02-13
And if it helps even more, when I start Mythbackend set-up and try to exit I get 
"Unable to create file "/var/lib/mythtv/recordings//.test -directory is not writable?"

I guess somehow I need to make this writable???

---

### Post by tgm4883 on 2015-02-13
> **hollywoodpete said:**
> Well, I might be closer. In /var/lib/ I have multiple folders including /var/lib/mythtv which contains lost+found and recordings and is 1.9 TB in size. There is also a folder /var/lib/mythtvold that contains the correct folders that I need to move.

mythuser@homer:~$ sudo cp &#8211;v &#8211;r &#8211;f /var/lib/mythtvold/* /var/lib/mythtv/
[sudo] password for mythuser: 
cp: cannot stat &#8216;&#8211;v&#8217;: No such file or directory
cp: cannot stat &#8216;&#8211;r&#8217;: No such file or directory
cp: cannot stat &#8216;&#8211;f&#8217;: No such file or directory
cp: omitting directory &#8216;/var/lib/mythtvold/banners&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/bare-client&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/coverart&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/db_backups&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/fanart&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/livetv&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/recordings&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/screenshots&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/streaming&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/trailers&#8217;
cp: omitting directory &#8216;/var/lib/mythtvold/videos&#8217;

And just for information in case it is helpful, this is a backend server only. There is no frontend installed

I'm not sure if logs will help but here [URL="http://pastebin.com/et7K9mH2"]http://pastebin.com/et7K9mH2


[/URL]

it's not pulling in your options correct. Please type the command in rather than copy and paste.


> **hollywoodpete said:**
> And if it helps even more, when I start Mythbackend set-up and try to exit I get 
"Unable to create file "/var/lib/mythtv/recordings//.test -directory is not writable?"

I guess somehow I need to make this writable???

You can do that by doing (again, type it in rather than copy and paste)

```
sudo chown -R mythtv:mythtv /var/lib/mythtv
```

---

### Post by hollywoodpete on 2015-02-13
Beautiful, now I'm up and and running

---

