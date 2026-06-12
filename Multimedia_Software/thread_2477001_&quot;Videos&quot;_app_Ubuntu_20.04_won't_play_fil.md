---
title: "&quot;Videos&quot; app Ubuntu 20.04 won't play files"
date: 2022-07-12
forum: Multimedia Software
---

### Post by csae2608 on 2022-07-12
Hello,

ui am using Ubuntu 20.04 and noticed the standard video player would refuse to play to certain files , quite a number of times incurring into this.

if it is standard player, why this behaviour'?


please see screenshot of one file that is not playable 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290715&stc=1[/IMG]

Thanks

---

### Post by SeijiSensei on 2022-07-12
```

sudo apt install mpv smplayer
smplayer &

```
When smplayer opens, point to your file with File > Open.

You'll find an icon for smplayer under Multimedia.

---

### Post by Yellow Pasque on 2022-07-13
> **csae2608 said:**
> if it is standard player, why this behaviour'?

Because Ubuntu needs to protect itself against patent laws when distributing software. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mIk3_08 on 2022-07-14
> **csae2608 said:**
> Hello,

ui am using Ubuntu 20.04 and noticed the standard video player would refuse to play to certain files , quite a number of times incurring into this.

You can also try to install vlc if you want via package manager or via repo. Regards and cheers.

---

