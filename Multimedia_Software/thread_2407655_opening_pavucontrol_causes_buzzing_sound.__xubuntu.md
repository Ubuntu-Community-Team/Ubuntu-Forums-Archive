---
title: "opening pavucontrol causes buzzing sound.  xubuntu 18.04."
date: 2018-12-07
forum: Multimedia Software
---

### Post by Adam_GUI on 2018-12-07
I'm having a recent issue where opening pavucontrol causes a buzzing noise to start from my tower's audio out jack.

It only happens when starting pavucontrol.  Killing pavucontrol causes the process and buzz to stop.

Making changes in alsamixer doesn't have any effect.

---

### Post by Adam_GUI on 2019-01-04
I hate to just bump a thread with no update, but this problem persists.

---

### Post by howefield on 2019-01-04
> **Adam_GUI said:**
> I hate to just bump a thread with no update, but this problem persists.

Feel free to bump your post once a day or so, put it back to the top of the pile. The person who can offer assistance may well not see it otherwise.

---

### Post by Adam_GUI on 2019-01-08
I couldn't attach audio, but, I can capture the buzzing on video.
So, I'm attaching a link to a youtube video describing a showing off the humming going on.

[https://www.youtube.com/watch?v=YNrWQNmIXFY]("https://www.youtube.com/watch?v=YNrWQNmIXFY")

I should add that the buzz isn't a constant.  It doesn't show up recording audio in Audacity.  But, with OBS or PAVUControl open, it's there.

---

### Post by Adam_GUI on 2019-01-12
The card identifies as:

HDA ATI SB
Realtek ALC662 rev1

Playing with capture levels in alsaconfig, I get no hum.

Opening pavucontrol, obs, or hitting record in audacity, I get the hum.

The front-side line-out doesn't hum.  So, I suspect it could be shielding.  Only, I don't know why it would hum only while recording and not all the time.

So, the plan becomes that I'm going to try creating an 18.04 USB disk and mess with audio there just to make sure it's not something in my audio config somewhere.

I had to do some office re-arranging recently.  The cables I used to connect the PC to the mixing board changed.  So, it could be a difference in cables?

I'm talking myself in circles.  I'm sorry.  I just don't understand why the channel just doesn't always hum.

EDIT:
It makes the hum with the live installer, too.
On boot into the user session, I get about five seconds of hum before it cuts off.
Same on the installer and the install.

So, it's doing something on init and something on init-record that causes the hum.

---

### Post by CatKiller on 2019-01-12
> **Adam_GUI said:**
> I don't know why it would hum only while recording and not all the time.

Automatically muting the mic input when not recording is generally sensible.

There may be a noisy pre-amp or other channel causing the noise, or it could be a shielding issue as you've suggested.

---

### Post by Adam_GUI on 2019-01-12
> **CatKiller said:**
> Automatically muting the mic input when not recording is generally sensible.

There may be a noisy pre-amp or other channel causing the noise, or it could be a shielding issue as you've suggested.

That's just the thing, though.  No jacks are being used for line-in.

It's line-out that selectively hums on record.

I've tried swapping the channel-in on the board and I get the hum regardless from that line-out jack.

---

### Post by CatKiller on 2019-01-12
> **Adam_GUI said:**
> It's line-out that selectively hums on record.

Yes, that's the output. The sound being fed to it comes from somewhere. When you hit the record button, monitoring of the inputs lights up and gets fed to the outputs. A noisy pre-amp will always be noisy if it's turned on. Electrical noise will always be noisy if you have a shielding problem. It's just that you're only hearing it when you're monitoring your inputs.

---

### Post by Adam_GUI on 2019-01-12
Well, I disconnected the output and connected headphones directly to the line out.  No hum.
I can get the hum to happen just by putting my fingers around the stereo lead to the board and applying pressure.

So, the problem is with my cables, it looks like.

I'll mark the thread solved and look for a replacement stereo to red/white cable.

---

### Post by Adam_GUI on 2019-01-12
My last bump of this thread, I promise.

I was wrong in my diagnosis.  

The buzz was the USB cable going from my PC to my mixing board.

I was right about init for record causing the hum.  But, I was blaming the wrong culprit, thinking it was on the PC end and not the mixing board.

I ran pavucontrol while the USB cable was disconnected and got no buzz or hum.

I've since replaced the cable with a spare I had around and the problem is either gone or vastly reduced to the point where I no longer notice it.

Problem solved.  Just not the way I thought I had to solve it.

---

### Post by CatKiller on 2019-01-12
Audio work is all about tracking down the hums :-(

Glad you sorted it.

---

