---
title: "USB Remote works like keyboard - how to map keys"
date: 2007-10-28
forum: Mythbuntu
---

### Post by musther on 2007-10-28
I have a USB DTV tuner with remote control.  The remote was easy to set up in that I didn't have to set it up at all, it was simply recognised as a keyboard.  

The annoying thing is that only the number buttons seem to do anything at the moment, I don't know what the others are mapped to, and even if I can find out, how do I somehow change them, translate them, or map the mythfrontend keys to them?

Cheers

---

### Post by superm1 on 2007-10-29
> **musther said:**
> I have a USB DTV tuner with remote control.  The remote was easy to set up in that I didn't have to set it up at all, it was simply recognised as a keyboard.  

The annoying thing is that only the number buttons seem to do anything at the moment, I don't know what the others are mapped to, and even if I can find out, how do I somehow change them, translate them, or map the mythfrontend keys to them?

Cheers
Use the **xev** tool to determine what they show up as.  You can change their bindings use **xbindkeys** I believe.

---

### Post by jakell on 2010-02-25
I find that xev only recognises the keyboard-like commands sent by the remote, it does not respond to the other buttons, which it does not recognise.

 Is there an application that will display the codes of the other remote buttons, when received, so that I can remap them?

---

### Post by jakell on 2010-02-26
OK.

 I have now figured out (via XEV) that Ubuntu is not just responding to keyboard-like commands, but to certain other buttons on the remote (Play, rewind, skip etc.), but some other buttons are ignored.
 This is only apparent in Gnome apps (Totem etc.) which is why I missed it.

 So, there must be a script somewhere that interprets the button presses, I just need to locate it, and edit it to suit my remote. Can anyone help me locate where this is ??

 I am keen to avoid using LIRC if possible, as it seems to me like a clunky, legacy solution. If vanilla Ubuntu can handle remote controls, without LIRC, then this seems to me like a more elegant solution.

---

### Post by Accidental on 2011-05-04
I am reviving this one from the grave since I have the same issue (and can't find a solution). Is there any way to map certain remote control commands to keypresses on the KB?

---

### Post by Laen on 2011-05-15
I have the same problem.

Some keys are ignored by xev!

Keytouch Editor recognises them and gives the USB code when I press them so they are working and are being received.

---

### Post by knnniggett on 2011-05-16
Don't know if this will help you, but you may want to read this:
[http://www.mythtv.org/wiki/Adesso_ARC-1100](http://www.mythtv.org/wiki/Adesso_ARC-1100)

Even if you don't have this particular remote, it describes the method by which the author determined what codes each button press sent. From there the author either used xmodmap to remap certain keys or he simply remapped the keys within MythTV.

---

### Post by Laen on 2011-05-16
> **knnniggett said:**
> Don't know if this will help you, but you may want to read this:
[http://www.mythtv.org/wiki/Adesso_ARC-1100](http://www.mythtv.org/wiki/Adesso_ARC-1100)

Even if you don't have this particular remote, it describes the method by which the author determined what codes each button press sent. From there the author either used xmodmap to remap certain keys or he simply remapped the keys within MythTV.

Unfortunately he uses xev which seems to be failing in my (and others') cases.
Ironically it's the largest button on my remote that's not being recognised (the OK between the arrows).

Very frustrating.

---

### Post by knnniggett on 2011-05-20
Assuming you are running MythTV, have you tried the following?

From Mythfrontend, go to Settings -> Edit Keys. From there attempt to remap a key (any key really, you don't have to save your changes). 

When you get to the point where it asks you to hit the new button... press the button on your remote in question. At that point it should tell you the code MythTV saw.

---

