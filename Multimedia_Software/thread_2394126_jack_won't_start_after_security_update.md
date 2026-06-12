---
title: "jack won't start after security update"
date: 2018-06-12
forum: Multimedia Software
---

### Post by babag on 2018-06-12
updated just now as per the notification i got. tried to run qjackctl after the update and jack won't start. what gives?

here's the info from "Messages/Status - JACK Audio Connection Kit:

```
15:56:24.044 Statistics reset.
15:56:24.094 ALSA connection change.
15:56:24.393 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
15:56:24.470 ALSA connection graph change.
```

thanks for any suggestions,
babag

---

### Post by babag on 2018-06-14
i guess this is a little out of the ordinary so no responses. anyway, for the next oddball with this problem, i found the cause and solution.

i have a firewire device for my studio which requires blacklisting the snd_dice driver in /lib/modprobe.d. when the system updated and installed a new kernel, it must have created a new blacklist file which, of course, did not have my modification (adding the line "blacklist snd_dice"). adding that line in got things back to normal.

thanks,
babag

---

