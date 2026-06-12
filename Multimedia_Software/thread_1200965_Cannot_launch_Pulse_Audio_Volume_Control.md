---
title: "Cannot launch Pulse Audio Volume Control"
date: 2009-06-30
forum: Multimedia Software
---

### Post by RD1 on 2009-06-30
Whenever I attempt to launch pavucontrol I get a brief flash of the window that immediately disappears. 

When launched from cli .... ```
rodger@Bodhisattva:~$ pavucontrol
E: shm.c: shm_open() failed: No such file or directory
E: memblock.c: Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.
Aborted

```

Any ideas?

---

### Post by RD1 on 2009-07-01
Anyone?

---

### Post by RD1 on 2009-07-01
Ok, no answers yet but I have found, it is related to Firefox. Pulse Volume Control works fine until I run firefox.

---

### Post by RD1 on 2009-07-01
Installed Opera to try out .... PAVC works fine with opera running.

Anyone willing to help out?

---

### Post by RD1 on 2009-07-01
Hello?

---

### Post by RD1 on 2009-07-02
Good Morning World! Anyone out there?

---

### Post by RD1 on 2009-07-02
Bump in the night....

---

### Post by bear24rw on 2009-07-02
idk what shm is but maybe you can try installing these packages?

libxcb-shm0
libmpich-shmem1.0gf

---

### Post by RD1 on 2009-07-03
libxcb-shm0 is already installed.

libmpich-shmem1.0gf is not installed but, I doubt it has anything to do with this problem.

I can confirm that there is some kind of conflict with Firefox. If Pulse Volume Control is open and Firefox is launched, PVC will crash. PVC cannot then be successfully launched until after logoff. This does not happen when using Opera which, I believe, uses the same plugins as Firefox. 

I have upgraded to Firefox-3.5 with no improvement.

P.S. Thanks for your reply. It didn't resolve the problem but, at least someone is trying. :)

---

### Post by RD1 on 2009-07-10
Bump

---

### Post by TKoorn on 2009-07-20
I have a similar problem but I don't have a problem with firefox. My pavucontrol sometimes starts if firefox is running and sometimes it does what you describe. Can't seem to figure out what causes it to sometimes work.
If it works it is great, I can redirect streams to different hardware.

---

### Post by RD1 on 2009-07-20
At least, I know I'm not alone. :)

---

### Post by wbee on 2009-07-20
RD 1.

I don't know if you have consulted it yet but if not,use the "search" feature to find markbuntu's thread explaining how to set up Pulse Audio correctly.

Also,if you Google "Pulse Audio Documentation",you will get the developer's page. Linking from that,you will find "the perfect setup".

Ubuntu is a labor of love among many volunteers and I say this not be be overly critical,but the Pulse Audio setup  is imperfect.

---

### Post by Mega_Fauna on 2010-01-25
> **RD1 said:**
> Whenever I attempt to launch pavucontrol I get a brief flash of the window that immediately disappears. 

When launched from cli .... ```
rodger@Bodhisattva:~$ pavucontrol
E: shm.c: shm_open() failed: No such file or directory
E: memblock.c: Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.
Aborted

```

Any ideas?


Hi,

I have exactly your problem and having read this thread, I get my stuff to work by closing firefox and using the System Monitor to kill all pulseaudio processes. Then I can restart the *Pulse Audio Device Chooser* and the *Volume Control* window will stay open.

Why I have to reset the damn thing every couple of reboots, I've no idea, could be a Skype thing, could be an Jaunty thing (I just upgraded)....

---

