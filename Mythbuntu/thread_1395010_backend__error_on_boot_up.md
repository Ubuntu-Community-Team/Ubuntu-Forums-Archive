---
title: "backend  error on boot up"
date: 2010-01-31
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-31
Hi all 

Had my system running great, but now it has developed a new wrinkle. 

Yesterday I booted up the system and I got a message saying something about having a new version database. Ever since then when ever I boot up my system, my backend fails to boot properly, all the tunners show an error.

I kill the backend and restart (go in to the backend setup and then out again) Then all is well. Until I have to boot again.

I'm thinking this is the result  of an update, but am not sure what I need to do to fix it?

thanks

---

### Post by nickrout on 2010-01-31
> **benlyboy said:**
> Hi all 

Had my system running great, but now it has developed a new wrinkle. 

Yesterday I booted up the system and I got a message saying something about having a new version database. Ever since then when ever I boot up my system, my backend fails to boot properly, all the tunners show an error.

I kill the backend and restart (go in to the backend setup and then out again) Then all is well. Until I have to boot again.

I'm thinking this is the result  of an update, but am not sure what I need to do to fix it?

thanks

Stop rebooting?

where are you seeing these error messages and what exactly do they say?

---

### Post by benlyboy on 2010-01-31
The error show up a few ways.

First up  if I try to watch live tv I get the error "mythtv is using all inputs, but there are no active recordings"

Then if I go to information/system status/tuner status. I will see an error next to all, or in a few cases some of the tuners.

I get the similar result going to mythwebs backend status page, there the encoders don't show up at all when there is a miss boot.

I don't reboot often at all, but in the winter in this part of the country power cuts aren't unheard of, and if I was away and the back end falls to boot that could be a pain :)

---

### Post by nickrout on 2010-01-31
If you can do all that the mythtv-backend process is running, or you wouldn't connect and get that info at all.

I suspect your backend process is starting before the tuners are fully initialised. Try putting a 10 second delay ```
sleep 10
``` in the /etc/init.d/mythtv-backend script, near the top, and see if that fixes it. If it does you can gradually shorten the delay until it is as short as possible.

I have also seen additions to the script to test whether all the video devices have been created, and delayng until they are. That would be a technically better approach, but the sleep method will at least tell you whether I am right!

---

### Post by benlyboy on 2010-02-01
Thanks for the reply

I will look into this next weekend. I have to make a trip to Minnesota with my wife this week for medical reasons. So I may not get a chance to post an update for a few days but I will give your idea a go, and let you know how I get on.

I did look in the directory you talked about and found myth_backend.conf is this the file you were talking about?

Thanks for the info

---

### Post by nickrout on 2010-02-01
you looked in /etc/init/ but I was referring to a script in /etc/init.d/

Cheers, hope the trip is successful.

---

### Post by benlyboy on 2010-02-05
[SIZE="6"]Help[/SIZE]:-(:-(:-(


ok somehow while making the change above I screwed up and wiped the myth-backend script file

is there away to repair this...?

---

### Post by benlyboy on 2010-02-06
ok fixed it...(repaired the file)

I also added the sleep line to the file. So fare early testing has gone well, so that may have done the job.

Thanks for the help, will mark as solved after a little more testing

---

