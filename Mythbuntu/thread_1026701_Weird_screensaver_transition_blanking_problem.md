---
title: "Weird screensaver transition blanking problem"
date: 2008-12-31
forum: Mythbuntu
---

### Post by newlinux on 2008-12-31
On at least two of my frontends (both nvidia GPUs) my screen goes and stays black  when I try to use mythfrontend ***in the couple seconds the screensaver is trying to come on*** (I can still see and move the mouse pointer when this happens). So If I let the screensaver fully come on I don't have that problem (this is using the glPicture screensaver, or whatever it is called). I also noticed that if I VNC into my machine when the screen is in this state on the TV I can still see and use the desktop in the VNC session, just nothing displays on the monitor except the mouse pointer, which is really weird. If I restart X everything comes back, but I'd like it just to wake up normally.

I'm on hardy, and I've had this problem since I installed, just getting sick of it now.

Any ideas?

---

### Post by uncle hammy on 2008-12-31
Have had this problem since day one as well.  I have just sort of trained myself not to touch anything on the remote when the screen starts to fade to the screen saver.  I always wait until the mouse pointer disappears.

---

### Post by august495 on 2008-12-31
I know it's not helpful, but happens to me to.

---

### Post by dsbw on 2009-01-01
Yep. I just turn off the screensaver.

---

### Post by newlinux on 2009-01-01
> **dsbw said:**
> Yep. I just turn off the screensaver.

My plasma gets image retention, so that's not an option for me.

---

### Post by newlinux on 2009-01-02
So there are no fixes for this? Do the other people that have this have nvidia GPUs or other? Are they running LIRC?

---

### Post by uncle hammy on 2009-01-02
I have a NVidia 7600GS (on all my machines), all using LIRC.

---

### Post by august495 on 2009-01-03
> **newlinux said:**
> So there are no fixes for this? Do the other people that have this have nvidia GPUs or other? Are they running LIRC?

8500gt and LIRC

---

### Post by newlinux on 2009-01-03
well in this unscientific sample at least seems related to LIRC and nvidia...

---

### Post by newlinux on 2009-01-17
a friendly bump in case anyone has any more ideas...

---

### Post by sikk on 2009-04-15
Bump also, and adding myself to the list of sufferers. 

How does one go about bugging this? It is driving me nuts, I'm tired of restarting gdm everytime I manage to hit a remote button during the fade transition. Happens a few times a week, and damages the WAF every time.

---

### Post by newlinux on 2009-04-15
Just to add, after the screen "blanks" if I move the mouse pointer (effectively turning off the screensaver) and then wait the amount of time it takes for the screensaver to re-enabled again I can see my desktop without restarting gdm. Not really a work around, just an observation. So when the screen saver blanks, and you move the mouse around, the screensaver is actually disabled, it just isn't displaying the the desktop (except the mouse). But it will the next time the screensaver is enabled.

---

