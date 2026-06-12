---
title: "pacmd set-default-sink doesn't work from the first time"
date: 2019-11-05
forum: Multimedia Software
---

### Post by 0x656b694d on 2019-11-05
Hello,

I made a script which allows me to switch audio setup for two use cases: analog stereo for desktop use and 5.1 digital for home theater.

I do two steps in this script:
```

pacmd set-card-profile <card> <profile>
pacmd set-default-sink <sink>
```

I.e. it looks like this:
```

pacmd set-card-profile alsa_card.pci-0000_00_1b.0 output:iec958-ac3-surround-51
pacmd set-default-sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51
...
pacmd set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-stereo
pacmd set-default-sink alsa_output.pci-0000_00_1b.0.analog-stereo
```

This worked fine in Ubuntu 19.04, but in 19.10 I have to set the default sink twice, since it doesn't work from the first try.

What would that be?

Update:
I noticed (looking at paman) that set-default-sink does work from the first time, but then (in a second) gets switched **sometimes** to a wrong sink (digital stereo).

---

### Post by 0x656b694d on 2019-11-05
The issue looks to be in the [Sound Input & Output Device Chooser]("https://extensions.gnome.org/extension/906/sound-output-device-chooser/") gnome extension!
Cannot reproduce the problem after disabling the extension.

---

### Post by nik.charles on 2019-11-10
use pactl commands instead of pacmd
pacmd commands do not work so good in bash script

---

