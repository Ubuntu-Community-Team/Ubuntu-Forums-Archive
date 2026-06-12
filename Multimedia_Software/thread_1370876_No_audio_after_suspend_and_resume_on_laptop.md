---
title: "No audio after suspend and resume on laptop"
date: 2010-01-02
forum: Multimedia Software
---

### Post by billrosenblatt on 2010-01-02
I just upgraded to 9.10 (Karmic Koala) on a Dell laptop.  Now when I close the laptop lid to suspend and then open it to resume, the audio disappears; have to reboot to get the audio back. 

I remember having this problem a while ago back on Hardy Heron and finding a kludge to fix it - a line inserted in a shell script that gets invoked on resume.  

Any help would be most appreciated!

---

### Post by inameiname on 2010-01-25
Did you ever figure out how to fix this issue? I'm having the same trouble.

---

### Post by sleepee on 2010-02-10
i also get the same problem sometimes.  it happens sporadically though. so far it's only happened to me when i leave it suspended for a few hours..

anyway, have you guys checked out this thread??
[http://ubuntuforums.org/showthread.php?t=810718&highlight=close+laptop+lid+suspend](http://ubuntuforums.org/showthread.php?t=810718&highlight=close+laptop+lid+suspend)

---

### Post by wgilthorpe on 2010-02-18
I have the same problem on a gateway mc7800 series machine (intel chipset and sound card).  I have been searching the forums for weeks now trying to find a solution.  

[LIST]
[*]asla force restart does not work
[/LIST]

[LIST]
[*]editing the etc/modprobe.d/alsa-base.conf has not helped
[/LIST]

[LIST]
[*]editing the power setting to hibernate=platform has not helped (although it greatly improved wakeup speed)
[/LIST]
I am seriously considering dumping ubuntu.  I have been really excited about it, but as much as i listen to music and watch movies on my lappy restarting everytime i open it is a huge hassle.  All help would be greatly appreciated.  Thanks in advance.

---

### Post by mörgæs on 2010-02-21
Have you tried ```
sudo alsa suspend
``` followed by ```
sudo alsa resume
``` ?

---

### Post by wgilthorpe on 2010-02-21
> **mörgæs said:**
> Have you tried ```
sudo alsa suspend
``` followed by ```
sudo alsa resume
``` ?

Thanks for the tip but no.  I have been playing around with mine and noticed it only happens when I suspend not when I hibernate.  Any further suggestions would be great.

---

### Post by mörgæs on 2010-02-22
There are several bugs in Launchpad describing this, for example
[https://bugs.launchpad.net/ubuntu/+bug/198218](https://bugs.launchpad.net/ubuntu/+bug/198218)

Maybe you can find a workaround here, or you could confirm the bug for 9.10, pushing it a small step towards a solution.

If you don't mind trying an alpha version, you could install Ubuntu 10.04. 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is surprisingly stable, at least on my machine. I can not promise that it is solved, but maybe worth a try.

---

### Post by inameiname on 2010-02-23
I am sadly still having this issue, ever since Karmic first came out. 

As for me, this issue of no sound when my Gateway laptop awakes ONLY occurs after it goes to sleep with the close of the lid. And it always happens, and can only be fixed with a quick restart. It's not a huge issue, but if I feel like leaving it for a spell and coming back to it, I will have no sound until I restart the computer. I have tested it to see if there is a specific time in which it turns the sound off, and from my testing, it seems to only occur after at least more than several seconds of 'sleeping' has occurred. 

One thing though that I haven't noticed on this thread is that for me at least, I did not have this issue in Jaunty. Therefore, something was done/changed in Karmic which altered how sound is 'awaken' or whatever when the laptop's lid is opened, and the computer awakes. 

I just may try Lucid's Alpha version, just to see if it's possible the solution was found and fixed for the next release of Ubuntu.

---

### Post by mörgæs on 2010-02-23
That might be the best solution. Let us hear how it goes.

Don't forget 9.04, if upgrading does not fix your problem. Unlike 9.10, it is a very stable and almost bug-free version supported through most of 2010.

---

### Post by inameiname on 2010-03-03
Unfortunately, trying Ubuntu Lucid's Alpha version (upgrading Karmic to Lucid), just to see if it's possible a solution would be  found, the very same audio problem occurred, no sound on opening/resume after closing the lid and waiting for several minutes while the computer was asleep. 

The very same audio files were played/used, from right before my experiment and right after, and again, no sound once I woke my laptop up.

Guess then whatever update that was done with the audio or it's dependents which causes this problem from Jaunty to Karmic seems carried over to Lucid as well; at least the Alpha version. 

So as it stands, the issue did not occur in Jaunty (that was my first experience with Ubuntu and thus, do not know about past versions), but does happen in Karmic, as well as in Lucid's Alpha release so far. Thus, I still don't have a solution. :(

The only thing I can think of that might be at fault here with my experiment is that I didn't install a fresh Ubuntu Lucid Alpha install, but an upgrade from Karmic. It may very well be something left from Karmic.

---

### Post by inameiname on 2010-03-03
Okay, so a quick update.....I decided to try a fresh install of Ubuntu Lucid Alpha 3 to see if it may have fixed the issue, and sadly it did not.

Doing the very same thing, no sound was achieved after opening up the lid. In addition, a 'program has crashed' error popped up regarding something called "indicator-sound-service'.

Oh, and I forgot to mention, most times, when the sound does not 'wake up', also messed up by this problem is video, as it seems more jumpy, slow, and not quite right. Not always, but often. Now, EVERYTHING is fixed just fine and dandy once I restart the computer.

---

### Post by mörgæs on 2010-03-07
Just being curious: 
What made you drop 9.04? It is supported through most of 2010.

---

### Post by inameiname on 2010-03-08
No reason in particular, other than wanting to have the latest version installed. Karmic works just fine for me in all manners, a few things have even been improved from Jaunty, so with the exception of this one issue, it hasn't really been problematic to warrant a downgrade back to Jaunty. 

One thing I still find interesting is that it's partially a hardware issue as well, as I installed the exact same Ubuntu Karmic (Remastersys custom DVD) onto a friend's laptop, and found my issue with audio not awaking is not there with it. 

Also, on one of these boards a while back, with Hardy I believe, somebody found the very same problem and solution, however, from my research, while the problem was addressed in more recent posts, they never repeated the solution. Doh! :P

---

### Post by inameiname on 2010-07-09
I just wanted to say that some update just in the past few days has  fixed this issue that I've been having this Karmic.

Hopefully it's not a fluke. Seems to be working. I'll mark this as  solved anyway.

I'm curious though as to which update it was, and whether it's a fix  everybody else who has had this issue too has found as well. 

Feel free to comment on it if you have, or have not.

I also wonder if it's an official update that fixed it, or an update  from one of my PPAs. It would be great to know so as to figure out what  could change it again if and/or when it happens again in another Ubuntu  release. 

Finally!!!!!!!!!!!!

---

### Post by wgilthorpe on 2010-07-09
I may be able to help isolate the update that fixed this issue.  I have been fighting this bug since the release of 10.04.  The fix came in kernel update 2.6.32-23-generic.  I had tried the upstream kernel and had no issues with this, but alas I could not compile virtual box to run with the upstream kernel.  So, I was forced to hibernate every time I closed the lid on my laptop.  I was going to go back to windows natively on my laptop the day that I applied this update.  I am so glad that I don't have to now.

---

### Post by lidex on 2010-07-09
From alsa documentation:
> reloading modules across APM suspend-and-resume
-----------------------------------------------
During suspension many peripherals are switched off; on resuming the
machine these peripherals need to be re-initialized.  Many ALSA
drivers do this properly but some still do not.

If this problem affects you and if your ALSA drivers are built as
loadable modules and your kernel supports module unloading then you
can work around the problem by unloading the driver before suspending
and loading it again after resuming.  This will be done for you
automatically if you add the name of the problematic sound card driver
module to the variable force_unload_modules_before_suspend variable in
/etc/default/alsa.  E.g., if your CS46XX and AZX cards don't work
properly after resuming from APM suspend, add the names of their
driver modules to the list:

    force_unload_modules_before_suspend="snd-cs46xx snd-azx"


restoring sound volumes across APM suspend-and-resume
-----------------------------------------------------
alsa-base provides an APM script in /etc/apm/scripts.d/alsa to
automatically store/restore sound volumes during APM suspension.
Since this option relies on alsactl, please install the recommended
alsa-utils package.


---

### Post by inameiname on 2010-07-09
To wgilthorpe:

Hmmm, I didn't think about it being the kernel 2.6.32-23-generic, especially since it's been out for longer than just a few days, which is when I first noticed this. I actually thought I had it narrowed down to indicator-sound and/or ubuntu-mono, to which both were updated from guido-iodice/guidoiclucid's PPA. But yours makes more sense.

Maybe I just never paid attention to if it worked or not until earlier today.

To lidex:

Thanks for the suggestion. So you think this was the issue, and the latest kernel, 2.6.32-23-generic fixed this specific thing to make it work? I'll remember to try it if it ever happens again.

---

### Post by lidex on 2010-07-10
> **inameiname said:**
> 
To lidex:

Thanks for the suggestion. So you think this was the issue, and the latest kernel, 2.6.32-23-generic fixed this specific thing to make it work? I'll remember to try it if it ever happens again.

Could very well be. Let's see if others can confirm it.

---

### Post by inameiname on 2010-07-10
Yeah, I'm curious if others having noticed the fix as well. I know there are several folks who've had this very issue on here for quite some time, so I'm sure somebody will respond.

---

### Post by lidex on 2010-07-10
Yeah. The OP is AWOL. If he would mark the thread solved I'm sure it would draw some attention. ;)

---

### Post by inameiname on 2010-07-10
I posted very similar postings probably half a dozen times over the past year to which I was hoping would get some responses when I marked them as solved this morning, yet this thread was the only one that did after my reply. :(

---

### Post by jsuhr on 2010-07-31
I have the latest kernel with all updates and my no sound on resume persists, and only when suspended for some time, sorry can't confirm exactly how long. I have tried modifying /etc/modprobe.d/alsa-base.conf (sorry don't remember exactly with what, but can dig it up if needed) and alsa force-reload, to no avail.
Interestingly if I suspend, resume, suspend, resume *then* alsa force-reload I get sound.
Dell XPS 420
Ubuntu Lucid 64 bit
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have had this problem since at least Intrepid.

---

### Post by jsuhr on 2010-08-10
Ok, new development...
An update within the last week must have fixed my issue, as I can't recall any relevant changes I made. Installed another monitor and now suspend is broken, well, more accurately, resume is broken. :)
I'm more than happy to post any output.

---

