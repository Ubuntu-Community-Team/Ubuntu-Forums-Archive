---
title: "Nvidia linux driver installation util.  Can it be used in Ubuntu?"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by circadianhelix on 2006-06-03
Hello, 

hoping someone can point me in the right direction with this.

Can the utility posted at [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html) be used gracefully in Ubuntu?   What i've been led to believe is that copious amounts of terminal entries are required (which isn't necessarily a bad thing) and that its hard to find information straight to the point. 

Basically it says to :   "Type "sh NVIDIA-Linux-x86-1.0-8762-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file."    I then get told in the terminal that it doesn't exist.

At the moment still struggling to find any focal points of learning(linoob), will get there tho.

---

### Post by tseliot on 2006-06-03
Try my guide or my script (for an automatic installation) here:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by meng on 2006-06-03
With Dapper, I had a similar experience trying to install with the .run package from nvidia. Apparently using the package manager to install nvidia-glx achieves the same thing.

---

### Post by circadianhelix on 2006-06-03
cheers people, 
just been going through your guide TS, was hoping on the offchance a more direct method may have come to light. Ill get into it.

Figure ill make this my first project before getting into more 'all round' learning.


* Unfortunately command line 1 of Method 2 when it tries to grab neccessary files from my local (countries) archive times out, is it possible to get them elsewhere somehow?

** Seem to be able to get the files via Synaptic Package Manager,   Could be of some consideration tho. (at least one directory asked for doesn't exist)

---

### Post by Marco Bresciani on 2006-06-04
[QUOTE=tseliot]Try my guide or my script (for an automatic installation) here:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")[/QUOTE]

Used your guide since I was using 5.04 (or 5.10... don't remember). It always worked well. Now I've just downloaded and installed 8762 latest driver and this time I've also tried using this automatic script [http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_8762_32]("http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_8762_32").

Never had problems... but I still saw inveterd colours in videos... It happened after an upgrade... actually don't remember which... :-k 

Any idea?

---

### Post by JoWilly on 2006-06-04
Geez..... installing nvidia-glx with synaptic is so easy.

Apparently you guys like to hack, don't you ;)

---

