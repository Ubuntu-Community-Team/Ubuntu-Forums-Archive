---
title: "Mythshutdown problem"
date: 2008-11-03
forum: Mythbuntu
---

### Post by browndog289 on 2008-11-03
Hello

I have been tinkering with my mythbuntu rig over the weekend.
I have been configuring mythshutdown to shutdown the system and wake it up before a recording.
My RTC seems to like a date in unix timestamp format so I have a setwakeup.sh script that writes the time to /sys/class/rtc/rtc0/wakealarm.

I have tested this manually and it wakes up as it should.
I've added all the scripts to mythtv-setup. The system shutdown last night and came back on at 8:50PM to record a programme at 9PM but the trouble is that is hasn't shutdown again afterwards.

I thought that maybe this was because mythfrontend was set to start automatically on boot so I removed this from autostart but it still doesn't shutdown.

I've also tried setting the timeout to 15 seconds but with no luck!

If I run mythshutdown --shutdown it does shutdown, and I have made the necessary changes to the sudoers file.

Can anyone help as I'd love to get this working properly.


Thanks

---

### Post by Roebi on 2008-11-03
> **browndog289 said:**
> 
I thought that maybe this was because mythfrontend was set to start automatically on boot so I removed this from autostart but it still doesn't shutdown.


You should have it automatically run Mythwelcome instead of the mythfrontend at startup.
Mythwelcome is able to shut down, mythfrontend is not. Also Mythwelcome estimates if the system was started up for a scheduled recording and then stays on Mythwelcome; or if it was started up manually, and then automatically starts up the front end as well. Once done with the front end, exiting it will take you back to Mythwelcome, which will handle the shutdown for you.

I hope this helps.


Roebi

---

### Post by browndog289 on 2008-11-06
Ok I fixed the first problem - I had it set to not shutdown unless a client had connected - I disabled this and it now shuts down.

I removed mythfrontend from the list of started apps and it comes on and shuts down fine. However when I add /usb/bin/mythwelcome to the list of autostarted apps it doesn't shut down. Also my mythwelcome seems to always launch the frontend. I've seen screenshots on the web of mythwelcome but mine just comes up with the front end.

When I close the front end for a split second I see the mythwelcome screen before it goes back to the desktop. Am I doing something wrong? Do I need to configure mythwelcome or something?

Thanks

---

### Post by browndog289 on 2008-11-06
I just solved it with a bit of hunting around the web.

For anyone else having this problem, do the following:

Start mythwelcome (when a recording is taking place). It will probably launch the frontend but if you close the frontend you should be back at the mythwelcome page.

Press I to get to the settings page and untick automatically start mythfrontend.

Now you will get mythwelcome but not automatically the frontend but you can launch it from mythwelcome.

---

