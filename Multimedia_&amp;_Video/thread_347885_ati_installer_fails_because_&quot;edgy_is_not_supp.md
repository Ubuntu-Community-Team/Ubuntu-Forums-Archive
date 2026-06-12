---
title: "ati installer fails because &quot;edgy is not supported&quot;"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by Rippy on 2007-01-27
following this guide,
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I got to the step where you run ati-driver-installer. It chugs for a couple seconds, then gives me this error:

```
The distribution 'Ubuntu-edgy' is not supported
```

And then it aborts.

I'm using 6.10 Edgy, obviously. My video card is a Radeon 9250. I just  re-installed Edgy over my old Dapper, which is why I'm doing this in the first place, so there shouldn't be any old drivers complicating things.

Any help?

-Rippy

---

### Post by agustin.g on 2007-01-28
Hmmm... I'm a Radeon 9250 user as well, although i don't remember very well how i got my card to work. The newest drivers do not support the video card anymore, you have to install the 8.28 version if i'm not mistaken. I'd suggest to check ATI's website, download the 8.28 drivers and then try installing from there. It's quite likely that the X server will crash. If the error description says "no screens found" try opening your xorg.conf and check if the names in the "Server Layout" section (almost at the end of the file) correspond to the ones in other sections. For example, if you have:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
```

the "screen" section should look like this: ```
Section "Screen"
	Identifier	"Default Screen"
```

(the names will most probaby not be the same)

hope that helps, if you need any help don't hesitate to ask or send me a pm

---

### Post by Rippy on 2007-01-28
Yeah, 8.28.8 was the version I was trying to install.

o_O

---

