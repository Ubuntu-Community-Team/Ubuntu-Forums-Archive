---
title: "nvideo video-in: rivatv compiling problems"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by cokekola on 2007-04-24
I hesitated where to post this problem, this category won the lottery:-)
I'm trying to capture video with video-in connection in  nvidia display adapter. This should be possible with "rivatv". (Does someone know other methods?)

There are installing instructions at [http://rivatv.sourceforge.net/users.html#install](http://rivatv.sourceforge.net/users.html#install). In my Ubuntu Edgy I got a flood of error messages after 'make'. 'Configure' did not give any errors.  Here are some examples of the messages by 'make'. Any ideas where is the problem? 

Those weird charaters in listing examples are because I use finnish system. Hence that should not cause any errors by itself. 
(By the way, linux-headers-$(uname -r) ja build-essentials are also installed.)

```

/usr/src/rivatv-0.8.5/bttv/tuner.c:1041:26: warning: "KERNEL_VERSION" is not 
defined
/usr/src/rivatv-0.8.5/bttv/tuner.c:1041:40: error: missing binary operator 
before token "("
/usr/src/rivatv-0.8.5/bttv/tuner.c: In function â?~tuner_probeâ?T:
/usr/src/rivatv-0.8.5/bttv/tuner.c:1060: error: â?~I2C_ALGO_BITâ?T 
undeclared (first use in this function)
```

```
/usr/src/rivatv-0.8.5/src/rivatv-driver.c:1004: error: expected â?~)â?T 
before string constant
/usr/src/rivatv-0.8.5/src/rivatv-driver.c:1011: error: expected â?~)â?T 
before string constant
make[2]: *** [/usr/src/rivatv-0.8.5/src/rivatv-driver.o] Virhe 1
make[1]: *** [_module_/usr/src/rivatv-0.8.5/src] Virhe 2
make[1]: Leaving directory "/usr/src/linux-headers-2.6.17-11-generic"
make: *** [all-kbuild] Error 2
```

---

### Post by snherbst on 2007-12-12
have you tried to read this post ?
[http://www.nabble.com/RivaTV-and-Debian-Etch-4.0-to11694920.html](http://www.nabble.com/RivaTV-and-Debian-Etch-4.0-to11694920.html)

---

