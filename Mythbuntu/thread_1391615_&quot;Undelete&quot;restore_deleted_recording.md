---
title: "&quot;Undelete&quot;/restore deleted recording"
date: 2010-01-27
forum: Mythbuntu
---

### Post by laffinet on 2010-01-27
Hi !

I'm looking for a (easy) way to restore ("undelete") a recording that was recently deleted. 

Since mythtv does't actually delete the file, just sets the recording to expire and removes it from the "recorded shows" list I'm hoping it's as "easy" as editing the database accordingly, but I have no idea how. Some easy to follow instructions would be great.

For those that are interested, here's why: I've got a user job set up that uses mythnuv2mkv to transcode the job and then deletes the original recording. Something went wrong when running that on a couple of shows, the transcoded file is rubbish but the job nevertheless deleted the recording. I'd like to recover it and rerun the job. 

Thanks for any help !

---

### Post by tgm4883 on 2010-01-27
You should be able to hit M when on the recordings page and change to the deleted shows. Then just undelete it.

By default though, I think it does delete the shows. I guess it depends on how you set it up.

---

### Post by laffinet on 2010-01-27
Thanks. I also noticed that there's an "undelete" button in mythweb.

The problem is: that doesn't seem to work. Regardless whether I do it in mythweb or via the recordings dialog, the status doesn't change. The recording remains under "deleted" and doesn't show up under "recordings".

I checked, the original file is still there. I tried with different deleted recordings, works with none.

---

### Post by laffinet on 2010-01-28
Okay, I managed to solve my problem. Sort of (see below).

In the end I found I can simply go into the recordings view, change the group filter to "deleted" (pressing "m"), highlight the recording, hit "M" again and select user jobs etc.

This obviously starts the user job again (honouring the cutlist I created earlier) and I ended up with the transcoded recording.

Still bugs me that the "undelete" bit doesn't work though.

---

### Post by neutron68 on 2010-04-08
> **tgm4883 said:**
> You should be able to hit M when on the recordings page and change to the deleted shows. Then just undelete it.

By default though, I think it does delete the shows. I guess it depends on how you set it up.
I think you're right.  My Mythbuntu 9.10 machine must be set up to delete shows when go into the recorded Programs list, highlight a show, hit the I key and scroll down to DELETE.  

I accidently deleted a show this morning.  It's gone.  :( 
It's not anywhere on the hard drive.  I looked in the /var/lib/mythtv/recordings directory to be sure...gone.  :(

Any idea where I can change the setting so the shows don't get deleted immediately - so I have time to rescue the show before I am SURE I want it gone?

Appreciated.

---

### Post by My Name on 2010-04-09
Myth can be set to expire instead of deleting. the default is to expire and delete. I'm not sure where the setting is, but it is there somewhere. Probably in the general settings bit.

---

### Post by SiHa on 2010-04-09
If they are in the autoexpire list but have not actually expired, I have found that you can get to them via the system information menu. The last page of this is the autoexpire list. If you hit 'm' on a recording, it will give you the option to expire now, or move to the 'default' group.

Edit: Just looked at the date of the OP. Duh.

---

### Post by neutron68 on 2010-04-09
Note, that I manually deleted my file.  It appears that if you do that, there is no safety net to pull the file back from.

I tried to recover the deleted video file last night.  I got parts of it, but not the whole file.

I went into the Synaptic Package manager and downloaded PhotoRec (part of the Testdisk package).  
see [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I let PhotoRec run for a couple of hours.  I put a USB hard drive onto my Mythbuntu box to catch the recovered files.  PhotoRec did recover chunks of my desired file, as well as various video files I had deleted over the last 3 months, but the whole, unbroken file I was looking for was not there. 

Oh well...  I tried.

---

