---
title: "where is pppoat.so?"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by kr0n1x on 2006-05-07
hello, i've installed ubuntu 5.10 yesterday!
i have this modem: fastrate usb 100; i have read this guide for install it: [http://wiki.ubuntu-it.org/FastrateUSB100](http://wiki.ubuntu-it.org/FastrateUSB100)
i can't install "bewan_adsl_status" because i haven't the correct packages...but this is only a tool! is nonessential.
note: in the guide...the first three packages are:
gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
cpp-3.4_3.4.4-6ubuntu8_i386.deb
gcc-3.4_3.4.4-6ubuntu8_i386.deb

i have downloaded that:
gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

in all packages...there is ".1" next "ubuntu8"...is a problem?

now...the modem works perfectly...the red light is ever on.
but, when i write: pppd call alice, the shell show me this error:
```
pasquale@ubuntu:~$ pppd call alice
pppd: /usr/lib/pppd/2.4.3/pppoat.so: cannot open shared object file: No Such file or directory
pppd: Couldn't load plugin /usr/lib/pppd/2.4.3/pppoat.so
pasquale@ubuntu:~$
```

in the directory i have found this file (nearly equal): pppoatm.so

why i have the error?:( where is the file???
thanks for help!
ps: i'm italian, i can't speak a good english. sorry!

---

### Post by mips on 2006-05-07
I dunno but going to take a shot at it and say it's calling a incorrectly named file.
The .1 is just a slightly newer version but should be ok.

```
sudo gedit /etc/ppp/peers/alice
```

Look for the line that reads:
```
plugin /usr/lib/pppd/2.4.3/pppoat.so 8.35
```

and change it to:
```
plugin /usr/lib/pppd/2.4.3/pppoatm.so 8.35
```


I'm assuming you made a copy and paste error, or so i hope.

---

### Post by kr0n1x on 2006-05-07
[QUOTE=mips]I dunno but going to take a shot at it and say it's calling a incorrectly named file.
The .1 is just a slightly newer version but should be ok.

```
sudo gedit /etc/ppp/peers/alice
```

Look for the line that reads:
```
plugin /usr/lib/pppd/2.4.3/pppoat.so 8.35
```

and change it to:
```
plugin /usr/lib/pppd/2.4.3/pppoatm.so 8.35
```


I'm assuming you made a copy and paste error, or so i hope.[/QUOTE]

i have resolved the problem thanks to my friends in chat.
the problems is this!!! that line:)
thanks also you!
very good support;) bye

---

