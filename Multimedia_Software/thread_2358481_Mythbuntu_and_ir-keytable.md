---
title: "Mythbuntu and ir-keytable"
date: 2017-04-14
forum: Multimedia Software
---

### Post by paul-norbealun on 2017-04-14
Me: one of the may sad Australians losing our TiVo EPG service at the end of October.
My rig: Mythbuntu 16.04, Myth 0.28, Shepherd listings grabber, 2 x AverTV Volar Green HD tuners, Asus laptop (while testing)
Remote: TiVo series three

Everything is working as it should be (at last)...

I have created a customised ir-keytable keymap to translate the TiVo remote scancodes but I'm stuck now trying to do two things:
[LIST=1]
[*]Map my "Play" button to Ctrl+P
[*]Map by rewind/fast-forward keys to < and > respectively.
[/LIST]

These mappings would make the TiVo produce a much more comfortable fit with the way the TiVo box works.

Now I understand the differences between keyboard events and characters, so I know that Ctrl+P would consist of the following keyboard events: KEY_LEFTCTRL down, KEY_P down, KEY_P up, KEY_LEFTCTRL up (or KEY_RIGHTCTRL).  And the "<" would consists of KEY_LEFTSHIFT down, KEY_COMMA down, KEY_COMMA up, KEY_LEFTSHIFT up.

Now I *could* rejig the keybindings in Myth, but I'd like to stick with the standard setup.  Does anybody know where/how I can translate the rewind scancode from the TiVo remote (0x853022d0) into the "<" character?

---

### Post by howefield on 2017-04-14
Thread moved to the "*Multimedia Software*" forum for a better fit.

---

### Post by paul-norbealun on 2017-04-15
Well, I've solved it enough to make me happy, although I never resolved the original question.

In brief:
I set up a keytable for ir-keytable that mapped as follows:
Pause -> KEY_PAUSE
Play -> KEY_PLAY
<< -> KEY_REWIND
>> -> KEY_FASTFORWARD

Then in Myth front-end I used the keybindings to map the button on the remote directly to the corresponding functions in addition to the standard keyboard functions.


The thing that I had tried to do - and couldn't - was use loadkeys to remap KEY_PAUSE, KEY_PLAY, KEY_REWIND and KEY_FASTFORWARD to the standard Myth keys.  It would have been nice to learn how to do that, and I'd definitely still be interested in answers.  It didn't seem to matter what I did in my keymap file I couldn't change the characters produced.  Perhaps I need to do something in the X or the Gnome layers...

---

