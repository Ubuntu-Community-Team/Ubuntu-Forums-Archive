---
title: "mythtv no videos"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by klandwehr on 2007-06-19
I am new to both Ubuntu and mythtv, so I need some help.   I managed to reinstall mythtv and now have a program guide, (yeah)  but when I record a program and then try to play it back it says there are no recorded video.  If I go into previous recorded video, they are listed.  I not sure what I need to do.

---

### Post by wjston on 2007-06-19
> **klandwehr said:**
> I am new to both Ubuntu and mythtv, so I need some help.   I managed to reinstall mythtv and now have a program guide, (yeah)  but when I record a program and then try to play it back it says there are no recorded video.  If I go into previous recorded video, they are listed.  I not sure what I need to do.

Check to be sure the mpeg files have actually been recorded. If you followed the Ubuntu/MythTV guides, you should be able to do this by going to Places>Computer>Filesystem>var>lib>mythtv. If the files are not there, I would check to make sure the folder that you are saving to is correct one and, if it is, I would then check the permissions to ensure mythtv has sufficient privileges to write to this folder. If the folder is not there, you may have selected a different location to store the recordings and this has to be accessible to mythtv or, you may need to check the settings in mythfrontend to ensure that the location mythtv is storing recordings actually exists.

---

### Post by klandwehr on 2007-06-20
When I go to Places>Computer>Filesystem>var>lib>mythtv., then Recording.  All I see is a recording of a show that was on this AM  (that I wasn't recording)  and png. files from a show I did try to record last night

---

### Post by rickliner on 2007-07-01
I have a somewhat similar problem with my new setup after many reinstalls and false starts.

My "Media Library" displays only shows auto-recorded while I was watching live TV.

My "Previous Recordings" list correctly shows recordings I previously scheduled.

My /var/lib/mythtv directory shows MPG files for *both* the live and scheduled recordings, which I am able to watch with gxine.

How do I get the "Media Library" listing to acknowledge these recordings?

I don't see any relevant error messages in /var/log/myth/mythbackend.log

Thanks for any help on where to look or tinker.

---

### Post by PhatBoy on 2007-07-03
Same problem here:

- mpg and png files exist in the recordings directory

- no recordings visible in Myth via watch recordings in media library but they do show up in the previously recorded list

---

### Post by wjston on 2007-07-03
> **rickliner said:**
> I have a somewhat similar problem with my new setup after many reinstalls and false starts.

My "Media Library" displays only shows auto-recorded while I was watching live TV.

My "Previous Recordings" list correctly shows recordings I previously scheduled.

My /var/lib/mythtv directory shows MPG files for *both* the live and scheduled recordings, which I am able to watch with gxine.

How do I get the "Media Library" listing to acknowledge these recordings?

I don't see any relevant error messages in /var/log/myth/mythbackend.log

Thanks for any help on where to look or tinker.

I am unsure why you have recordings in your mythtv directory but are unable to view them using "Watch Recordings." I would suggest that you start Mythfrontend in a terminal by typing>mythfrontend and hitting enter. Once MythTV loads, trying watching a recording. It should fail as usual; however, you should have a detailed description as to why the recording was unable to load (i.e. permissions problem). Post the results and hopefully someone can help resolve this issue.

Just Thought of Something.
When you set MythTV up, could it be possible that you may have changed some of the settings in Mythfrontend? Check under "Utilities and Settings">"Setup">"TV Settings">"Playback">go to the fourth screen>make sure that the default group filter to apply is set to "All Programs." Also, make sure that "Show 'LiveTV' recordings when using "All Programs" filter is [COLOR="Red"]checked.[/COLOR]

---

### Post by MCMcButtah on 2007-07-16
I have this same problem too. What kills me is I had mythtv running perfect for a year and then 2 weeks ago I get this problem out of nowhere where my videos are missing from the watch recordings section. The videos are on the drive along with the pngs, I can play them with mplayer, I can use the mysql query browser to connect to the database and I see the recordings listed in the recordings table, I have assigned 777 permissions to the entire drive holding my recordings, and I have checked that it is not default group / all programs thing. If anyone can think of anything please post here. If I get this working again I think I will never do another apt-get upgrade.

---

### Post by wjston on 2007-07-16
> **MCMcButtah said:**
> I have this same problem too. What kills me is I had mythtv running perfect for a year and then 2 weeks ago I get this problem out of nowhere where my videos are missing from the watch recordings section. The videos are on the drive along with the pngs, I can play them with mplayer, I can use the mysql query browser to connect to the database and I see the recordings listed in the recordings table, I have assigned 777 permissions to the entire drive holding my recordings, and I have checked that it is not default group / all programs thing. If anyone can think of anything please post here. If I get this working again I think I will never do another apt-get upgrade.

As I mentioned in my previous post, starting MythTV from a terminal is one way of diagnosing a problem. Selecting "Watch Recordings" will provide some input as to why the frontend is having a problem connecting to the backend. It could be as simple as repairing your MySql table; however, it will be near to impossible to help anyone if no one tries what is suggested and reports back with the results. I also not recommending updating your systems if they are working. Many of the issues that fellow MythTV users experience are due to allowing Ubuntu to update your Myth system. I say **"if it is running well..........leave well enough alone."**

---

### Post by MCMcButtah on 2007-07-17
Thank you for the reply. I have tried to look at the output from mythfrontend on a terminal but I do not see anything obvious. I saw a suggestion about using the verbose -V option. I am going to try that tonight and see if it sheds any light on this.

---

### Post by theorganloft on 2008-01-11
Was there ever any fix for this problem?  

My new system is doing this.

---

### Post by Seantiago on 2008-01-24
As is mine. Same exact problem everyone else is having, with my "Previously Recorded" and "Media Library" files getting mixed up.

This guy fixed his stuff this way, but he's not sure why:
[http://ubuntuforums.org/showthread.php?t=516309&highlight=previously+recorded+media+library](http://ubuntuforums.org/showthread.php?t=516309&highlight=previously+recorded+media+library)

---

### Post by Seantiago on 2008-01-24
> **wjston said:**
> 
Just Thought of Something.
When you set MythTV up, could it be possible that you may have changed some of the settings in Mythfrontend? Check under "Utilities and Settings">"Setup">"TV Settings">"Playback">go to the fourth screen>make sure that the default group filter to apply is set to "All Programs." Also, make sure that "Show 'LiveTV' recordings when using "All Programs" filter is [COLOR="Red"]checked.[/COLOR]

This fixed it for for me, by the way.

---

