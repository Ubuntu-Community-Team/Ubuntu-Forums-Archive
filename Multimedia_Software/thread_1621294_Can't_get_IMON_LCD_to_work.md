---
title: "Can't get IMON LCD to work"
date: 2010-11-14
forum: Multimedia Software
---

### Post by matthias.sitte on 2010-11-14
Hi everybody,

I've been trying to get my IMON LCD front panel to work under Ubuntu Maverick for some days now, w/o success so far. `lsusb' identifies the device as

ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

I've installed lirc and successfully set it up after reading somewhere that I need to load the `imon' driver instead of the `imon_lcd' driver due to some changes in the kernel. So, the remote control works fine!

Now I would like to display some info on the LCD. It works under XP, I tested this because I sent the previous LCD back asking for a replacement which didn't work. After installing `lcdproc' and setting up LCDd (almost) nothing happens. When turning on the power, it lights up for a second, then goes to an intermediate state and stays this way. It doesn't even turn off when I shut down Ubuntu, only when I unplug the power cord.

I'm really puzzled. What am I doing wrong?? Any help is appreciated, even "read the forum here or there."

Best,
Matthias

---

### Post by Scorpuk on 2010-11-14
Do you have lcd0 in /dev?

If you do then check its permissions. Ensure your user can read and write to it. Then try the following:

```

echo "Hello World" > /dev/lcd0

```

---

### Post by matthias.sitte on 2010-11-14
> **Scorpuk said:**
> Do you have lcd0 in /dev?

Yes, it exists:

```
matthias@tachyon2:~$ ll /dev/lcd*
crw------- 1 root root 180, 144 2010-11-14 12:54 /dev/lcd0
```

> If you do then check its permissions. Ensure your user can read and write to it.

Not sure what the correct permissions are. Using ```
chmod 666
``` on /dev/lcd0 for now:

```
matthias@tachyon2:~$ ll /dev/lcd*
crw-rw-rw- 1 root root 180, 144 2010-11-14 12:54 /dev/lcd0
```

> Then try the following:

```

echo "Hello World" > /dev/lcd0

```

Well, this gives an odd error:

```
matthias@tachyon2:~$ echo "text" > /dev/lcd0 
bash: /dev/lcd0: Device or resource busy
```

Any ideas?

Best, Matthias

---

### Post by Scorpuk on 2010-11-14
Are you running LCDd?

Something is running that is taking control of lcd0 and not allowing you to use it.


Not sure how helpful this will be as this was for way back in ubuntu 6.10:

[http://venky.ws/forums/viewtopic.php?f=2&t=279&sid=2fa596d3c146a8c3ac1e9719e04d391a](http://venky.ws/forums/viewtopic.php?f=2&t=279&sid=2fa596d3c146a8c3ac1e9719e04d391a)

In which I give a rough How To from the second post. :-)


You were spot on with chmod 666. ;-)

---

### Post by matthias.sitte on 2010-11-15
Thanks Scorpuk for the quick replies.

I realized shortly after posting that probably LCDd is having a handle on the /dev/lcd0. So, after stopping it, the echo command works but, unfortunately nothing happesn.

Meanwhile, I've begun to read the src from lirc and lcdproc, and now I'm really confused. I'll remove & purge lirc and lcdproc and start from scratch. I'll follow your other thread and post my results when I find the time.

Best, Matthias

---

### Post by Scorpuk on 2010-11-19
Another point is that I am now realising there has been some major changes in Ubunbtu 10.10 for lirc and remotes, as I am having problems with my remote which worked flawlessly in 10.04. (Actually quite a few people are having similar problems)

However I did find this post that might help me. Will check tonight.

[http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-and-lirc-works-843751/]("http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-and-lirc-works-843751/")

---

### Post by matthias.sitte on 2010-11-19
> Another point is that I am now realising there has been some major changes in Ubunbtu 10.10 for lirc and remotes, as I am having problems with my remote which worked flawlessly in 10.04. (Actually quite a few people are having similar problems)

Yeah, i was hoping for something like that 'cause then it should work in principle. I found this two posts interesting:

[http://wilsonet.com/?p=85](http://wilsonet.com/?p=85)
[http://wilsonet.com/?page_id=95](http://wilsonet.com/?page_id=95)

The first one basically says that in kernel 2.6.35 they ported the stuff from lirc_imon to something like imon, the second one saying that you shouldn't configure lirc to use iMON but the Linux input devices (/dev/input/BY-ID/...).

This actually works, I got it to work that way, i.e. sudo irw recognizes by iMON Pad remote. Unfortunately, the mouse didn't work this way (why?). Had to start from scratch after messing with lirc sources, so I'll give it a try over the weekend.

Well, lirc now hopefully working I'd also like to see some output on the LCD. Any suggestions??

Best, Matthias

**UPDATE:** Mouse input works.

---

