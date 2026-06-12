---
title: "New computer, SERIOUS wireless problems"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by thezman007 on 2013-08-08
Ok, so I purchased an HP 17-E017CL laptop and after some UEFI issues installed 64 bit Ubuntu 12.04 LTS. I did not expect my wireless to work out of the box as it never has thus far on anything I have owned. I'm used to it. Updating my system did not produce any proprietary drivers I could install or activate. Strange, but whatever. My wireless menu does not offer the option to enable or disable my wireless connection. It's as if it doesn't exist. Following the Ubuntu help tutorial I ran the command 'nm-tool' It didn't show a wireless device. 'sudo lpsci' returns 'command not found' in terminal. It suggests that I need the package 'pciutils'. 'sudo apt-get install pciutils' goes through the motions, but downloads nothing, installs nothing, upgrades nothing, etc. It tells me it's already the latest version. I have not yet found a way to determine my wireless chipset's manufacturer, version, etc. but I am working on it. I am out of my admittedly shallow depth. Can anyone help me? :confused:

Thanks in advance :)

---

### Post by prodigy_ on 2013-08-08
> **thezman007 said:**
> 'sudo lpsci'
It's **sudo lspci**. :) Alternatively you could use ```
sudo lshw -C network
```

---

### Post by thezman007 on 2013-08-08
Well, I feel like a dummy LOL Now I know it's a Ralink 3290. Thanks :)

---

### Post by prodigy_ on 2013-08-08
NP. Here's a [HOWTO](http://ubuntuforums.org/showthread.php?t=2104690) for Ralink 3290.

---

### Post by thezman007 on 2013-08-10
Thanks, I found a usb wifi stick after looking around and am using that at the moment. I will post back when I have used the tutorial and freed up that USB slot :)

---

