---
title: "Keyboard layout changes reset after restart"
date: 2008-09-17
forum: Multimedia Software
---

### Post by emco83 on 2008-09-17
I have tried to alter my keyboard layout from US to BG but on restart it always resets itself to the US Layout. It actually shows the BG keyboard as still selected even though it has changed back.

Has anyone else come across this or knows how to resolve?
i'm using ubuntu hardy 8.04

---

### Post by Bucky Ball on 2008-09-17
Hi. Open a terminal and paste:

**sudo nano /etc/X11/xorg.conf**

Find this line:

**Option          "XkbLayout"     "us"**

 and make it look like this:
[B]
Option          "XkbLayout"     "bg"[/B]

Hit CTL and X at the same time to exit. Will ask if you want to save and answer 'Y'. Should fix it. Tell us how you went. :)

---

### Post by ianhaycox on 2008-09-17
I had a similar problem and changing it in /etc/X11/xorg.conf fixed it for me.

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection
```

Change XkbLayout from gb to us or bg etc.

---

### Post by emco83 on 2008-09-17
no it didn't work.after restart it was messed.it uses only bulgarian but i want to use bulgarian phonetic.and it wasnt able to change the language.then i opened preferences keyboard layouts selected layouts  switching and its back again with the bulgarian phonetic.after restart the same problem appears.maybe its not "bg" for bulgarian phonetic.may its something else?

---

### Post by ianhaycox on 2008-09-17
Looks like it might be a bug. See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197414](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197414)

Reading the bug report, it seems like you can change /etc/X11/xkb/symbols/bg to fix it.

---

### Post by emco83 on 2008-09-17
i can see its very difficult to do that:(

---

### Post by emco83 on 2008-09-17
i've tried another way
i edit /etc/X11/xorg.conf
 and put Option "XkbLayout" "us,bg"
Option "XkbOptions" "grp:alt_shift_toggle"
now its changing the language after restart but not on phonetic :(

---

### Post by Bucky Ball on 2008-09-17
Try this. Change it in keyboard layout from System->Preferences then check your /etc/X11/xorg.conf file and see if it has changed that in any way. If so, copy that file as a text document (or as a backup if you are confident), restart and change the lines in there that have changed from your saved file, if you follow me. Just a wild idea, but just might work.

:)

---

### Post by emco83 on 2008-09-17
i've finally done it :)
the thing is for phonetic you have to add one more line
  Option          "XkbVariant" ",phonetic"
and now its working perfectly

---

### Post by Johann-1.0 on 2010-05-13
I have a similar problem. I'm actually using two keyboard layouts: Lam and Rus (Spanish Latin America and Phonetic Russian) but everytime I restart or turn on my computer, the russian layout changes and shifts into another, although spanish layout still works fine.
How can I fix this? This is: What can I do to use both layouts even restarting my computer?
Note: Latin American layout works fine after restart.
Thank you very much.

---

### Post by Bucky Ball on 2010-05-13
Johann, this thread is a year and a half old. Start a new one giving as much detail as possible about your issues. Honestly, no one will see you here. This is long gone.

---

### Post by Johann-1.0 on 2010-05-14
Thank you.

---

### Post by ockac23 on 2012-03-27
Hi folks,

I have Xubuntu 11.10. and I am a newbie.
I have tried to enable the bulgarian phonetic keyboard as described above by "Bucky Ball". 
But this /etc/X11/xorg.conf seems to be an empty file. I can not find this line - Option "XkbLayout". Actually there is no text in the file. Am I doing something wrong? Could you please describe for me the intermediate steps also. 

Many thanks

---

### Post by Bucky Ball on 2012-03-27
> **ockac23 said:**
> Hi folks,

I have Xubuntu 11.10. and I am a newbie.
I have tried to enable the bulgarian phonetic keyboard as described above by "Bucky Ball". 
But this /etc/X11/xorg.conf seems to be an empty file. I can not find this line - Option "XkbLayout". Actually there is no text in the file. Am I doing something wrong? Could you please describe for me the intermediate steps also. 

Many thanks

This thread is four years old and you're not going to be found here. Please post a new thread with a title describing your problem and all relevant info. Thanks. ;)

---

### Post by ockac23 on 2012-03-27
> **Bucky Ball said:**
> This thread is four years old and you're not going to be found here. Please post a new thread with a title describing your problem and all relevant info. Thanks. ;)


OK thanks, I did it: 

here: [http://ubuntuforums.org/showthread.php?t=1947657](http://ubuntuforums.org/showthread.php?t=1947657)

---

