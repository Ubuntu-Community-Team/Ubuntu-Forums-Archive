---
title: "ir-keytable works but I only get number and arrow keys in X"
date: 2015-01-23
forum: Mythbuntu
---

### Post by Colin_Bates on 2015-01-23
Hi,

I am trying to setup my ir remote. I am using ir-keytable to set the scancode to keycode mapping and this works well, with "ir-keytable -t" showing the correct codes when the remote buttons are pressed. However, only certain button presses will get through to X and mythtv. I am not using LIRC.

The working buttons are passing key codes for:
[LIST]
[*] KEY_1 to KEY_9 
[*]KEY_LEFT, KEY_RIGHT, KEY_UP, KEY_DOWN 
[*]KEY_ESC. 
[/LIST]

The buttons that don't work are:
[LIST]
[*]KEY_M 
[*]KEY_P 
[*]KEY_SPACE 
[*]KEY_I 
[*]KEY_G 
[/LIST]

The checks and tests I have done are:

[LIST]
[*]Reboot. 
[*]Drop to console, chvt 1. All the buttons that do not work in X start start to work fine. 
[*]In an X terminal, "ir-keytable -t" shows all button presses are correct, with the correct KEY_ code. 
[*]With xinput --test, number keys work, letter keys don't. 
[*]When pressing the remote numbers keys, those numbers will work in an X terminal. 
[*]Run lircd, for testing only, with -devinput and run irw. Again the letter keys are blocked. 
[*]Map a letter key to a number button. The number button not longer works. So, it is the KEY_ code that is blocked, not the button press. 
[*]Map KEY_1 to the OK button. OK button will now give '1' in the X teminal. Again, it is the KEY_ code that is blocked, not the button press. 
[/LIST]

To me it seems like X is blocking the letter keys, but I can not figure out why. 

I am using the xfce4 window manager.

I have googled and all I have managed to find is a reference to a conflict with inputlirc. I don't have inputlirc installed.

Any help or pointer greatfully recieved.

Cheer,

Colin

---

### Post by wyliecoyoteuk on 2015-01-23
this might help:
[https://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/](https://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/)

---

### Post by Colin_Bates on 2015-01-23
Thanks for the turorial [wyliecoyoteuk]("https://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/").

I actually fround cure here: [http://www.gossamer-threads.com/lists/mythtv/users/576414](http://www.gossamer-threads.com/lists/mythtv/users/576414).

If you add new key codes with ir-keytable, then you must restart X. X only accepts the key codes it knows about when it is started. Hopefully this will help others avoid "a long evening of frustration".

Cheers,

Colin

---

