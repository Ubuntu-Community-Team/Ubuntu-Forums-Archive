---
title: "TV Card won't find any TV channels"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by super breadfish on 2007-04-09
I've got a Tevion XPERT TV7134 TV card in my computer and I'm trying to get it to work with Ubuntu. It's an SAA7134 card, and after looking at a few posts here I've got it to work with the composite port - my Gamecube works just fine with TVtime. 

However, no matter what I do I can't get the TV tuner to work. TVtime doesn't find anything and gives the message "No Signal" all the time. At first I though it must be the aerial, but after getting my TV in and plugging it in the aerial works just fine. I've tried several guides suggested in other posts but they are too complicated and I can't follow them. 

Does anyone know how to fix this, or know of a more noob friendly guide to look at?

---

### Post by josesanders on 2007-04-09
Usually when people have problems with the saa7134 cards, it's a problem of the card not being detected correctly.  What is the result if you run the command:

$ dmesg

If the card type is not being detected at all, you should see some error messages that were logged when your machine booted up.  Sometimes, though, the card appears to be detected, but it still isn't loaded correctly.  In either case, you need to load the driver with the correct card number.  The easiest way to find the right number is to copy this into a new file, called perhaps "script1" or something:

```
#/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=$i
  echo "Actual card is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done
```

Then change the permissions of the file to make it executable, and run it:

$ chmod 755 script1
$ ./script1

It will load the driver for the card with each card number, and then run TVTime so you can see if it worked.  When you close TVTime, it will load the next card number and run TVTime again.  Sometimes when TVTime starts up, it will start up with the composite input rather than the tuner, so make sure you try changing the input.  If you find one that works, go to the command line and type CTRL+C to stop the script.  Then, to get the driver to load correctly each time you start up your computer, edit the file /etc/modprobe.d/options and add the following line:

Option saa7134 card=<card number>

where of course <card number> is the card that worked for you.  I'm sorry if this is confusing and complicated.  Let me know if you get stuck.

---

### Post by NT4usB on 2007-04-09
I spent days cornfingering my AverTV A180, also a saa7134.
iirc, I had to blacklist saa7134 to get saa7134_dvb to load.
Works sweet now. HBO and MAX are having a free week so it's busy grabbing all the shows it can.

---

### Post by super breadfish on 2007-04-10
Mmm, no luck. The script goes through all of the card numbers, but none of them work, not even card 59, which is what my card should be. I get these two errors when running the script though:

ERROR: Removing 'saa7134_alsa': Operation not permitted
ERROR: Module saa7134 is in use by saa7134_alsa

If I edit /etc/modprobe.d/options with different card numbers manually nothing works either. If I reboot between changes it still doesn't work, and dmesg shows the card still isn't detected properly. I also get this error message when /etc/modprobe.d/options is edited with the card number:

WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'Option'

I've seen this when running the script and once at boot. The line in question is:

Option saa7134 card=59

which looks ok to me.

---

### Post by angelman99 on 2007-04-10
Change the line of code from

```
rmmod saa7134_alsa saa7134
```

to

```
rmmod -f saa7134_alsa saa7134
```

This will force it to unload (even if in use).

---

### Post by super breadfish on 2007-04-10
I added the -f but it still does the same thing. I still get the three errors and it doesn't seem to work.

---

### Post by super breadfish on 2007-04-10
I realized that

Option saa7134 card=59

should have been

Option**s** saa7134 card=59

and after correcting that I no longer get the bad line error.

However, I still get my original problem of not getting an channels. I noticed this in dmesg:

[17179588.700000] tuner 1-0060: TEA5767 detected.
[17179588.700000] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[17179588.700000] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179588.708000] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[17179588.708000] tuner 1-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))

Two tuners are mentioned, one of which is NTSC which seems odd for what is supposed to be a UK PAL TV card. Editing  /etc/modprobe.d/options with the tuner= bit as suggested elsewhere doesn't seem to make any difference. Any ideas?

---

### Post by super breadfish on 2007-04-11
Success! I got it to work. After Googling for help for a few hours I found a foreign website about my card ([here's the URL]("http://www.alessandropagano.net/wiki/index.php?n=Linux.SchedeTv")). I couldn't understand the instructions, I think it's Spanish but I'm not sure, but there was one line about my card and card/tuner numbers. 
I didn't expect much but I edited /etc/modprobe.d/options with them anyway as it couldn't really hurt. I ran tvtime-scanner expecting it to find no signal again, but it found some channels! I could now watch BBC1, 2 and ITV with TVtime (reception isn't great where I live and I have a cheap aerial so I don't expect to get 4 or 5). After unmuting the Line-in I also got sound.

So, in case there are any other Ubuntu users out there with a Tevion XPERT TV7134 (it's a clone of the KWorld PVR-TV 713X so that's possibly the same), try using card number 59, and tuner number 56.

---

### Post by dikndaisy on 2007-04-20
Hi Super breadfish

I purchased the same card from Aldi stores awhile back  it worked fine with hoary & warty using modprobe saa7134 card =1 but after upgrades never worked again, cards still stuck in compy & have had no luck using with edgy, tried all suggestions on this post , still no stations found , any chance you could post your /etc/modules.d/options 

got to keep trying.............Cheers

---

### Post by super breadfish on 2007-04-22
Sure, here's the contents of my /etc/modprobe.d/options:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=59 tuner=56
```

Do you dual boot? If so you could try it in Windows and see if it works, that would rule out a problem with the card itself.

---

### Post by dikndaisy on 2007-04-28
Thanks for that, card recognised & loaded, FM tuner works great but still tvtime shows nothing i`ll try a little more tweaking & see how it goes...
No i don`t dual boot with windows
Cheers for your help.

---

### Post by dikndaisy on 2007-05-07
Well, all works great now. Solved by deleting home .tvtime & re-installing tvtime
sudo rmmod saa7134_alsa saa7134
modprobe -v saa7134 card=5
tvtime-scanner input=0
tvtime --frequencies=custom

Strange as card 5 is a SKNet monsterTV  & mine is a Tevion xpert tv7134, well, thats what it says on the box, seems like these 7134 cards can be quite hard to configure.
Maybe this could help anyone else with one of these cards...

---

### Post by lefthand on 2007-07-30
That setup worked for my "Kworld PlusTV analog lite PCI" I tried using the oft mentioned script to iterate through the cards, but that never worked.  I was about an hour away from taking the card back for a more expensive one too!

---

