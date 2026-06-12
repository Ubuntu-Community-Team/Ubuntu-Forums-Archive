---
title: "e-GeForce 8800 GT drivers won't download in 9.04"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Rlad78 on 2009-04-25
So I just installed Jaunty after I had previously uninstalled 8.04 (forgot the name o.0) and I go to system/administration/Hardware Drivers and two drivers come up just as they did on 8.04.

The only difference is that this time, when I go to download either of the two drivers, the download won't start; it just stays at 0%.

Is there an alternate way to download the drivers?
Or maybe a fix to my problem?

Oh, forgot to mention that my internet connection is working and I've already downloaded all the recommended updates.

---

### Post by inobe on 2009-04-25
are you sure that it's locked at 0% ?

sometimes that can take time due to server lag etc....


how long have you waited ?

---

### Post by Rlad78 on 2009-04-25
> **inobe said:**
> are you sure that it's locked at 0% ?

sometimes that can take time due to server lag etc....


how long have you waited ?

Never mind

Let it run for about 30min and it finally worked.

Guess I'm just impatient...#-o

---

### Post by inobe on 2009-04-25
yeah' the servers are stressed from everyone trying to activate drivers.

hardware drivers utility actually downloads the drivers from a server !

---

### Post by bonissauro on 2009-04-29
It happened to me exacly the way you described, rlad78. But, after apparently install sucessfully the drivers, Ubuntu asked me to reboot the machine. When I did it, after the Ubuntu progress bar end up, the screen became blank with a "No signal" warning, as if there was no conection between CPU and monitor. So, I restarted in safe mode and run that option "try to restore graphic configuration" (or something like it). So, the driver changes were rolled back and I could use my Ubuntu again (without those great graphic features I had in 8.04, but the basics were working, at least).

Does anybody have an idea of what is happening? I have a core 2 duo 2.6,a NVidia Geforce 8800gt and 4gb RAM .

What other information can I give you ?

Almost forgetting, the command "lspci | grep -i nvidia" returns the following:
```

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

```10x everybody in advance and sorry about my terrible english ;)

Bonissauro

---

