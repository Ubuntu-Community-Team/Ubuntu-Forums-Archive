---
title: "Boxee Beta 64bit"
date: 2010-05-15
forum: Multimedia Software
---

### Post by smuggly on 2010-05-15
Ive got the new beta working in ubuntu 64 bit lucid 10.4. But, I have to go to admin/sys monitor and end the boxee "sleeping" process B4 it will start again after exiting The app? Id sure like to fix it. Anyone have any ideas? Thanks Tom

---

### Post by Cowboybebop79 on 2010-05-18
Hi Smuggly I have had a quick look around for a bash script and found this which might solve the problem.

```

#!/bin/sh
SERVICE='inkscape'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    killall inkscape
	inkscape
else
	inkscape
fi

```

it is a bit basic but it does the job all you would need to do is find out what the name of the boxee process is by running ps aux in terminal.

---

### Post by derrick81787 on 2010-05-27
How did you get Boxee working?  I've been trying to do the same, and I have the application "working" (as in it comes up and I can navigate the menus and stuff) but none of the online videos, like Hulu or Youtube, play.  I just get a blank screen.  Did this happen to you?  If so, how did you overcome it?

- Derrick

---

### Post by Cowboybebop79 on 2010-06-02
Do you have restricted extras installed from the repositories and or medibuntu repository nonfree codecs?

---

### Post by derrick81787 on 2010-06-02
> **Cowboybebop79 said:**
> Do you have restricted extras installed from the repositories and or medibuntu repository nonfree codecs?

I know I had the flash player installed, but I don't remember which codecs I had.  I ended up reinstalling Karmic, and I pretty much have Boxee running now.  Other places that I've looked said that there have been problems with Boxee in Lucid, which is why I downgraded.  It sounds like smuggly is one of the minority of users who actually got it working in Lucid.

The only problem I'm having now is that the UI is really slow unless I run Boxee as root.  I haven't figured out why running as root makes a difference, though, but it definitely does.  Once I get this working as a normal user, Boxee will be running perfectly on Karmic.

- Derrick

---

