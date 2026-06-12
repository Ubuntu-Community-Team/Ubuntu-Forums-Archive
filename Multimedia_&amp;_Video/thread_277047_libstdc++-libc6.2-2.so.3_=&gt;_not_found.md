---
title: "libstdc++-libc6.2-2.so.3 =&gt; not found"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by mateamargo on 2006-10-13
I'm trying to play VQF files in XMMS. I have downloaded the libvqf.so and placed in **/usr/lib/xmms/Input** but I'm unable to see the plugin options inside XMMS preferences.
If I run 
```

ldd libvqf.so

```
trhows me this:
```

linux-gate.so.1 =>  (0xffffe000)
libstdc++-libc6.2-2.so.3 => not found
libm.so.6 => /lib32/libm.so.6 (0x5568f000)
libc.so.6 => /lib32/libc.so.6 (0x556b1000)
/lib/ld-linux.so.2 (0x56555000)

```

How can I install the missing **libstdc++-libc6.2-2.so.3** library in Ubuntu Dapper-Drake?

Thanks

---

### Post by darkultra on 2006-10-30
I have similar problem when I run vncviewer. I have just upgraded to edgy, and i can't find libstdc++-libc6.2-2.so.3 in System - Administration - Synaptic Package Manager.
```

starfleet@zippo:~$ vncviewer
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: canno
t open shared object file: No such file or directory
```

---

### Post by doudy on 2007-03-27
**for darkultra** : 

```
sudo apt-get install libstdc++2.10-glibc2.2 
```

solution from this url : [http://lems.kiskeyix.org/puntoyaparte/index.php?story_id=78](http://lems.kiskeyix.org/puntoyaparte/index.php?story_id=78)

Have a nice day ;) 
doudy

---

