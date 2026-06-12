---
title: "Need Help to Understand the following Instruction?"
date: 2008-05-24
forum: Multimedia Software
---

### Post by davidkyn on 2008-05-24
Need Help to Understand the following Instruction?
Hi,
I dont quite understand how to change the line...I follwed the part about the update and that was good,,,,,but If I can refer to to the BOLD print below:


Mute Speakers when Headphones are used

* This has been a big deal for folks with Intel HDA type sound cards. The fix is as follows. Information about this fix is gotten from here.
o Update ASLA to the latest (1.0.16 as of this writing). I have instructions here.


o In your /etc/modprobe.d/alsa-base add the following line.
+ options snd-hda-intel probe_mask=8 model=lenovo
+ save and exit
+ reboot the machine and when you insert headphones the speakers will mute.

???HOW DO I OPEN /ECT/MODPROBE.D/ALSA-BASE & do I simply cut and paste the options snd- ect... into the terminal or what?????????????????

I have no experience so go easy...I just came back to ubuntu after leaving a year ago becuase of this problem....thanks in advance:)

---

### Post by Kevbert on 2008-05-24
Go to terminal via Applications-Accessories.
Enter the following:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Enter your log-in password when prompted.
A new window will open with the alsa-base file.
At the bottom of the file enter:
```
options snd-hda-intel probe_mask=8 model=lenovo

```
Save the file and exit the editor.
In terminal enter
```
exit
```
to exit terminal.
you may need to restart the PC for the code to take effect.
You can copy the code here by using Ctrl+C and Ctrl+V to paste (Ctrl+Shift+V in terminal).

---

### Post by davidkyn on 2008-05-24
Thanks man,
that was an excellent reply...just the sort of thing I need:)<
Ufortunately I some how stuffed it up before logging back in here and now I have no sound.

Its a long story, but I am not going to let it beat me this time around...
I am going to reistall then come back here and ask for help with the Damn Headphone and speaker issue with HD sound cards like mine.........

I hope I will get similar help...I like other newbies dont mean to offend when we say we find some of the help a bit vauge (lol I cant even spell)

Some of us dummies can use all the patients we can get...

I tired suse10.3 but the networking side was way out of my league...Ubuntu really does rock...even though I still got to learn.

Guess I'll be seeing you round
Thanks again man:guitar:

---

### Post by cdtech on 2008-05-24
Good luck...

This is a great site for help, I agree.

---

