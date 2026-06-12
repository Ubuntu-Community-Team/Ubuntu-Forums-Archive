---
title: "DVDs won't play after 10.10 upgrade"
date: 2011-05-15
forum: Multimedia Software
---

### Post by kmarzi on 2011-05-15
Dear forum,

Since upgrading to 10.10 I have, on the whole, been very happy :D

However, I've just realised that since upgrading, I'm unable to play DVDs. This was fine in 10.04. I've tried various things (e.g. From Medibuntu, I installed repositories, installed "playing encrypted DVDs", etc) but, alas, I still can't play DVDs. (Well, *some* DVDs work, e.g., out of 4 I've just tried, 1 "kind of" works - after my DVD has thought about it for a long time!)

My DVD-ROM also makes a few weird sounds when I put certain DVDs in there. I can assure you the hardware is working and this has only just become a problem since installing 10.10 and only with certain DVDs. Also, with certain DVDs, when trying to open with VLC, I get this error message:

"Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details."

I've done a basic search for this problem and followed what I found on the forums (such as what I have mentioned above) but some DVDs still won't work :s

Can any one help with this? 

Many thanks,
Kmarz

---

### Post by Kri5 on 2011-05-15
I remember having the same problem, have you installed the 'Ubuntu restricted extras' i think it is in Synaptic?
 
I think that is what cured it for me.

---

### Post by kmarzi on 2011-05-15
Hey, thanks for the reply!

I have installed that now and... Well, it seems to work (albeit, some DVDs work immediately and I am prompted to play them after inserting the DVD; others don't start-up immediately, and I have to find the DVD in, say, VLC, via file, open, etc. Is that normal?)

But thanks for the help with this: it seems to be working now :D

However, there are still 1 or 2 DVDs which don't work :o

I've just booted up in Windows (please don't hate me!) and one in particular (a brand new DVD) doesn't work with Windows either... 

Very odd... Any idea?

Ta,
Kmarz

---

### Post by kmarzi on 2011-05-15
With the last DVD, I just received the following message from Movie Player:

"Could not open location; you might not have permission to open the file."

---

### Post by Kri5 on 2011-05-15
Glad to hear the majority now work, as for:
 
"Could not open location; you might not have permission to open the file." 
 
I'm affraid i've not come across that before, i'd have to do some googling myself.
 
You could perhaps insert the DVD and right click on the desktop icon, in the window that opens there should be a permissions tab and i beleive somewhere at the bottom is a tick box to allow the file to be executable.
 
I know this works with certain file types not sure about DVD's etc though.
 
As for Windows, you are forgiven LOL, unfortunately i haven't used Windows for a long time.
 
Sorry forgot to say right click and select properties

---

### Post by kmarzi on 2011-05-15
Thanks man.

I've just tried what you suggested but no luck either. :s

Will do a bit more googling to see if there are any solutions...

---

### Post by cottfcfan on 2011-05-15
This fixed it for me:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
under: installing libdvdcss.

---

### Post by kmarzi on 2011-05-15
I've tried that too: thanks for the link...

Still nothing... This darn DVD just won't work! 

Any other ideas? (I've tried the DVD in a standard DVD player and it worked fine...)

---

