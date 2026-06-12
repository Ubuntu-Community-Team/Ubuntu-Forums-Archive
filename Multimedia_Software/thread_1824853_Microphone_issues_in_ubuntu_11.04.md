---
title: "Microphone issues in ubuntu 11.04"
date: 2011-08-14
forum: Multimedia Software
---

### Post by subinthegladiator on 2011-08-14
[SIZE=2]Hi All,

Just bought a new headphone and mic, head phone works perfect. But mic  doesn't works.  I  am using UBUNTU 11.04.[/SIZE] [SIZE=2]

I saw another thread, and tried their suggestion as well, [/SIZE] [SIZE=2]

First what i did is installed the following packages[/SIZE] [SIZE=2]

libao4 libasound2-plugins[/SIZE] [SIZE=2]

Then created a new file in /etc/asound.conf and added the following values[/SIZE] [SIZE=2]

cm.pulse {[/SIZE] [SIZE=2]
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

Then modified /etc/iibao.conf changed default value to pulse[/SIZE] [SIZE=2]

Please let me if you can help me, Thanks in advance.[/SIZE]

---

### Post by subinthegladiator on 2011-08-15
Has anyone faced this issue?

Thanks
Subin

---

