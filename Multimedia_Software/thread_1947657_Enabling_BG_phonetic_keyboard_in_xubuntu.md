---
title: "Enabling BG phonetic keyboard in xubuntu"
date: 2012-03-27
forum: Multimedia Software
---

### Post by ockac23 on 2012-03-27
Hi folks,

I have Xubuntu 11.10. and I am a newbie.
I have tried to enable the bulgarian phonetic keyboard as described in another post in this forum:

Open a terminal and paste:

sudo nano /etc/X11/xorg.conf


The Output should be:

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection


Find this line:

Option "XkbLayout" "us"

and make it look like this:

Option "XkbLayout" "bg"

Hit CTL and X at the same time to exit. 




I have tried this but /etc/X11/xorg.conf seems to be an empty file. I can not find any line in it. Actually there is no text in the file. Am I doing something wrong? Could you please describe for me the intermediate steps also if I miss something. 

Many thanks

---

### Post by Bucky Ball on 2012-03-27
This will might work for you:

[FONT=Verdana]http://askubuntu.com/questions/85054/lubuntu-keyboard-problem

Check the first answer. I advise backing up the bashrc file before editing it.

[/FONT][FONT=Verdana]
[/FONT]

---

### Post by ockac23 on 2012-03-27
Thanks for the update. I'll try this tonight.

---

### Post by LewisTM on 2012-03-27
You should start by using the solutions made available by Xfce before editing config files and startup commands.
Install xfce4-goodies which provides the xkb panel plugin.
Once this is done, add the Keyboard layouts plugin to one of your panels.
Right-click it and choose Properties to edit your layouts and special keys.
Make sure that in the Xfce Settings Manager/Keyboard/Layout the option 'Use system defaults' is checked to avoid conflicts with the plugin.

Cheers!

---

### Post by ockac23 on 2012-03-27
> **LewisTM said:**
> You should start by using the solutions made available by Xfce before editing config files and startup commands.
Install xfce4-goodies which provides the xkb panel plugin.
Once this is done, add the Keyboard layouts plugin to one of your panels.
Right-click it and choose Properties to edit your layouts and special keys.
Make sure that in the Xfce Settings Manager/Keyboard/Layout the option 'Use system defaults' is checked to avoid conflicts with the plugin.

Cheers!

Thank you very much. It worked!

---

### Post by Bucky Ball on 2012-03-27
> **ockac23 said:**
> Thank you very much. It worked!

Beautiful and nice tip. Please mark thread as 'Solved' from Thread Tools to help others. ;)

---

