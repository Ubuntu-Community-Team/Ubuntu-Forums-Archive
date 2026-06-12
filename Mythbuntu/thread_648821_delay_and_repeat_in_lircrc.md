---
title: "delay and repeat in lircrc ?"
date: 2007-12-24
forum: Mythbuntu
---

### Post by erland on 2007-12-24
I just installed Mythbuntu and after some configuration my Harmony universal remote currently works towards the LIRC configured as iMon PAD,  but I'm not completely satisfied how it behaves.

The arrow keys sometimes generates multiple events, so when I press down in mythfrontend it sometimes steps down several steps. I thought the delay/repeat parameters in .lircrc where supposed to solve this, but they doesn't seem to have any effect at all. I've restarted mythfrontend after editing the .lircrc file.

Is there something else that also needs to be restarted ?

Do I need to do anything special to get the delay/repeat parameters in .lircrc to work in Mythbuntu ?

---

### Post by p$y on 2007-12-24
try to edit the ~./mythtv/lircrc file, this is the one which works for me.
see my other thread, too: 

[http://ubuntuforums.org/showthread.php?p=4002817#post4002817](http://ubuntuforums.org/showthread.php?p=4002817#post4002817)

---

### Post by erland on 2007-12-26
The problem seems to be in lirc and the handling of the iMON protocol. I'm using a Logitech Harmony remote and it seems like the iMON PAD profile for it sends arrow key IR event that isn't compatible with lirc.

The result is that the lirc events produced are single keypresses instead of repeats.

When running irw and hold down an arrow key I get:
```

000000006aca81b7 00 Left iMON-PAD
000000006aca81b7 00 Left iMON-PAD
000000006aca81b7 00 Left iMON-PAD
000000006aca81b7 00 Left iMON-PAD

```

But for the repeat/delay functions to work I need to get:
```

000000006aca81b7 00 Left iMON-PAD
000000006aca81b7 01 Left iMON-PAD
000000006aca81b7 02 Left iMON-PAD
000000006aca81b7 03 Left iMON-PAD

```

When I run mode2 to see the ir codes produced a fast single click on the left arrow produces 4 32-bit numbers. I've put the first one in the lircd.conf conf file. I guess it might work if I was able to enter a 128-bit number instead, but as far as I've seen all the remote codes in the lircd.conf file needs to be the same length.

---

### Post by rich86 on 2007-12-27
Hi, i am having a similar problem with my remote, when i press a button it sends out two identical pulses but both are being read. For example if i press play/pause it pauses and mediating plays again or channel change changes two channels at a time.

Have you found a solution or a work around for this problem?

Richard

btw The thread i posted is [HERE]("http://ubuntuforums.org/showthread.php?t=650762")

---

### Post by erland on 2007-12-31
> **rich86 said:**
> 
Have you found a solution or a work around for this problem?

Since I have a Harmony universal remote, I just programmed the arrow keys on the remote to use different IR commands.

---

### Post by babel2 on 2008-04-07
Hi
I have the same problem, I just cant make it count from 00 to 02, I really need some help with this. I hope you have some ideas and may help me.

This is what irw tells me:
[http://paste.ubuntu.com/6556/](http://paste.ubuntu.com/6556/)

my lirc.conf:
[http://paste.ubuntu.com/6557/](http://paste.ubuntu.com/6557/)

Im using mythbuntu 8.04 beta
If there is anything else you need to know, please tell me

---

### Post by Markus72 on 2010-05-06
no solution so far?

---

### Post by Markus72 on 2010-05-09
Hi - I found the reason and the solution at least for my IMON-PAD remote... have a look into this thread - maybe it solves your problem, too: [http://ubuntuforums.org/showthread.php?t=1474509](http://ubuntuforums.org/showthread.php?t=1474509)

---

