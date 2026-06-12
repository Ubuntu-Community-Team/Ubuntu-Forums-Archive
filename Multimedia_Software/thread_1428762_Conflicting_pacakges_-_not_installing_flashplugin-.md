---
title: "Conflicting pacakges - not installing flashplugin-installer"
date: 2010-03-13
forum: Multimedia Software
---

### Post by smooth_dudes on 2010-03-13
Hi there.

I am trying to reinstall flash as i had some troubles with flash videos and compiz. I completely removed flashplugin-installer from synaptic but when i then try to reinstall flash from synaptic i get the error showing in the screenshot.

I have tried removing all flashplugin-installer related files but to no avail.
Anyone have a good idea?

I am running 9.10 64bit.

Thanks :)

---

### Post by gradinaruvasile on 2010-03-13
Remove adobe-flashplugin.

---

### Post by smooth_dudes on 2010-03-13
I have no such package installed.

```

sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin

```

---

### Post by lovinglinux on 2010-03-13
Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

> **[COLOR="Sienna"]Note:[/COLOR]** Make sure you use the "Remove" button before doing a new install using that tool.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by smooth_dudes on 2010-03-14
Thank you very much it worked great :)

---

