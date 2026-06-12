---
title: "Boot with VLC + start reading media files from a given folder"
date: 2015-02-12
forum: Multimedia Software
---

### Post by pasha5 on 2015-02-12
Hi guys, 

I need your help.

I'm quite new in Ubuntu (I'm more Mac or Windows user)
But I need to come up asap with a solution to:

1. Open VLC on Ubuntu boot
2. VLC should start reading media files from a concrete local folder (ideal in Full Screen mode. there's a way to open VLC and indicate a folder to play, but how to sett it up straight away on the boot)

Thank you very much for your help in advance!
I'm very bad with codes etc. will be very thanks full for a detailed advice or instruction.

Thanks

---

### Post by mc4man on 2015-02-13
actually very simple for basic setup for a user.
Open Startup Applications (just open the Dash, start typing in, will show up around sta or so.
In the opened window click on Add
For Name use something simple like vlc-login
For Command use, replacing blue with actual  -
```
vlc -f [COLOR="#0000CD"]/path/to/foldername[/COLOR]
```
The Comment doesn't matter

If you wish more specific then post the location & name of folder
Here I usually delay some startups by a couple of sec's, that has to be manually edited it the startup file after creation, just ask...

---

### Post by pasha5 on 2015-02-16
Thank you very much for your help!

Well, I haver managed booting with VLC, which is very good, BUT:

1. I didn't specify correctly the reading folder
2. after booting it just hangs with an error message of: "Your input can't be opened" and "File reading failed" 
3. the most important, I can't do anything else now, the side bar dosen't appear. I can quite VLC, but no way to enter the startup options to remove or modify the VLC path.

Any ideas how can I get back to modify VLC boot path?

Thank you in advance!

Regards

---

### Post by mc4man on 2015-02-16
post results of 
```
ls ~/.config/autostart
```

---

