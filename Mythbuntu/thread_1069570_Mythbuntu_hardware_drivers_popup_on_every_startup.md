---
title: "Mythbuntu hardware drivers popup on every startup"
date: 2009-02-14
forum: Mythbuntu
---

### Post by insanity54 on 2009-02-14
I'm using Mythbuntu 8.10. I'm using proprietary Nvidia drivers, and every time mythbuntu is started up, it loads mythtv automatically, then it is rudely interrupted by the "Hardware Drivers" where you choose which proprietary hardware driver you want to use. It requires getting out the mouse/kb and closing the window every time mythbuntu starts up, which is insanely annoying.

I know that in plain old ubuntu there are "sessions" that you can assign startup programs, but in Mythbuntu there is not a GUI to do that as far as I know. I google'd a bit and found that /etc/init.d/ and ~/.config/autostart have startup scripts/programs, but in those folders, I see nothing that indicates that mythbuntu is loading the "Hardware Drivers" utility.

Where might I find the script(?) or other cause that is starting this utility at startup, so that I may disable it from running and interrupting my mythtv experience?

---

### Post by deece803 on 2009-07-25
hi there, 

firstly, try going to settings program which is in the main menu(in desktop mode). There should be an option there for auto-start apps or something along those lines. you should see the hardware drivers checkbox there in the list. uncheck it and next time you reboot it should be sweet ;)

second, i'm having the same problem except my program is synaptic. a box comes up on the start-up screen saying i don't have admin priveleges so i click close and synaptic package manager opens up. i've looked through the preferences and can't find anything to stop it opening on start-up. any ideas on what might be causing this?

any help at all will be much appreciated ;)

---

