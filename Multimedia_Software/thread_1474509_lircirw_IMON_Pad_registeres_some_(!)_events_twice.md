---
title: "lirc/irw: IMON Pad registeres some (!) events twice"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Markus72 on 2010-05-06
Hi,

I use Mythbuntu 9.10 with an IMON PAD IR/VFD.
Everything is fine except that two buttons (MyDVD and menu) fire their event twice.

In that case, I'm not talking about a normal repetition in case of a long button press but they fire their initial events twice.

Here is what irw shows:
0000000029a3d5b7 00 MyDVD iMON-PAD
0000000029a3d5b7 00 MyDVD iMON-PAD
000000002ba385b7 00 Menu iMON-PAD
000000002ba385b7 00 Menu iMON-PAD

I pressed the buttons only once each - and not long enough for a repetition.

For all other buttons it's fine.

Any idea what could be the reason and how to cope with it?

As far as I understand, using the .lirrc file to cope with repetitions is no valid approach (at least it didn't work for me) because the events are all numbered with "00", and not with "00", "01",... - so .lircrc is out of this, right?

Any idea why only these two buttons are nuts or how to investigate? I've no clue.

Thanks in advance
Markus :-)

---

### Post by Markus72 on 2010-05-06
found some other threads with no solution: [http://ubuntuforums.org/showthread.php?t=650762](http://ubuntuforums.org/showthread.php?t=650762) and [http://ubuntuforums.org/showthread.php?p=9247463#post9247463](http://ubuntuforums.org/showthread.php?p=9247463#post9247463)

---

### Post by Markus72 on 2010-05-07
noone? help! please! :-)

---

### Post by Markus72 on 2010-05-09
I found the reason and thus the solution: within the 32bit IMON-PAD definition within the lircd.conf file the buttons "MyDVD" and "menu" are named twice - one time in the standard section, another time within the "different code" section.

By chance I found out that there is a 64bit configuration for the IMON-PAD within the same file, too...
And there, the button codes in the "different code" section are declared inactive because they are the button-release codes.

So - the normal section describes the button press codes and - at least for the two named buttons - the "different code" section names the button-release codes.

Since a button press is always followed by button release, there are two events fired for each button press.

Simple solution: deactivate the release codes within the 32bit section as well.

Done. :-)

---

