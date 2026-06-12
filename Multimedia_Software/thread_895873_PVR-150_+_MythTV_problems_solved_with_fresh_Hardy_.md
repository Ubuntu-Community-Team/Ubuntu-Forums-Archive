---
title: "PVR-150 + MythTV problems solved with fresh Hardy install"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Lodurr on 2008-08-20
Hi.

I just wanted to report that I had several PVR-150 problems fixed by a fresh install of Hardy.  Before, I was running off a Feisty->Gutsy->Hardy upgrade.

My PVR-150 remote used to be unresponsive while watching recordings.  Sometimes it would take a few seconds, sometimes a whole minute before my button press registered.  That problem is gone.

I used to get occasional tinny audio in recordings (about 1/20).  I had tried an extra script to reset the audio input, but that wasn't working.  Now I'm not using the script and at about 30 recordings so far (and lots of channel switching), with no tinny audio.

The one part of my reinstall I'm not happy about is that it nuked my /var/lib/mythtv directory, with all my recordings and vids, even though I told it to not format that partition.  It said it was removing conflicting directories, but I don't see how a directory full of .mpgs could conflict with a new OS install.

Some other notes that would've helped if I could go back in time and tell myself:

- IR blaster codes can have partial functionality.  For example, just because you get the box to power on and off doesn't mean that the rest of the buttons should work

- MythTV wants the channel change script to be in /usr/local/bin

- don't forget to chmod +x your channel change script (i.e. "sudo chmod +x change-channel-lirc.pl")

- be sure to download the patched PVR-150 firmware from [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin)

That's all I can think of for now.

---

