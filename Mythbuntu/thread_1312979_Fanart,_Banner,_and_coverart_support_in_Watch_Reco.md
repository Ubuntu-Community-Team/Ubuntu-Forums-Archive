---
title: "Fanart, Banner, and coverart support in Watch Recordings"
date: 2009-11-03
forum: Mythbuntu
---

### Post by williammanda on 2009-11-03
I've looked over the wiki and can't find any real info for the Fanart, Banner, and coverart support in Watch Recordings. I'm not using the standard storage group setup with mythtv .22 since it can't play .vob & iso files. I have setup recordings and live tv storage groups on both backends. I get the coverart & fanart for recordings on the master backend but not the slave backend. Is there any setup for this?
Thanks

---

### Post by shocksafe on 2009-11-03
Edit: sorry misread the end of your post read this - 
[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)
Specifically the _setup without storage groups_ part.


Try using jamu.
[http://www.mythtv.org/wiki/Jamu](http://www.mythtv.org/wiki/Jamu)

If your using mythbuntu 9.10 it's installed by default. Not sure about earlier releases.

I haven't set up a config file as descrbed on the jamu wiki above and it works fine. heres what I do

in a terminal
#/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -M
This should mass update your videos directory.

#/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -MW
This should do your recordings directory.

You can run the videos one with -MI instead of just -M for interactive mode I think that is more acurate as it will sometimes give a choice between multiple matches to the query. If not interactive I think it just skips these.

Then set them up as cron jobs

#crontab -e

add the following
00 24 * * * /usr/share/mythtv/mythvideo/scripts/jamu.py -l en M > /home/usr(replace with your user)/tmp/jamu_videos.log
30 24 * * * /usr/share/mythtv/mythvideo/scripts/jamu.py -l en MW > /home/usr(replace with your user)/tmp/jamu_recordings.log


Numbers at front set time for job ie 12:00 and 12:30 respectively above
2nd part is the script and then the options
The part after  > is to pipe the output to a log file, can be anywhere just create them first.

---

### Post by williammanda on 2009-11-03
shocksafe
Thanks for the info!
To clarify things...I'm running ubuntu 9.10 and mythtv .22 (used mythtv control center to load mythtv). I had read the mythtv transistion guide previously, my reference in the earlier post of not being able to play iso or vob files came from that info. But I'm not sure your reply answers my question...I get the coverart & fanart for recordings on the master backend but not the slave backend. Is there any setup for this?
I have mythtv setup like .21 since the new storage group setup in .22 which has the limitations of video playback. I have setup the master backend to export through nfs all the directories...banner, coverart and fanart. The slave backend has fstab entries for these as well. What is interesting is that the slave backend worked this morning (showed all art work for recordings) but later on it doesn't do it.

---

### Post by shocksafe on 2009-11-03
Yeah sorry, as I said in my edit, I misread your post.
I'm not running multiple backends so I'm not sure I understand entirely. I would have thought your directories for fanart etc would be on the master backend and then shared and mounted on the frontend machines where you would point each myth frontend at these mounted directories. Then run a cron job on the back end to update it all with jamu.

Other than that and without actually doing it I'm out of ideas.


Cheers

---

