---
title: "passing IR commands from lircrc to the OS/screen manager"
date: 2014-06-17
forum: Multimedia Software
---

### Post by diyhouse on 2014-06-17
I am using stanzas similar to the following in order to pipe commands to mythtv,....

  # Button Zero
  begin
    prog = mythtv
    button = KEY_NUMERIC_0
    config = 0
  end

My question is how do I pipe a command, eg Ctrl-Alt-left/Right to the OS in order to switch view screens.

What "prog" entry do I need to use?

Many thanks

---

### Post by diyhouse on 2014-09-19
As a point of closure on this question I have found that the following should sort my problem out,.. although I must confess I have not got round to trying it out yet as I have other issues to work and fix.


 irexec will allow you to run programs. irxevent will allow you to trigger X11 key presses.

---

