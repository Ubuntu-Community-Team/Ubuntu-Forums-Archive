---
title: "make unload on v41-dvb error"
date: 2010-06-15
forum: Multimedia Software
---

### Post by BenTheN00bie on 2010-06-15
I am trying to execute the make unload command on the v41-dvb cx18 driver and I am getting this error.  (Ubuntu 10.4)

/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by cs5345,tuner,cx18,cx2341x
/sbin/rmmod videodev
ERROR: Module videodev is in use by cs5345,tuner,cx18,v4l2_common
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple is in use
/sbin/rmmod s5h1409
ERROR: Module s5h1409 is in use
/sbin/rmmod tuner_types
ERROR: Module tuner_types is in use by tuner_simple
/sbin/rmmod tda9887
ERROR: Module tda9887 is in use
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod dvb_core
ERROR: Module dvb_core is in use by cx18
/sbin/rmmod mxl5005s
ERROR: Module mxl5005s is in use
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by cx18
/sbin/rmmod tuner_types
ERROR: Module tuner_types is in use by tuner_simple
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple is in use
/sbin/rmmod tda9887
ERROR: Module tda9887 is in use
/sbin/rmmod cx18_alsa
ERROR: Module cx18_alsa is in use
/sbin/rmmod cx18
ERROR: Module cx18 is in use by cx18_alsa
/sbin/rmmod tuner
ERROR: Module tuner is in use
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by cx18
/sbin/rmmod cs5345
ERROR: Module cs5345 is in use
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by cs5345,tuner,cx18,cx2341x
/sbin/rmmod videodev
ERROR: Module videodev is in use by cs5345,tuner,cx18,v4l2_common
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple is in use
/sbin/rmmod s5h1409
ERROR: Module s5h1409 is in use
/sbin/rmmod tuner_types
ERROR: Module tuner_types is in use by tuner_simple
/sbin/rmmod tda9887
ERROR: Module tda9887 is in use
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod dvb_core
ERROR: Module dvb_core is in use by cx18
/sbin/rmmod mxl5005s
ERROR: Module mxl5005s is in use
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by cx18
Couldn't unload: tveeprom mxl5005s dvb_core v4l1_compat tda9887 tuner_types s5h1409 tuner_simple videodev v4l2_common cs5345 cx2341x tuner cx18 cx18_alsa tda9887 tuner_simple tuner_types

---

