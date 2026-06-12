---
title: "VNC server issues"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by JohnnySage50307 on 2009-07-02
I have recently installed Ubuntu 9.04 Desktop version, but have been tinkering with its server capabilities because I am teaching a beginners programming class. Because some students are a little intimidated by terminal interaction, I wanted to open a VNC server for them. I attempted to install TightVNC using compressed sourcecode from their website, and I was able to use another VNC client to access the server (this client is running on Windows Vista).
 
After opening the client, if I begin to type anything in it (either in an opened terminal window or textpad, etc.), the keyboard is scrambled. Home row is now "a b f h q r d 4 9 o". Can anyone tell me what to do to fix this? If I SSH into the machine, this phenomenon doesn't occur; only in VNC. Thank you in advance!
 
~John

---

### Post by superprash2003 on 2009-07-02
there is an issue of ubuntu 9.04 + vnc + compiz .. so incase you have compiz fusion enabled , disable it..

---

### Post by JohnnySage50307 on 2009-07-02
How would I go about disabling compiz?  I don't believe I've encountered it yet.

---

### Post by jonobr on 2009-07-02
Hello

Go to
System -> Preferences -> Appearance -> Visual Effects
Select none,

---

### Post by jonobr on 2009-07-02
Oh, and 


WELCOME TO THE FORUMS!!!!!!!!!!!!!!!!!!!:guitar:

---

### Post by JohnnySage50307 on 2009-07-02
I don't think compiz was the problem, then.  Following what you just told me, the visual effects were already set to none.  Any other sugestions?  As I said before, the only thing that doesn't seem to work properly is the keyboard through TightVNC.
 
And thank you for the welcome!!

---

### Post by quantumlemur on 2009-08-09
I spent so much much time trying to fix this, and was so relieved when I finally did, I registered to try to spare someone else the frustration...

This is a workaround that finally worked for me, from [https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955](https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955):

> obviously if you are trying to do this with a messed up terminal, you won't be able to. The fix for that is to enable gconf editor by right clicking on Applications > Edit Menus and enabling "Configuration Editor" under "System Tools" then you can do everything with mouse clicks

 1) navigate to desktop > gnome > peripherals > keyboard > kbd
 
2) find the key name "layouts" and double click it. This will bring up an "Edit Key" window. Click on add, then type any two characters and click "OK".
 Note: it seems that any two characters will work, so what you type shouldn't matter
 
3) Close out of gconf editor, and then kill and restart your vnc session. You should now see expected characters when you type. You may see an ugly error screen that KBD has failed, but this does not seem to affect anything.
My "layouts" key had two duplicate "us" values in it, because I had already been fiddling around with keyboard layouts to try to fix it.  I deleted one of them and changed the name of the other, and that worked for me.  If you do have (and want to keep) more than one, you might have to have the top value be something that you've edited, but I'm not sure.  From the comments in there, I kind of got the impression that any change to the values, no matter what it was, caused it to fix itself somehow.

Hope it helps!

---

### Post by SR_ELPIRATA on 2009-08-09
I keep wondering why people use VNC rather than using Ubuntu's integrated option with the remote desktop viewer and vinagre. Whenever I want to control my main computer I just go to the remote preferences in System > Preferences and from the other just execute the remote desktop viewer and you dont even have to type the address, it finds it right away.

I control my HTPC from the room using this remote desktop tool. The HTPC runs windows (ewww) and has tightvnc installed, but I can connect easily with the remote desktop tool provided with Ubuntu.

I also connect via internet to my client's computers whenever support is needed, and have basically the same behaviour, they use windows with tightvnc and I connect with the provided tool with no problems whatsoever.

So, if possible, could any of you enlighten me with the why? :) Much appreciated.

ELP

PS: Hehehe, the sig shows the HTPC being the Ubuntu but I havent done that change physically yet, so is the other way around as explained above.

---

