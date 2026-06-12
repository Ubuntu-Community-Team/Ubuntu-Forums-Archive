---
title: "First Analog Recording After a Digital one is Corrupt (pchdtv 5500)"
date: 2007-11-01
forum: Mythbuntu
---

### Post by napsilan on 2007-11-01
I'm using a pchdtv 5500 capture card, and I record both digital HD and analog cable.  The first analog recording after a digital one always ends up being snow.  I'm guessing this is because it doesn't switch drivers correctly right away.  Any other analog recordings are fine.  What's also weird is that the corrupt analog recordings are much larger in size than normal ones (2.1gb vs 600mb), similar to an HD program.  However, it's still in SD resolution and mpeg4.  Perhaps the capture card is trying to use HD encoding on the analog signal?  Is there a way to record < 1 second of analog after each digital recording to reset the tuner?

---

### Post by tgm4883 on 2007-11-05
Thats odd.  Is it possible that it is trying to record both analog and digital at the same time?

---

### Post by napsilan on 2007-11-06
Something is off in the recording besides the fact that it's all snow, because the file size of the corrupt analog recording is the size of an HD recording.  I'm almost positive that this happens even when there is a delay in between the shows (i.e. record an HD program from 1-2pm, then nothing from 2-3, then an analog at 3pm will get corrupted).  All other analog recordings and all the digital recordings are fine.  I suspect this is due to switching the driver from DVB to V4L right when it starts trying to record.

---

### Post by napsilan on 2008-03-14
old post I know, but the mythtv wiki was updated with a possible fix
[http://mythtv.org/wiki/index.php/PcHDTV_HD-5500#Other_analog_options](http://mythtv.org/wiki/index.php/PcHDTV_HD-5500#Other_analog_options)

add 
options dvb_core dvb_shutdown_timeout=0
to
/etc/modprobe.d/options

---

