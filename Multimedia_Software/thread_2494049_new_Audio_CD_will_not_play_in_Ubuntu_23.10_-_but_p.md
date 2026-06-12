---
title: "new Audio CD will not play in Ubuntu 23.10 - but plays perfectly in a VM"
date: 2024-01-03
forum: Multimedia Software
---

### Post by layolayo on 2024-01-03
New installation of 23.10 - I have a new Audio CD that when I attempt to play in my BluRay drive, the disc is unplayable.

If I leave the disc in the drive and load up a windows 10 VM, and give the same drive to the VM, the disc plays fine.

Are there some extra codecs needed or drivers needed to have Linux read and play the disc?

---

### Post by BicyclerBoy on 2024-01-04
Do you mean an audio CD?
Is it a Sony Music audio CD?

---

### Post by layolayo on 2024-01-05
Yes, audio CD from a recent release - not published by Sony AFAIK (unfortunately not home to double check this)

I was thinking maybe Linux has a higher restriction on failed reads, and the Windows VM being a little more lenient? If this is the case, can the amount of errors accepted be increased?

---

### Post by Holger_Gehrke on 2024-01-05
Is your problem limited to that one CD ? Then it's more likely that you've got what the German magazine c't called "Un-CD" - a disk that's just slightly out of spec so that it will play in most audio CD-players but won't play on a computer and therefore supposedly can't be ripped. That's why BicyclerBoy asked whether the CD was published by Sony since they are kind of notorious for doing this.

Holger

---

### Post by layolayo on 2024-01-05
I've had a similar issue with DVD just never spotted this quirk at the time, as I say - the hardware doesn't change same PC, running Ubuntu 23.10 as the base, to play the disc all I have to do is open a VMWare Windows VM and the disc plays perfectly. It hasn't moved from the exact same player which Ubuntu had issue with 10 seconds before. When I get home I'll get out a collection of Audio and DVD discs to get a sense of more detail. Is there anyway of tracking the attempted reads from Linux, I can hear the drive erratically moving under Linux control, under Windows control via VM is smooth.

Just remembered, two discs came with the package (latest Live Album from Porcupine Tree - Closure/Continuation) yes both discs did the same, though when one of them showed up as a disc and listed the tracks, but they wouldn't play. Then when trying again later, the disc wouldn't appear. Once it appears in Linux however, then the VM can read it perfectly. So somehow Linux is passing the drive and access to the VM which has better read access than the base operating system... &#65533;&#65533;

---

### Post by layolayo on 2024-01-05
BicyclerBoy and Holger, thank you for your attention - looks like it was a reading error in the drive and Windows was being a little more lenient.

I got back to basics and stripped the drive, cleaned the lens with Isopropyl and an earbud - Disc now appears in Linux and plays without error.

Nearly one of those "Have you got it plugged in?" moments...

---

