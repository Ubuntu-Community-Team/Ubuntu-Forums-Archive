---
title: "Ctrl-Alt-Plus/Minus not working anymore"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by patsissons on 2007-03-03
My setup is a dual monitor twinview setup.  pretty standard otherwise.  I used to be able to switch resolutions on the fly using ctrl-alt-plus (or minus), but now the key combination does nothing.  I can still change resolutions on the fly with the new nvidia control panel (with the newer drivers) or painfully with xrandr, so this issue is not critical at all.  It is, however, still an annoyance as going through the nvidia control panel is slower.  Just curious if anyone out there is experiencing the same thing as I am.  I'm running edgy, with nvidia drivers 1.0-9746 on xorg 7.1.1 x86.

thanks.

---

### Post by guni82 on 2007-03-09
I have the same problem with nvidia drivers 1.0-9629. I'm using edgy too.

---

### Post by reduz on 2007-03-22
SAME PROBLEM, HELP PLEASE!

Any ubuntu developer or experienced user? THIS STOPPED WORKING WHEN UPGRADING FROM DAPPER TO EDGY EFT!!!! NO ONE ON IRC HAS A CLUE!!

---

### Post by guni82 on 2007-03-22
I found a solution that works for me :) 

To switch meta modes i use *xvidtune -prev* and *xvidtune -next*.

To bind it to a keyboard shortcut:
Run *gconf-editor*. 
Go to apps -> metacity -> keybinding_commands
Edit key *command_1* and enter value *xvidtune -prev*
Edit key *command_2* and enter value *xvidtune -next*
Go to apps -> metacity -> global_keybindings
Edit key *run_command_1* and enter any shortcut you like
Do the same with *run_command_2*

Using Crtl-Alt-+ wont work as shortcut and you have to do this for each user.
Maybe someone knows how to set a shortcut for X11.

---

### Post by reduz on 2007-03-22
Thanks! I was planning to do something like this if all else failed, however.. do you know why the usual alt-ctrl-plus/minus just dont work anymore? Also this wont fix the switching to textmode console problems...

---

### Post by guni82 on 2007-04-16
I dont't know why ctrl-alt-plus/minus does not work. But i don't have any problems switching to text mode. Ctrl-Alt-F1 works fine.

---

