---
title: "Sound System Woes - ALSA/OSS? aoss?"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Zorael on 2007-04-25
I'm running Feisty x64 on my "fairly beefy" laptop. It's one of those huge things with a 20" screen, 2gb ram, and $2500 less coin in your purse. I'm one of those World of Warcraft addicts, which I play on said laptop. Having a proper graphics card (GeForce Go 7600) and a decent processor (Core 2 Duo 2.0ghz), it plays it marvelously under Windows. I'm also one of those who can't help but feel attracted to the idea behind GNU and Linux, so I ended up repartitioning and installing Feisty alongside Vista. I've been toying with it for about a month now (starting with the beta, and now the real deal), and while I'm no wiz, I like to think I've gotten my sea-legs.

I've gotten World of Warcraft to work in both Wine and Cedega, though with a noticeable slowdown compared to the performance under Windows. I heard stories about people enjoying sizable boosts, but it's just not happening for me.


The one thing I fail at, however, is setting sound up properly. I understand that there are two major sound systems, the older OSS and the newer ALSA. I also understand that OSS will grant exclusive access to the sound card to whichever application asks for it first, while ALSA has a software mixer to split access to the device.

Whenever I "force" something to use ALSA, by wrapping it using aoss, the results are horrible. The sound cracks continuously, or sometimes play at 200% its normal tempo, and often just dies after a while (or ends up in white noise static).

Now, along with Warcraft, my other "requirement" must be the availability of a voice communication client. I googled extensively and saw several hints on how to get Ventrilo up and running through Wine and Cedega, and most mentioned the issue with both WoW and Ventrilo utilizing OSS, and as such, ending up mutually exclusive. Further, they recommended that you start both Ventrilo and WoW with the aoss wrapper, to make sure it properly emulates OSS while still letting both applications enjoy access to sound input/output.

But I fail. I can't get it to work satisfactorily. After much ado, I managed to get Ventrilo to *work*, but my fellow Ventriloquists all complain that they can barely make out my voice over all the cracking. With Ventrilo running in the background, the sound in WoW is not much better, with cracks and ultimately white noise. I generally play under Cedega, partly due to having paid for it, and partly because of its Direct3D support; OpenGL frankly seems to run slower, and no support for Hardware Cursor (which is a life-saver when FPS drops).

There seems to be a Linux-native client of TeamSpeak, but I understand that it also does its thing under OSS.

As for my sound card, I'm not quite sure, as I didn't build the system myself. The only thing I can divine is "Realtek High Definition Audio", but Ubuntu found some non-proprietary drivers by its own.


Am I doing something obviously wrong? Are there some alternatives to aoss, which does the same job with, potentially, better results (on my system)? Am I simply naïve to think I could get sound working satisfactorily with on-board sound?

---

### Post by Severun on 2007-12-02
Had the same problem with aoss.

Try using arts  I believe it's installable via apt-get

You start up the daemon

artsd -d 

(-d puts it in full duplex so teamspeak works)

Then run your app like you do with aoss, i.e.

artsdsp wine WoW.exe

or 

artsdsp TeamSpeak

I've so far had it running w/ WoW, RythmBox and Teamspeak all going at the same time w/ no static or dropouts.

Myself, I'm looking for the config file in cedega where I can tell it when it starts wine to start it with the prefix of artsdsp.

Hope that helps.

---

