---
title: "[SOLVED] ircat bad file format"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by burningstar4 on 2007-07-23
I'm running a minimal install of Ubuntu Feisty, and am trying to get a Streamzap PC Remote set up for a MythTV install.  I used a premade lircd.conf, and irw outputs button presses correctly.  However, when I run mythfrontend, the remote doesn't do anything.

My .lircrc file is locate at /home/mainuser/.lircrc and /home/mythtv/.lircrc and /home/mythtv/.mythtv/lircrc and looks like this:

```
begin
prog = mythtv
button = 9
config = 9
end

begin
prog = mythtv
button = UP
config = Up
end

begin
prog = mythtv
button = DOWN
config = Down
end

begin
prog = mythtv
button = LEFT
config = Left
end
```

When I run ircat mythtv (as mainuser) in virtual terminal, it gives me the following two lines:
" in /home/mainuser/.lircrc:1 ignored
mythtv: bad file format, /home/mainuser/.lircrc:2

I'm not sure what to do from there, I've checked and followed several guides and none mentioned this.  Any ideas?

---

### Post by burningstar4 on 2007-07-23
Ok, I got it figured out, if anyone else has the same problem.

The problem is the line endings of all the lines, they were all DOS format.  To fix it, I opened the file in nano and then made a commented-out line (didn't matter, just changing the file).  I pressed Ctrl-X to exit, and when it prompted me to save, I pressed Y.  At the prompt asking for the filename to save as, it said:

```
File Name to Write [DOS Format]: .lircrc
```

Pressing Menu-D removed the [DOS Format], and I then hit Enter to save.  Now ircat works just fine!  Sorry I didn't catch this earlier, but I hope this might be useful to someone.  It may be an issue with any pregenerated lircrc files, who knows.

---

### Post by bolapara on 2007-09-24
thanks!  fixed my mythtv problems too.

fwiw, i generated mine from here:  [http://lircconfig.commandir.com](http://lircconfig.commandir.com)

---

### Post by NJHokie on 2007-10-02
YES, this helped me also!  

THANKS

---

