---
title: "Creative Zen works some of the time"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Eman64 on 2008-09-21
Hey guys,

My Creative Zen 16gb only works some times. I usually have to keep unplugging and plugging it back in about a hundred times before it finally is recognized by MTP. I would really like it to work on the first go.

I've tried installing the latest libmtp, libusb and gnomad2, and have tried using Amarok. Nothing seems to work! 
I'd also like to know how to put album on to the machine. The two albums I got from Amazon Download have them, but nothing else.

If it helps, here's what happens when I tried to read it using sudo mtp-detect:
```
user@computer:~$ sudo mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
PTP: Opening session
LIBMTP PANIC: Unable to read device information on device number 1, trying to continueDetect: There has been an error connecting. Exiting
user@computer:~$ 

```

Thanks a ton

---

### Post by Eman64 on 2008-09-21
Please help
Bump

---

### Post by Eman64 on 2008-09-22
can someone help a brother out?

---

### Post by Eman64 on 2008-09-29
I'm begging you guys, please help!

---

### Post by Edserman on 2008-09-29
I have tried a few options, I installed a good few players, the one that works and reported in other forums to work is Banshee. However its not that stable, the problem is as you say, the Zen seems to reboot alot, and then settles down. I found using a different USB cable helped, but that just could be sheer luck. I 'll let you I have a more scientific explanation. I'm also looking for a more stable solution. One mind you is using VirtualBox, but be wary of the initial USB issue, which can be easily solved, through a few tweaks of Ubuntu config

---

### Post by Edserman on 2008-09-30
> **Edserman said:**
> I have tried a few options, I installed a good few players, the one that works and reported in other forums to work is Banshee. However its not that stable, the problem is as you say, the Zen seems to reboot alot, and then settles down. I found using a different USB cable helped, but that just could be sheer luck. I 'll let you I have a more scientific explanation. I'm also looking for a more stable solution. One mind you is using VirtualBox, but be wary of the initial USB issue, which can be easily solved, through a few tweaks of Ubuntu config

Well further to this, forget about trying the VirtualBox option for now, as it only partially works, e.g. read is ok, but transfer is not working...

What a pity there doesn't seem to be a good solution, now I'm considering installing a windows XP partition, mounting a NTFS partition...can someone save me from this desperate measure. gnomad2 ain't any good, its very basic, but it seems the most solid solution. Banshee breaks if you transfer too many files...Amarok refuses to see it at all..yes I have installed the mix of libraries suggested by other forums. If ubuntu can't get multi-media right, what hope has it got....

---

### Post by clancymf on 2008-09-30
I have just bought a Creative Zen and having had any issues (at least with mp3s) using gnomad2 as long as you check the box for mtp.  Check to make sure that this option is checked in gnomad2.

Now for videos, I have figured out a way to rip dvds and put them onto the player but I am unable to retain the chapters and I cant fastforward through them.  Not having the chapters isnt a huge deal since I can rip chapter by chapter and load them into a play list, but the inability to fastforward is becoming one

---

### Post by Eman64 on 2008-10-05
> **clancymf said:**
> I have just bought a Creative Zen and having had any issues (at least with mp3s) using gnomad2 as long as you check the box for mtp.  Check to make sure that this option is checked in gnomad2.

Where exactly is this box?

---

### Post by minky311 on 2008-10-06
Does your creative zen have its latest firmware?

---

### Post by Eman64 on 2008-10-11
If I told you no, would you be able to tell me how to update said firmware?
If so, no, I don't think it does.
If not, no, I don't think it does.

---

### Post by Eman64 on 2008-10-13
News Update:
Now libmtp doesn't work at all. I installed libmtp-0.3.3 in the hopes that it would fix my problem. Nope. Not happening. Here's what I get when I try to run either gnomad2 or mtp-detect.

```
user@Computer:~$ gnomad2
gnomad2: error while loading shared libraries: libmtp.so.8: cannot open shared object file: No such file or directory

```

Anyone know what I can do to fix this?

---

### Post by Eman64 on 2008-10-13
Never mind that last post. I fixed the problem by reinstalling libmtp7 from Synaptic.

Now it all works, but still isn't detecting my player. Err, at least Gnomad isn't. Here's my new mtp-detect output:

```
user@Computer:~$ mtp-detect
libmtp version: 0.3.3

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN (041e:4157) @ bus 0, dev 14
Attempting to connect device(s)
PTP: Opening session
PTP: request code 0x1001 sending req wrote only 0 bytes instead of 12
LIBMTP PANIC: Unable to read device information on device 14 on bus 0, trying to continueUnable to open raw device 0
OK.

```

---

### Post by aragorn2909 on 2008-10-14
I had a real hard time getting my Zen recognized properly.  The only thing I could do to get it working 100% was to install libmtp8 from Flavio Martin's PPA

[https://launchpad.net/~xhaker/+archive]("https://launchpad.net/~xhaker/+archive")

---

### Post by TracyO on 2008-10-23
I have an almost three year old Zen Sleek, and it works with Gnomad.  This may be a silly question, but in transferring albums, are you going into the album and selecting the actual files to transfer over or just clicking on the album folder?  You should be doing it through the files, and it will put them in the album on the player.

---

### Post by ubunter1 on 2009-01-07
> **aragorn2909 said:**
> I had a real hard time getting my Zen recognized properly.  The only thing I could do to get it working 100% was to install libmtp8 from Flavio Martin's PPA

[https://launchpad.net/~xhaker/+archive]("https://launchpad.net/~xhaker/+archive")

how do i install the file and which one(ones) is it.thanks.

i cannot get my player to do anything but charge.:(

---

### Post by CK05 on 2009-03-21
I know this is an old topic, but I may as well post here since I've got a Zen issue as well.

(As I've updated to Banshee 1.4.3, I've found the Zen behaving much better for anyone still interested in the original topic)

But the problem I have is that album art is not transferred across to my Zen even though the files are tagged properly. I've used the same files on my windows box and it transfers across...Did you guys have this same issue? 

Album art is important to me, anyone know how to resolve it? 

Many thanks.

---

### Post by ubunter1 on 2009-03-22
i think i may try to install the last version of ubuntu(gutsy) and see if it works as nothing ive tried seems to work and im not that technical, none of my usbs do anything but charge.i will try banshees new version but i tried the last one and no luck.

---

### Post by CK05 on 2009-03-23
libmtp 8 and the new Banshee work perfectly. The only problem is album art doesn't come across even though it is correctly tagged. But hey, it's better than nothing.

---

### Post by granny6989 on 2009-03-27
I didn't see any check box for enabling MTp, unless you were talking about Rhythmbox... Anyways, I have a temporary fix if your problem sounds similar. I am using Jaunty and currently helping with testing. When I plug in my Zen (Vision), it docks and shows it as busy. When I open Gnomad2 (various versions), it says I have no devices available. If I look in the Places menu, it is listed down with disk drives. Open it as if it were a disk. On the left side, there is an option to eject. Click on that once and the Zen 'ejects', you should see your screen free up and the player looks like it's un-docked.

At this point it will work with Gnomad, and probably any other Zen compatible software. It will work everytime as long as it is plugged in, but if I unplug and plug in again, the problem stays, and I have to 'eject' again.

Hopefully this helps

S*

---

### Post by Mempho on 2009-03-30
Granny, thanks. Gnomad was working fine in Intrepid, but Jaunty Beta won't recognize my Creative Zen V Plus, failing with the message "No jukeboxes found on USB bus". Your trick of "ejecting the disk" works for me. Hopefully a real solution will turn up, but a workaround is better than nothing.

---

### Post by BDNiner on 2009-03-30
My Creative Zen works perfectly except for the album covers. It works with Rhythmbox, Amarok, Exaile and Banshee. 

The album covers do get transfered over when using Amarok now. I upgraded to the latest version. But Amarok has a real problem with downloading the proper covers even if i select the correct cover it doesn't update. I have already gone through and done this with Rhythmbox so i don't really want to do it again.

---

### Post by Oasu4g on 2010-02-02
Is there any program that will sync the album covers to my Creative Zen?

---

