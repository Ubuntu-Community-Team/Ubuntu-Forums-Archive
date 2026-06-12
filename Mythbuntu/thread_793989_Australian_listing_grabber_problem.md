---
title: "Australian listing grabber problem"
date: 2008-05-14
forum: Mythbuntu
---

### Post by Dionikon on 2008-05-14
I have just finished my 2nd installation of mythbuntu and almost everything works perfectly.

I am having issues with setting up the listings grabber.

I have followed the instructions here: [http://www.ozmyth.com/wiki/Configuring+MythTV+for+Australian+Digital+TV](http://www.ozmyth.com/wiki/Configuring+MythTV+for+Australian+Digital+TV)

But when I configure the video source I have no option to select Australia as the listings grabber, the only options I see are 
- "no grabber"
- "EIT only"
- "North America"

Have I missed something in the instructions?  I'm pretty sure I did everything as I should have.  My previous install had exactly the same issue.

---

### Post by nasha on 2008-05-14
I had exactly the same problem with one of my installations, for no reason at all. Thats when i made the change to Shepherd listings grabber:
[HTML]http://svn.whuffy.com/[/HTML]
Shepherd data is more reliable and much better guide data.

You can download the tv_grab_au script and put it in whichever directory its looking for it (sorry, can't recall it)

---

### Post by wombo on 2008-05-14
I also use Shepherd. Very good

---

### Post by Dionikon on 2008-05-15
Thanks guys, tried Shepherd, not quite as straight forward as it seemed to begin with but it's all working now.

My mythtv box is now 100% functional, except for my second capture card, but I can live with that for now.

w00t!
:guitar:

---

### Post by Lindsay.Mathieson on 2008-05-16
Chiming in on the shepherd love

What card is your second tuner?

---

### Post by Dionikon on 2008-05-16
The second tuner is almost exactly the same as the first.  Except the PCIe version.

It's a Dvico DVBT Plus, the one that's working is a DVBT Pro.

I read somewhere, don't remember where, that PCIe has only limited support so I figured I'd just leave it alone and test it every so often with updates. :)

---

### Post by Horticom on 2008-06-09
> **Dionikon said:**
> Thanks guys, tried Shepherd, not quite as straight forward as it seemed to begin with but it's all working now.

My mythtv box is now 100% functional, except for my second capture card, but I can live with that for now.

w00t!
:guitar:

Hi Dionikon,
My name is Horticom and I am pretty new to Linux.Trying to set up Mythbuntu.Most works well but have a great problem setting up Shepherd.
Can you please explain to me how you did this and where to install it.I tried several different possibilities.
Installed in /home/jan did not work for me.
    /home/jan is me as user.
             /home/mythtv did not work for me either.
I am thinking is all comes down to a permission problem,but I can't work out where and why.
Thanks for the help.

---

### Post by jbman on 2008-06-09
What part of the guide are you stuck on?

The setup guide for the grabber is pretty clear. If you follow it to the letter it will work.

---

### Post by Horticom on 2008-06-09
> **jbman said:**
> What part of the guide are you stuck on?

The setup guide for the grabber is pretty clear. If you follow it to the letter it will work.

I have installed Shepherd in /home/jan
When Mythfilldatabase runs automaticly it don't fills the EPg.
When I check /var/log/mythtv/mythbackend.log it tells me that Mythfilldatabase runs,but Shepherd needs to be configured.
Shepherd is configured in /home/jan

---

### Post by jbman on 2008-06-09
there is your problem.

mythfilldatabase is running as another user and not the one you configured the grabber with.

just put mythfilldatabase into a crontab for easy timed grabbing rather than stuffing around with permissions and what not with mythfilldatabase.

Try this.

as the same user as you installed the grabbed run mythfilldatabase from the command line. It will run and will download he data.

if this works all good (i think it will)

then create a crontab entry under the same user who the grabber was installed under.

don't know much about crontabs? check out this 
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

pretty easy just choose the time you want to run mythfilldatabase. 

Once you have done this turn off the mythfilldatabase in mythtv.

---

### Post by KillerKiwi on 2008-06-09
Try [gnome-schedule]("apt:gnome-schedule") if you dont know cron.

[IMG]http://gnome-schedule.sourceforge.net/gnome-schedule.png[/IMG]

---

### Post by Horticom on 2008-06-10
> **jbman said:**
> there is your problem.

mythfilldatabase is running as another user and not the one you configured the grabber with.

just put mythfilldatabase into a crontab for easy timed grabbing rather than stuffing around with permissions and what not with mythfilldatabase.

Try this.

as the same user as you installed the grabbed run mythfilldatabase from the command line. It will run and will download he data.

if this works all good (i think it will)

then create a crontab entry under the same user who the grabber was installed under.

don't know much about crontabs? check out this 
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

pretty easy just choose the time you want to run mythfilldatabase. 

Once you have done this turn off the mythfilldatabase in mythtv.

Will try that.Thanks for the info.Will let you know if it worked.

---

### Post by Horticom on 2008-06-11
> **jbman said:**
> there is your problem.

mythfilldatabase is running as another user and not the one you configured the grabber with.

just put mythfilldatabase into a crontab for easy timed grabbing rather than stuffing around with permissions and what not with mythfilldatabase.

Try this.

as the same user as you installed the grabbed run mythfilldatabase from the command line. It will run and will download he data.

if this works all good (i think it will)

then create a crontab entry under the same user who the grabber was installed under.

don't know much about crontabs? check out this 
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

pretty easy just choose the time you want to run mythfilldatabase. 

Once you have done this turn off the mythfilldatabase in mythtv.

I did exactly what you said and it seems to wrk.
Thanks very much,been bashing my head over this for a couple of weeks.
Thanks again.

---

