---
title: "changing channels on D12-100 using MCE IR Blaster"
date: 2009-05-12
forum: Mythbuntu
---

### Post by heartburnkid on 2009-05-12
Need a little help setting up my Mythbuntu box...

I'm trying to use Mythbuntu with a DirecTV D12-100 box, and not having much success.  I'm using an IR blaster hooked to a Media Center remote receiver.  I've activated the IR blaster in Mythbuntu control center, and am attempting to use the Perl script from [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer) to change the channel; however, nothing happens when I attempt to change the channel.

Here's the relevant section of mythbackend.log:

```
2009-05-12 18:15:08.628 TVRec(1): HW Tuner: 1->1
2009-05-12 18:15:10.400 ret_pid(0) child(4762) status(0x0)
2009-05-12 18:15:11.403 ret_pid(0) child(4762) status(0x0)
irsend: command failed: SEND_ONCE directtv ENTER
irsend: unknown command: "ENTER"
2009-05-12 18:15:12.405 ret_pid(4762) child(4762) status(0x0)
2009-05-12 18:15:12.410 External Tuning program exited with no error
```

From what I can tell from this, this means that it's failing to send the ENTER command, but the other buttons should be going through fine.  Yet, I don't even see them show up.  I have the IR blaster stuck directly on the sat box, right over the remote sensor, so I'm confident that's not the issue.

Do I need a different configuration file for this model of sat box?  If so, where can I get it?  If not, then what should I do?  I've read that I can hook up a USB->Serial adapter to the box, and control it via serial port, and that is definitely an option; however, I'd prefer to control it with the hardware I already have, if at all possible.

---

### Post by phroman on 2009-05-13
Hi, one thing to check is the config file for your STB receiver, which is probably /usr/share/lirc/transmitters/directtv/general.conf.  In the channel change script ENTER is capitalized, but in the receiver config file it's probably not. that will result in an error as the case must match.  You'll probably have to use it in the script in lower case.

---

### Post by heartburnkid on 2009-05-13
OK, the error message has disappeared from mythbackend.log, but the channel still isn't changing.  Anything else I can try?

---

### Post by heartburnkid on 2009-05-16
The plot thickens... the IR blaster doesn't seem to be blasting at all.  I've tried 2 different blasters, and neither one of them seems to show up on my cell phone camera (which does pick up IR; I tested it on the remote).

---

### Post by phroman on 2009-05-17
Can you post your /etc/lirc/hardware.conf  and  /etc/lirc/lircd.conf files?

---

