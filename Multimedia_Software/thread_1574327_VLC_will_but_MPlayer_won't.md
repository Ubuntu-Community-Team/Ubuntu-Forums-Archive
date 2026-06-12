---
title: "VLC will but MPlayer won't"
date: 2010-09-14
forum: Multimedia Software
---

### Post by mikulator on 2010-09-14
I have searched and searched - updated and updated but with no luck

Has anyone experenced the following - VLC will play an .iso, but Mplayer won't? :confused:

Mplayer will play some of my .iso but not all, the ones I get an error on have to do with a standerd "permission denied".

All of my iso file are located in the same directory

I would nomally just give up at use VLC, but I use the PS3 Media Server which uses Mplayer...

Cheers,
Mik

---

### Post by mikulator on 2010-09-14
I can add that the error message is:

Could not open location: you might not
have permission to open the file

---

### Post by howefield on 2010-09-14
Try initiating the movie via terminal, ie

```
mplayer name-of-file
```

You might get more of a clue in the terminal as to what is wrong.

---

### Post by mikulator on 2010-09-14
I just did - and i worked that work running as root.:-?

[INDENT]as user I got the following:
*mplayer: could not connect to socket*
*mplayer: No such file or directory*
*Failed to open LIRC support. You will not be able to use your remote control.*

*Playing TOY_STORY.iso.*
*File not found: 'TOY_STORY.iso'*
*Failed to open TOY_STORY.iso.*
[/INDENT]
Looking at the permissions there is no difference - visible difference

---

### Post by howefield on 2010-09-14
> **mikulator said:**
> [INDENT]as user I got the following:
*mplayer: could not connect to socket*
*mplayer: No such file or directory*
*Failed to open LIRC support. You will not be able to use your remote control.*

*Playing TOY_STORY.iso.*
*File not found: 'TOY_STORY.iso'*
*Failed to open TOY_STORY.iso.*
[/INDENT]
Looking at the permissions there is no difference - visible difference

Wouldn't worry too much about the top half, although I should have said to run it from the folder the file is in, or provide the full path to it.

---

### Post by mikulator on 2010-09-15
I have not solved it, but I am leaning twards an issue with the ISO files them selves... Mplayer works, VLC works but Movie Player does not work.

Now looking at solving this problem...](*,)

---

