---
title: "DVD Playback"
date: 2013-10-10
forum: Multimedia Software
---

### Post by jamesfbays on 2013-10-10
I essentially asked this question before[URL="http://ubuntuforums.org/showthread.php?t=2172416"]

http://ubuntuforums.org/showthread.php?t=2172416[/URL]

The answers that I received worked on a Lubuntu system. All I did was cut and paste the commands into the terminal and, somehow, it worked. Now I am trying to get DVD playback on a Xubuntu 12.04 system, but this time I'm not having any luck. After cutting and pasting what I thought were the correct commands, I still cannot play a DVD. Please help (by which I mean please spoon-feed me the commands that will work) and I will be eternally greatful. Thanks.

Edit:

Here is the problem: 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Here is the discussion:

[http://ubuntuforums.org/showthread.php?t=2135070](http://ubuntuforums.org/showthread.php?t=2135070)

Here is (at least) one solution:

[http://ubuntuforums.org/showthread.php?t=2146227](http://ubuntuforums.org/showthread.php?t=2146227)

I did not want to bump this thread, so I edited my original post. If you come across this thread, I hope this helps.

---

### Post by Yellow Pasque on 2013-10-11
Please mark the thread solved. It's confusing without that bit of info...

---

### Post by varunendra on 2013-10-11
..And here is the latest fix (if I understand your question correctly), stolen from mc4man's post [post=12812210]here[/post] -

**1)** Open Software Sources (press Alt-F2 > type "software-properties-gtk" > press "Enter")
**2)** Goto "Updates" tab > Enable "proposed" repository. Close it.
**3)** Open a terminal (Ctrl-Alt-T) and run -
```
sudo apt-get update
```
**4)** Install/Upgrade "libdvdread4" package -
```
sudo apt-get install --reinstall libdvdread4
```
**5)** Repeat steps 1 and 2, this time disable the repo again in step 2. Then repeat step 3 to be safe from unwanted updates.
**6)** Finally, assuming you have the new version of "libdvdread4" installed by above, run the following command -
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Now run VLC again, press Ctrl-D to open "Load Disc" dialogue, load the DVD and let us know if it plays it now.

**EDIT:** Just noticed the last post. Apparently I was indeed confused if it was a 'guide' instead of a support question :|

---

### Post by jamesfbays on 2013-10-11
No, this was not intended to be a guide. Sorry for any confussion, thanks for the help, and I will mark the thread solved.

---

### Post by varunendra on 2013-10-11
No problem, and thanks for taking time to mark it Solved. :)

---

