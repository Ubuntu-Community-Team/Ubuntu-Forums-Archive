---
title: "problem importing DVD in Myth 8.04"
date: 2008-05-06
forum: Mythbuntu
---

### Post by mixersoft on 2008-05-06
I just installed the new 8.04 release and have been trying to configure it to be my DVD jukebox. I'm using a KPC which doesn't have an optical disk, but I have a dvdrom mounted at /mnt/dvdrom over smbfs from my PC over a Gigabit ethernet connection. 

The DVD plays fine from OpticalDisks>PlayDVD. But when I try OpticalDisks>ImportDVD it just sits there with "No Jobs, Checking/waiting for DVD". Do I have to configure the device differently for import? What am I doing wrong?

I have also copied the DVD from my PC to a local directory on the Mythbuntu box, and the video_ts files also play fine. Is there a workaround that allows me to rip the DVDs from my PC to the Mythbuntu drive?

TIA.

---

### Post by GordonEndersby on 2008-05-06
Im not sure if this is the same for you as it was for me especially as you are mounting it remotely.
But have enabled the proprietary codes in the control centre?
You need them to enable Mythtv to read encrypted protected DVD's.
This was stopping both playing and ripping on my system until I enabled them.

Gordon

---

### Post by mixersoft on 2008-05-06
Yes, I tried that. All the proprietary codecs have been enabled.

---

### Post by mixersoft on 2008-05-06
How does ImportDVD work? It seems like it's looking for a locally mounted DVD before it creates a transcoding job. Can I just start a transcoding job manually?

BTW, what happens when you import a DVD? Does it get converted/compressed into a native MythTV format? Can you still use the menu to choose chapters? I'm just starting to play with this.

m.

---

