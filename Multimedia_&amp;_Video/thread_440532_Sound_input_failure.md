---
title: "Sound input failure"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by gewitty on 2007-05-11
Has anyone experienced a loss of microphone input in Feisty? When I first installed it I had perfect sound record/playback functionality (unlike Edgy, which was very intermittent). However, having installed Skype and got it working OK, I suddenly lost all sound input yesterday. I've been through every sound setting I can find - Volume Control, Sound Settings, Alsa Mixer - but can't find anything that looks wrong.

Sound recorder is also behaving strangely. If I try to record something, it appears to be running and creates a file, but no sound is actually recorded. During and after recording, the progress bar remains greyed out, although the timer count is running. If I then do a Save As, the progress bar becomes active, but the file is still silent. 

I've seen a post about this happening on Macs, but no-one seems to have found the cause/solution yet.

---

### Post by nduanetesh on 2007-05-18
I came to the forums this morning looking for a solution to this exact issue.  The mic seems to work in skype for 15 mins or so, and then will just cut out completely.  If I shut down skype and restart it, the mic again works, but for not as long.  Same problem you're having?

I'm using an Acer Aspire 3100 laptop, btw.  Don't know what the sound hardware is off the top of my head.

If I figure anything out, I'll post back here.  Hopefully we'll be able to get this figured out, as it's the only major problem I've had with Ubuntu since installing it about a week ago.  (That's right, I'm a noob.)

ND

---

### Post by gewitty on 2007-05-18
My mike input (in fact all sound input) failed a short time after I installed Skype. Despite trying several things, including uninstalling and reinstalling the all ALSA apps, I still can't get it working.

I had intermittent sound output problems with Edgy, but this has only happened a couple of times since upgrading to Feisty. The only fix I can think might work is a complete fresh installation, but that's a real pain if you have a lot of other stuff loaded and configured.

---

### Post by nduanetesh on 2007-05-24
Hrm.  I don't know if you and I are actually experiencing the same problem...I have only one sound input, so cannot test to see if any other inputs on my lappy have failed.  And as I said, a reboot seemed to fix things temporarily.  I DO have good news, though...

I installed the alpha of Skype 1.4, (and I see the alpha has been updated as of yesterday).  Find it at this [link]("https://developer.skype.com/LinuxSkype").  Since installing, I have had no problems at all with the mic cutting out, and the sound quality is greatly improved.  Apparently there are a bunch of additional features implemented into the updated alpha, so I'm eager to check it out.

Hope this helps. 

ND

---

### Post by nduanetesh on 2007-05-24
woops. spoke too soon.  I was using the newest version of skype this afternoon, and after about ten minutes in a call, my microphone completely cut out.  grrr!!

So, here we are back at square one.  Seems like it's really an ubuntu problem, rather than Skype?

---

### Post by grahams on 2007-05-25
I use Ekiga (which is open sources and uses the SIP standard) on Feisty rather than skype and I've never had problems with mcirophones. Try switching to standards based softphone lile Ekiga or Gizmo

---

### Post by gewitty on 2007-06-04
Do Ekiga and Gizmo talk to Skype users? I have a large address book of Skype contacts and need to be able to continue contacting them.

---

### Post by QwUo173Hy on 2007-06-06
I have the same problem. My mic stopped working in Skype after about 10 minutes. It's not an Ubuntu issue. I can record with my microphone using Audacity. I'd like to try Ekiga or Wengophone but I don't think you can call skype users with it and that's what my colleagues are using as they run Windows.

---

### Post by grahams on 2007-06-06
Skype uses a proprietary protocol and open standard tools like Ekiga and Gizmo can not talk directly to Skype users. Because of this a lot of folks are dropping Skype and signing up for open standard based tools.

---

