---
title: "agnclient libraries"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by skatona on 2011-12-09
I am trying to get the agnclient to work on 11.10  

I think I have some libraries that are not linked.  can anyone tell me how I might be able to link these "not found" libraries?

steve@steve-ThinkPad-W500:/opt/agns/bin$ ldd NetVPN
    linux-gate.so.1 =>  (0xf775a000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf771f000)
    libssl.so.4 => not found
    libcrypto.so.4 => not found
    libdl.so.2 => /lib32/libdl.so.2 (0xf7719000)
    libc.so.6 => /lib32/libc.so.6 (0xf759f000)
    /lib/ld-linux.so.2 (0xf775b000)

Thanks - Steve:confused:

---

### Post by TheNonBornKing on 2011-12-15
You need to download the packages that contain those libraries. As long as the correctly named file resides within the right directory those libraries should be automatically detected. I'm sorry I don't know the specific packages to find.

---

### Post by skatona on 2011-12-17
this is really strange.  it all worked with 10.10.  I did not try it with 11.04.  but now with 11.10 I can't seem to get it to work.  I have tried probably 20 times installing it by following the directions to load up the 32 bit libs, but nothing seems to get these libs to link.  I installed RHEL 6.2 on another hard drive I have and it worked with out a hitch.  problem is that I am not a big fan of red hat.

thanks for the response.

---

