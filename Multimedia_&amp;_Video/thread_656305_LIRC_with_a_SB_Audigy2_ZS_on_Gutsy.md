---
title: "LIRC with a SB Audigy2 ZS on Gutsy"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by tbranham on 2008-01-02
Hey cats & kittens,

OK, so I'm trying to get the remote (RM-1500) working on my SB Audigy2 ZS with LIRC. I've done some extensive searching online, and come up with essentially zilch. Not that there aren't any topics available online -- it's just that the pages I've found all seem to have incomplete/inaccurate information. 

I remember trying to get this same remote running on a gentoo box I had a few years back. I had to add some module options to get the IR receiver to be turned on by default. Here's the line in /etc/modules.d/alsa-base :
```

options snd_emu10k1 index=0 extin=0x3fcf extout=0x1fcf enable_ir=1
```

So, I've installed lirc from the repos, and I used 'mythbuntu-lircrc-generator' to make my .lircd file. All looks fine there. Strangely enough, I get no response from 'irw' when I try to run it the first time, and errors if I try again:
```

tbranham@gemini:~$ irw
tbranham@gemini:~$ irw
connect: Connection refused
tbranham@gemini:~$ 
```

I tried the above after a reboot as well, just to be sure. No dice.

Anyway, 'dmesg' comes up with nothing; in fact, the only thing I can find at all is in /var/log/syslog :
```

syslog:Jan  2 11:55:00 gemini lircd-0.8.2[6762]: initializing '/dev/usb/hiddev0'
syslog:Jan  2 11:55:00 gemini lircd-0.8.2[6762]: unable to open '/dev/usb/hiddev0'
```

Oh, before you ask: the battery is good :)

So, does anybody have an Audigy2 ZS running with the remote in Gutsy?

Thanks for the assistance, and Happy New Year.

---

### Post by tbranham on 2008-01-03
Some more info:

I thought udev might be part of the problem...
```
tbranham@gemini:~$ cat /etc/udev/rules.d/85-lirc.rules | grep -v '#'
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"

```

Interesting that I do not have a device in dev. I do, however, have a /dev/lircd...

Again, any info you've got is helpful.

Merci Beaucups.

---

### Post by tbranham on 2008-01-04
OK, last update before I give up...

After some more digging, I found this:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/123557](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/123557)

I remembered that I still needed to enable the IR Receiver by sending a string to /dev/snd/midiC0D1. I've got that taken care of, but, as the above thread reports, still no luck.

Anyway, after still more searching, I'm beginning to think that it would be worth my time to get another remote. Oh well.

As always, thanks for whatever assistance you can provide.

---

### Post by Skybinary on 2008-01-06
OMG:O, OMG, Ubuntu is absoflogginlootly brilliant.

well sort of.

I installed the gutsy live cd last weekend, and the problems i developed, ie :sound(volume is set to mute on new install) doh!, and gfx by downloading the correct driver i was so happy.

Unreal torny, TvTime Bt card WOOHOO!, DVD player played my Die Hard 4.0 after some minor updates. Even all my other Hard drives showed up on the desktop so i could play my media etc..

I am currently dual booting with XP.

I am v-new to linux, v-v-v-new, thought i would give it a wurl. lol.  Even told my boss i would sack $MS WIndros all together.

I have everything on this linux box now i had on XP, except my IR. <dramatic music 'dum dum duuuuuuhhhh'>.

So this weekend i have spent omg like forever bashing in this line, bashing in that line, rebooting but no joy, i am so thouroughly dissapointed with myself and the foolsome idea that linux could handle an old serial IR receiver. dang!

The 1 and only reason i want to use a remote control with this box is just to mute, mute the audio, nufin else.  So now come bedtime i have to reboot into Xp so i can lie in bed and watch tv and use my sky remote to mute the box so i can sleep.

Maybe i am not worthy to be a linux user, i should call it a day and go back to uncle bills os.

---

### Post by tbranham on 2008-01-07
Hi Skybinary,

Welcome to Linux! I've gotta' say, if the remote control issue is your only trouble with Linux, you're in some seriously good shape :)

Seriously, you should ask around a bit in the forums for the make/model of your serial IR receiver. You never know -- someone might have gotten it to work.

As for me, I'm not too worried about the remote control. I'm buying a wireless keyboard next week (the left arrow key on this one stopped working, so now I have an excuse...) which will take care of my limited need. Actually, if all you're using the remote for is mute/unmute, you might just save yourself the hassle and get a wired volume control for your speakers. Just a thought.

Good luck.

---

### Post by Skybinary on 2008-01-08
tbranham,

Thank you for your warm welcome;)

I hope my wander thru linix/ubuntu has been more than just luck.  It is a blessing the support existing.

About the wired option, I have been thinking for sometime having smaller speakers at the head of the bed anyway, that would help reduse my noise polution also, because the volume would only have to travel inches rather than feet.

I havent given up, yet, i asume it is possible. girder did it for me with an igor plug. SFH-56, input signal DSR on COM1.
Girder showed a receiver schematic - IR detector, TSOP17xx, SFH506-xx.
It was a serial gizmo with a sensor i acquired for 5gbp years ago and was never easy to get going on my other OS.

Because the first time i hadnt a clue what i was doing. The 2nd time was no different, lol, but i had to move forward. i thought i had nothing to lose trying again, but when the $irw would do nothing i found a wiki article stating to follow their steps to the letter and at one point i had $irw waiting. woot!

I couldnt go much further, it was late and a reboot or two later kept displaying a startup text 3x with lirc amongst the output and later i came to realise, its not so easy to walk away, as in RL for a day and walk right back in.

When i returned a problem arose where i somehow lost my gfx setup, something i was convinced i `sudo'd` into some startup file.

I think i removed it all now, ready for another weekend, i removed mythbunto contols too, i thought i installed it so it would be easier to get my ir rolling but the only noticible affect it spawned was a splash login.

Using girder i could press a button on the rc and choose to mute as i stated but i also used another button to power off the monitor.  Not a wired option i could consider tbranham ;).

I feel optimistic i can do it with ubuntu, not confident at all, but the experience so far has been enlightening, I am not sure i have enough space up there for anymore data :$. or to put it another way `my head hurts`.

---

