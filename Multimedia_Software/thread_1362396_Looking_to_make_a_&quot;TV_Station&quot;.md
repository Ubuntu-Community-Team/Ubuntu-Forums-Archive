---
title: "Looking to make a &quot;TV Station&quot;"
date: 2009-12-23
forum: Multimedia Software
---

### Post by ELF_O8 on 2009-12-23
I've been contemplating this idea for a while now. Basically, I have an extra computer just lying around that I plan on making a "TV Station." I have several TV shows and movies ripped onto the hard drives, and I need a way to set up a schedule for them to playback.
What I'm looking to do is have SHOW1 play between, say, 12 AM and 4 PM, then show a movie, then play SHOW2, etc. I also want this program or script to be able to choose the individual AVIs at random from specified folders (SHOW1, SHOW2, Movies, etc).

If all or any of this can be done, it would be greatly appreciated to be informed of a way to accomplish it. If it's just a point in the right direction, a way or structure to write a script, whatever, it's all appreciated. I've been researching this for some time and haven't found anything helpful so far.

P.S. - If this can actually be done, an extra bonus would be for the program/script to send an email of the upcoming schedule daily.

---

### Post by lovinglinux on 2009-12-23
You can do that with the streaming capabilities of VLC. Just open the files with the "Advanced Open File" option, then hit "ALT+S" to launch the stream options. After filling alll options and testing, you can copy the command from the GUI to use as a template and create a script to randomize the programming. The forum has several threads with VLC commands.

---

### Post by ELF_O8 on 2009-12-23
Alright, I understand what you're saying, but could you point me toward one of these VLC command threads? I don't really understand all of the options or how to output the GUI commands to a terminal or write them to a text file so I can modify it.

---

### Post by lovinglinux on 2009-12-23
> **ELF_O8 said:**
> Alright, I understand what you're saying, but could you point me toward one of these VLC command threads?

[http://tinyurl.com/ykkjcu4](http://tinyurl.com/ykkjcu4)

> **ELF_O8 said:**
> I don't really understand all of the options...

[http://wiki.videolan.org/Documentation:Streaming_HowTo](http://wiki.videolan.org/Documentation:Streaming_HowTo)

> **ELF_O8 said:**
> I don't really understand...how to output the GUI commands to a terminal...

To run a command, open "Applications >> Acessories >> Terminal", then paste the command in the terminal and hit Enter.

> **ELF_O8 said:**
> I don't really understand...how to...write them to a text file so I can modify it.

Copy the command from VLC or from a web page, then open the text editor and paste.  If you want to automate the process, you will have to create scripts. See these:

[http://www.panix.com/~elflord/unix/bash-tute.html](http://www.panix.com/~elflord/unix/bash-tute.html)
[http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by ELF_O8 on 2009-12-23
Though your answers may have been a little...harsh, I appreciate your input.

---

