---
title: "HP / Compaq laptop weak sound - Solved"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by marcw on 2006-11-03
I bought a new Compaq v5209us laptop a couple months ago.  After shrinking the Windows partition a lot so that I could install Dapper, I soon discovered that this machine had two serious issues with Linux.

1) The built in wireless networking didn't work.
2) The sound from the speakers was so faint as to be almost unusuable.  (The headphones were a bit better).

#1 was caused by Compaq (HP) using a new Broadcom wireless chipset and was solved by rebuilding NetworkManager, ndiswrapper, wireless-tools, and wpa-supplicant from the latest source code available.  This might be fixed in Edgy since these updated tools were available well before Edgy was released.  I'm not sure because I haven't installed Edgy yet.

#2, my sound problem, was more difficult to solve.  Compaq (HP) decided to use a new Conexant sound/modem chipset, the driver for which Alsa hasn't even included in their latest cvs (as yet).

I'll explain how I fixed the sound problem.  These instructions should work for anyone with a Compaq or HP laptop with the identical chipset as mine.  Judging from these forums, there's quite a few others out that this may help.

[COLOR="Red"]***WARNING***[/COLOR]
These instructions are not for the faint of heart.  Nor are they for people who haven't compiled and/or patched before.  If you fall into this category, DO NOT PROCEED!  Go away and wait a few months for the next version of Ubuntu which by then should have a new version of Alsa and the kernel with these fixes in place.  I'm not going to be doing much hand holding here.  These instructions worked *for me*.

That said, if you have compiled programs before, this should be a piece of cake.

[COLOR="Red"]Caveat: [/COLOR]This process, while making my sounds normal again, disabled my system sounds.  All other sounds - web, tunes, etc. work just fine.  For me, this is ok.  I don't care for those system beeps and boops anyway.  But if anyone can figure out why this would happen and how to fix it, please chime in.

It's my understanding that the following two commands should help you identify whether or not this patch will work for you.  Here are those commands and the results they gave for my computer:

```
sudo lspci -s 0:1b -vn
```

My result:
0000:00:1b.0 0403: 8086:27d8 (rev 01)
        Subsystem: 103c:30a5
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable+
        Capabilities: [70] #10 [0091]

```
head -n 5 /proc/asound/card0/codec#0

```
My result:
Codec: Conexant CXT5047
Address: 0
Vendor Id: 0x14f15047
Subsystem Id: 0x103c30a5
Revision Id: 0x100000

I think the most important identifier here is the second one.  If it says you have a Conexant 5047, these instructions should work.  I would think that the closer to these results you can get with your computer, the greater the likelyhood of these instructions working for you.

I pretty much followed the patch instructions here:
[http://thread.gmane.org/gmane.linux.alsa.devel/41570/focus=41570](http://thread.gmane.org/gmane.linux.alsa.devel/41570/focus=41570) with a few differences.  Here's my steps:

First, make sure you have the correct kernel headers installed e.g. ```
apt-get install linux-headers-386
```
Then
```
cd
mkdir source
cd source
wget http://cache.gmane.org//gmane/linux/alsa/devel/41570-001.bin
mv 41570-001.bin conexant-test7.patch
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2
tar -jxf alsa-driver-1.0.13.tar.bz2
cd alsa-driver-1.0.13
./configure --with-debug=full --with-cards=hda-intel --with-oss=yes --with-kernel=/usr/src/linux-headers-$(uname -r)
patch -p1 <conexant-test7.patch
make
sudo make install
```

Assuming no errors, reboot.  With any luck at all, you'll have glorious, full volume sound.

If you want to revert back, I think this should work:
```
cd
cd source/alsa-driver-1.0.13
sudo make uninstall
sudo apt-get --reinstall install linux-image-$(uname -r)
```

If you undertake this solution, please post back here whether or not this worked for you.  I'll answer questions to the best of my abilities as long as it doesn't involve a lot of hand holding.  Also, if the patch works for you, please advise the author of the patch.  His email address is in the link I posted.  If you have any suggestions as to how to make this process work better, please let me know.  Also like I said earlier, if you can figure out a way to make this patch process work *without* losing system sounds, please advise.

---

### Post by jazzymood on 2006-12-21
Thanks to **marcw** ..my compaq laptop sound is now working properly..  but seems like **41570-001.bin** was updated.. therefore yesterday I used **41767-001.bin** but today I look at the [http://cache.gmane.org/gmane/linux/alsa/](http://cache.gmane.org/gmane/linux/alsa/) thereis no devel directory anymore.. I don't know why.. :p

---

### Post by Danie1a on 2008-02-09
I haven't found ..any of the patches ..you sugested and I have exactly the same problem of you had. 

Can you help me with this?

---

