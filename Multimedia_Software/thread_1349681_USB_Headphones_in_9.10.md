---
title: "USB Headphones in 9.10?"
date: 2009-12-08
forum: Multimedia Software
---

### Post by rapha on 2009-12-08
Hi,

first off, I'm hoping this is the right forum to ask this question ... my problem is that my USB Headphones which worked just fine under Ubuntu 9.04 stopped working with 9.10. When I plug them in and open the sound properties, I can choose them for *input* but not for *output*. What can be done to fix this?

Regards,
Raphael

---

### Post by rapha on 2009-12-08
> **rodrick said:**
> Don't know about this. :---)

Interesting ... a long nose is normally a sign for somebody lying :D ... but thanks for replying anyway! That's far less frustrating than no reply at all...

... if it helps for anybody to answer, I'm suspecting some change in PulseAudio between 9.04 and 9.10 to be the culprit here. Apparently there were a lot of changes. Interestingly, my BlueTooth headset works much better now - but its batteries just ran dry :-/

---

### Post by rapha on 2009-12-08
The friendly guys in #ubuntu-de hinted me towards looking for the headset's USB id, which is "0d8c:0006" (names itself "C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset", sold as "Speed-Link Medusa 5.1 USB"). If there is additional diagnostics that could help troubleshoot this problem I'll gladly provide it! :-?

---

### Post by rapha on 2009-12-08
Just in case anybody else stumbles over this at some point: a simple reboot solved the problem. Thanks.

---

### Post by Ernak on 2010-02-24
hello

i have the same problem
i have speedlink medusa 5.1 usb headset
my input is already work but i still have problem with output

do you know any solutions?
because the reboot did not work for me

-----------------------------------------------

i almost solve my problem
i installed the package called: pulseaudio-dbg
but its not 100% yet
now my problem is that the system thinks that this is a 7.1 sound headset but its 5.1

---

### Post by xenopat on 2010-11-19
I just got a pair of the same headphones, which worked just fine until I unplugged/replugged them, when the Output disappeared... am totally hopeless when it comes to anything technical, could you please walk me through how to install pulseaudio-dbg?

---

### Post by john1982 on 2010-11-20
Sadly, 10.10 hasn't solved the problem for me, but I've since discovered that when you disable PulseAudio autorespawning and then start it manually in a terminal like "pulseaudio -vvvv", the headphone's output sink is present and works. The quadruple "verbose" argument seems to be necessary, too, so it is a little spooky. Still a good workaround though until the problem gets fixed.

---

