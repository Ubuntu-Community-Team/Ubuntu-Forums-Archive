---
title: "CD Audio playback  impossible even with pristine discs."
date: 2011-04-24
forum: Multimedia Software
---

### Post by Mr Bean on 2011-04-24
I have recently been trying to play Audio CDs on my computer. I have tried a number of discs now, some scratched and some without a mark on them and in every case I get the same problem:

There are long periods of silence, frequent skipping, and half the tracks fail to play at all. This is regardless of the audio player I use (though I prefer to use Rhythmbox). 

If I copy the files off the disc and play them as WAV files, they work fine. But trying to get them to play straight off the disc is an impossibility. 

Please note I will give you any information you need but I am not a computer scientist so I do not automatically know what information you will need or where to get it. 

For what it's worth:

```
$ sudo hdparm -i /dev/dvdrw3

/dev/dvdrw3:

 Model=TSSTcorp, FwRev=SB01, SerialNo=A
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  *mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


```I do not experience any problems with this drive when transferring data (installing operating systems, applications, burning discs). Indeed I installed an OS only last week using this drive, and having taking the precaution of selecting the "check disk integrity option" everything checked out okey dokey. 

My computer is about a billion times more powerful than the computer I owned in 1995, which could play CDs just fine. Though that computer was running Windows so perhaps that's why it actually worked.

---

### Post by KegHead on 2011-04-24
Hi!

It sounds like it could be a cd problem.

When was the last time you cleaned your cd?

KegHead

---

### Post by Mr Bean on 2011-04-24
I have tried it with pristine discs, literally not a mark on them. I think if I tried to clean them I would just make them dirtier. Though I did try to clean one of the scratched discs and that didn't help. 

I cleaned the drive today, with one of those CD laser lens cleaners (essentially just a CD with a brush sticking out of it - like this: [http://upload.wikimedia.org/wikipedia/commons/c/c8/CD_Lens_Cleaner.jpg](http://upload.wikimedia.org/wikipedia/commons/c/c8/CD_Lens_Cleaner.jpg)) and that didn't make a difference.

This has all the hallmarks of being a software problem.

---

### Post by KegHead on 2011-04-24
Hi!

Just fishing:

Is your cd an older model that does not read DVD's ?

Is your music on a DVD?

KegHead

---

### Post by KegHead on 2011-04-24
Hi!

Another thought:

Can you get into your bios?

KegHead

---

### Post by Mr Bean on 2011-04-24
They're just regular store-bought audio CDs.

It's quite a new drive, it will read DVDs. I can get into my BIOS if necessary.

---

### Post by andrew.46 on 2011-04-24
There have been a few posts on these forums relating to the failure of some gui applications to properly play audio cds. What happens when you play your audio cds from the commandline in the following manner:

```

mplayer -cache 2048 cdda://

```

You will of course have to have mplayer installed :).

---

### Post by Mr Bean on 2011-04-24
Thank you for the advice.

I had to use the command: 
```

mplayer -cdrom-device /dev/dvdrw3 cdda://
```It plays slightly better than in the GUI, but I am still experiencing pausing. The playback will pause for anything between 1 and 5 seconds and then resume. This happens reasonably frequently, once every 10 to 20 seconds.

It's an improvement over Rhythmbox, but the problem definitely seems to be effecting mplayer as well.

---

### Post by Mr Bean on 2011-04-25
Oh silly me I forgot to add the "-cache 2048" parameter back in. I did that, and now it plays fine. So yes, it works in mplayer. 

What do I do to get it to work in Rhythmbox?

---

### Post by andrew.46 on 2011-04-25
Good to hear that at least MPlayer works :). Unfortunately I do not know how to get Rhythmbox kick started but I know you are not alone with this frustrating problem that has a fair coverage in these Forums and on Launchpad. Hopefully someone has some ideas??

---

### Post by lidex on 2011-04-28
I have no problems playing audio CDs so I have to wonder if it is hardware related. Perhaps a firmware update would help? Do you have gstreamer ugly, bad and ubuntu-restricted-extras installed?
Reference:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

