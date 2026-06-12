---
title: "[SOLVED] No sound in Gutsy"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by TaoBoogie on 2007-12-28
Hello
I have had this problem once before on the same machine with Feisty but I managed to fix that problem with some wonderful help. [This is that thread]("http://ubuntuforums.org/showthread.php?t=518695") I've followed the same steps as far as I see but I still have no sound. I have checked the mute switches.
> tao@tao-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
tao@tao-desktop:~$ lspci | grep -i audio
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
tao@tao-desktop:~$ 
I have downloaded and installed the latest ALSA drivers, utils, tool and library, and *I think* all went well.

Thanks

---

### Post by TaoBoogie on 2007-12-30
For the record:
I completed another install of all things ALSA then I ran > alsamixer and turned **all** sliders up to max.
We now have sound :D

---

