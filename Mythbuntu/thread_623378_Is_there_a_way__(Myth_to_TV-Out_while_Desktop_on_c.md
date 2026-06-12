---
title: "Is there a way?  (Myth to TV-Out while Desktop on computer monitor?)"
date: 2007-11-25
forum: Mythbuntu
---

### Post by wilberfan on 2007-11-25
I installed Mythbuntu a few days ago, and I'm still climbing that learning curve (as multiple re-installs will attest to!).

I selected "TV-OUT" in the install options, so when it booted, my computer monitor went blank--and all the output was to the TV (I had an s-video cable running from my GeForce 5200 to the TV).   To configure anything, I had to drag the keyboard and mouse into the next room (!).

After some experimentation, I managed to get two screens configured (TV and LCD monitor)--and managed to get the myth output to the TV and an xfce desktop on the monitor.

What I found, though, was that if I opened, say, Firefox from the computer desktop, the browser window would open on the TV.   It's tough to use firefox sitting in the next room (and at an angle, to boot!)!

What i'd like to be able to do (and I'm not convinced it's possible):  Have the mythtv output (livetv, video, music, etc) always go to the TV-OUT, and all other computer-related stuff  (firefox, thunar, terminal, settings windows, etc) show up on the computer LCD.

Is this do-able?

Plus, I haven't been able to figure out the difference between "twinview", "mirror", and "xinerama", etc.   Is there some combination of those that would enable what I'm trying to do?

---

### Post by foxbuntu on 2007-11-26
It is doable. However more work than it is most likley worth to you. If you enable the VNC service you can use that to access that machine remote to manage it. 

Basically Twinview is Two monitors same desktop. Mirror is similar but the there is only one desktop total where is twinview the desktops are the same but operated seperatly. xinerama is what you are looking for (dual desktops). None of these setups are easy to do but are well documented in Wiki's

---

### Post by wilberfan on 2007-11-26
I might settle for the same desktop....

Thanks for the explanation!

---

### Post by Lester_Burnham on 2007-11-26
Hi,

I have one machine which has a nVidia video card and is using twinview. (I that is what it is)

When I launch Mythfrontend, I launch it to a display 1.

Down near the bottom of this page [http://gentoo-wiki.com/HOWTO_X_Window_through_Hauppauge_350_TV_Out](http://gentoo-wiki.com/HOWTO_X_Window_through_Hauppauge_350_TV_Out)

It doesn't come without promlems though, as I think I needed to tell mplayer etc. to launch on that screen as well. There must be easier ways to do it in xorg.conf

Lester

---

### Post by Whiffle on 2007-11-26
[http://www.extremetech.com/article2/0,1697,2172587,00.asp](http://www.extremetech.com/article2/0,1697,2172587,00.asp)

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)

---

