---
title: "Downgrade to a stable NVidia driver? (Trying to fix a VMWare Workstation issue)"
date: 2011-02-25
forum: Multimedia Software
---

### Post by Flaminghedgehog on 2011-02-25
[SIZE=2]I was directed from [this thread]("http://ubuntuforums.org/showthread.php?t=1694747") in a neighboring forum to ask this question here. *Just about every bit of my system information can be found in that thread*.[/SIZE]
[COLOR=Red][COLOR=Black]
To keep things blunt and to the point: Currently, I am using a beta NVidia Driver. I am currently under the presumption that I need to revert to an earlier NVidia Driver version to remedy this Virtual Machine (VMWare Workstation 7.0, Windows XP Guest) problem I currently face.

At this present time, I have downloaded a .run file from the NVidia website (NVIDIA-Linux-x86_64-260.19.36.run to be specific). I am tempted to execute this .run file in the terminal to see if I'm able to revert my driver with this .run file. My nVidia driver version is 270.18, the .run file contains version [/COLOR][/COLOR][COLOR=Red][COLOR=Black]260.19.36 [Judging by the file name] ([/COLOR][/COLOR][COLOR=Red][COLOR=Black]I could be wrong though)[/COLOR][/COLOR][COLOR=Red][COLOR=Black].[/COLOR][/COLOR][COLOR=Red][COLOR=Black]

Ultimately, would running this .run file in the terminal be the best thing for me to do? Or should I try an alternate method? I'm all for suggestions.

Thanks in advance!
[/COLOR][/COLOR]

---

### Post by Flaminghedgehog on 2011-02-25
Downgraded my NVidia driver to version [COLOR=Red][COLOR=Black]260.19.36.[/COLOR][/COLOR]

Doesn't seem to have a major impact on my system. I'm still getting an error that my libGL is too old when I try and run the driconf.

Also, when I try and emulate a game under the Dolphin emulator, an error of this nature appears.

[IMG]http://img189.imageshack.us/img189/4179/screenshotwarning.png[/IMG]

What should I do?

---

### Post by Flaminghedgehog on 2011-02-26
I'm leading myself to believe that I have some form of unique nVidia driver issue where VMWare crashes if I try and use any form of Direct3D acceleration in my Windows XP Guest OS. Additionally, some openGL driver issue that is making me not able to use certain features of my system.

I'm quite tired and frustrated that nothing has been helping me in my unique situation as of yet. I've been trying various procedures with many other users who might be familiar in what I'm dealing with, but to no avail, nobody has been able to help me. Commonly causing more harm than good to my system.
Surely someone must know.. :(

---

