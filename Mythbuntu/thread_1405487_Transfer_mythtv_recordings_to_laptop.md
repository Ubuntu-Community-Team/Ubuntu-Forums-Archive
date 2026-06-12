---
title: "Transfer mythtv recordings to laptop"
date: 2010-02-12
forum: Mythbuntu
---

### Post by brian_hayward on 2010-02-12
I have about a months worth of recordings on my mythtv box that i have not gotten around to watching.  I travel quite a bit for my job and i want to transfer my recordings to my laptop so i can watch them on the road.  I don't know how to transfer the recordings to another computer so they have a file name of show and show date.  I tried a couple searches on the internet but all i can find are tutorials on backing up my myth database and doing a restore, which is not what i want to do...i just want to transfer the recordings to another computer.  i understand i can put them on a dvd but like i said...i have about a months worth of recordings of a few different shows, burning them on to DVD would take a long time.  is there another way i can transfer my recordings so they all have file names describing what the show is and a date it was recorded?  Any help, suggestions or if this has been answered already a link to the explanation would be greatly appreciated...Thanks.

---

### Post by azmyth on 2010-02-12
Haven't used it myself but you may want to look at MythExport.

[http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)

---

### Post by brian_hayward on 2010-02-13
> **azmyth said:**
> Haven't used it myself but you may want to look at MythExport.

[http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)

I have looked at Mythexport, but i don't want to do any transcoding jobs or any kind of processing to the recordings...i just want the file name to be changed to a file name that tells me what the recording is and transfer it to my laptop.  I am extremely green at database work...does anybody know of a script i could use that would query the data base and match the recording title to the recording itself?

---

### Post by chipppy on 2010-02-13
Good Evening

Dont know of a script but here a quick and dirty idea for you.
You need a portable harddrive or USB stick of suitable size.  Personally I would grab you portable harddrive.

Jump into the file structure from memory it is something like
var/lib/mythtv/recording might be a user in there to cannot remember at the moment.

set view to details and there you can see a date that the file was made.  therefore you have a date.  The recordings are numbers (decodes to the date as well but easier to use the details part)

Copy and paste all the file from the date you want to your portable harddrive.

start up each file one by one and then you know which show it is.
Right click and rename the files to what you want (show name and date as an example)

Plug your portable harddrive into you laptop and and copy and paste.

Quick and dirty but gets the job done.

But do keep looking for a script because I am sure there is one out there.

Cheers
chipppy

---

### Post by klc5555 on 2010-02-14
> **chipppy said:**
> Good Evening

Dont know of a script but here a quick and dirty idea for you.
You need a portable harddrive or USB stick of suitable size.  Personally I would grab you portable harddrive.

Jump into the file structure from memory it is something like
var/lib/mythtv/recording might be a user in there to cannot remember at the moment.

set view to details and there you can see a date that the file was made.  therefore you have a date.  The recordings are numbers (decodes to the date as well but easier to use the details part)

Copy and paste all the file from the date you want to your portable harddrive.

start up each file one by one and then you know which show it is.
Right click and rename the files to what you want (show name and date as an example)

Plug your portable harddrive into you laptop and and copy and paste.

Quick and dirty but gets the job done.

But do keep looking for a script because I am sure there is one out there.

Cheers
chipppy

Still easier is to use nuvexport to copy the shows into the portable harddrive. 

Run "nuvexport" from a prompt. Use option 11, "export the nuv and sql" (which is really just a file copying function). When all the shows on the machine are listed in alphabetical order, pick the show and its episodes you want. Put the path to where the portable drive is mounted for the shows to be copied to, and let nuvexport work. The .mpg file for each episode will still retain its mythtv-formatted channel-date-time numerical filename, but will be tucked away inside an individualized folder on the portable drive that will have the show's name and episode name in plain English as listed in the database. No trouble finding the recordings you're looking for; use any kind of player app on the laptop to play them.

---

### Post by teet on 2010-02-14
If you have mythweb set up you could always just browse to your backend on your laptop and then click on the "download" button from the mythweb interface.  You could then rename the filename to whatever you wanted in the save diaglog box.

It's not a perfect solution, but I love using mythweb because I can quickly browse through all my shows.

-teet

---

### Post by nickrout on 2010-02-14
use mythrename [http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl) **with the --link option (thats very important!)** then just use whatever file transfer programme you like to transfer them. Assuming your laptop runs linux too, you could scp or rsync them across.

On the backend, assuming your nicely titled filenames are in /var/lib/mythtv/nicenames:

```
rsync -avPp /var/lib/mythtv/nicenames/show_i_want.mpg /var/lib/mythtv/nicenames/other_show_i_want.mpg user@laptop:~/Videos/
```

will transfer them over the network to your laptop (which you may want to plug into the lan rather than do it at wireless speeds.

---

### Post by brian_hayward on 2010-03-10
Sorry i haven't posted back, i've been very busy with work and all.  i just wanted to drop another note to give an update.  I used the mythrename script and it worked great.  I higly recommend this to anybody else looking to do what i did.  Now i have a second issue.  After i got back from an extended travel session i upgraded my Mythbuntu to 9.10 and i didn't save that mythrename script to a location where i could find it again.  I've looked in all the locations listed on the mythrename wiki and i still can't find it.  can somebody either provide me with the script or let me know where to find it?  Thanks.

---

### Post by pu15e on 2010-03-10
We simply copy the files via MythWeb and run them through AVIDemux as appropriate ;-)

Cheers,
 Mattt.

---

### Post by nickrout on 2010-03-10
> **brian_hayward said:**
> Sorry i haven't posted back, i've been very busy with work and all.  i just wanted to drop another note to give an update.  I used the mythrename script and it worked great.  I higly recommend this to anybody else looking to do what i did.  Now i have a second issue.  After i got back from an extended travel session i upgraded my Mythbuntu to 9.10 and i didn't save that mythrename script to a location where i could find it again.  I've looked in all the locations listed on the mythrename wiki and i still can't find it.  can somebody either provide me with the script or let me know where to find it?  Thanks.

```
locate rename
```

---

