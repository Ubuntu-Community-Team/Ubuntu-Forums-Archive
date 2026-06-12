---
title: "No sound on my Lenovo laptop"
date: 2008-10-05
forum: Multimedia Software
---

### Post by R2D2! on 2008-10-05
I don't know &#305;f somebody else has had th&#305;s problem, but I can't hear anyth&#305;ng from my Lenovo 3000 N200 laptop. I have d&#305;sabled mute, and tr&#305;ed to &#305;nstall alsa-driver-1.0.17, but w&#305;th an error &#305;n sudo make:
```
  CC [M]  /home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/soc-dapm.o
In file included from /home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: En la función ‘dapm_pop_time_store’:
/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: declaración implícita de la función ‘strict_strtoul’
make[3]: *** [/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/alsa-driver-1.0.17$ 

```

I have kernel 2.6.24-19, and my Ubuntu &#305;s &#305;nstalled IN W&#305;ndows V&#305;sta, w&#305;thout a ded&#305;cated part&#305;t&#305;on.

Any &#305;deas?

—Ilhu&#305;temoc &#948;

---

### Post by Yellow Pasque on 2008-10-06
There is a script to do it for you.
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by martinlall on 2008-10-06
Hi there!

I had same problem. It solves the problem, if you haven't broken anything by installing and uninstalling everything yet:

[http://ubuntuforums.org/showthread.php?p=5290526](http://ubuntuforums.org/showthread.php?p=5290526)

Cheers!

Or, install 8.10 beta,

Works great!

---

### Post by R2D2! on 2008-10-06
> **Temüjin said:**
> There is a script to do it for you.
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

Thanks, now I have sound!

—Ilhu&#305;temoc &#948;

---

