---
title: "Specifying a channel in Mplayer"
date: 2009-01-14
forum: Multimedia Software
---

### Post by sofasurfer on 2009-01-14
I watch tv with Mplayer. The command is "mplayer dvb://". I change channels with the "h" or "k" keys. These keys tell Mplayer to use the next or previous channel in the channels.conf.atsc file. Another way would be to use "mplayer dvb://####" with the channel name in place of the "####". This info comes from [http://ubuntuforums.org/archive/index.php/t-369653.html](http://ubuntuforums.org/archive/index.php/t-369653.html)
Here is their example...
=============================================
You know that:
mplayer dvb://=
plays the first dvb channel in your list

You can then add a channel name like so:
mplayer dvb://BBC1
Plays BBC1
=============================================

Here is my question...

When I try to specify a channel I try something like "mplayer dvb://wnem" and I get nothing. Here is my channels.conf.atsc file...```

WDCQ-DT&#382;:479028615:8VSB:49:52:3
WDCQ-DT&#382;:479028615:8VSB:65:68:4
WDCQ-DT&#382;:479028615:8VSB:81:84:5
WDCQ-DT&#382;:479028615:8VSB:97:100:6
WSMH-DT:485028615:8VSB:49:52:3
WNEM Digital Television:521028615:8VSB:49:52:3
WNEM HDTV:521028615:8VSB:65:68:4
WFUM HD:557028615:8VSB:49:52:1
WFUM SD:557028615:8VSB:65:68:2
WEYI High Def:569028615:8VSB:65:68:4
WEYI Digital Television:569028615:8VSB:49:52:3
WJRT-HD&#382;:605028615:8VSB:49:52:1
WJRT-S1:605028615:8VSB:65:68:2
WJRT-S2:605028615:8VSB:81:84:3
WAQP High Definition:677028615:8VSB:49:52:3
WAQP Standard Definition:677028615:8VSB:65:68:4

```

So, what do I use out of this list as a channel name?

What does all of the information in each line mean?

---

### Post by sofasurfer on 2009-02-15
Bump

---

### Post by Jose Catre-Vandis on 2009-02-15
Try 
```
mplayer dvb://"WNEM Digital Television"
```

It's everything before the ":" and if there are spaces you need to put it on "".

I usually edit dwon my channels.conf to make like easier, for example:

```
From WNEM Digital Television:521028615:8VSB:49:52:3
To WNEM-DT:521028615:8VSB:49:52:3
```

then all I have to type (or use in code) is
```
mplayer dvb://WNEM-DT
```

---

### Post by sofasurfer on 2009-02-15
Thanks Jose. You helped a lot. As you can see from my channels.conf.atsc file...

```

#Channel 19.1
kWDCQ-DT:479028615:8VSB:49:52:3
#Channel 19.2 or 19.4
WDCQ-DT:479028615:8VSB:65:68:4
#Channel 19.2 or 19.4
WDCQ-DT:479028615:8VSB:81:84:5
#Channel 19.2 or 19.4
WDCQ-DT:479028615:8VSB:97:100:6
#Channel 66.1
WSMH-DT:485028615:8VSB:49:52:3
#Channel 
WNEM Digital Television:521028615:8VSB:49:52:3
WNEM HDTV:521028615:8VSB:65:68:4
WFUM HD:557028615:8VSB:49:52:1
WFUM SD:557028615:8VSB:65:68:2
WEYI High Def:569028615:8VSB:65:68:4
WEYI Digital Television:569028615:8VSB:49:52:3
#Channel 12.1
WJRT-HD:605028615:8VSB:49:52:1
#Channel 12.2
WJRT-S1:605028615:8VSB:65:68:2
#Channel 12.3
WJRT-S2:605028615:8VSB:81:84:3
WAQP Standard Definition:677028615:8VSB:49:52:3
WAQP High Definition:677028615:8VSB:65:68:4

```

...I was able to decipher which is which and I am able to use a command such as  mplayer dvb://WJRT-HD to display channel 12.1.

But as you can see, there are a few channels that I am unable to display by entering them manually, such as the last one in the list, WAQP High Definition:677028615:8VSB:65:68:4.

If I enter it as mplayer dvb://WAQP - HD I get the following printout...
```

daryl@ubuntu:~$ mplayer dvb://WAQP - HD
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor LE-1250 (Family: 15, Model: 127, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://WAQP.


DVBIN: no such channel "WAQP"

Failed to open dvb://WAQP.


Playing -.
Reading from stdin...

```

...and thats as far as it goes.

Using dvb://WAQP-HD I get...
```

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor LE-1250 (Family: 15, Model: 127, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://WAQP-HD.


DVBIN: no such channel "WAQP-HD"

Failed to open dvb://WAQP-HD.


Exiting... (End of file)

```

What am I doing wrong?

---

### Post by wolfen69 on 2009-02-15
btw, what kind of tv tuner is it?

---

### Post by sofasurfer on 2009-02-15
Hauppauge HVR 1600. Using it with MPlayer because I never figured out how to configure MythTV.

I have now managed to label every channel in my channels.conf with its proper channel number but am still unable to enter a few of them in terminal.

---

### Post by Jose Catre-Vandis on 2009-02-16
spaces sofasurfer you have spaces in your first example WAQP - HD. This needs to be in quotes.

But the reason it's not working is that you do not appear to have edited down the channel name to match in channels.conf:

```
WAQP High Definition:677028615:8VSB:65:68:4
```
needs
```
mplayer dvb://"WAQP High Definition"
```
or in channels.conf needs to be changed to
```
WAQP-HD:677028615:8VSB:65:68:4
```
then
```
mplayer dvb://WAQP-HD
``` should do it for you

---

### Post by sofasurfer on 2009-02-17
Interesting. I do not need the quotes for all channels, just the ones I had trouble with. But to make life less confusing, I see that I can use quotes with all of them. 

We sure do a lot of hard work to watch tv don't we? I am not conplaining though. My tv went out yesterday, so this computer TV is looking pretty dang good right now.

Have you figured out MythTV yet?

Thanks for your help.

---

### Post by Jose Catre-Vandis on 2009-02-17
You should have seen things before all the tv card drivers were in the kernel, that was hard work :)

Unable to get my PhD in Astrophysics in order to be able to run MythTV successfully (;)), instead I use bash scripts to watch and record tv on my PC (see [here]("http://ubuntuforums.org/showthread.php?t=369653")), then transfer to a media center that "just works" - GeexBox. (You can set up GeexBox to watch DVB tv, but not record...yet, waits in anticipation for GeexBox 2.0!)

---

