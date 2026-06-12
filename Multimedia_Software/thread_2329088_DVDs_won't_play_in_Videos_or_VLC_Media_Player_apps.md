---
title: "DVDs won't play in Videos or VLC Media Player apps"
date: 2016-06-27
forum: Multimedia Software
---

### Post by dean.w.schulze on 2016-06-27
When I try to play a DVD in the Videos application it just shows a black screen.  The play button does nothing.  This is after installing several dependencies it asked for initially.

I installed VLC Media Player and it won't play DVDs either.  It recognizes the DVD title in its title bar, but when I click Play (and go through the popup and select Disk) is shows something for about a second and then shows a black screen.

Is there an application for Ubuntu 16 that will play DVDs?

Thanks.

---

### Post by X-RED_Tech on 2016-06-27
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

The above should be enough for playing commercial encrypted DVDs.

---

### Post by dean.w.schulze on 2016-06-28
I followed those instructions for both 15.10 and newer and for older versions of Ubuntu and neither work.  I still can't play DVDs.  The versions of Ubuntu 15.04 and earlier include this:

sudo /usr/share/doc/libdvdread4/install-css.sh
but there is no install-css.sh file in that directory.

---

### Post by mc4man on 2016-06-28
Run this & report what happens
```
sudo dpkg-reconfigure libdvd-pkg
```

---

### Post by dean.w.schulze on 2016-06-28
It says libdvdcss2 is already installed.

Just installed 16.04 and it would not play a DVD out of the box and after following the various recommendations I've found on the web it still won't play DVDs.  Will an earlier version of Ubuntu reliably play DVDs?  How about any other Linux distros?  I could try installing Windows 10 in a VM if that will work well, but I wonder about playing DVDs in a VM.

16.04 has other serious problems (Software Center won't install chrome, apt-get dependency management is broken).  My experience with 16.04 has me ready to move away from Ubuntu so if another Linux distro will play DVDs reliably I'd like to hear about it.

---

### Post by mc4man on 2016-06-28
Put a dvd in the drive, close any popup, & once drive has settled run this command, post back everything shown in the *-cdrom section
```
sudo lshw -c disk
```

---

### Post by QIII on 2016-06-28
Hello!

To keep everyone from going over ground you've already been on, could you tell us what recommendations you have followed?

Ubuntu will not play DVDs OOTB because some localities restrict the use of some codecs and technology.  Canonical does not install them by default.  They are, however, available to download and install.

---

### Post by mc4man on 2016-06-28
> **QIII said:**
> Hello!

To keep everyone from going over ground you've already been on, could you tell us what recommendations you have followed?

Ubuntu will not play DVDs OOTB because some localities restrict the use of some codecs and technology.  Canonical does not install them by default.  They are, however, available to download and install.
Well the Op has a thread right under this one, not much feedback as of yet.

(- see this forums having some little issues

---

### Post by dean.w.schulze on 2016-06-28
Everything covered here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I've installed the restricted package and DVDs still won't play.

---

### Post by QIII on 2016-06-28
You installed the restricted extras as described for your release?

Did you run the script as in the earlier versions?

What are you using to try to play the DVDs?

---

### Post by dean.w.schulze on 2016-06-29
> **QIII said:**
> You installed the restricted extras as described for your release?

Did you run the script as in the earlier versions?

What are you using to try to play the DVDs?

Yes, I installed the extras per the page linked above.  The script (installcss.sh or something like that) doesn't exist.  Maybe that is the problem.

I've tried the Videos application and VLC player.

---

### Post by QIII on 2016-06-29
No, that's not the problem.  Actually, if the script isn't there you are good for 16.04.

OK.  You say it doesn't work.  What happens?  Are there messages?

---

### Post by dean.w.schulze on 2016-06-29
> **QIII said:**
> No, that's not the problem.  Actually, if the script isn't there you are good for 16.04.

OK.  You say it doesn't work.  What happens?  Are there messages?

Nothing happens.  VLC player briefly shows the title of the DVD and looks like it tries to play it before showing a black screen.  The Videos app just shows a black screen and the play button does nothing.

---

### Post by mc4man on 2016-06-29
90% of the time this can be fixed in a few minutes. You'd need for starters to provide the requested info in your dupe thread.

---

### Post by howefield on 2016-06-29
Duplicate threads merged.

---

### Post by QIII on 2016-06-29
Try starting VLC from the terminal.  Check to see if there are any errors, warnings or messages in the terminal.

---

### Post by dean.w.schulze on 2016-06-30
It turns out that you need to run software updater and install the 187 MBytes of updates.  They fix the problems with videos not playing and the broken package system that comes with the 16.04 .iso.  When I ran the software updater it failed because the package system is broken.  It said to run 'apt-get install -f' or something like that.  Once I ran that (using sudo) and re-ran the software updater and installed the updates I could play videos.

The 16.04 .iso is very broken.

---

### Post by dean.w.schulze on 2016-07-03
Doing a system software update fixed the problems.  DVDs play with either the Videos app or with VLC Media Player.

---

### Post by deadflowr on 2016-07-03
If you found the solution to the problem at hand, please feel free to [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

