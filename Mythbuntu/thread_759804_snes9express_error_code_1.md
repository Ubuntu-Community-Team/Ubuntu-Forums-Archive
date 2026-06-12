---
title: "snes9express error code 1"
date: 2008-04-19
forum: Mythbuntu
---

### Post by voctikal on 2008-04-19
Tried searching but never found an answer besides try ZSNES.

Currently using snes9express, works great but my logitech wiress game pad does not work.  When I enable the game pad and launch a game it gives me error code 1(which im sure others are familiar with).

If i disable the joypad and use the keyboard it loads with no problems.

I have check to make sure the input is set to /dev/input/js0 but still no luck


Any suggestions?

---

### Post by voctikal on 2008-04-19
update

to make the situation more weird, when i set the gamepad driver and load a rom (before config the buttons) it loads.  

So...im thinking that it has something to do with the joypad configuration  .



bump for tonite.

---

### Post by voctikal on 2008-04-20
Bump

Im sure some has had the same issue

---

### Post by voctikal on 2008-04-21
Bump

---

### Post by voctikal on 2008-04-23
Seems no one knows


Mods, please close this thread since no one has an answer

---

### Post by Naerymdan on 2008-04-24
Actually, I have your answer :)

The latest build of snes9x removed the gamepad button setting option from the command line and put it in the config file.

Since snes9express was not updated, it still tries to put the gamepad configuration in the command line.

The easiest solution I have is to remove the gamepad configuration from snes9express, open the snes9x configuration file and put your gamepad config there.

It is quite written plainly, and to get the control codes of your gamepad buttons, just install:

sudo apt-get install jscalibrator

and use it in a console. Numbers will apear continously and change depending on your button presses. Note down what code means what button, press ctrl-z to kill jscalibrator and put thoses in the snes9x config file (I don't remember where it is).

---

### Post by voctikal on 2008-04-25
I tried running the jscal program and it halfway worked. The buttons work but the joystick wont move anything.

When you said run it in a console do you mean the gui jscalibrator program or something different.

---

