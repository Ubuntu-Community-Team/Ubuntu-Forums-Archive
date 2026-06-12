---
title: "sound working only one way over home network"
date: 2015-03-29
forum: Multimedia Software
---

### Post by tomaasj on 2015-03-29
Dear Ubuntu people,

configuration

1) home wireless network , ssh
2) laptop A: ubuntu 14.04
3) laptop B: ubuntu 12.04

An interesting problem occurred:

On both laptops I can play audio files using Rhythmbox, mpg123 and nvlc.  No problems.

When I connect from laptop A to laptop B, using ssh, logging in as user of laptop B, I can access the files on laptop B, copy files from laptop A to B etc.  I can activate the audio players on laptop B, from laptop A, and activate the music files on laptop B which then can be heard from laptop B through its own speakers.  So far so good.

I can also connect from laptop B to laptop A using ssh and move files around, copying files from laptop B to laptop A etc., however, when connected to laptop A and logged in, I cannot activate the music files using the mentioned audio applications also installed on laptop A.  Instead I get the following error message:

--

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
exec of JACK server (command = "/usr/bin/jackd") failed: No such file or directory
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[jack.c:252] error: Failed to open jack client: 0x11
[jack.c:58] warning: FIXME: One needs to wait or write some silence here to prevent the last bits of audio to vanish out of the ringbuffer.
Segmentation fault (core dumped)

--

Why should this happen ?  When I am sitting behind laptop A and activate the same audiofile, on laptop A, using the mentioned audio app's, this message does not pop up and the audiofiles behave as expected.

Can anybody help me out ?

Thanks,

Tomaasj

---

### Post by tgalati4 on 2015-03-29
Boot laptop B with a LiveUSB of 14.04 and (while connected with a wire since wireless will probably not work out-of-the-box) install *jackd* and anything else you need to perform your test.  It's probably a framework/security difference between 12.04 and 14.04 involving *ssh* and *jackd* trying to open ports.

---

### Post by tomaasj on 2015-03-29
OK, I'll try to do that.

Thanks,

T

---

### Post by tomaasj on 2015-03-29
> **tgalati4 said:**
> Boot laptop B with a LiveUSB of 14.04 and (while connected with a wire since wireless will probably not work out-of-the-box) install *jackd* and anything else you need to perform your test.  It's probably a framework/security difference between 12.04 and 14.04 involving *ssh* and *jackd* trying to open ports.

Hallo tgalati4,

I did what you recommended and it did solve the issue.  It seems indeed to be an 'incompatibility' between 12.04 and 14.04.

I have to read more about this framework/security difference, since I do not understand it very well.  I am surprised that there is this incompatibility.  I would assume that you should be able to have audio files played across a network involving linux computers.

Although I do not understand the underlying problem, I will designate this thread as solved.

Thanks for your help,

Tomaasj

---

### Post by tomaasj on 2015-03-30
Hallo Ubuntu people,

empirical observation:

another reason why the connection from laptop B to laptop A did not give the desired result could be due to the fact that the ssh command was followed with the -X parameter.

eg.: $ ssh -X user_laptop_A@ip_address

After ommiting this -X parameter, I was able to play music files located on laptop from laptop B.

$ ssh user user_laptop_A@ip_address

T

---

### Post by tgalati4 on 2015-03-30
-X and -Y allow X-Windows (xorg) graphics commands to be sent across the connection.  X-Windows runs in a quasi-root security level since multiple people can be using the graphical environment at the same time.  So, by not using X-forwarding, you are not using the X-authentication framework.  If you dig deep enough you can probably find the difference in security policy.

One expects things to work in linux.  Sometimes they don't.  Using mixed distributions can reveal these issues.

---

