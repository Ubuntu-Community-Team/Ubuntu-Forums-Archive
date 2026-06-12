---
title: "Mailing List - Ubuntu Linux Distribution Tailored For PC-DC Server"
date: 2010-11-02
forum: Michigan Team - US
---

### Post by TeamXlink on 2010-11-02
This is a mailing list, I sent.

What does everyone think of it?

> This idea has been floating around various Dreamcast forums, such as Dreamcast-Talk and Dreamcast.Onlineconsoles.

The Dreamcast comes standard with a modem (56K in NTSC & 33.6K In PAL).

A good number of games supported online play back then, but as of now these are the only ones that can still be played online:

Phantasy Star online
StarLancer
4x4 Evolution
Maximum Pool
Quake III Arena

To play these games online you could either:

Pay for Dial-Up
Or
Create a PC-DC Server

A PC-DC Server is the most used method to get online, but it can be annoying to setup and is hard to setup.

The best guide for setting one up is located here:

[http://www.ryochan7.com/blog/2009/06/23/pc-dc-server-guide-part-0-introduction/](http://www.ryochan7.com/blog/2009/06/23/pc-dc-server-guide-part-0-introduction/)

[http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-1-pc-side-configuration/](http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-1-pc-side-configuration/)

[http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-2-dc-side-configuration/](http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-2-dc-side-configuration/)

[http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-3-connection/](http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-3-connection/)

There are also other complications.

Most of the games support Blind-Dial, which means it doesn't require a dial-tone to connect, however one of the most played ones don't support Blind-Dialing, Quake III Arena.

Supposedly there is a way to make the modem produce the dial-tone, here:

[http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2608](http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2608)

# resets the modem
ATZE1

# puts the modem into voice mode
AT+FCLASS=8

# opens the connection
AT+VLS=1

# produces the tone
AT+VTS=[440,350,255]

# closes the connection so it can answer
ATH

# answers the connection
ATA

However, nobody has figured out how to actually put this information in use.

There is also another problem, it requires you to be using your computer while connecting.

You have to issue the mgetty command and then a few seconds later use the killall command, which means it can't be headless.

I found a way to make it headless and wrote a tutorial on it here:

[http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2681](http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2681)

But it isn't very reliable and often times doesn't work.



It would be nice to fix this, the priorities should probably be this:

1. Make the server headless
2. Make it produce the Dial-Tone

And eventually:

Make a Distribution and/or Live cd that would have all of this setup.

This would also require drivers such as the Linux modem drivers for Conexant modem provided for free from dell, here:

[http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/)

For priority one and two, I've made topics on the Ubuntu forums, but nobody seems to know how to accomplish this, but I know that it can be done.

Here is a link to one of the forum topics discussing the dial-tone:

[http://ubuntuforums.org/showthread.php?p=10063265#post10063265](http://ubuntuforums.org/showthread.php?p=10063265#post10063265)

Please help the Dreamcast community with priorities one and two.

Dreamcast-Talk - Make Modem Send Out Dial Tone
[http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2608](http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2608)

Dreamcast-Talk - Headless PC-DC Server
[http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2681](http://dreamcast-talk.com/forum/viewtopic.php?f=3&t=2681)

Ubuntu - Producing Dial Tone With Mgetty
[http://ubuntuforums.org/showthread.php?p=10063265#post10063265](http://ubuntuforums.org/showthread.php?p=10063265#post10063265)


Thank you

-TeamXlink

---

