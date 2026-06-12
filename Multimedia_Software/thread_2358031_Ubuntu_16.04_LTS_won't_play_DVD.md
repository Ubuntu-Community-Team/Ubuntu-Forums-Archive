---
title: "Ubuntu 16.04 LTS won't play DVD"
date: 2017-04-08
forum: Multimedia Software
---

### Post by John_Patrick_Mason on 2017-04-08
I'm having trouble playing a DVD. I tried playing it using the VLC program and got the following error:

 [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not open the file "/media/mason/XYZ" (Permission denied).[/COLOR]

 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'file:///media/mason/XYZ'. Check the log for details.[/COLOR]

 [COLOR=#000000]
For some reason, it won't boot directly, but it does give me the option of opening the files stored on the DVD using a file manager.
[/COLOR]

---

### Post by wildmanne39 on 2017-04-08
*Thread moved to **Multimedia Software**.*

---

### Post by speartip on 2017-04-15
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
This might help.

---

### Post by John_Patrick_Mason on 2017-04-22
[QUOTE=speartip]https://help.ubuntu.com/community/Re...ts/PlayingDVDs
This might help. [/QUOTE]

I did what you suggested, still getting the same error message in VLC Media Player.

---

### Post by speartip on 2017-04-23
Is it just that one DVD, or are all others giving the same error message?

---

### Post by walterav on 2017-05-04
Think its more a right issue here, could you post the terminal output of:

```

ls -la /media/mason
id
who

```

Are you on a default ubuntu user/admin account or are you using some custom privileged account?

---

