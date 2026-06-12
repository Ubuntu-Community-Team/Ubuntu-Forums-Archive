---
title: "Recompile Jaunty's kernel with RT support?"
date: 2010-02-19
forum: Multimedia Software
---

### Post by temcat on 2010-02-19
Hi,

I would like to recompile the latest Jaunty kernel (that is 2.6.28-18 ) with RT support i order to have sufficient time resolution for accurate MIDI playback.

The stock -rt kernel in Jaunty is not suitable for me because my CDMA modem doesn't work, and Jack won't start on boot with it for some reason. Some other custom-built realtime kernel that I found on the Net has the same problems.

Therefore, I need to rebuild the exact same kernel I have now, only with RT support added. Can anyone point me to the relevant instructions - preferably made specifically for Jaunty? I can find the generic custom kernel instructions ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)), but AFAIK the RT system underwent some overhaul recently, so I need to know the exact patches/config options I should apply to the 2.6.28-18 kernel. 

Thanks in advance!

---

