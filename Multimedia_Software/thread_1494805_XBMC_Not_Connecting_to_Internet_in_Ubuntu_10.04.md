---
title: "XBMC Not Connecting to Internet in Ubuntu 10.04"
date: 2010-05-27
forum: Multimedia Software
---

### Post by boygenuis on 2010-05-27
I recently installed XBMC and Boxee on my Linux laptop, but neither of them are connecting to the internet.  Since I'd like to try XBMC first, I'll talk about that here.  When I run the program, I do not have a Live TV icon or link on the side.  I can see my Music, Programs, Settings, Pictures, Video and Weather links on the sidebar, but my Weather page is blank as in I do not see any weather forecasts or whatever else ought to be on that page.  I thought that maybe since I was running XBMC as a user there might be some permissions issues, so I ran "sudo xbmc" and received an error message "Do_Wait: DRMWaitBlank returned -1, IRQs Don't Seem to be working correctly.  Try adjusting the vBlank_mode configuration parameter."  No idea what that means.  I've tried connecting both via Ethernet and my WiFi.  No dice.

---

### Post by derrick81787 on 2010-05-27
I had your exact same problem the day before yesterday.  Are you running 64 bit Ubuntu?  I'm not sure, but that might have something to do with it.  Either way, here are the instructions that fixed it for me:

[http://forums.boxee.tv/showpost.php?p=100377&postcount=24](http://forums.boxee.tv/showpost.php?p=100377&postcount=24)

Basically, just install [tinyproxy]("apt://tinyproxy") and in Boxee, set the host to "localhost" and the port to 8888.

If that works, please remember to mark the thread as solved.

- Derrick

---

