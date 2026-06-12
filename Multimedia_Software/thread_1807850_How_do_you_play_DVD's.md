---
title: "How do you play DVD's?"
date: 2011-07-19
forum: Multimedia Software
---

### Post by VivNelson on 2011-07-19
Hi,

I am sorry if this has been asked before, but I need to ask.

Last night I installed ubuntu on my pc, I am having problems in playing DVD's, can someone please talk me through how to do this. I have installed various players but nothing seems to play, VLC SmPlayer, Dragon, Gnome.

Please can you guide me in the form of an idiots guide, no offence will be taken.

thanks in advance
Viv

---

### Post by aromo on 2011-07-19
Look for and install ubuntu-restricted-extras, that should do

---

### Post by ron999 on 2011-07-19
> **VivNelson said:**
> 

Please can you guide me in the form of an idiots guide, no offence will be taken.


Hi
Paste this command into the terminal:-

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by ajgreeny on 2011-07-19
Those two posts will help, but in order to understand all about this, I suggest you have a good read through [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and do everything it suggests.

I particularly recommend the links on that page which will take you to **medibuntu**.

---

### Post by VivNelson on 2011-07-19
Wow, excellent it works!

Thank you both for your time and patience.

Ps: I am really a novice at this, I had to search google to find out what a terminal was.   

Thanks once again.

---

