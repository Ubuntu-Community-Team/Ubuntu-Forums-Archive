---
title: "On the fly settings changes"
date: 2011-02-20
forum: Mythbuntu
---

### Post by xinix on 2011-02-20
Does anyone know how to do on the fly settings changes with 0.24?

I'm working on setting up a button on my remote to toggle between external speakers and a bluetooth headset.  I've made plenty of progress but I still have a ways to go.

With 0.23 I could change the audio device either via mythweb or mysql and all I would have to do is stop my playback, exit to the frontend, and restart my playback.  Now, with 0.24, I cannot do this.  The audio device is changed in the settings database but it does not take unless I go into the Settings screen and click through (I don't actually have to change anything) the 'next' button for the change to take effect.

Is there any way to get 0.24 to use changes made via mysql in the commandline?

Edit:  It is actually more convenient for me to exit the frontend and restart it than to click through the settings screen.  It would be nice to not have to do this though.

---

### Post by newlinux on 2011-02-20
I have the same issue with a button I made uses sql to dynamically change the playback profile settings. I ended up having the script restart the frontend too...

---

### Post by xinix on 2011-02-20
Yeah,  it's a shame that restarting the frontend seems to be the best way to do it; considering that 0.23 picked up on the change by stopping playback.  I think I'll have my script restart the frontend while I work on this.

---

### Post by xinix on 2011-02-20
> **newlinux said:**
> I have the same issue with a button I made uses sql to dynamically change the playback profile settings. I ended up having the script restart the frontend too...

Do you have an elegant way to have your script restart the frontend or are you sending a "killall" command?

---

### Post by newlinux on 2011-02-21
killall - no elegance for me.

---

