---
title: "multiple cards setup in order to prevent them from moving"
date: 2009-05-07
forum: Mythbuntu
---

### Post by jeremycobert on 2009-05-07
hello guys,
i am having a problem with my capture cards moving from dev/video 0 to 1 ,2 etc. i found this in a post that looks like my same problem, but i have 2 pvr150 cards and 1 pctv5500.

> Might be easier just to edit the "options" file (under /etc/modprobe.d ) and add one line for the PVR 150 along this vein:

options ivtv ivtv_first_minor=1

which should compel the pvr 150 always to load as /dev/video1

Then, after the reboot, set the card to the /dev/video1 in the backend setup, as usual.


i also added this to suppress the pctv's cx8800 driver since i am only using it for the Digital tuner.

> 2. Force suppress the cx8800 driver (so that the /dev/videoX device doesn't appear). In /etc/modprobe.d/blacklist, add the line:

blacklist cx8800


so my question is should i keep the > line options ivtv ivtv_first_minor=1 or change it to something else ? should i add another  rules like this for the second pvr150 ? 

someone said to write a udev , but it looked way beyond my capabilities at this time.

---

### Post by ian dobson on 2009-05-07
Hi,

Have a look here [http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150](http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150) maybe this might help.

Regards
Ian Dobson

---

### Post by jeremycobert on 2009-05-07
> **ian dobson said:**
> Hi,

Have a look here [http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150](http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150) maybe this might help.

Regards
Ian Dobson
thanks Ian, i should hire you on a retainer :P

anyway ,yeah that's where i got my initial information from. and i setup 
options ivtv ivtv_first_minor=1
to assign my first pvr150 card to /dev/video1 but i was wondering if the second card will try to go into /dev/video0 where the pctv5500 card is now or does that rule make any pvr-150 cards start at /dev/video1 and then only go up to /dev/video2 ,3 etc etc.

---

### Post by klc5555 on 2009-05-07
> **jeremycobert said:**
> thanks Ian, i should hire you on a retainer :P

anyway ,yeah that's where i got my initial information from. and i setup 
options ivtv ivtv_first_minor=1
to assign my first pvr150 card to /dev/video1 but i was wondering if the second card will try to go into /dev/video0 where the pctv5500 card is now or does that rule make any pvr-150 cards start at /dev/video1 and then only go up to /dev/video2 ,3 etc etc.

You have the analog tuner of the pchdtv5500 suppressed --it doesn't go anywhere. And its digital tuner does not occupy a /dev/videoX device.

The ivtv howto here [http://ivtvdriver.org/index.php/Howto](http://ivtvdriver.org/index.php/Howto)
is somewhat obsolete, but they also recommend using the udev rules for multiple 150s in a system. While the "options" solution works perfectly for a single 150 combined with other, non-ivtv tuners, users at the mythtv list over at Gossamer Threads point out that the "options" edit will cause problems when you have two or more ivtv devices in the same machine. 

Cheers!

---

### Post by jeremycobert on 2009-05-08
thanks guys, i followed this thread and used kiwi's script
 
[http://ubuntuforums.org/showthread.php?t=753434&highlight=udev+rule](http://ubuntuforums.org/showthread.php?t=753434&highlight=udev+rule)

it seems to have worked. i think that script really needs to be included in a faq or something.

---

