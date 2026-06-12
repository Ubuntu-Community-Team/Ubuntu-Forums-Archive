---
title: "(some more) ATI Graphics problems"
date: 2009-09-23
forum: Multimedia Software
---

### Post by humphreybc on 2009-09-23
Hi there,

Firstly let me explain my setup/situation:

----------------

I have a Toshiba Laptop (specs in my signature, resolution 1280x800) that I use at home and also _take to uni each day._ I just bought a Dell 24" LCD monitor for home, full HD (1920x1080) with HDMI input (my laptop has HDMI out). 

I want to be able to use my laptop during the day, and then come home at night, plug my LCD into my laptop via HDMI with _no fuss_ and then have my big 24" screen as my **second workspace,** where I can _drag windows across to_ (for example a movie) and watch it fullscreen on my big LCD monitor.

At the moment I am using Catalyst 9.4 drivers on Jaunty, I would use the latest 9.9 drivers but [this bug]("https://bugs.launchpad.net/bugs/423711") is preventing me from doing so until I upgrade to Karmic. I don't play many games although I have a couple of 3D games that I hardly ever play (I could give them up) and I also use Compiz, but i'm not bothered by losing that... usability over eye-candy for me. I also use Google Earth and a few other OpenGL apps.

[B]NOTE:
This is NOT a "_big desktop_" stretched setup that I want, and this is also not a _clone_ setup, but two "workspaces" - ie, both monitors have my _panel, dock and desktop icons_, but they have individual windows that can be _dragged across to either screen._[/B]

----------------

So I have a couple of questions:

1) What driver would be best for me to use? The proprietary fglrx driver from ATI or the open source radeon driver?

2) Depending on the answer to 1), how would I go about setting my system up to have the second monitor as the 2nd workspace (when plugged in), and when unplugged just have the 2nd workspace act as normal?


Many thanks for your replies,
Benjamin

P.S (I know there is a lot of information on the net about this stuff, but I have noticed most of it pertains to dual monitors of the *same make and model* set up for "big desktop" instead of two workspaces... also most of it pertains to _desktop_ computers, not portable laptops that change their screen configuration all the time.)

---

### Post by IGM0937 on 2009-09-23
It feels like you and I are the same guy.... I'm in the same exact situation as you...

I too have a laptop for uni and a Dell 24" S2409W Monitor with HDMI.

I love using my Ubuntu Desktop as most of my important stuff is on there, but I have to go back to vista so I can use my Massive screen that I love to look at HEHE

So far I tried to use the ATI Display Manager but it don't seem to have many options like in vista...

Like in Vista I want to plug in the HDMI, so that Ubuntu to switch screen from my laptop monitor to my Dell monitor and also turn it into 1080p. Have to got any ideas on how to do this...

I'll try to look on the Internet for any alternative Display Managers

---

### Post by humphreybc on 2009-09-23
What drivers are you using? I had a bit of luck last night with using the second display as an extended desktop... which wasn't what I was after but it was usable... although making windows fullscreen didn't work properly (it covered both monitors instead of just one).

Basically I edited my xorg.conf file to force the Dell 24" monitor to use its native resolution of 1920x1080, and then I unchecked mirror displays under Preferences > Display and then dragged the big display to the right of my screen and set its resolution.

I logged out and logged back in and it sort of worked, and with a bit of tweaking I had it working okay but I had to change my Cairo Dock settings to get it to position itself in the middle of my laptop screen, and I had to change my wallpaper because my current one was stretching and was pretty ugly....

Good thing is that I unplugged it just now to go to uni for today and when I booted into Ubuntu with the external unplugged it started up fine, all I had to do was re-align Cairo Dock and change my wallpaper back. I'm not sure what's going to happen when I plug it back in tonight though. I'd like to think my settings will still be saved in my Xorg.conf file and I should be able to plug it in, log out and then back in and it should work.... but I'm not too sure.

Hopefully, fingers crossed, that the 9.10 Catalyst drivers released with Ubuntu Karmic 9.10 fix the problem where "Xinerama" is greyed out in CCC, and then once we can enable that, we should be able to maximise windows and make them fullscreen on either monitor, instead of across both.

I emailed ATI to see if this was the case with the new drivers.

P.S Compiz seemed to work fine with this setup as well... but I'm starting to shy away from Compiz... metacity does the job good enough until Compiz plays nicer with ATI and fullscreen video.

---

