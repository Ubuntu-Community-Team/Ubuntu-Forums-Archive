---
title: "Screen tearing curse = no cure?"
date: 2011-09-30
forum: Multimedia Software
---

### Post by Pasta on 2011-09-30
Hi

I´ve used Ubuntu 10.04 10.10 11.04 all of them in both 32 & 64bit and tried Kubuntu and Xubuntu as well.
Even tried alot of other distros to on my laptops.
A constant issue is screen tearing for me.
I´ve tried the standard video player in gnome and VLC, mplayer.
Nothing ever works for me.
I´ve tried alot of differnt settings with compiz and playback options in vlc but no luck.
I´ve also tried with bumblebee on computer 2 but no luck either.
I´ve tried both proprietary and open-source drivers.
Ubuntu restricted extras has been tried as well.
Formats that i have problems with is divx, mkv, mpeg.

Computer 1;
Acer Extensa, Intel Core 2 Duo 1,66Ghz, 4Gb RAM 667Mhz, ATI Radeon 2400XT 256Mb.

Computer 2;
Intel Core i5 2410m (Sandy Bridge), 4Gb RAM 1333Mhz, nVIDIA GT540m 1Gb + Crucial m4 SSD.

Any help is very welcome, i´m trying to use the standard Ubuntu (Unity) as my default desktop but with the problems i do test alot of distros...

Thanks,
/Gustav

---

### Post by aeiah on 2011-09-30
there are options for 'sync to vblank' and other sync settings in nvidia-settings. stops tearing for me. i dont know about ati but i imagine its similar. Also, you should probably test it with compiz off first as there might be separate compiz related issues

---

### Post by Pasta on 2011-09-30
> **aeiah said:**
> there are options for 'sync to vblank' and other sync settings in nvidia-settings. stops tearing for me. i dont know about ati but i imagine its similar. Also, you should probably test it with compiz off first as there might be separate compiz related issues


I´ve already tried turning compiz off but it hasn´t worked.
Not sure if i can find the "sync to vblank" settings

---

### Post by papibe on 2011-09-30
> **Pasta said:**
> Not sure if i can find the "sync to vblank" settings
Open 'Nvidia X Server Configuration'.

From the right list select 'X Server XVideo Settings', then on the left is the field 'Sync to VBlank'.

Then rrom the right list select 'OpenGL Settings', then on the left will be another  field called 'Sync to VBlank'.

Hope that helps,
Regards.

---

### Post by Pasta on 2011-10-01
> **papibe said:**
> Open 'Nvidia X Server Configuration'.

From the right list select 'X Server XVideo Settings', then on the left is the field 'Sync to VBlank'.

Then rrom the right list select 'OpenGL Settings', then on the left will be another  field called 'Sync to VBlank'.

Hope that helps,
Regards.


Thanks but i can't seem to find it in Unity (Ubuntu 11.04 64bit)
I just installed bumblebee and i can now run Unity and 1080p movies on youtube in fullscreen without any screen tearing what so ever :)
Gonna do some more testing before i declare the problem solved but it seems solved :)

---

### Post by Pasta on 2011-10-06
> **Pasta said:**
> Thanks but i can't seem to find it in Unity (Ubuntu 11.04 64bit)
I just installed bumblebee and i can now run Unity and 1080p movies on youtube in fullscreen without any screen tearing what so ever :)
Gonna do some more testing before i declare the problem solved but it seems solved :)


Bumblebee didn't solve it unfortunately, some action clips later on and there was tearing, not as bad as before.
When i enter the nvidia settings is always sais that "it seems like you're not using nvidia card" ...
Seems like this optimus technology can't switch between graphic cards yet maybet?

---

