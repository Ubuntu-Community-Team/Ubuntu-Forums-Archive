---
title: "[SOLVED] add repeat function to remote"
date: 2008-09-23
forum: Mythbuntu
---

### Post by iitywygms on 2008-09-23
Trying to figure out how to make the remote control scroll the guide when I hold down the page down button.  I have been reading about lirc but honestly it just confuses me.  Can anyone point to a good simple guide or just tell me how to make the buttons behave like I want.
Sorry for the newb question

---

### Post by SiHa on 2008-09-24
You need a repeat statement in the relevant keys in your lircrc: which should be in one of these two locations:
```
/home/<mythuser>/.mythtv/lircrc
or
/home/<mythuser>/.lircrc
```

If the lircrc just consists of a bunch of 'include' statements, you'll need to navigate to the mythtv file declared in there, something like:
```
/home/<mythtuser>/.lirc/mythtv
```

The key definitions for each key you want to repeat should look like this:
```
begin
    prog = mythtv
    button = ArrowRight
    repeat = 3
    config = Right
end
```

The default if there's no 'Repeat' is repeat = 0, so only a single keypress is sent, repeat = 3 sends every third repeat of the remote to Myth.

You might want to add a delay in there if you struggle to get to only move one line because it repeats too fast.```
delay = 5
``` to wait 5 before starting to send repeats.

That should work. If it doesn't, run irw from a terminal, hold a button down on the remote and see what output you get, you should get something like:

```
00000000000017E5 00 Hauppauge OK
00000000000017E5 01 Hauppauge OK
00000000000017E5 02 Hauppauge OK
00000000000017E5 03 Hauppauge OK
00000000000017E5 04 Hauppauge OK
```

The second number increments to indicate repeats. If you don't, there's somthing wrong with your lircd.conf, and probably the toggle bit mask isn't correctly defined. Try recording a new lirc with irrecord. Shout if you're not sure how to do this - I've got to go to work now...

HTH

Simon

---

### Post by iitywygms on 2008-09-24
Thank you so much.  Now I have an idea of what to do.  It will now slowly scroll thru the menu line by line while holding down the button.  That is a definite improvement.
Now can i get it to scroll page by page?  If so, how?

---

### Post by SiHa on 2008-09-25
Not too sure about that - I don't think there's a 'Page Down' function, but I'm pretty new to Myth myself so I'm prepared to be proven wrong.
A 'dirty' way to do it might be to map a remote key you don't use to produce multiple keystrokes. I *think* (but can't confirm as I'm at work), that if you repeat the 'config = ' line:```
begin
    prog = mythtv
    button = Yellow
    repeat = 3
    config = Down
    config = Down
    config = Down
    config = Down
    config = Down
end
```

...lirc will send a keypress for each one. So if you have, say, 5 lines per screen in the guide, each press of the button would scroll 5 lines - 1 screen.

As I say - this is untested, but may be worth a try?

Cheers,

Simon

---

### Post by SiHa on 2008-09-28
OK scratch that. Sorry.
All that does is each time you press the button, irexec cycles to the next 'config =' line. I'm sure there's a way of sending multiple keystrokes when you press a button, bu I don't know what it is...

---

### Post by iitywygms on 2008-09-28
GOT IT!!!

Really simple.

config = PgUp
config = PgDn

:D

---

### Post by iitywygms on 2008-09-28
Spoke to soon.

The page up works, but the page down does not.  Strange.  More investigation is in order.

---

### Post by iitywygms on 2008-09-28
Correction

config = PgUp
config = PgDown

NOW it works correctly.

---

