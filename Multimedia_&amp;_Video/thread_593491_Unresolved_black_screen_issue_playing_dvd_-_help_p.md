---
title: "Unresolved black screen issue playing dvd - help please"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by bwallum on 2007-10-27
I need help please. When I play dvds I get a blank screen exactly 10 minutes after the last mouse event. When I move the mouse the video returns. Audio remains throughout.  I am running VLC player and have the 'Disable Screensaver'' option on. 

I have tried different times with the Gnome screensaver (just in case VLC didn't disable) without any effect on the timing of the blank screen.

I have completely removed and re-installed VLC, no change. I have completely removed Compiz and reinstalled, no change.

The exact rig I am running on played dvds fine with VLC and Fiesty.

Does anybody have any idea how I can fix this please. I have made a similar post in Absolute Beginners but not received any responses so I am posting here. Apologies for any duplication.

Regards
Bob

---

### Post by Rinzwind on 2007-10-27
Hello is this a laptop?

Did you check 
preferences > power management?

---

### Post by asphixmx on 2007-10-27
Seems to me a power saving issue, rather than a screen saver issue. With the screensaver preferences, there is a "power saving" button (on Gutsy Gibbon). There, is a slider to setup the inactivity for the display. Maybe you should increase the time...or cancel it at all. If it doesn't work, check the bios on your computer, maybe the energy saver from the bios is turning off your display. Also, if you are using a laptop, check the energy saver settings.
Greetings.

---

### Post by bwallum on 2007-10-27
Thanks guys.

It is a PC and when in 'Power Management' both timeouts are set for 'never'. ACPI is disabled in BIOS at the moment.

Problem still with me. What's next??
Bob

UPDATE: I'm getting some odd screensaver behaviour. When I set screensaver time to 1 minute and activate it, the screen flashes at 1 minute but the screensaver does not kick in.

UPDATE2: the Screensaver has returned. Not too sure why, i just did some work in OpenOffice and Gmsh. The Screensaver kicked in as normal and is now working normally. Blank screen issue still persists.

---

### Post by Evagrios on 2007-12-01
I have the same problem. It doesn't matter what player I use, or if that player is set to disable screensaver or not. I have turned of both screensaver and pover saving, but it still turns the screen off after ten minutes. 

I looked in the BIOS but I can't find any setting relevant to the problem - are there more options available that I can't see by entering the BIOS the normal way (in my case by pressing f2 at startup)?

This is really annoying - do I have to boot up vista to watch a movie on my laptop?

---

### Post by Evagrios on 2007-12-02
bump

---

### Post by bwallum on 2007-12-02
No, don't bump your computer, it won't like it!

Have a look at this link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947]("https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947")
[http://ubuntuforums.org/showthread.php?t=584406&p=3651954]("http://ubuntuforums.org/showthread.php?t=584406&p=3651954")


riverfr0zen has some interesting workarounds, there are others...

Try to read it all before doing anything, I started out removing a file and regretted it. In the end I used Movie Player for playing dvds and don't have the problem. The root seems to be in Gnome so i guess it will get resolved eventually for VLC player.

Regards
Bob

---

### Post by bwallum on 2007-12-02
more interesting stuff here ...

[http://www.shallowsky.com/linux/x-screen-blanking.html]("http://www.shallowsky.com/linux/x-screen-blanking.html")

---

