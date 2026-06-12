---
title: "Problem burning CD ISO file with K3b"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by Zeikcied on 2007-10-17
This isn't exactly "Multimedia," but I'm putting it here because it seems most K3b related topics are in this forum.

I cannot get K3b to write an ISO file.  I'm trying to burn the Kubuntu 7.04 Feisty CD ISO to a disc.  (More as a test at this point, as Gusty is coming tomorrow.)

I went to Tools -> Burn CD Image.  K3b opens the ISO, gives the correct MD5 sum for the ISO, and seems to burn the ISO to the disc.  The problem is that nothing shows up.  After burning, K3b tells me that the disc doesn't match the original content (with the Verify Data option selected, of course), and it also tells me that it cannot mount the disc.  Konqueror does not display any files on the disc, even though K3b seems to have gone through the entire writing process.

I know it's not a hardware issue, as I also tested K3b by creating a Data CD, and burning a few individual files to the same disc.  That worked just fine.  The files show up, and the disc can be mounted.

I don't know why K3b can burn individual files, but not a CD image.  I don't think I'm doing anything wrong.  When I go to Help -> About K3b, it tells me that it's version 1.0.  I checked the website, and it's not the latest version, but I figured Adept would take care of the upgrades.  Still, I don't know if it's a version issue or what.

Any help would be greatly appreciated.

---

### Post by pbcartwright on 2007-10-17
with movies, I have to eject the DVD, then reinsert it ( eject and eject -t) to get it to recognize the contents..

---

### Post by Zeikcied on 2007-10-17
> **pbcartwright said:**
> with movies, I have to eject the DVD, then reinsert it ( eject and eject -t) to get it to recognize the contents..
That didn't work.

Also, I'm burning a CD ISO onto a CD-RW.  Not a DVD ISO, and not on any form of DVD media.  Also, it's a Kubuntu ISO, not a movie.

Anyway, I just tried burning the ISO again.  K3b can't mount it.  Kubuntu doesn't auto-mount it.  And I can't seem to manually mount it.  The odd thing is that K3b can at least tell that it's a Kubuntu disc.  The label is at least correct.  But it cannot mount the disc.

I have the Writing Mode set to Auto, speed set to Auto, Image Type set to Auto Detection, and Data Mode set to Auto.  K3b sends a CUE sheet (I don't know why, but I'm not a burning expert or anything) and proceeds with burning.

Either it's burning with an unrecognizable file system, or something is messing up somewhere along the lines.

---

### Post by julian67 on 2007-10-17
> **Zeikcied said:**
> **  After burning, K3b tells me that the disc doesn't match the original content **

It's obvious that the burned disc is bad, it shouldn't be a surprise that it can't be mounted etc. 

Bad media? This is the cause of most burning problems. Use a high quality unblemished CD.

Also possible is that the burner does not have dma enabled which causes buffer underrun and bad burns. 

People will tell you that you need to burn at 1x or 2x or 4x but if you have a modern burner (anything that can burn CD at 48x or 52x) and use good media you can let k3b take care of the speed or even select maximum speed and should get an error free burn with matching checksum. If you have a 5 year old burner OK try it at 1x or 2x

---

### Post by Zeikcied on 2007-10-17
> **julian67 said:**
> It's obvious that the burned disc is bad, it shouldn't be a surprise that it can't be mounted etc. 

Bad media? This is the cause of most burning problems. Use a high quality unblemished CD.

Also possible is that the burner does not have dma enabled which causes buffer underrun and bad burns. 

People will tell you that you need to burn at 1x or 2x or 4x but if you have a modern burner (anything that can burn CD at 48x or 52x) and use good media you can let k3b take care of the speed or even select maximum speed and should get an error free burn with matching checksum. If you have a 5 year old burner OK try it at 1x or 2x
This burner (CD-RW & DVD combo drive) comes from my previous PC, which I got in 2003.  (The DVD burner on this computer died a couple weeks after I got it, and I never bothered replacing it.)

The media is 4x speed, though the drive can do higher speeds.

I've tried on three separate discs, with the same results on all three.  One was an older Memorex disc that had data on it (I erased it and attempted to burn the ISO).  The next was a newer Memorex.  And the last is a brand new Sony disc.  All three have the same problems.

I don't see how it could be a disc issue, because I was able to burn seven or eight individual files on the Sony disc, and the burn went just fine.  K3b burned the files, and was able to mount the disc after finishing.  Konqueror was able to view the contents, and everything was right with the world.

So despite being able to write individual files to this disc, K3b messes up with writing an ISO file to the same disc.  It's not the hardware, it's not the disc, and K3b is at least able to perform a regular data burn.  It just won't burn the ISO properly.  I don't know if I need to upgrade K3b using a different repository, or if I'm missing a plug-in somewhere.  (I know K3b complains about the lack of an MP3 plug-in when it starts.)

---

### Post by julian67 on 2007-10-17
I still suspect the hardware or media. Burning "seven or eight individual files" doesn't necessarily  mean all that much. To make a good comparison they would need to be very large files and be checksummed before and after.

But let's find out if k3b is the culprit by bypassing k3b and do the burn from the command line:

```
 cdrecord -v speed=<burning speed> dev=<your device> /path/to/foo.iso ; eject
```

---

### Post by Zeikcied on 2007-10-17
> **julian67 said:**
> I still suspect the hardware or media. Burning "seven or eight individual files" doesn't necessarily  mean all that much. To make a good comparison they would need to be very large files and be checksummed before and after.

But let's find out if k3b is the culprit by bypassing k3b and do the burn from the command line:

```
 cdrecord -v speed=<burning speed> dev=<your device> /path/to/foo.iso ; eject
```
Wow.  That totally worked.  It auto-mounted, and I can see all the files.  Awesome.

Anyway, K3b says it's version 1.0.  I don't know if the more recent versions still say that or not.  Adept says that the version in the official repositories is version 1.0.  So, I can't tell if it's a current bug, or one that's been fixed in a more recent version that isn't in the official repository.

But the console command you gave wrote the ISO properly.  Thanks for that. :)

---

### Post by bigken on 2007-10-17
thne best way I have found to make and burn iso files is as simple as right click
make image and to to burn same as right click write to disc

---

### Post by julian67 on 2007-10-17
> **Zeikcied said:**
> Wow.  That totally worked.  It auto-mounted, and I can see all the files.  Awesome.

Anyway, K3b says it's version 1.0.  I don't know if the more recent versions still say that or not.  Adept says that the version in the official repositories is version 1.0.  So, I can't tell if it's a current bug, or one that's been fixed in a more recent version that isn't in the official repository.

But the console command you gave wrote the ISO properly.  Thanks for that. :)

You're welcome :-) 

It's been a while since I used kde or k3b but I remember it being very good. Bearing in mind that it is essentially a front end for cdrecord/wodim I'd assume that there is some config problem with it rather than a serious problem with the application. Perhaps you can delete the k3b config files and start over.

---

### Post by Fintan on 2008-04-11
I am having exactly the opposite issue:

Kubuntu Hardy.

I haven't needed to use k3b with hardy up until now.

I wanted to backup some data and burn an iso (kde4 beta).

The iso burns fine but when trying to burn a data disk k3b tells me it doesen't like my medium.

Same cd producer (EMTEC CD-R)

Any ideas please? This is important for me.

Edit:
When trying the cli solution I get this:
fred1@fintanws2:~$ fred1@fintanws2:~$ cdrecord -v speed=<burning speed> dev=/dev/scd0 /home/fred1/SusaneKobler/ ; eject
bash: burning: No such file or directory
fred1@fintanws2:~$

I am not very good at the cl so I am probably missing something here

---

### Post by Zeikcied on 2008-04-20
I'm still having problems with K3b 1.0.4.

I deleted what I believe to be the config file at ~/.kde/share/config/k3brc and started the program again.  But the same thing happened.

From what I can tell, K3b is running mkisofs then cdrecord, so I don't know if it's something wrong with mkisofs, or what.  But it still won't burn an ISO file properly.

In this case, I was attempting to burn a Xubuntu Gutsy ISO for my mom's computer.  I finally got the disc burned with cdrecord, but I can't tell if all the files are on the disc.  It wouldn't boot on her computer, so I just used my Kubuntu Gutsy disc instead.  There are files on the disc, but I don't know if they are all there.

EDIT: Actually, looking at the Programs tab, K3b is using genisoimage and wodim.  I have cdrecord installed, but it isn't displaying it in the Programs list.  I don't have mkisofs installed, but I'm about to do that now.

---

