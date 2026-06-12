---
title: "Can't play or rip DVDs"
date: 2010-01-02
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-01-02
I used to be able to do both in Mythbuntu 8.10, but now I've upgraded to 9.10 I can't do either.

I have enabled proprietary codecs via the Mythbuntu control centre, which I seem to remember was all I had to do in 8.10 to get DVDs to work.

I noticed that the location of DVDs in the frontend setup was given as /dev/dvd, which didn't exist. I've changed it to /media/cdrom, which is where DVDs seem to get mounted. Was that sensible?

I'm hoping there's something simple I can do to get DVDs working again, in which case if anyone can tell me what it is, that would be great. If it's not likely to be something simple, what's the next thing to try?

Thanks
NM

---

### Post by klc5555 on 2010-01-02
It may be looking for the scsi device label for the dvd removable drive, since Ubuntu is all scsi all the time, even when the drive is IDE or SATA. Something along the lines of /dev/sr0, /dev/sr1, or similar.

---

### Post by ubnewbie2 on 2010-01-02
/dev/cdrom and /dev/dvd  are both links to the required device aren't they?

---

### Post by klc5555 on 2010-01-02
> **ubnewbie2 said:**
> /dev/cdrom and /dev/dvd  are both links to the required device aren't they?

They should be, but in point of fact by default (at least in the all-scsi Ubuntu versions 8.04 through 9.04) /dev/cdrom works, while /dev/dvd usually seems to generate a "no such device" error. Substituting the scsi device label (/dev/sr0 or similar) for /dev/dvd wherever it occurs in the Mythtv frontend setup was the usual solution for Mythtv. Likewise for any other players/software that by default look for "/dev/dvd" 

I don't know whether this behavior was corrected in 9.10.

---

### Post by NautiusMaximus on 2010-01-03
OK, I've figured it out now, I think it was just a permissions thing. The directory in which videos are stored was read-only.

Once I made it read and write, everything just worked again. By that time, I'd set the location of the DVD drive to /media/cdrom, which is where it seems to be. I didn't try it with the default value of /dev/dvd.

I can completely understand why it was unable to rip DVDs if it couldn't write to the directory, but it's a bit weird that it couldn't play them either (which it now can). Still, it works, so I'm happy.

Note to MythTV developers: would it be possible for the software to issue error messages in cases like this rather than just not doing anything? I would have figured this out a lot sooner than I did if it simply gave a message like "access denied", and quicker still if it had even told me which folder it couldn't access.

---

### Post by ubnewbie2 on 2010-01-03
> **NautiusMaximus said:**
> 

Note to MythTV developers: would it be possible for the software to issue error messages in cases like this rather than just not doing anything? I would have figured this out a lot sooner than I did if it simply gave a message like "access denied", and quicker still if it had even told me which folder it couldn't access.

Was there nothing in the error log?

---

### Post by NautiusMaximus on 2010-01-08
> **ubnewbie2 said:**
> Was there nothing in the error log?

Don't know. My point was that a message on screen would be useful.

---

### Post by YogiPaolo on 2010-01-09
I am having the a "no rip" issue as well. I found a reference in the forums about a "missing path" but I'm not sure where the path needs to be added - the database or the frontend setup. I have storage directories set up in the frontend and backend. All directories are owned by mythtv and set 775.

Here are the links referred to above:
> DVD ripping does not work until 'Directories that hold videos' is filled with a valid path
[https://bugs.edge.launchpad.net/mythbuntu/+bug/469583](https://bugs.edge.launchpad.net/mythbuntu/+bug/469583)

I am not sure where else I can add a valid path for ripping dvds

A line in /var/log/mythtv/mythfrontend.log 
states " I can't rip, as i have nowhere to put finished files. Is mythvideo installed?"

---

### Post by Xailia on 2010-02-02
Make sure you have a video directory specified in the frontend (not the rip directory, but a video directory)

setup->media settings->video settings->General Settings

---

