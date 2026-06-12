---
title: "MythFrontend startup issues, fresh 14.04 / MythTV 27"
date: 2015-11-23
forum: Mythbuntu
---

### Post by wpcprez on 2015-11-23
Hello all,
Anyone have startup issues with mythfrontend? Every time I reboot I get the select country option. I don't reboot that often but it always happens. Anyone know a hack to get it to stop doing that? 

Thanks,
Johnny

---

### Post by philip7 on 2015-11-23
Are you able to get to the mythfrontend or are you stuck in the "select country option"?

The only time I've had that problem is when there was an issue connecting to the backend, but I was always stuck in the country option and couldn't get Frontend to load, it sounds like you are able to get to the frontend.

Something else you might want to try is delaying the time before the frontend starts, just google "delay mythfrontend startup", it might be caused by your frontend starting before your backend.

---

### Post by wpcprez on 2015-11-23
> **philip7 said:**
> Are you able to get to the mythfrontend or are you stuck in the "select country option"?

The only time I've had that problem is when there was an issue connecting to the backend, but I was always stuck in the country option and couldn't get Frontend to load, it sounds like you are able to get to the frontend.

Something else you might want to try is delaying the time before the frontend starts, just google "delay mythfrontend startup", it might be caused by your frontend starting before your backend.

I am able to get in after I select country. I've only seen this when the backend doesn't know the front end and starts it up with default settings. But the front end still has all of my settings I configured it for like which HDMI to talk to for audio and etc. It's very strange. I wonder if it's some how related to my upgrade from 26.x to 27.x?

---

### Post by wpcprez on 2015-12-03
> **wpcprez said:**
> I am able to get in after I select country. I've only seen this when the backend doesn't know the front end and starts it up with default settings. But the front end still has all of my settings I configured it for like which HDMI to talk to for audio and etc. It's very strange. I wonder if it's some how related to my upgrade from 26.x to 27.x?

what's strange is one of my frontends doesn't do it anymore but my backend / frontend still does it every reboot. weird....

---

### Post by afremont on 2015-12-05
> **wpcprez said:**
> what's strange is one of my frontends doesn't do it anymore but my backend / frontend still does it every reboot. weird.... 

I'm assuming that it's launching the setup program.  Can you simply exit out of it and then start the frontend?  If so, I was having a similar problem.

You probably need to add a sleep statement to mythfrontend to wait for the backend to be ready.  I have this problem with a box that uses an SSD for the Linux part.  Everything comes up so fast, that the network isn't ready so the backend isn't ready when the frontend starts.  I modified /usr/bin/mythfrontend like this:

#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007
[COLOR=#ff0000]**/bin/sleep 5**[/COLOR]
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0
....

The sleep command gives the network time to start before the frontend starts.  You may see the "network connected" thingy show on the screen.

---

### Post by wpcprez on 2015-12-05
> **afremont said:**
> I'm assuming that it's launching the setup program.  Can you simply exit out of it and then start the frontend?  If so, I was having a similar problem.

You probably need to add a sleep statement to mythfrontend to wait for the backend to be ready.  I have this problem with a box that uses an SSD for the Linux part.  Everything comes up so fast, that the network isn't ready so the backend isn't ready when the frontend starts.  I modified /usr/bin/mythfrontend like this:

#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007
[COLOR=#ff0000]**/bin/sleep 5**[/COLOR]
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0
....

The sleep command gives the network time to start before the frontend starts.  You may see the "network connected" thingy show on the screen.

oh you're probably right. I used an old SSD on this box when upgrading to 27 and it is probably loading too quickly. Thanks for the tip. I'll have to modify my script and see what happens next reboot. Thanks!

---

