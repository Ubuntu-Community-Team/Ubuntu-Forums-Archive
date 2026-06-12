---
title: "TV Tuner won't work"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by zhinker on 2007-04-21
Thanks for this beginner forum, hopefully I'll find more responses here.

I'm trying to get my TV tuner to work.  It's an AverMedia's UltraTV 1500 MCE card and I'm trying to run it on Ubuntu 6.10  I already tried running TVTime and Zapping, but when I tried to use TVTime it would just open up for a split second and then close again. And when I tried Zapping I would get an error saying:
[INDENT]Couldn't open /dev/video0, try other devices?[/INDENT]
and when I said yes I'd see the error
[INDENT]Sorry, but "/dev/video0" could not be opened:
    The device cannot be attached to any controller[/INDENT]

Any ideas on how to fix that?

---

### Post by tgm4883 on 2007-04-21
did you install ivtv?

---

### Post by zhinker on 2007-04-21
I don't see it in the Add/Remove Applications window

---

### Post by bapoumba on 2007-04-22
@ zhinker: movedyour thread to "Multimedia & Video"

---

### Post by zhinker on 2007-04-22
Sorry, I just started using linux a couple days ago.  How do I install ivtv?  I didn't see it in add/remove applications

---

### Post by zhinker on 2007-04-22
This might help a bit.  Whenever I try opening Zapping TV Viewer I get the following two erros:
[INDENT]Couldn't open /dev/video0, try other devices? (Y/N)[/INDENT]
and
[INDENT]Sorry, but "/dev/video0" could not be opened:
The device cannot be attached to any controller[/INDENT]
I guess the problem is to get linux to detect my TV tuner card.  Any ideas how to set that up?

---

### Post by sbelial on 2007-04-22
I'm also having this same problem! It looks like there is no dev/dvb directory so hence the error. I have a Hauppauge Nova-T DVB-T PCI card which worked fine before my upgrade to 7.04 :(

Output here:

root@sootica:/home/marcus/Desktop# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

---

### Post by zhinker on 2007-04-22
That sucks, do you remember how you got it to work in Edgy?

---

### Post by sbelial on 2007-04-22
I followed this excellent guide for edgy: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

It worked like a charm, no problems at all. This problem seems to be that although the card is fully detected the node thing isn't being created.

That's specifically the guide for MythTV but I believe the part where the TV tuner is set up will be the same for any application, such as Kaffeine which also used to work.

---

### Post by sbelial on 2007-04-22
I've now just tried installing the ivtv application/driver as suggested earlier in this thread but still no luck. The annoying thing is that Ubuntu does detect the hardware as it is correctly listed in the hardware information application on the system menu. Perhaps I should go out and buy vista :lolflag:

---

### Post by zhinker on 2007-04-22
I'm in the exact same boat, I see the card in the device manager but still nothing.  Right now this is the only reason I need to keep windows dualbooted on my pc, and it is a REAL pain to reboot to windows just to watch TV

---

### Post by sbelial on 2007-04-22
Yeah, seems to be a common problem. I have a little experience with Linux so I'm going to try and work on a solution and see if I can come up with anything. From reading around it looks like this is a common problem with the new version so someone must know how to fix it.

---

### Post by zhinker on 2007-04-22
Hey, how'd you install ivtv?

By the way, I was looking at the device manager and I found it has a few string values that seem to be system paths.  The value for all of them was '/sys/devices/pci0000:00/0000:00:1e.0/0000:03:02.0'  I'm thinking if we change that to '/dev/video0' it might work...it's worth a shot, after all, it's not like we can mess it up or something (I hope)

---

### Post by zhinker on 2007-04-22
Here's a screen shot below of everything shown in the device manager

---

### Post by zhinker on 2007-04-22
never mind, the manager won't let me change the values

---

### Post by fenian on 2007-04-22
One of your problems is that you are trying to use TVTime with a hardware encoding card.TVTime only works with software encoding cards.In order to see if your card is working with the ivtv driver the easiest way  is with MPlayer.Install Mplayer with...

> sudo apt-get install mplayer

after it installs open MPlayer from the terminal with the command...
> 
mplayer /dev/video0

this may produce only static which is ok to change the tuner to a different channel (one with a signal) in a seperate terminal run the command...
> 
ivtv-tune -c # -d /dev/video0

replacing # with the channel number you want.

---

### Post by fenian on 2007-04-22
I'm sorry to tell you that your tuner card follows the 'Blackbird reference design' and unfortunately won't work with ivtv and thus won't work in linux.More info can be found [here]("http://www.ivtvdriver.org/index.php/Supported_hardware")

---

### Post by zhinker on 2007-04-22
> **fenian said:**
> I'm sorry to tell you that your tuner card follows the 'Blackbird reference design' and unfortunately won't work with ivtv and thus won't work in linux.More info can be found [here]("http://www.ivtvdriver.org/index.php/Supported_hardware")

[SIZE="7"]NOOOOOOOOO!!![/SIZE]

Any chance there will be some support offered in the (hopefully near) future?

---

### Post by sbelial on 2007-04-22
Now my card used to work, Hauppage Nota-T PCI Model 909. This seems quite a popular card amongst Linux users and was working very well with Edgy. 

So, what I am doing wrong? I've installed everything (and more) that I needed before but MythTV doesn't recognise the card as being a DVB card and when I run the tzap scan command I get this error:

[COLOR="DarkSlateGray"]scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory[/COLOR]

Any pointers are welcome :) 

Thanks,

SB

---

### Post by sbelial on 2007-04-22
*** RESOLVED ****
***********************

Aha, I fixed my own problem. Turns out I had to run this line from a terminal as root:

modprobe cx88_dvb

The card is now detected properly. 

:KS

---

### Post by gusjones on 2007-04-23
> **sbelial said:**
> *** RESOLVED ****
***********************

Aha, I fixed my own problem. Turns out I had to run this line from a terminal as root:

modprobe cx88_dvb

The card is now detected properly. 

:KS

I will go and try this when I get home from work, got the identical problem to you... and I bought this card specifically for Ubuntu.

---

### Post by gusjones on 2007-04-23
It works... Hoorah! :guitar:

---

