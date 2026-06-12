---
title: "Skype / No incoming call sound."
date: 2010-07-14
forum: Multimedia Software
---

### Post by Thomas Kenobi on 2010-07-14
I'm having a problem with Skype. Whenever someone calls me, the incoming call popup shows up, but I can hear no sound playing. Further, if I go in Options/Notifications and try to test the incoming call event, I'm having the same problem.

The .wav file exists and Skype can play it back. I have tested this by assigning that particular .wav to a different event, where it works as expected. Additionally, the other events, e.g. outgoing call, appear to be working normally. This would suggest, that the problem lies with the incoming call event, rather than the particular sound.

Skype version 2.1.0.81 (Beta)

Any suggestions would be welcome.

---

### Post by brianfriedkin on 2010-08-02
I had the exact problem and found the solution on the Skype website: [http://blogs.skype.com/linux/](http://blogs.skype.com/linux/)  "The PulseAudio volume for alert sounds should be maxed (on Ubuntu: Preferences > Sounds > Sound Effects > 'Alert Volume' slider).
In my case (hopefully yours too), I dislike system sounds and did set this to zero in order to remove all system Ubuntu sounds. I was wrong, because this slider does not govern 'system sounds', it governs Alert sounds, from any application. The right thing to do is to max the slider, and set the 'Sound theme' to 'No sounds'."

Or, you can try enabling the system alert sounds and you should hear Skype ring you.

---

### Post by Thomas Kenobi on 2010-08-02
Honestly, I had completely forgotten about this thread. :)

I did solve the issue about a week ago, in the same way that you mention. I too didn't know, that that slider governs all alerts, not just the OS ones.

Thanks for taking the time to post this anyway.

---

### Post by oooh on 2010-11-07
Same problem here 

But that solution does not work for me

I set the slider of alerts in vol settings to max, and still I hear no sound when I am called

The rest of skype works fine though

OK I JUST FOUND OUT WHAT THE PROBLEM WAS:

If my state is BUSY , then alert sounds are muted in Skype !!
If my state is NOT AVAILABLE, alert sounds are NOT MUTED !!

Frankly, I had no idea about this ... Anyways, the solution above is still applicable :) and works, just remember that if you are in BUSY state, you will hear no alert sounds at all !

---

### Post by rrios on 2011-06-16
At last a solution, it works!! thanks a lot.

> **brianfriedkin said:**
> I had the exact problem and found the solution on the Skype website: [http://blogs.skype.com/linux/](http://blogs.skype.com/linux/)  "The PulseAudio volume for alert sounds should be maxed (on Ubuntu: Preferences > Sounds > Sound Effects > 'Alert Volume' slider).
In my case (hopefully yours too), I dislike system sounds and did set this to zero in order to remove all system Ubuntu sounds. I was wrong, because this slider does not govern 'system sounds', it governs Alert sounds, from any application. The right thing to do is to max the slider, and set the 'Sound theme' to 'No sounds'."

Or, you can try enabling the system alert sounds and you should hear Skype ring you.

---

### Post by sanchaz on 2011-11-09
> **brianfriedkin said:**
> I had the exact problem and found the solution on the Skype website: [http://blogs.skype.com/linux/](http://blogs.skype.com/linux/)  "The PulseAudio volume for alert sounds should be maxed (on Ubuntu: Preferences > Sounds > Sound Effects > 'Alert Volume' slider).
In my case (hopefully yours too), I dislike system sounds and did set this to zero in order to remove all system Ubuntu sounds. I was wrong, because this slider does not govern 'system sounds', it governs Alert sounds, from any application. The right thing to do is to max the slider, and set the 'Sound theme' to 'No sounds'."

Or, you can try enabling the system alert sounds and you should hear Skype ring you.

How can i set the 'Sound Theme' to 'No sounds' in Ubuntu 11.10?

---

### Post by natrium on 2011-11-27
> **brianfriedkin said:**
> I had the exact problem and found the solution on the Skype website: [http://blogs.skype.com/linux/](http://blogs.skype.com/linux/)  "The PulseAudio volume for alert sounds should be maxed (on Ubuntu: Preferences > Sounds > Sound Effects > 'Alert Volume' slider).
In my case (hopefully yours too), I dislike system sounds and did set this to zero in order to remove all system Ubuntu sounds. I was wrong, because this slider does not govern 'system sounds', it governs Alert sounds, from any application. The right thing to do is to max the slider, and set the 'Sound theme' to 'No sounds'."

Or, you can try enabling the system alert sounds and you should hear Skype ring you.


was the solution for me! thx!

---

### Post by shinyblue on 2011-12-09
[COLOR="DarkGreen"][SIZE="4"]thank you[/SIZE][/COLOR]:)

---

### Post by sianliu on 2011-12-23
Oooh no pun intended, thanks for sharing! The status change fixed my problem. Happy Holidays!

sianjon

> **oooh said:**
> Same problem here 

But that solution does not work for me

I set the slider of alerts in vol settings to max, and still I hear no sound when I am called

The rest of skype works fine though

OK I JUST FOUND OUT WHAT THE PROBLEM WAS:

If my state is BUSY , then alert sounds are muted in Skype !!
If my state is NOT AVAILABLE, alert sounds are NOT MUTED !!

Frankly, I had no idea about this ... Anyways, the solution above is still applicable :) and works, just remember that if you are in BUSY state, you will hear no alert sounds at all !

---

### Post by silverhead on 2012-02-24
THANK YOU!! Sliding to max of  Preferences > Sounds > Sound Effects > 'Alert Volume' slider in Skype fixed my problem.

---

### Post by papa canaria on 2012-04-10
Thanks!!  *Preferences > Sounds > Sound Effects > 'Alert Volume' *working for me too!!

---

### Post by adgsfuzwe on 2012-05-31
Thank you for help.

---

### Post by Cotopaxi on 2012-11-28
Now I need help:

Anyone knows how to make this trick with **K**ubuntu?

Thanks!

---

### Post by oldos2er on 2012-11-28
Old thread closed. Please start a new thread.

---

