---
title: "Backend Setup can no longer see Nova T 500 card"
date: 2009-10-19
forum: Mythbuntu
---

### Post by fatmonk on 2009-10-19
I went to retune my system after the mux changes here in the UK a few weeks ago and found problems setting my system to do a channel scan - I was getting messages that the card couldn't be opened.

I've now deleted the capture card etc and am trying to re-add but am having the same problem.

Nothing has changed hardware wise, but I have allowed the system to do its latest updates (the problem is the same as before the updates though).

When I go into backend setup and try to add the cards I get the following in the console (how to I copy text from the console - typing is a pain!):

```

Couldn't get handle
eno: No such file or directory (2)
GetSTBListPrivate -- begin
GetSTBListPrivate -- got lock
GetSTBListPrivate -- end
Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
DiSEqCDevTree, Warning: No device tree for cardid 0

```

I've not typed the dates and times to save typing. If I select the other tuner on the card I get the last few lines repeated for adapter1.

The card appears to initialise OK according to dmesg:

```

[   11.633694] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   11.633909] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.315339] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.896118] dvb-usb: schedule remote query interval to 150 msecs.
[   12.896121] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   12.896352] usbcore: registered new interface driver dvb_usb_dib0700

```

And the dev entries appear to be there every time I reboot, not sure about the permissions though:

```

:/dev/dvb# ls -l
total 0
drwxr-xr-x 2 root root 120 2009-10-18 17:01 adapter0
drwxr-xr-x 2 root root 120 2009-10-18 17:01 adapter1

```

```
:/dev/dvb/adapter0# ls -l
total 0
crw-rw---- 1 root video 212, 4 2009-10-18 17:01 demux0
crw-rw---- 1 root video 212, 5 2009-10-18 17:01 dvr0
crw-rw---- 1 root video 212, 3 2009-10-18 17:01 frontend0
crw-rw---- 1 root video 212, 7 2009-10-18 17:01 net0

```

Any ideas?

Cheers

FM

---

### Post by GuiGuy on 2009-10-19
> 
When I go into backend setup and try to add the cards I get the following in the console (how to I copy text from the console - typing is a pain!):

AFAIK you can copy and paste in most consoles. You should also be able to select text with the mouse and RIGHT CLICK > COPY and RIGHT CLICK > PASTE

Hot keys are usually CTRL+SHIFT+C (copy) and CTRL+SHIFT+V (paste). Works for me, anyways. 

Regarding the NOVA-T-500, I don't know if I can be of much help. However, mine plays up from time to time. When it happens a power down and cold restart always brings the card back up. There is currently some discussion about the card in the [mythtv-users@mythtv.org]("http://mythtv.org/cgi-bin/mailman/listinfo/mythtv-users") list. I had an issue yesterday when the LNA wouldn't activate. Again, a power down and cold start fixed things.

---

### Post by fatmonk on 2009-10-20
Thanks for the response, I'll give that a go re the copy from the console window.

Regarding the card, I've seen the issue with the card hardware not being recognised before where a hard (power down) reboot solves the problem, but in this instance the OS seems to be recognising the card no problem (see the dmesg extract above) and creating the stream links in the the dev tree.

It seems that it may only be Myth that isn't finding the card... is there any other easy way to test the card from the OS point of view to try to narrow this down?

Cheers,

FM

---

### Post by AJ1000 on 2009-10-20
When you run mythtv-setup, are you using the card type: 'DVB DTV capture card (v3.x)' ?

Another thing you could try is [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)

---

### Post by fatmonk on 2009-10-20
I am using 'DVB DTV capture card (v3.x)', yes.

That's different to when I initially set the system up, and actually makes more sense as a selection (I don't remember what it used to be when I first installed the system).

I'l try the xine test tomorrow evening hopefully - a bit late to start playing now.

Ta,

FM

---

### Post by AJ1000 on 2009-10-21
A solution I saw on another site is to 'change the PCI slot that the card is in'. Try that as well.

---

### Post by SiHa on 2009-10-21
> A solution I saw on another site is to 'change the PCI slot that the card is in'. Try that as well.
...and make sure it's the only card in a PCI slot, if possible. I had issues with my first setup, where one of my tuner cards (one of which is the Nova-T 500, but I can't remember if it was that one), would only detect properly if it was the only one plugged in.

---

### Post by fatmonk on 2009-10-21
I don't think this is a hardware issue...

The OS seems to be seeing the card ok still, and the box has been running with this card (and no other hardware changes) for a year now.

This must surely be a software issue...

-FM

---

### Post by jayg1169 on 2009-10-22
please post the output of

```
ls -l /dev/dvb
```

---

### Post by jayg1169 on 2009-10-22
Sorry i see youve already posted these!

try changing the group permissions in /dev/dvb and all included files to mythtv

---

### Post by fatmonk on 2009-10-23
That's the problem jayg!

Changed both adapters and everything below to the mythtv user and group and Myth can now see the tuners again.

Ta for that.

Next question is why udev (it is udev that creates the devices isn't it?) is creating them with the wrong ownership when the box boots...

-FM

---

### Post by jayg1169 on 2009-10-24
does this happen after every reboot?

i only had this problem with initial set up. once i changed the group permissions it was fine.

---

### Post by fatmonk on 2009-10-24
It seems to be after every reboot now.

As I mentioned, the box has been working for months now and has only just started doing this.

After a reboot the tuner devices are as follows:

```

:/dev/dvb$ ls -l
total 0
drwxr-xr-x 2 root root 120 2009-10-25 00:33 adapter0
drwxr-xr-x 2 root root 120 2009-10-25 00:33 adapter1
mythbox:/dev/dvb$ cd adapter0
mythbox:/dev/dvb/adapter0$ ls -l
total 0
crw-rw---- 1 root video 212, 4 2009-10-25 00:33 demux0
crw-rw---- 1 root video 212, 5 2009-10-25 00:33 dvr0
crw-rw---- 1 root video 212, 3 2009-10-25 00:33 frontend0
crw-rw---- 1 root video 212, 7 2009-10-25 00:33 net0
mythbox:/dev/dvb/adapter0$ 

```

Cheers,

FM

---

### Post by jayg1169 on 2009-10-25
Im sorry Fatmonk but this is beyond my knowledge!

Ive just checked my permissions in /dev/dvb after a reboot and there the same as yours but ive got no problems!

lets hope me bumping this will help you find someone who does know.

there is also alot of other posts lately about the nova-t 500 maybe one of those could help.

sorry again Fatmonk:(

---

### Post by fatmonk on 2009-10-26
Thans jayg - here's hoping someone else can help out now then.

Unfortunately after I reboot and the device ownership resets to root:video the Myth backend setup can no longer see the card properly.

If I change the ownership to mythtv:mthtv then backend setup can see it again.

Is this something to do with udev? Is this something that's easily configurable or have my users and groups maybe got messed up somewhere along the line?

As I've mentioned, the box was working fine and the only thing that could possibly have affected this are the standard repo updates.

Hmmm...

Cheers,

F(rustrated)M

---

### Post by fatmonk on 2009-10-27
Think I've solved this... with a bit of help from [this page]("https://help.ubuntu.com/community/NovaTHowTo").

The rules file location has actually changed from what's described in the link above and there are now multiple rules files located in:

```
/etc/udev/rules.d/
``` rather than there being a single file called udev.rules, however grepping for 'video' ```
grep video *
``` in the rules.d directory and looking for a likely candidate (the dvb entry) led me to the right file to edit.

That file was named 40-???something or other.

Changing the group for the dvb device to 'mythtv' from 'video' and rebooting saw the devices created with the right permissions for the Myth backend to access the tuner cards properly.

-FM

---

