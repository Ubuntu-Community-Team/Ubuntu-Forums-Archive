---
title: "IR Blaster FIOS Box"
date: 2009-09-26
forum: Mythbuntu
---

### Post by johnelle on 2009-09-26
Conversion from Analog cable to FIOS ruined my nice little myth box.  I bought a IR Blaster.Info serial unit and I am about to attempt to use it to control the small FIOS cable box (not the main one).  Anybody have any short cuts for this?  I was just going to choose a random serial IR Baster (Motorola) then beat it into submission. 

Has anybody gone through this process so that you can save me some missteps?  

I am running 8.04 but I can upgrade (not looking forward to it but I could if it makes this easier).

John

---

### Post by johnelle on 2009-10-18
Ok...time to answer my own question so that others don't have to spend as much time as I did on this.

I set-up a Mythbuntu box connected to the DCT700 that Verizon FIOS supplies for the TVs not using their bigger set-top unit.  I am using a serial irblaster.info transmitter.

[LIST=1]
[*]Use Mythbuntu setup to install Transmitter IR Serial Motorola as a base for the LIRC and reboot.
[*]Do not use the existing DCT2000 config because it has the infamous "zero problem."  Instead replace the **/etc/lirc/lircd.conf **with [this one]("http://www.mythtv.org/pipermail/mythtv-users/2008-June/224658.html").
[*]Use the contrib change-channel-lirc.sh but with the [following tweaks ]("http://www.mythtv.org/pipermail/mythtv-users/2008-June/224659.html") to get around the problem of the DCT sometimes missing the first digit. I just added a send "ok" to the top of the digit loop and that seems to work.
[/LIST]

I would also recommend that you edit your FIOS lineup on schedule direct before starting.  The complete channel list is huge and really slows down things like Mythweb if you don't trim it back.  Its fairly difficult to get things corrected later--much easier to do it before you start.

---

