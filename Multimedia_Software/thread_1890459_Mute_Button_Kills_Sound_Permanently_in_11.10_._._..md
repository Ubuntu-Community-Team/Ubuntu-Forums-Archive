---
title: "Mute Button Kills Sound Permanently in 11.10 . . ."
date: 2011-12-03
forum: Multimedia Software
---

### Post by BuntuSeriously on 2011-12-03
Greetings!

Been really enjoying my installation of Xubuntu 11.10 on a new Lenovo Thinkpad Edge 15.  After setting up my preferred apps and configuring the basic UI to taste, all has been well in general: A thoroughly serviceable alternative to Windows anything.

UNTIL

I pressed the mute hotkey (silly me).  Now *_NOTHING_* will resurrect the sound for any application running on this laptop.

What on earth happened here?  Will my installation ever work properly again???

Thanks a Buntu :D

---

### Post by bluexrider on 2011-12-03
did you go to the sound preferences and see if the machine dropped the "audio device"

---

### Post by BuntuSeriously on 2011-12-03
@bluexrider:

Thanks for your response.  Yes, the machine borked the sound card implementation.

I never received a notification email from the forum that you had posted; so I dug about and found [this fix]("http://askubuntu.com/questions/5500/how-to-fix-audio-issues").

It seemed terribly draconian, but it worked (after messing around with Mixer for about 15 minutes).  I discovered everything gets really squirrelly whenever ANY mute function is called; either by hotkey or through Mixer!

So, to patch the issue here, I guess that I could simply disable the hotkey which provides mute functionality.

Do you know of any way this might be accomplished with XFCE :confused:

Any other things come to mind?

Thanks again for stepping up to help!

---

### Post by bluexrider on 2011-12-03
the e-mail is really slow anyway so I don't doubt that

actually NO. I ran across a different article utilizing "alsa-mixer" but it wasn't relevant.

if you don't get any more hits on the post bump it tomorrow.

happy *buntu

---

### Post by BuntuSeriously on 2011-12-03
Thanx again; and have a great weekend, bluexrider.

:popcorn:

---

### Post by BuntuSeriously on 2011-12-03
I figured out a pretty good fix.

Get it [here]("http://ubuntuforums.org/showthread.php?t=1890561").

:D

Cheers!

---

### Post by gewone on 2012-03-11
Nice going. Big thanks for this solution. I installed Xubuntu just a week ago and this "issue" was the killer that got me vibes of major instability. Thankfully, it seems just as easily resolved. Now, are we to expect that this issue is taken care of (out of the box) in the upcoming 12.04? I sure hope so.

---

