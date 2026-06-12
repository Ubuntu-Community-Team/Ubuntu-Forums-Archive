---
title: "Jerky machine when reading/playing CDs and DVDs..."
date: 2009-04-11
forum: Multimedia Software
---

### Post by ragtag on 2009-04-11
When playing back DVD's on my machine I get jerky playback, bot sound and pictures. Generally the DVD will play a little, then start spinning fast and playback will become jerkey. Actually the whole system becomes jerkey, the mouse pointer and everything. VLC and PulseAudio seem to be using most of the CPU power. I'm kind of stumped on this one.

I'm running Ubuntu 8.10, I have libdvdcss2 libdvdread3 libdvdnav4 vlc all installed. The DVD drive is an internal Sony IDE player. I've eliminated a few things.

- VLC, Mplayer, etc. give the same result.
- Tried running VLC from the terminal, but got no errors.
- The hardware works, booted into WinXP and played the DVD in VLC there just fine.
- Was able to play the DVD on an external USB drive connected to the machine (which would indicate that DVD playback actually works on my Ubuntu install, just not from the internal IDE drive).
- Replaced the internal DVD drive and IDE cable (no difference).

I'm really not sure what to try next. I searched the forum, and found others had similar problems, but found no solutions. The problem also seems to be unrelated to DVD playback, as ripping a CD with Audio Juicer was much slower on the internal drive than the external USB one, and was causing the whole system to slow down and become jerky, just like DVD playback.

So, in short, it seems to be something is wrong when reading from my internal IDE DVD player. Any ideas what I should try next?

```

bla@bla:~$ hdparm - /dev/scd0

/dev/scd0:

 Model=Optiarc DVD RW AD-5200A                 , FwRev=1.05    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no

 * signifies the current active mode

```

I have an NVIDIA 6800 card, commercial drivers installed, OpenGL works fine both with glxgears and in Blender. The machine is an AMD machine around 3Ghz (I forget) with 3Gigs of RAM.

Oh, I should add that DVD playback used to work on this machine a few months back.

---

### Post by iduriduridur on 2009-05-01
I'd try a Debian/Centos(older kernels) install I'd like to see if you get the same problem I see with Ubuntu. 

Ubuntu copies DVD/CD slow. Yes DMA is on in my tests. I can't get it to work normally.

---

