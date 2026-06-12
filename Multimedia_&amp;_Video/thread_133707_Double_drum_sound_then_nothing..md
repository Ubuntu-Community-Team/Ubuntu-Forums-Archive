---
title: "Double drum sound then nothing."
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by DonQuixote on 2006-02-20
I have both Gnome and KDE installed on my box, and when I get to the login screen (Ubuntu login) I hear the drum sound twice, one very closely followed by the other.

After login I get an error about how the sound will be set to the null something-or-other.

I'm assuming that there are two different sound driver(?) vying for the sound card.

I could use some help in knowing where to look.

Thanks!

---

### Post by DonQuixote on 2006-02-20
Additional info:

The error message I get on starting up in KDE is:

"Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using null output device"

Thanks.

---

### Post by DonQuixote on 2006-02-20
Okaaaaaaay..... I follow this guide: [http://ubuntuforums.org/showthread.php?t=32063&page=5](http://ubuntuforums.org/showthread.php?t=32063&page=5)  thinking that it might solve the problem...

Now I get **four** drum sounds.  WOW! ;)

I then removed Arts using Synaptic, rebooted, but there is no love on my sound...

---

### Post by DonQuixote on 2006-02-21
Alright... I re-installed (for about the 20th time! :)) and found that upon the installation of the newest ATI drivers on my Sager 5680 with ATI Mobility Radeon 9600 it breaks my sound.

Can anyone tell me why my video drivers would affect my sound?

---

### Post by DonQuixote on 2006-02-21
More information:

I walked backwards along the ATI driver version numbers until I reached version 8.19.10

This version did not blow my sound.

JFYI

---

### Post by Sp@z on 2006-02-21
All I can say is WOW Nice job resolving your issue, and wonderful determination in updating your own thread. Hopefully someone will be helped by it.

---

### Post by DonQuixote on 2006-02-22
Thanks.  I hope it does help someone.  I know sometimes I have a bear of a time finding just the right information.

---

### Post by DonQuixote on 2007-01-18
Gonna dig up this thread.

On upgrading from Breezy to Dapper the version of ATI driver that was working with my machine is no longer working.  So, I'm back to square one.

Will someone direct me to where resources are assigned to the sound card and to the video card.  I'm thinking that I would like to pursue the possibility of a conflict between resources that is creating this problem.

Thanks!

---

