---
title: "trying to view an online webinar, get unsupported OS"
date: 2013-09-13
forum: Multimedia Software
---

### Post by msousa on 2013-09-13
Hi,

When trying to view an online webinar, for example, any of those here:

[http://www.robotics.org/robotic-content.cfm/Robotics/Webinars-Education/id/robotic-content.cfm?id=127](http://www.robotics.org/robotic-content.cfm/Robotics/Webinars-Education/id/robotic-content.cfm?id=127)

picking any one of them, for example:

[https://www1.gotomeeting.com/register/643549817](https://www1.gotomeeting.com/register/643549817)


I get:
**"Unsupported OS**

                                                     [FONT=arial][SIZE=2]This recorded Webinar is only available for Windows 2000 or higher."[/SIZE][/FONT]

Is there a way for me to view this in Ubuntu 12.04?

Thanks...

Mike

---

### Post by kostkon on 2013-09-13
You could try using [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to switch your user agent string to something that will be accepted.

---

### Post by ajgreeny on 2013-09-13
> **kostkon said:**
> You could try using [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to switch your user agent string to something that will be accepted.

@msousa.

Yes, I can confirm for you that it works if you choose, for example **MSIE 8 for Windows 7** in User-Agent Switcher

---

### Post by msousa on 2013-09-16
Thanks for the info. I installed the User Agent Switcher and that got  further. I then got a request to install Gstreamer so I installed,  ubuntu-restricted-extra:

```

$sudo apt-get install ubuntu-restricted-extras

```

and that got to the point where it asks:

```

Required plugin could not be found
Python (v2.7) requires to install plugins to play media files of the following type: video/x-asf-unknown decoder

```

What do I now install to get past the video/x-asf-unknown decoder request?

Thanks...

Mike

---

