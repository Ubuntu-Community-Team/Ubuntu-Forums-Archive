---
title: "Mythbuntu 7.10 : screen saver"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by Sdx1978 on 2007-09-20
Hi all,

I installed Mythbuntu 7.10 on a PC as mediacenter. When watching a video, the screen saver is turning on every 10 minutes:
- the mouse appears
- the image is getting black

Could you tell me which file to modify to remove this option ? It is quite annoying to make an action every 10 minutes to avoid complete black screen.

Thank you

---

### Post by leech on 2007-09-20
I'm having the same issue, in the middle of watching a DVD the mouse pointer appears, then the screen fades out.

It's been touch and go, I'll do some updates and then it'll work right (the screensaver stays off, and when sitting idle, DPMS will turn off the monitor) but the last time I updated everything, it's simply been turning on the screensaver during DVD playback and doesn't turn off the monitor when it sits idle.

Hopefully by the time Gutsy is released, it'll work right.  

Everything else works pretty well, though I'm still wondering why it sets up the mythbuntu.org repository, yet can never download from it.

Leech

---

### Post by oddessy74 on 2007-09-20
Yep I am in the same boat and would love to be able to disable or fix this problem.   :(


Edit:

Goto the Mythbuntu Control Center and start a console

su [account] "Use the account that is set to auto login to mythbuntu"

gnome-screensaver-preferences  "from here disable the screensaver"

---

### Post by Sdx1978 on 2007-09-25
Hello again,

I tried disabling DPMS, I believed to do it in my xorg.conf file ... but no change.

Still that black screen starting 10 minutes after the movie starts ... any idea ?

I updated my mythbuntu distrib with no more luck ;-)

Thanks for ur help !

---

### Post by superm1 on 2007-09-26
There has been a variety of mixed reports upon this.  

To clarify towards what everyone is experiencing:

Is it literally a *fade* to black, or does it just go black instantly?

A fade to black indicates gnome-screensaver is kicking in for some odd reason.  

If its an instant cut to black, this is the 'X' screensaver or dpms kicking in.

Hopefully we can narrow this down.  I'd like to take care of it before our next disk :)

---

### Post by Sdx1978 on 2007-09-26
Hi,

in my case, it is a *fade* to black !

First the mouse cursor appears, then the screen fades to black. When moving the mouse, or pressing a key, the fade to black stops, and screen comes back to normal.

Do you any temp solution for that problem ?

Thanks

---

### Post by superm1 on 2007-09-26
> **Sdx1978 said:**
> Hi,

in my case, it is a *fade* to black !

First the mouse cursor appears, then the screen fades to black. When moving the mouse, or pressing a key, the fade to black stops, and screen comes back to normal.

Do you any temp solution for that problem ?

Thanks
Well i'm still trying to narrow down the cause.  It's appearing to be because now gnome-screensaver is being launched setuid/setgid due to some changes with gdm likely.  For now, the best solution is to disable it via the above method. (su username from a m-c-c terminal followed by gnome-screensaver-preferences)

---

### Post by Gouz on 2007-09-26
Try to see if the power mangament is conflicting and then the screensaver options.
If everything is as it should be then maybe it is a bug.
Go to options and change your Xv, X11/Xv to X11 X11(Ximage/Shm) of the other way test is couple of time and best luck ;)

---

### Post by Sdx1978 on 2007-10-01
> (su username from a m-c-c terminal followed by gnome-screensaver-preferences)

That works fine, thank you ...

What a good think not to have to move during a movie !!

---

### Post by ian6 on 2007-10-04
If you're using mplayer, adding

stop-xscreensaver=1

in ~/.mplayer/config should fix it.

---

