---
title: "Volume Control - How to change the default mixer?"
date: 2005-12-02
forum: Multimedia &amp; Video
---

### Post by PsyberOneZero on 2005-12-02
I've scoured the forums and found plenty of ways to map the special keys and add new keymapping programs but noone has answered this clearly.  Where is it set which mixer is controlled by the media keys.

My example specifically:

Nvidia CK804: I use the s/pdif output
Logitech USB Headset: use 99% of the time

the media keys adjust the Master Volume mixer in Nvidia CK804 which isn't helpful for either use.

I've seen several other confused and frustrated people in the forum searching for the same thing.

---

### Post by drkemp on 2005-12-03
I have used Lineak [http://lineak.sourceforge.net/]("http://lineak.sourceforge.net/") in the past to get lots of flexibility over the key mapping.

---

### Post by PsyberOneZero on 2005-12-03
[QUOTE=drkemp]I have used Lineak [http://lineak.sourceforge.net/]("http://lineak.sourceforge.net/") in the past to get lots of flexibility over the key mapping.[/QUOTE]
Thank you for responding. I've used that but there's a wrinkle in my case.  I'm using the Vol+ and Vol- on my headphones (which are recognized but, again, only contol the Nvidia CK804 Master) and my keyboard isn't on the Lineak supported list (cheap GE keayboard, it's only $9.99 but It's survived longer than my expensive ones).

Somewhere in the Gnome code it tells it that the Volume Up command no matter what key it's assigned to will effect this mixer device.  There has to be a hidden gconf setting or an obscure file that tells it what to move.

---

### Post by schdefan on 2005-12-05
you can store volume settings with 
```
$ sudo alsactl store
```

schdefan

---

### Post by stefann on 2005-12-23
Still no solution to this problem? Strange.

---

### Post by Megatog615 on 2007-02-18
Old thread but, update please? How exactly do you specify what the multimedia buttons do, besides change the master control on card 0?

---

### Post by nelfer on 2007-10-10
:(
I'm having this same problem. The multimedia keys are recognized and I have the option to assign them to "Volume Up", "Volume Down" and "Mute". The problem is that those 'actions' only work with the "master" and I'm connected to the "headphone" output, which doesn't get affected at all by this.

In Fedora Core, changing the device in the volume applet in the task bar will automatically change the keys to use whatever that device is. Meaning, whatever device I have selected in my volume applet to control, that's the one that the multimedia key setups should obey too.

Too bad there is no answer for this. I was really hoping I was gonna find an answer here.:(

---

### Post by nelfer on 2007-10-10
Ah..I found a solution. It worked for me.

Go to System > Preferences > Sound

Then in the first tab, under Device, select first your device and then there will be a list of "elements" of that device underneath. Just select the one you want Headphone, speaker, master, etc.

That's it! That should take care of it.

---

### Post by bve on 2008-04-05
Thanks for posting your solution, solved my issue too.


Burke

---

