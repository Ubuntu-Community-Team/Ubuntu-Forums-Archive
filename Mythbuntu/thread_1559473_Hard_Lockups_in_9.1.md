---
title: "Hard Lockups in 9.1"
date: 2010-08-23
forum: Mythbuntu
---

### Post by scim on 2010-08-23
I am generally very happy with Mythtv/Mythbuntu but I have one significant problem that is driving me mad trying to fix so I would welcome any suggestions.

The symptoms are that during play back of certain recordings the pc server will randomly lockup, for a few seconds the picture will remain on screen frozen and then will turn black at which point the entire machine is locked solid with no disk activity and resetting is the only option. The problem only seemed to appear when I installed a Via 6421 based pci to sata adaptor with a 1TB Samsung hard drive but I have not been able to pin anything specific that is causing this.
Observations are:-
- Mainly (but possibly not exclusively) occurs on recordings made from UK terrestrial freeview ITV3 channel.
- The problem occurs playing the recordings back in VLC so does not appear to be Mythtv related
- I have set the drive to 150Gb/s mode.
- I have tried the disk in another pc with native sata support and couldn't reproduce the problem (using VLC in Kubuntu).
- I have repartitioned to move all files physically to the first 320GB of the disk in case it was related to physical location but the problem still exists in the same files.

I realise that some of the above appear contradictory but they are my observations. Help...

Thanks

---

### Post by LowSky on 2010-08-23
sounds like the PCI SATA card is bad, and subsequently the files o the drive are corrupted from interupted service.

---

### Post by scim on 2010-08-23
I wouldn't deny that the card is my main focus but the recordings playback OK on another pc - and why does it seem to be one channel exhibits the problem but others eg BBC1, ITV1 never seem to?

Thanks

---

### Post by ian dobson on 2010-08-23
Hi,

Could it be a hardware conflict? Maybe interrupt?, maybe try using a differnt PCI slot if possible.

Via aren't know to be the best chips.

Have a look here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263160](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263160) at about post number 17 onwards.

Regards
Ian Dobson

---

### Post by scim on 2010-08-23
Thanks for the reply, I have tried swapping pci slot but didn't make any difference, I have not found anything in logs suggesting IRQ conflicts. I looked at the link you gave and I have seen some very similar errors to those but not always and not on every failure (possibly because the logs don't always get flushed?), also I am running a later version of ubuntu and according to that thread the problem should be fixed?

---

### Post by ian dobson on 2010-08-23
Hi,

Have you tried disabling the write cache on you harddisks (hdparm /dev/sdX -something)

Regards
Ian Dobson

---

### Post by scim on 2010-08-24
I gave that a go but made no difference, when I thought about it I can't see how it would since the problem only occurs reading from the disk not writing to it, the problem files do seem to be readable on another pc (although due to the random nature of the lockup I can't be 100% sure).

Thanks

---

### Post by nickrout on 2010-08-24
If it's one channel only it is conceivably either a signal issue, or the channel is using a different transmission method (different codec or container format?)

---

### Post by scim on 2010-08-24
I understand why you say that but the SD freeview channels are all mpeg video and audio, also there is no sign of poor signal, add to that the fact that the file will play on another pc suggest that it can't be simply the file itself that is faulty. What I did wonder though is whether it may be due to the bitrate on that channel which is causing a problem with the drive controller?

Thanks

---

### Post by ian dobson on 2010-08-24
Hi,

To test "just" the disk, go to the terminal and type

dd if=/dev/zero of=/some/file/on/disk bs=4k count=100MB

to create a 100MB file and

dd if=/some/file/on/disk of=/dev/zero  bs=4k count=100MB

to read the file back. Make sure the file you write to/read from doesn't exist (/some/file/on/disk)

**Warning: If it's a disk problem then the system might crash.**

Regards
Ian Dobson

---

### Post by scim on 2010-08-24
Thanks for that, I tried it and wrote and read an 8GB file fine, I also used a disk benchmarking program called bonnie++ and that completed its benchmark OK so the disk seems OK at the moment. I'm beginning to wonder about glitches in the mpeg file again?

---

### Post by ian dobson on 2010-08-25
Hi,

So your still have problems with ITV3, or does it happen on other channels aswell?

It could well be that the stream your getting for ITV3 isn't 100% standards conform (I get ITV through my cable provider and I ended up disabling the channel as recording from it produced a large number of errors in the frontend log during playback. On top of that there wasn't anything intersting).

Could you please upload a small 50Mb or so recording from ITV3 to some source that I can download and have a look at. 

Regards
Ian Dobson

---

### Post by scim on 2010-08-25
Sorry for the delay in responding, but I now think that it can't be anything to do with the video content since I get the same lock up issue even if I just cp the file from the offending disk to another one. I need to do more checking (difficult because the machine is often recording) but I picked a file at random (can't be sure that it wasn't an offending file due to mythtv's annoying cryptic file naming - why does it do that?) and copying this one also locked the pc after copying 197MB. I have no idea why this would fail when benchmarking etc works fine?

Thanks

---

### Post by ian dobson on 2010-08-25
Hi,

A stupid question, have you tried running a memory test for a longer period of time. Benchmarking doesn't create large files/hit the fs cache that hard. Copying files hits the readahead caching on the fs, so memory problems could cause a problem.

Could you also try coping the "bad" recording to /dev/null, this would just test reading from the hd.

It really looks like a strange hardware problem. The only thing to try is disabling ncq and replacing all your sata cables. I had lots of problems with my big (6x2Tb wd drives) array/backend data storage until I bit the bullet and replaced all the sata cables.

Regards
Ian Dobson

---

### Post by scim on 2010-08-26
Stupidly I hadn't run a memory test but I have now but no errors were shown, I also checked ncq and the queue size is set to 1 which I believe means it is disabled. In addition I have swapped the sata cable with a known good one from another pc and this also made no difference.
 
The thing that puzzles me the most about this problem is despite it seeming to be illogical, the problem certainly exists on certain channel(s) but not others, for example recordings from BBC1 and ITV1 have never (to the best of my knowledge) displayed this problem and all the ones I am aware of at the moment are from ITV3 although I do have the feeling that there may have been others (possibly on the same mux). However the copying issue seems to be accross the board (I will test this further tonight by seeing if I can copy a file that I am sure has played OK).
 
The only other point which may have some relevance is that the motherboard is a dual channel nForce2 board with 3 memory slots, I have never understood quite how this works but it seemed to be fine in the past (configuration is a pair of 256MB and a single 512MB).
 
I appreciate the time you have spent looking at this for me.
 
Thanks,
Dave

---

### Post by ian dobson on 2010-08-26
Hummm,

nForce2 chipset, I remember something about problems with SATA, can't remember what exactly (I'll have a look in my notebook (Paper version) this evening).

Maybe try looking in the bios for various options for the SATA ports (IDE mode,RAID Mode) etc. There might be a conflict there.

Regards
Ian Dobson

---

### Post by scim on 2010-08-26
Interesting but bear in mind that this motherboard does not have native sata support which is why I am using the pci to sata card.

Thanks,
Dave

---

### Post by ian dobson on 2010-08-26
Hi,

Do you have a differnt sata card that you could use. Before I got my new big box I used a sil 31xx PCI card on a dual opteron system. Which actually worked quite well.

Regards
Ian Dobson

---

### Post by scim on 2010-08-26
No sadly I don't, if I knew a (cheap) card that would definitely work I would probably get one since I think it is most likely that that's causing the problems but I'm reluctant to spend money if I'm not sure it will do the job.

Dave

---

### Post by scim on 2010-08-26
Further update - I have tried copying a file that I know plays back OK and that copied fine so it does appear that if a file won't play it also won't copy. I will try again tomorrow to do this with the drive on a different pc.

Thanks,
Dave

---

