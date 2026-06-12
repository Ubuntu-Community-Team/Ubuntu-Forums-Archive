---
title: "My sound only works as root"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by spiritualized on 2007-04-16
Can anyone point me in the direction of the file i need to chmod? I'd be very grateful.

---

### Post by joft on 2007-04-16
Is the user in question member of the "audio" group?

---

### Post by spiritualized on 2007-04-18
Thanks for the response, the answer's yes, it still doesn't help.  I've noticed I've got no .asoundrc in the users home account, only in roots so i'll have a go with that.

---

### Post by joft on 2007-04-23
Hmmm, very strange. AFAIK you don't need an .asoundrc file just to have sound working, it's for additional features. So, I don't think this the reason.

Are you sure, that as long as you are logged in as a normal user there is no other process sitting on and blocking the whole sound device? You could try (as normal user):
```

lsof | grep /dev/dsp
lsof | grep /dev/snd

```
Besides that, does the mixer work? That means, are you able to move sliders? Or no mixer, too? You could try that with
```

alsamixer

```
or of course the Gnome Volume Control.

Sorry, for being a little bit late, with this answer.

---

### Post by TradiZ on 2007-04-24
I have the exact same problem,

If I kill gdm, login as root, aplay -l shows me the soundcard, startx, sound works,

If I login as my user, aplay -l shows  "no sound device found", no sound at all. (I hear the two knocks before giving my login name) I also tested to create another user, same problem.

I am on Fiesty with Intel-hda,

it must be permissions somewhere, and yes, my user is in the audio group as well as the group users and root.

lsof | grep /dev/dsp
lsof | grep /dev/snd

gives me no input as normal user, alsamixer: no such device

alsamixer works as root when gdm is off.

Anyone?

Best Regards
Tradiz

---

### Post by spiritualized on 2007-04-26
> **joft said:**
> Hmmm, very strange. AFAIK you don't need an .asoundrc file just to have sound working, it's for additional features. So, I don't think this the reason.

Are you sure, that as long as you are logged in as a normal user there is no other process sitting on and blocking the whole sound device? You could try (as normal user):
```

lsof | grep /dev/dsp
lsof | grep /dev/snd

```
Besides that, does the mixer work? That means, are you able to move sliders? Or no mixer, too? You could try that with
```

alsamixer

```
or of course the Gnome Volume Control.

Sorry, for being a little bit late, with this answer.




Thanks for the response, i'm slapping my forehead not thinking of lsof, having said that it hasn't helped.  I found one process that had hold of snd:

xfce-mcs- 4738       neil    5u      CHR      116,9                8200 /dev/snd/controlC0

as that was the xfce-mcs-manager i was a little reluctant to kill it but bit the bullet and killed it off, another lsof confirmed nothing now had hold of snd or dsp however still no sound.

alsamixer works fine (visually) as non root user.

---

### Post by TradiZ on 2007-04-29
SOLVED!

Well, I installed the latest updates and then checked /etc/group file, and I saw something in the row for audio:

Before updates: 

```
Audio:x:29:root:username

After update:

audio:x:29:username,username
```

Restarted gdm, sound now works.

Best Regards

TradiZ

---

### Post by anirban.sam on 2007-05-05
try "sudo chmod 666 /dev/dsp"

---

