---
title: "lirc with hauppauge nova-t 500: only receives numbers"
date: 2013-07-07
forum: Mythbuntu
---

### Post by mcld on 2013-07-07
Hi - I've installed the mythbuntu stuff on this Xubuntu 13.04, and MythTV works fine. The tuner is a Hauppauge NOVA-T 500 dual tuner that comes with a remote.

But lirc is only giving me numbers, none of the other controls (ok, left, right, play, fwd, rw, pause...). I see this in Mythfrontend (I can change channels while watching live TV but can't do anything else) and also in "irw" (if I press the numbers on the keypad the numbers come out in the Terminal window, but nothing else).

When the lirc package was installing, I selected the appropriate model. As a result,   /etc/lirc/lircd.conf  only contains some comment lines plus:

```
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novat500"
```

Has anyone seen this? I've been searching the web and couldn't find anyone having the same symptoms, but I imagine it's a symptom of a misconfiguration somewhere. I'd be grateful for any of your suggestions.

---

### Post by PhilWig on 2013-07-15
I’m by no means an lirc guru but I was very puzzled by this when I first used Mythtv.  

A few things to check:

1.  I could never get the T500 remote working unless it was about 10cm away from the receiver, but that was under 9.04 and I suspected a hardware/driver problem.  Remotes are more stable under 12.04.   I’ve since seen comments about the jack plug fouling the holding plate and not being pushed fully home which might have been my issue, but meanwhile I bought another remote and have not used the T500 one again.

2.  In mythtv control centre > infrared check you have the right remote selected.

3.  Follow the software chain:  

3a) First bit:

Exit frontend, start a terminal session and run irw.   Press keys on the remote.  This is what I get on screen if I press 1, 2, 3, up, down, left, right, ok on my MCE remote.
  
> 000000037ff07bfe 00 KEY_1 mceusb
000000037ff07bfe 01 KEY_1 mceusb
000000037ff07bfd 00 KEY_2 mceusb
000000037ff07bfd 01 KEY_2 mceusb
000000037ff07bfc 00 KEY_3 mceusb
000000037ff07bfc 01 KEY_3 mceusb
000000037ff07be1 00 KEY_UP mceusb
000000037ff07be1 01 KEY_UP mceusb
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 01 KEY_DOWN mceusb
000000037ff07bdf 00 KEY_LEFT mceusb
000000037ff07bdf 01 KEY_LEFT mceusb
000000037ff07bde 00 KEY_RIGHT mceusb
000000037ff07bde 01 KEY_RIGHT mceusb
000000037ff07bdd 00 KEY_OK mceusb
000000037ff07bdd 01 KEY_OK mceusb

The columns are I guess are the hex code, 00=press or 01=release, key name and name of remote.  Note the two entries - one for press, one for release.

Let’s say your key down code is not working.  Note the exact text KEY_DOWN and the device (in my case mceusb – yours might be mceusb_hauppauge).  Both case sensitive.   

Quit irw with ^C


3b)  Second bit:
Now look in the file ~/.lirc/mythtv  (I think it’s a link) where you should see loads of entries like this:

> begin
    remote = mceusb
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 3
    delay = 0
end

It says KEY_DOWN (button) from that remote should be passed to prog mythtv by dumping the config character (Down) in mythth’s keyboard buffer.

Check that you have an entry with matching remote and button lines.


3c)  Third step.


What does frontend do with this keyboard buffer input?  Just what it would do if you pressed Down on a real keyboard.  That action is defined in edit keys, but I wouldn’t suggest you alter these at this stage.  To complete the chain:

Mythtv frontend > setup > edit keys

Select the context eg TV playback > channeldown or Global > down.

- Note that these are triggered by ‘Down’.  Down will do other things in other contexts.


Hope you fix it.
Regards
Phil

---

