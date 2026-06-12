---
title: "IR Blaster Problem"
date: 2010-09-13
forum: Mythbuntu
---

### Post by dtaylorl on 2010-09-13
I'm having a problem where sometimes my IR Blaster is not sending the channel to my STB box correctly, thus causing my Myth box to record the wrong channel. Usually only one or two button presses are dropped (e.g. it records channel 3 when I wanted 83). I'm really not sure how to go about testing whether the problem is with:
a) A configuration issue with MythTV or lirc.
b) The IR Blaster (An mceusb receiver/transmitter).
c) The IR cable that plugs into the blaster and stick onto the STB.
or
d) The STB which may not be receiving the signals as it is supposed to (Motorola DCT 700).

Any help which could lead me in the right direction is appreciated. My MythTV box isn't much good if it always records the wrong channel.

---

### Post by LocoJeeper on 2010-09-14
The first step I would double check ... 

Make sure the script that MythTV is using to send the channels (check in the MythTV Backend settings for the given tuner) is using a "sleep " and then a number (probably 5 - 10) to allow a minimal delay between signals.  

Then on to other steps... but that is the easiest to check.

- Ben

---

### Post by dtaylorl on 2010-09-14
Yup, its using a sleep.  I have played with the sleep length quite a bit with little or no effect.  Its also inconsistent which button gets dropped - sometimes nothing is received by the STB, sometimes only the first number, sometimes only the second, etc.  I should mention that I also get the same problem if I run irsend from the terminal.  I really doubt that its an lirc/MythTV problem but I'm not sure how to go about testing the other things.

---

### Post by LowSky on 2010-09-14
well if its sending the wrong channel, make sure the blaster is corretly atteached to the set top box and that its fully connecting to the PC, im betting that its losing the feed somewhere. if its contantly failing, maybe the unit is bad.

You can always try channel changing and recording with Firewire if your set top box has those ports.

---

### Post by klc5555 on 2010-09-15
Are you running any other USB peripherals simultaneously to your transmits?

I've had this problem (dropped channel changes or individual digits) with the IguanaIR USB blaster (on a Pace DC50X DTA). In this case it turned out that the USB bus itself seems to be the problem. My box also uses a USB mini-firefly remote (and a USB keyboard) and I discovered that if something else was going on over USB at the time the channel-change script was running, LIRC's signals to the blaster seem to get swallowed up and never make it to the blaster to be transmitted. Sometimes it also crashes LIRC, which daemon has to be killed and restarted. Sometimes not.

I also found this was frequently an issue if the machine was doing some sort of high-load activity, like watching Hulu desktop, at the time when the backend decided to fire up a tuner card and run the channel-change script. Possibly a matter of thread priority. Also tended to crash LIRC.

---

### Post by azmyth on 2010-09-15
I had the same issue on a SA STB. About 2 in 10 would miss the change. Someone told me to add an irsend command that sends the "exit" command and then another line with a sleep of 0.5 sec to the STB right before the loop that sends out each digit one at a time in your change channel script. I haven't had a miss since I've done this. :D

---

