---
title: "Help with bash script to unload ALSA modules"
date: 2011-08-01
forum: Multimedia Software
---

### Post by magicalplug on 2011-08-01
Hi.

I'm using the following bash script to load a null sink and loopbacks on command.

I want to have a separate script that will unload the modules loaded in this script. However, the pacmd unload-module only accepts the index number, not the name. I have no way of knowing what the index numbers will be as they change each time, so I've got stuck writing the script.

Can someone help me write the unload.sh equivalent to this load.sh:

```
#!/bin/bash

pacmd "load-module module-null-sink sink_name=mywiretap"
pacmd "load-module module-loopback source=alsa_output.pci-0000_04_03.0.analog-stereo.monitor sink=mywiretap"
pacmd "load-module module-loopback source=alsa_input.pci-0000_04_03.0.analog-stereo sink=mywiretap"


```

Thank you so much.

---

### Post by aeiah on 2011-08-02
[this page]("https://wiki.archlinux.org/index.php/PulseAudio") gives this example 

```

#!/bin/bash
SINKID=$(pactl list | grep -B 1 "Name: module-jack-sink" | grep Module | sed 's/[^0-9]//g')
SOURCEID=$(pactl list | grep -B 1 "Name: module-jack-source" | grep Module | sed 's/[^0-9]//g')
pactl unload-module $SINKID
pactl unload-module $SOURCEID
sleep 5
```

so if this command works, you can use it to identify the ID:
```

pactl list | grep -B 1 "Name: mywiretap" | grep Module | sed 's/[^0-9]//g'
```

in the same way they have to unload modules.

---

