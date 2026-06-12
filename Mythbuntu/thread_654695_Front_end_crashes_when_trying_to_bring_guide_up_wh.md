---
title: "Front end crashes when trying to bring guide up while watching TV"
date: 2007-12-31
forum: Mythbuntu
---

### Post by GLMontyWV on 2007-12-31
As the title says, watching TV, hit the S key to bring up the schedule, works for about a half second and then the front end disappears taking me back to desktop.  Just installed Mythbuntu this weekend, watching TV, watching recordings and Schedules Direct for recording is working great, just this crash when I try to bring up the guide while watching TV.

Thanks!

Monty (loving Mythbuntu!)

---

### Post by volkswagner on 2007-12-31
I don't want to hijack but I have a similar problem.  

Rather than hitting S I hit M to bring up the guide.  All is ok until I hit enter to change the channel to the selected channel via the guide.  My frontend crashes bringing me to my desktop when selecting a channel this way. I would be interested if you get the same results.

OK Just verified hitting S while viewing live tv closes mythfrontend.  I think one setting that does change the behavior a little bit is in TV settings enable check box for allow browse mode or somthing like that.  When enabled the guide will display until I select a channel.  When disabled frontend will crash immediatly.  

I am running Mythbuntu AMD64 7.10

---

### Post by volkswagner on 2007-12-31
Strange.  I disable browse mode in TV settings and guide crashes.  I changed it back enabled browse mode in TV settings and now when I hit M for guide I get a popup window with five or six choices, if I select guide the frontend will crash, If I select, "select browse mode" the lower part of the screen shows current show info, arrow up/down will show info for prev/next channel, and arrow left/right displays half hour increments.  Anyway I can change the channel browsing in this fashion.  I am not sure why the behavior will not go back when resetting to my original TV settings allow browse.

WOW I am sure this is more confusing.  I will stop now!

---

### Post by GLMontyWV on 2007-12-31
Yep, sounds like we pretty much have the same problem.

Monty

---

### Post by GLMontyWV on 2008-01-01
> **volkswagner said:**
> I don't want to hijack but I have a similar problem.  

Rather than hitting S I hit M to bring up the guide.  All is ok until I hit enter to change the channel to the selected channel via the guide.  My frontend crashes bringing me to my desktop when selecting a channel this way. I would be interested if you get the same results.

OK Just verified hitting S while viewing live tv closes mythfrontend.  I think one setting that does change the behavior a little bit is in TV settings enable check box for allow browse mode or somthing like that.  When enabled the guide will display until I select a channel.  When disabled frontend will crash immediatly.  

I am running Mythbuntu AMD64 7.10

Posted the question over on the MythTV mailing list and the first reply suggested that in may be a video drive issue.  Went to the Restricted Drivers Manager and enabled the nVidia driver for my onboard video.  Took two reboots (first one the monitor said the signal was out of range) and everything is working great.  You might give it a shot.

Monty

---

### Post by laga on 2008-01-01
Don't you get a message asking you if you want to file a bug report? If yes: please report it so we can fix it.

If not: please install the "apport-gtk" package. Now you should be asked if you want to report a bug if it crashes again :)

Thanks!

/me wanders off wondering if apport is installed or not...

---

### Post by GLMontyWV on 2008-01-01
> **laga said:**
> Don't you get a message asking you if you want to file a bug report? If yes: please report it so we can fix it.

If not: please install the "apport-gtk" package. Now you should be asked if you want to report a bug if it crashes again :)

Thanks!

/me wanders off wondering if apport is installed or not...

Nope, I've never seen anything requesting a bug report.  Would this be a bug since it appears the issue is an incorrect video driver?  

Apport was installed, apport-gtk was not but is now.  Should I go back and recreate the bug?

Thanks, Monty

---

### Post by volkswagner on 2008-01-01
I am afraid to enable the restricted driver.  I am running ATI 1250 onboard.  This is my second install.  The first install I enabled restricted driver (thought it was required to use TV-out) by following instructions manual download and install of latest ATI drivers.  Well I was very unhappy with the results on LCD monitor, and less impressed on S-video out to CRT TV.  The screen resolutions are far too limited.  I am not sure how I will proceed now.

  :(

---

### Post by volkswagner on 2008-01-02
Well no luck here in ATI land.  I enabled the restricted drivers and rebooted (twice) still no joy.

---

### Post by GLMontyWV on 2008-01-03
> **volkswagner said:**
> Well no luck here in ATI land.  I enabled the restricted drivers and rebooted (twice) still no joy.

Might try adding a cheap nVidia card, mine is working perfect now.  Got my Mountaineers recorded tonight, couldn't be much happier!  :)

Monty

---

### Post by volkswagner on 2008-01-03
Well I just installed Envy and can get guide to display, and can select channel via the guide.  The only problem is the current channel does not initialize into upper right window.  It displays upper left and is distorted.  

Definitely video driver issue.  If I get ambitious I may install latest ATI drivers.

---

