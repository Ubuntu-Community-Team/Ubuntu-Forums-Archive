---
title: "Frontend crashes at startup"
date: 2009-06-23
forum: Mythbuntu
---

### Post by chrispoole on 2009-06-23
Hi guys,

I'm new to MythTV, so hoping someone can help me diagnose this.

When I start my frontend up (also the backend), the frontend starts, but then freezes as it shows the window where it caches the theme imagery.

I'm just left with a bunch of black and grey gradients (I'm using Mythbuntu-wide theme).

This is what frontend.log shows:

    Starting mythfrontend.real..
    2009-06-22 10:35:53.384 New DB connection, total: 2
    2009-06-22 10:35:53.384 Connected to database 'mythconverg' at host: localhost
    2009-06-22 10:35:53.385 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
    2009-06-22 10:35:53.385 Enabled verbose msgs:  important general
    2009-06-22 10:35:55.384 Primary screen 0.
    2009-06-22 10:35:55.384 Using screen 0, 1024x768 at 0,0
    2009-06-22 10:35:55.385 Switching to wide mode (Mythbuntu-8.04-wide)
    get fences failed: -1
    param: 6, val: 0
    2009-06-22 10:35:55.717 Using the Qt painter
    2009-06-22 10:35:55.717 JoystickMenuClient Error: Joystick disabled - Failed to read /home/chris/.mythtv/joystickmenurc
    2009-06-22 10:35:55.717 lirc init success using configuration file: /home/chris/.mythtv/lircrc


I'm not sure what's wrong here, can anyone help?

Thanks.

---

### Post by klc5555 on 2009-06-23
Do you have ATI Radeon graphics? If so there's a known bug.

But there's a workaround. In some cases the mythfrontend can be started from a command prompt by:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

If this workaround does it for you, then David Dean shows how to automate it here:

[https://lists.ubuntu.com/archives/ku...ay/074607.html](https://lists.ubuntu.com/archives/ku...ay/074607.html)

---

### Post by chrispoole on 2009-06-24
Unfortunately not.

It's an older model Mac mini (Core 2 duo, Intel 945GM chipset graphics).

If it's connected to my computer monitor, it works ok.

If it's connected to my TV via composite output, this happens.

Any ideas?

---

### Post by TravisEvans on 2009-06-26
Hi I am extremely new to this and am looking for help.
Yes I do have an ATI graphics card its a radeon something with 256 ram and 256 bit
anyway I'm trying to do this Mythbox setup and I can't get anywhere, all i get is a black screen with an outlined Grey beveled rectangle and thats it. If i hit a lot on the arrow keys i then get a different outline and i can move a box up and down to make a choice. But i see no text at all with anything. so if i hit escape and then chose the lower option i finally get the desktop. I get the same thing when i try to configure it like i need to. and I tried disabling all the theams to see if some odd default would work but no luck. here is a log file that i was able to make, again i just want to record tv with this computer and then watch it here and there. I have it coming in from an intenna and I know it all went to digital but with this same cord i can plug it into a tv in my room and watch tv just fine, an old crt tv, the antenna is really really big on top of our house and i live in the city so...

here can anybody just help me i don't even know how to create a new thread in this thing or a post. I have never used forms really ever.
I'm 19 I've been puttzing with computers for a long time and i have built six for firends and family. 

man this is odd I hope that error log made it on here as an attachment.

Ok well I hope i can get help here and there I am just gonna post this everywhere and hope i can get some help set up.

Travis Evans

and my error log text is too big so...

It says to put this link somewhere?
[http://mythbuntu.pastebin.com/f3633a24](http://mythbuntu.pastebin.com/f3633a24)

---

