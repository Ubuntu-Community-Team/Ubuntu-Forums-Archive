---
title: "lirc for firefox, default lirc?"
date: 2009-08-03
forum: Mythbuntu
---

### Post by mathog on 2009-08-03
Our Mythtv box runs only with a remote control - there is no keyboard or mouse.  Consequently some of the menu options are a one way street, since they start functions which do not respond to the remote.  At that point, either a restart is needed (just frontend or whole system) or I have to log in with ssh and "kill" the unwanted program.

Issue 1.  The most common of these programs is firefox. Do any of you have firefox working under lirc control?  If so, please post your config file.  It would be nice to be able to do some navigation in that browser, but if not, at least to be able to exit it.

Issue 2.  If the program started isn't firefox, it could be anything.  Is there a way to make lirc default to a common setting file when the program name does not match any of the special config files in the system?  For instance, this would allow one to send ^c , Q, ^Q and other common exit codes.

Thanks.

---

### Post by jis on 2009-08-04
You can use irxevent daemon together with lirc daemon to pass keypresses to programs.

---

### Post by mathog on 2009-08-08
> **jis said:**
> You can use irxevent daemon together with lirc daemon to pass keypresses to programs.

I'm already using lirc with entries like this one to talk to mythtv:

begin
    remote = RM-VL600_8201
    prog = mythtv
    button = enter
    config = Return
    repeat = 0
    delay = 0
end

and that works fine, however, this does not, apparently, send anything to firefox that it recognizes:

begin
    remote = RM-VL600_8201
    prog = firefox
    button = enter
    config = Return
    repeat = 0
    delay = 0
end

(Based on the first pop up screen which is about restarting from the last
session or starting a new one, which starts with two options, one highlighted.  I also tried defining Tab and the highlight would not shift from option to option either.)

I have seen examples using irxevent to talk to Firefox, but irxevent is X11 window oriented, not program oriented, and I don't see how to make it coexist with my present lirc files for mythtv and the like, which are per program.  Sure, when firefox is running irxevent would do the right thing, but when it isn't running who sees the keypress and how is it processed?  What I would want is it for to go through the existing .lirc configuration, but I suspect that instead irxevent will grab it and send it to the top window, which would typically be mythtv but might be xine or something else.  Since the button -> config maps aren't the same for all of these there would be trouble.

How does one make these play nicely with each other?

Thanks.

---

