---
title: "ALSA won't work with non super user account."
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by sistoviejo on 2007-06-14
When I try to use the sound mixer or to play sound with Xmms I get error messages saying that a sound card can't be found. This is the exact message that appeared when trying to open alsamixergui: "alsamixer: function snd_ctl_open failed for default: No such device"
It must be noted that this only happens when I try to use sound applications with my non super user account. If I try to run alsamixergui or xmms using my super user account they both work propperly as they should. I guess for some reason only super user is allowed to use ALSA. Can anybody give me any suggestions as to how I can get sound to work with my non super user account?
Thanks in advance!

---

### Post by muximus on 2007-06-14
did you compile alsa??... this kinda behaviour does not occur out of the box.. if you did.. then i guess you did it as root, and the file permissions do not allow any other user besides root to access them..so just recompile and install alsa using sudo..

---

### Post by bcrowell on 2007-06-14
Try adding the other user to the audio group.

---

### Post by sistoviejo on 2007-06-14
> **bcrowell said:**
> Try adding the other user to the audio group.

ok. how do I do that? thanks for your reply

---

### Post by sistoviejo on 2007-06-14
> **muximus said:**
> did you compile alsa??...
no i didn't.  thanks for your reply

---

### Post by sistoviejo on 2007-06-15
> **sistoviejo said:**
> ok. how do I do that? thanks for your reply

Edit: Sorry for the silly question. I will try this when I back to my computer.

---

### Post by sistoviejo on 2007-06-26
I got it working. Adding my user to the audio group didn't solve the problem.
I solved it by enabling access of root user to gnome. Now I use root all the time. :D
*[COLOR="White"][SIZE="1"]I know this ain't 100% safe but I ain't the pentagon either.[/SIZE][/COLOR]*

---

