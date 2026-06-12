---
title: "Dual Monitor Setup Help"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by EerFoolWVU on 2007-04-25
is there any sort of automated process to setup dual monitors in Ubuntu?


I've tried some of the more difficult methods I've read about on various forums, but there always seems to be some sort of snag that I run into preventing me from getting things setup.

If it matters I'm running a BFG 7800 GTX (yeah, huge waste of money I know)

---

### Post by rsambuca on 2007-04-25
It is actually pretty easy with nVidia cards.  First question:  What version of ubuntu are you using?  Feisty, Edgy, Dapper?

Second question.  Have you installed the proprietory nvidia driver, and if so, what method?

---

### Post by EerFoolWVU on 2007-04-25
I just upgraded to Feisty Fawn yesterday evening.


The last time I updated my drivers I used EasyUbuntu or whatever program that is.

---

### Post by rsambuca on 2007-04-25
Actually with Feisty, all you have to do to install the nvidia driver is to go to System -> Administration -> Restricted Drivers Manager.  Then just enable nvidia.

After you have done that, you will have to restart the Xserver by pressing control-Alt-Backspace.

Hopefully things are running OK.

Then enter this command in a terminal to edit the xorg.conf:```
gksudo gedit /etc/X11/xorg.conf
```

enter your password, then add these lines to your "Device" Section before the "Endsection":```
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
```

Save and exit.

Then restart xserver again.

---

### Post by EerFoolWVU on 2007-04-25
well hot damn...that was awesome! so much easier than what I'd be trying to do previously



one question, is there a way to flip things so my primary monitor is on the right instead of left? thanks, so awesome

---

### Post by EerFoolWVU on 2007-04-25
man, this is awesome



ubuntu now officially and entirely pwns windows

---

### Post by rsambuca on 2007-04-25
> **EerFoolWVU said:**
> well hot damn...that was awesome! so much easier than what I'd be trying to do previously



one question, is there a way to flip things so my primary monitor is on the right instead of left? thanks, so awesome

I've never tried it, but see if changing this line works ```
Option "TwinViewOrientation" "LeftOf" 
```

---

### Post by Crashmaxx on 2007-04-25
> **EerFoolWVU said:**
> well hot damn...that was awesome! so much easier than what I'd be trying to do previously



one question, is there a way to flip things so my primary monitor is on the right instead of left? thanks, so awesome
Just change this line:
```
Option "TwinViewOrientation" "RightOf"
```
To this:
```
Option "TwinViewOrientation" "LeftOf"
```
And you should be good to go.

---

### Post by EerFoolWVU on 2007-04-25
worked like a charm, thanks again


the only problem now (albeit a small one) is the the taskbars don't show up on the 2nd monitor but i still can't use those small portions of that monitor

---

### Post by Tylo on 2007-04-25
Any easy ATI Solutions?

---

### Post by greenwom on 2007-05-04
> **EerFoolWVU said:**
> worked like a charm, thanks again


the only problem now (albeit a small one) is the the taskbars don't show up on the 2nd monitor but i still can't use those small portions of that monitor

I'm running a fresh install at the moment, so I can't test this.  You should be able to go to the second display and add a new panel.   Right click your old panel and click new panel, then just drag it over

---

### Post by Arrrgh4life on 2007-05-14
> **Tylo said:**
> Any easy ATI Solutions?
Agreed, I am having lots of trouble getting dual monitors with my ATI 9550.  I am on Ubuntu Studio.  It has an image on both monitors, but its just cloned.

---

### Post by jagou on 2007-05-16
Any help getting the dual monitor setup with a 9550 would be appreciated. I am trying to acquire an Nvidia card, but until then It'd be great to be able to do more than clone.

---

