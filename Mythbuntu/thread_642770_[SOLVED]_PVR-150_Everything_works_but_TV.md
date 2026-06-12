---
title: "[SOLVED] PVR-150 Everything works but TV"
date: 2007-12-17
forum: Mythbuntu
---

### Post by ubuntology on 2007-12-17
Hi, I have Mythbuntu 7.10 installed on a machine with a PVR-150. Everything works beautifully except for watching TV. When I hit OK on the remote while Watch TV is selected, the screen blanks for about 3-5 seconds, then comes back to the main menu.

All of this hardware was working in Mythdora 2 weeks ago, and if I do cat /dev/video0 > /tmp/test.mpg
I can watch that video file.

The video card is a PNY nVidia 5200. This happens whether I am using a monitor on the VGA port or a TV on the svideo port.

I believe my mythtv settings are correct, but would be happy to post logs, conf files, etc. if needed.

Can anyone help? I'm out of ideas.

---

### Post by ubuntology on 2007-12-17
Just to double-check the hardware, I installed mythdora. Watching TV works there.

Can anyone help?

---

### Post by majoridiot on 2007-12-18
yer shooting in the dark here without providing more info ;)

look in your logs @ /var/log/mythtv/mythbackend.log and see what sort of errors
it's giving.  post anything suspicious you might find here.

you did not mention- is this livetv only?  do recordings record and vew correctly?

---

### Post by OffAxis on 2007-12-18
> When I hit OK on the remote while Watch TV is selected, the screen blanks for about 3-5 seconds, then comes back to the main menu.
How about the keyboard?
Does it work as expected?
Here's a listing of the default keyboard settings
[http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.1]("http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.1")

depending on your remote's config file, it may not be configured how you would think.

---

### Post by ubuntology on 2007-12-19
Sorry guys, I'm an idiot. On the very first install screen, where it asks for the mythtv IP address, I changed it from 127.0.0.1

---

