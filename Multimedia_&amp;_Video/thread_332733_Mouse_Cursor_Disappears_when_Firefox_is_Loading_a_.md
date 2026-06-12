---
title: "Mouse Cursor Disappears when Firefox is Loading a Page"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by PWill on 2007-01-06
This is really weird.
I just installed the latest stable nVidia drivers from nVidia.com.
The problem is, now whenever Firefox begins to load a page, my cursor disappears. I can still click things and select text, but the cursor just isn't there.
I enabled the cursor finder in the Gnome mouse settings, so I will know where my cursor is when Firefox is rendering...
[img]http://www.smoothweb.net/images/cursorgone.png[/img]

---

### Post by WakkiTabakki on 2007-01-10
Hi
Same thing happened to me, but not because I installed nvidia drivers... It also happens regardless of what I do. Here's the posting I was about to make before I found your post...

Since a few days I've had this annoying problem. Whenever the circular rolling wait-for-it mouse cursor is supposed to show, the cursor disappears completely. This happens no matter what cursor theme I use, and to both the sort-of-wait cursor with the arrow and the proper wait one. I've tried all the themes that comes with Edgy as well as a couple I got off gnomelooks.org. All other cursor types (resize, move, arrow, write etc) seems alright.

When I go into /use/share/icons and check the folders with the cursor themes, I don't get previews anymore, only a blank icon with 0:s and 1:s in it (indicating an unknown binary file). Eye of gnome crashes when I try to open one... They *are* mouse cursors, though (all files start with 'Xcur').

The prob may have started when I tried to compile and install an updated gstreamer from source. It miserably failed so I uninstalled it and made a reinstall of the repo one.
I am also a sucker for Beryl-SVN (this is why I didn't react sooner, just had it down to another temporary oddity in Beryl, but then I realized it also happens in Metacity) so it may  have someting to do with that?

[Edit] Oh, yeah, one more thing. Don't know if it's related but it seems to have started at the same time. Whenever I try to open a file with anything but the default application I get this error message stating "could not add application to application database".


I'm running
* Edgy with all the updates, including backports and stuff 
* Nvidia 97.42
* Gnome
* Beryl and Metacity (same thing happens regardless)

Does anyone have a suggestion? 
I watch movies using the comp and the cursor is hard to see on the TV as it is, so this problem really drives me up the walls...

Cheers
/N

---

### Post by Amt0571 on 2007-01-12
The same is happening to me... has anybody a solution?

Thanks!

---

### Post by Tampler on 2007-01-13
I have the same problem also. It's very annoying ](*,)  If somebody can find decision I'll appreciate that.

---

### Post by Amt0571 on 2007-01-13
If I reebot the problem sometimes is solved... altough it appears again sooner or later... I think it has something to do with Beryl.

Are all of you using Beryl?

---

### Post by Amt0571 on 2007-01-13
I've just found out that it starts doing it if I zoom in in Beryl with the option to hide the original size cursor turned on. Have turned this off for now...

---

### Post by WakkiTabakki on 2007-01-13
> **Amt0571 said:**
> If I reebot the problem sometimes is solved... although it appears again sooner or later... I think it has something to do with Beryl.

Are all of you using Beryl?

Yep, same here. It happened once when I reinstalled the nvidia drivers. And once in a while it boots up and just works with no particular reason.

If you browse a folder containing mouse cursors using nautilus, does it also fail to render previews for you guys? 
Does eog crash if you try to view a mouse cursor file (check in /usr/share/icons/Human/cursors).

Can you also not use the open-with command without getting a "cannot add application to the application database". 
It may sound far fetched, but the problems started (or at least, manifested themselves) at the same time for me.

Maybe it's time to install Feisty instead...

/N

---

### Post by nalmeth on 2007-01-20
I can confirm this problem on:
Edgy
Beryl-svn installed, but occurs with metacity too
Nvidia-driver
Gnome

When rolling busy cursor is supposed to appear, cursor just disappears. Restarting X solves the problem for a while, but it comes back.

---

### Post by PWill on 2007-01-21
Found a fix!
Open the beryl settings manager, and go to accessibility
DISABLE "Input Enabled Zoom"
ENABLE "Zoom Desktop"
Once you restart X (Ctrl+Alt+Backspace), it will be fixed!

---

### Post by WakkiTabakki on 2007-01-21
> **Amt0571 said:**
> I've just found out that it starts doing it if I zoom in in Beryl with the option to hide the original size cursor turned on. Have turned this off for now...

Yep! This solved it for me. 

/N

---

### Post by matt_risi on 2007-01-23
Also solved here, bravo xiamcitizen.

This forum rules!

---

### Post by Vodkaneat on 2007-01-25
I can fix the cursor issue using input enabled zoom, as long as I don't have 'Hide normal cursor' checked.

---

### Post by MagicalMoose on 2008-03-22
that worked great for me! Thanks!

---

