---
title: "Sabrent TV Tuner SAA7134/7130"
date: 2009-10-04
forum: Multimedia Software
---

### Post by NaOH on 2009-10-04
Hello,

I wanted to offer a little help to anyone who purchased or considering purchasing one of the $20 Sabrent TV-PCIRC TV tuners.  I bought this yesterday, from TigerDirect, came in a black box, board was black as well, and I mention that because it seems like they change chipsets on these cards daily.  Like many of the cards in this price range it falls under SAA7134 territory, and this one was not so kind as to identify itself so a card/tuner assignment could happen automatically.

Before I explain my resolution any further I should mention I'm working with Kubuntu 9.04 (Mint 7 KDE), and I used tvtime for trial and error.

Another important point to mention:  Searching the forums and elsewhere on line you'll find many posts saying "use this card# use this tuner#."  **Take it with a big grain of salt!**  As I said these cards have a variety of differences going on from model to model.  What set me on the right path was this:

[http://www.hartzenberg.net/wordpress/2009/01/02/chronos-tv-card-in-ubuntu/](http://www.hartzenberg.net/wordpress/2009/01/02/chronos-tv-card-in-ubuntu/)

What will be the most troubling part of finding the right tuner/card combination is finding out how to try these combinations without restarting/logging out, the link above explains:

"So unload everything again:

    sudo modprobe -vr saa7134_dvb
    sudo modprobe -vr saa7134_alsa
    sudo modprobe -vr saa7134

and then load up with the card and the tuner options set:

    sudo modprobe -v saa7134 card=42 tuner=38  "

In my case I had to kill kmix to avoid the driver in use errors.  That's about it.  Being able to quickly load, test, unload, repeat was key to getting the right combination for me.

What threw me for a loop was that the initial combination I used, card=42/tuner=43 would show my cable tv on the Composite channel, and No Source bluescreen on the Television channel.  This combination seemed logical for this card as Card=42 was the only Sabrent device listed, and 43 was NTSC Phillips, which seemed to match the specs of this card.  Not so much.  As it turns out Card=10/Tuner=43 is what worked best for this particular card, and despite this being a Sabrent card, Card=10 is actually referenced as a Kworld/KuroutoShikou SAA7130-TVPCI.

After finding the combination I had to make an Options.conf file under /etc/modprobe.d containing:

options saa7134 card=10 tuner=43 alsa=1

Hopefully this can help someone else out.  All in all its a decent card, nothing spectacular, but for 20 bucks I can't complain.  Again, whatever generic card you may end up with, try as an many combinations of card and tuner before you throw in the towel.

Good luck!

---

### Post by dealcorn on 2010-03-12
This is a wonderful post, but what is the procedure to unload modules saa7134_alsa and saa_7134?  I do not have kmix installed but the modprobe -vr commands do not work as the modules are in use.  Maybe I am asking how to identify how the modules came to be in use.

---

### Post by Herdocia on 2010-09-09
Thanks
I have the same issue, in TWIL, gave me this link, and my tv card is up and running 
Than You So Muuuuchh!!!!!!!!!
\\:D/

---

### Post by meaje on 2012-06-09
> **dealcorn said:**
> This is a wonderful post, but what is the procedure to unload modules saa7134_alsa and saa_7134?  I do not have kmix installed but the modprobe -vr commands do not work as the modules are in use.  Maybe I am asking how to identify how the modules came to be in use.

try:
# lsmod |grep saa

Then add the modules that are still using the saa7134 module to the modprobe -vr saa7134_alsa saa7134 command such as:

# modprobe -vr saa7134_alsa saa7134_dvb saa7134_empress saa6752hs saa7134

I know this has been a dead post but hopefully it will help someone else, it threw me for a few minutes while I stumbled trying to figure out what was locking the module in memory.

---

