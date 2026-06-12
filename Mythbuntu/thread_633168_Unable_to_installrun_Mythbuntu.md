---
title: "Unable to install/run Mythbuntu"
date: 2007-12-06
forum: Mythbuntu
---

### Post by jack-100 on 2007-12-06
Okay, bit of background to this one..here goes -

I recently got a Dell SX270 ([http://www.dell.com/downloads/us/products/optix/sx270_spec.pdf](http://www.dell.com/downloads/us/products/optix/sx270_spec.pdf)) and am planning on using it as a media center pc sort of thing deciding MythTV would be the best.

Now ive not used Linux before but am pretty confident with computers, i downloaded Mythbuntu as the PC was formatted already and thought this would be the easiest option

When booting from the disc if i try to 'install or run Mythbuntu' it will show the Mythbuntu splash screen then when it loads it properly the monitor stops receiving signal. However it does sound like its working properly but just not outputting video.

I decided to boot it up in safe graphics mode instead, it then comes up with the message saying it needs configuring. Im pretty sure the driver to use is the Intel Integrated drivers (865g chipset). 
When i chose this and tested it came up with the message saying it will revert to the other settings in 15 seconds, keep or revert settings. Obviously as i could see the message i selected to keep settings. However the background at the time looked like TV static, not sure if its meant to be like that.

Anyways once it returns im guessing it tries to load Mythbuntu where it gets to the screen stating 'Starting lird daemon:' then lists about 4 processes which are all [OK]. The last one being running local boot scripts which is also [OK], however it just sits there and doesnt load any further.

Anyone know where im going wrong?
Ive probably left out some details so feel free to ask any questions

Thanks,
Jack

---

### Post by twkisner on 2007-12-06
[http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2](http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2)

For a Thinkpad, but it might help?

---

### Post by jack-100 on 2007-12-06
That went straight over my head, like i said ive never used linux before
However i did manage to get it working in the end, had to use the startx command and it got it working (read it in another thread)

Now next question is this - I have 2 x 500gb External USB hard drives which both already have aload of videos (mainly avi's) on. I was wondering if i could plug these into the PC and watch them through Mythbuntu? And if so, how?

Cheers

---

### Post by twkisner on 2007-12-06
> **jack-100 said:**
> Now next question is this - I have 2 x 500gb External USB hard drives which both already have aload of videos (mainly avi's) on. I was wondering if i could plug these into the PC and watch them through Mythbuntu? And if so, how?

Cheers


Yes-

1. Make sure you have the propretary codecs installed in the Mythbuntu Control Panel

2. You will probably have to mount the drives manually (since they were not plugged in when you installed)

Something like:

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1

3. You'll have to goto Video setup on the mythtv setup and put in /mnt/sda1 as the storage directory for your videos.

---

### Post by jack-100 on 2007-12-07
okay i managed to make the directory. Im assuming im supposed to mount the external hdd to that directory or something? (or so it looks like) Im not sure what /dev/sda1 is supposed to be referring to
The hard drive is mounted as /media/Storage_

I havent got the second plugged in yet as want to get it working with one first

When i try what you suggested MythTV says its unable to create a test file in that directory as its not writable

---

### Post by jack-100 on 2007-12-09
Anyone?

---

### Post by superm1 on 2007-12-09
You will need to set permissions on the drive appropriately.

```
sudo chown mythtv:mythtv /media/Storage
```

---

### Post by jack-100 on 2007-12-10
Right, ive tried everything people have suggested and still cant get anything to show in the Watch Videos section.

Just to make sure im doing the rest right, what bit do people specify the location of video files in?
Also do they have to be in any structure? Like can they be in folders within folders etc..

Ta

---

### Post by jack-100 on 2007-12-16
bump

---

### Post by jack-100 on 2007-12-21
to the top...

---

