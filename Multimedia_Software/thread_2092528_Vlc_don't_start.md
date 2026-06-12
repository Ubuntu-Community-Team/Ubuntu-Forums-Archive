---
title: "Vlc don't start"
date: 2012-12-08
forum: Multimedia Software
---

### Post by jobam on 2012-12-08
Hi all,

I've a little server amd/celeron with ubuntu 10.04. As server he doesen't have audio hardware.

I've try to install VLC, when I try to open ... nothing happen!!
I download all libraries as possible... nothing the prog doesn't open.


Can some people help me?
Is there alternative progs?

Thx in advance

---

### Post by zombifier25 on 2012-12-08
Launch it, and check the output to see if there are any errors:
```
vlc
```

---

### Post by jobam on 2012-12-08
Thx for your time zombifier25 !

The problem is tha when I launch VLC nothing happen.. no window open .. no erroro message..

I've tried to uninstal and reinstall thru synaptic.. but ..nothing.

The prog is in the the program installed list.. but is like there's no on server

:confused:

---

### Post by andrew.46 on 2012-12-08
Try:

```
vlc -vvv
```

and post the terminal output here...

---

### Post by jobam on 2012-12-08
this is the output:

```
vlc -vvv
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
```

---

### Post by andrew.46 on 2012-12-08
There is a compile-time option to run as root but this usually used with embedded devices:

```

  --enable-run-as-root    allow running VLC as root (default disabled)

```

Any particular reason you are not logging on as an ordinary user?

---

### Post by jobam on 2012-12-08
No reason. Until now, I haven't needed it.

---

### Post by andrew.46 on 2012-12-08
Try as an ordinary user then, there are some pretty heavy security implications for running vlc as root...

---

### Post by jobam on 2012-12-09
I've tried to search the command to pass from root to jobam (user with admin privilege) but I find a lot of confusion.

Can you help me about this prob?

Thx in advance

---

### Post by zombifier25 on 2012-12-09
```
su jobam
```
Still, you should really log in as a normal user. Logging in as root is rather dangerous.

---

### Post by jobam on 2012-12-09
Cannot execute /dev/null: Permission denied

---

### Post by jobam on 2012-12-09
xxxxxx:~# su jobam
Cannot execute /dev/null: Permission denied

---

