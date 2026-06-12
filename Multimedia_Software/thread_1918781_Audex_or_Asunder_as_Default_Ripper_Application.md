---
title: "Audex or Asunder as Default Ripper Application?"
date: 2012-02-01
forum: Multimedia Software
---

### Post by markymark64 on 2012-02-01
Does anyone know how to set Audex or Asunder as the default app for ripping my music. When I insert a cd I get several options but Audex and Asunder aren't in that list of choices and I don't know how to add them to this group. Can anyone help me please?

---

### Post by djfake on 2013-01-03
nano ~/.local/share/applications/mimeapps.list

add "x-content/audio-cdda=asunder.desktop"

then go to systemsettings>details>removable media and it should be listed for CD Audio

---

### Post by markymark64 on 2013-01-03
DJFake,

Thanks m8. I actually figured it out awhile ago and forgot to mark the ticket as solved. I'm sure you probably noticed this ticket was from last year. My background is technical so if I don't figure something out in 72 hours I'll wipe the pc and start over.

---

### Post by lambart on 2013-02-07
Thank you djfake for posting the solution. It worked for me on 12.04.

This question turns up on the 1st page of google results for "asunder ripper ubuntu" and I was glad to find it marked [Solved]!

---

### Post by dreddguy on 2013-10-26
Hi. This is my first post on ubuntu forums. 
I too am looking to set Asunder as my default programme for ripping cd's and to have it do so automatically when I insert a disc.
Although I'm sure djfake answer is correct I would appreciate a step by step guide for an ubuntu newbie.
Many thanks in advance.

Dreddguy

---

### Post by The Cog on 2013-10-26
Nano is an editor. You may find gedit easier to use (assuming you have it installed). Run this command from a command prompt:
```
gedit ~/.local/share/applications/mimeapps.list
```
Then add this line to the end of the file and save:
```
x-content/audio-cdda=asunder.desktop
```
that should be it.

---

### Post by dreddguy on 2013-10-27
Super. Got it. Solved. Cheers.

---

