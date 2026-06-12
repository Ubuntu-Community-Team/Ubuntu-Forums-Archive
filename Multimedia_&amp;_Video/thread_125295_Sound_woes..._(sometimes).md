---
title: "Sound woes... (sometimes)"
date: 2006-02-03
forum: Multimedia &amp; Video
---

### Post by wncben on 2006-02-03
Ok,  so I admit I am a wet behind the ears linux/ubuntu noob, but am slowly, with the help of the awesome support on the forums, getting the various issues worked out, and have even braved the scary command line to fix my screen resolution problem \\:D/  

  I don't like to post on the technical forums if I don't really need to, let's face it even a noobie has some pride, but this sound issue has really got me stumped.

  Basically,  I start my computer, (emachines w3052, amd sempron, nvidia gforce4 onboard video, nvidia ck8  onboard sound) ubuntu loads up, the login page appears, the drums do their thing, I log in and no more sound.  I go to the alsamixer, and try to mute the iec device but there is no way to mute it ( the little square under the slider is missing, pressing the m key does nothing).

If I go to the volume control panel I can click on the mute icon under the iec thing and a little red x appears on the mute icon, but if I close the window and then reopen it the iec unmutes itself.

If I go to the volume control, and mute the iec, log off the system, saving settings, restart computer, start the session as a gnome session on the login page, tada I get sound (although sometimes on the internet it is garbled) but some random number of sessions later, the sound reverts back to naughty silence (except for the taunting drums on the login page)

If I go to system/preferences/multimedia system selector and run the audio tests I get an error on all of them (ie: "failed to construct pipeline for 'OSS-open sound system')
  If i go through the rigamarole to get sound to work and then run the tests I get a tone and a sliderbar on the 'default sink' tests. I get a slider bar but usualy no tone on the default source' tests and  sometimes it will crash on these, requiring a hard reboot (ie turning the power off and on)

The most annoying thing about this problem is that it is so variable, some times it works, sometimes it doesn't.  I am sure that there must be a pretty simple fix, but I just don't know enough about linux to hazard a guess as to what it might be.  It seems that it is related to the iec device setting in the alsa mixer, but I dont know how to fix it.

Thanks in advance for any help.  I have tried lotsa the ideas that have been posted already, which is where I got the iec thing, but the way the system is acting is beyond my limited experience in the computer world. 
~ol' Ben

---

### Post by FarEast on 2006-02-04
Let me help you with solving the issue :).
What I would like to know at first is which sound chip your PC has and
how you have configured it.
Paste the output:
$ cat /proc/asound/cards
$ lsmod | grep snd

---

### Post by wncben on 2006-02-04
Thank you, here is the info you requested:

[ATTACH]5853[/ATTACH]

---

### Post by wncben on 2006-02-04
By the way, I know there is a simpler way to transfer info from terminal to the forums, I just don't know how to do it.  Could someone please point me in the right direction?  Thanks!
~ol' Ben

---

### Post by wncben on 2006-02-04
Judging from what I have found elsewhere on the forums, and on the irc help, I think I have an issue where the iec device in alsamixer is not being properly disabled.  I am not able to mute the iec in alsa mixer, but can on volume control, (but it unmutes itself if I close the window) I am able to get sound (sometimes) by muting iec on volume control, saving settings, restarting computer, and logging in in gnome.  Sometimes I get sound, which might or mightnot still work at the next login.  the drums always beat on the login page, though when the sound is working they only beat once.

~Ol' Ben

---

### Post by FarEast on 2006-02-05
Sorry, my reply was late.

> I know there is a simpler way to transfer info from terminal to the forums,
> I just don't know how to do it.

Select strings by dragging them, right-click and choose 'copy'.
Then activate the browser and paste them in the same way;) .

Here I have met many people who have problem with sound chips which
should be driven by 'snd-intel8x0'.  And I have not been able to help them.
The only thing that I could suggest was to use OSS driver instead.

I hope that those who have troubles with 'snd-intel8x0' exchange information
and help each other.

EDIT: Please visit ALSA User ML to look for clues.
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/)

---

### Post by wncben on 2006-02-08
Thanks for your help,  
  I am still getting used to the way linux works, and I appreciate all the great tips I'v gotten out here.  It does seem like there are lots of people with similar sound problems.  I don't understand why my particular problem is intermittant.  It seems like there is some setting somewhere that is periodically resetting the alsa settings.  just wish I knew where to look...  ~Ben

---

### Post by wncben on 2006-02-13
Hey FarEast, I've found a pretty good Howto:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

I still don't understand how any of this sound stuff works, abd I now have no system sounds, only application sounds, but this is a big improvement from no sound;)    The drums don't beat anymore, I wonder what I changed?

~O'l Ben

---

### Post by wncben on 2006-02-13
I found that by going back to system/preferences/sounds and turning 'enable sound server startup' back on I also have system sounds too!

~Ol'Ben

---

