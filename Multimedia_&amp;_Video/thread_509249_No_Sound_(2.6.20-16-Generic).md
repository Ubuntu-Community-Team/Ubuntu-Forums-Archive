---
title: "No Sound (2.6.20-16-Generic)"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by te77y on 2007-07-25
Good Afternoon All,

Made the mistake of tinkering today trying to get 5.1 working and now I have no sound at all!  Hence if any one could shed some light I'd be ever so grateful.

I've been following the instructions from top to bottom here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

And got to the point where it says "Start a new thread, your stuffed" but politer...

Before I paste in the build log results, it's worth pointing out that when I now type in "aplay -l" I have no sound cards listed.  But I do have a CK804 (nforce4) listed when I type "lspci -v".

It's probably also worth pointing out that this is going through the SPDIF out on the machine to an external amp.  Given the sound was working prior to my tinkering (there's a lesson there I'm sure! :)), I know the hardware is all aok.

Any help gratefully received!  Thank you kindly peeps.
______________________________________-

sudo lshw -class sound

*-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: b
       bus info: pci@00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: ioport:b400-b4ff ioport:b800-b8ff iomemory:f7004000-f7004fff irq:12
______________________________________________

cat /proc/asound/

No asound directory...

_______________________________________________

The output I get in the build log (which is a little winded) reads;

---snip---
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[6]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

---

### Post by mohnkern on 2007-07-25
We're testing a theory, so this is by no means a guarantee to an answer by try:

sudo nvidia-xconf


and see if sound  works.

---

