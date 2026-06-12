---
title: "Using LIRC remote with other apps (MAME, screensavers, etc.)"
date: 2013-08-29
forum: Mythbuntu
---

### Post by yonkiman on 2013-08-29
LIRC is working great for MythTV, but I'd really like a "Stop" (esc) remote keypress to be seen by other apps as well.  That way I can run a screensaver and my wife can get out of it by pressing a button on a remote (as opposed to finding a keyboard/mouse).  Also if we're playing MAME with the controller box I have, pressing "Stop" on the remote would escape out of MAME as well.

I've looked around but it's not clear to me how I can make another app accept and LIRC command - is there a simple way to do it?  Or does the app have to support LIRC?

Cheers...

---

### Post by squakie on 2013-08-29
As far as I know, all you do with LIRC is basically map button presses to key presses - I don't *think* it makes any difference for a regular app.  Instead, I would double-check to be sure you actually have the required key stroke(s) mapped to the button you are using - perhaps ESC to the STOP button.  You'll also need to make sure this doesn't affect your media center software - perhaps STOP is mapped to a different keystroke(s) for it.

---

### Post by williammanda on 2013-09-05
> **yonkiman said:**
> LIRC is working great for MythTV, but I'd really like a "Stop" (esc) remote keypress to be seen by other apps as well.  That way I can run a screensaver and my wife can get out of it by pressing a button on a remote (as opposed to finding a keyboard/mouse).  Also if we're playing MAME with the controller box I have, pressing "Stop" on the remote would escape out of MAME as well.

I've looked around but it's not clear to me how I can make another app accept and LIRC command - is there a simple way to do it?  Or does the app have to support LIRC?

Cheers...

Lirc has irexec that can be used to control other programs. Google it...there is alot of info on it.

---

### Post by bullwinkle2 on 2013-09-15
AAARRRRGH… WHY does this forum eat all my line breaks?  Anyway...

Mythbuntu has its own lircrc file in the ~/.mythtv directory, that is not shred with any other software.  Some other software may have their own variation of that file, that takes care of mapping button presses to commands.  If, in your user directory, you have a file named .lircrc, that can be used at all times in all applications, or in individual apps depending on the configuration.  As an example, if you had this in your .lircrc file...

begin
  prog = irexec
  button = KEY_GREEN
  config = ~/startmythtv.sh &
  repeat = 0
end

... Whenever you press the green button on the remote, it will run a bash script named startmythtv.sh in your user directory (where you can do things like making sure old instances of Myth are killed before starting a new one).  And it should work from within any prorgram or even from the desktop, because you specified "prog =" line, then that command would only work while that program is running (in theory, anyway).  That can be a bit tricky to set up, but hopefully that will get you started.

---

