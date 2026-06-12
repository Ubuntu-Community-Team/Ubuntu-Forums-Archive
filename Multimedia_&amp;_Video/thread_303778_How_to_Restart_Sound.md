---
title: "How to Restart Sound?"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by shade73 on 2006-11-20
Ok, so I'm having problems with my sound.  Sometimes it will work fine and other times in the same program nothing will come out.  So i can watch democracy tv all night one night.. open it up the next morning and it's fine.  Then that afternoon my sound no longer works.  So my first question is can I just restart the sound without shutting the whole computer down?  Also, what would be the best way to troubleshoot this so I can get it fixed for good?  Thanks!

---

### Post by drphilngood on 2006-11-20
Have you experimented with Alsa to make sure that nothing is muted/turned-down?  Not meaning to offend, just checking...

---

### Post by shade73 on 2006-11-20
yeah actually I read that about 3 days ago and I checked everything in the sound settings and they all seem fine.  I was hoping that there was just a program muting my output when i ran it but it doesnt' seem that way.  Once it goes off the only way to make it come back on is to reboot.  However, once I reboot it's good again until I run like mythTV which it seems to never fail to kill my sound ever after that.  It seems as if other programs are doing it too but that one seems to be a sure thing.  I don't have any sound coming out of the TV tuner when i turn it on either, so I'm thinking that is what is causing it to die?  At any rate I'm just looking for away to restart the sound without restarting my computer at this point, and then I'll try to work out why it keeps cutting off

---

### Post by adwait on 2006-11-20
Try
```
sudo /etc/init.d/alsa-utils restart
```

I think that restarts the sound system.

---

### Post by drphilngood on 2006-11-20
Did you try:

```
gksudo alsamixer
```

If not, give it a try.  You use your left & right arrow keys to navigate, top & bottom ones to adjust and ¨M¨ key to mute/unmute.

This is how I fixed a problem with my radio & TV tuners in one of my boxen and it did ¨restart¨ my sound(so to speak).

---

### Post by shade73 on 2006-11-20
Thanks alot guys.  My sound works right now so it'll be a few before I can test it.  Thanks for those tips though I will definately give it a go!  I also disabled my on board sound just to see if i could fix it by doing that as well.

---

