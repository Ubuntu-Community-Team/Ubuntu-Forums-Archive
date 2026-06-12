---
title: "No sound?"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by malilini on 2007-11-11
I just installed 7.04, but have encountered a problem already.
There is no sound!
I installed the codecs for mp3's, but I've clearly missed something along the way seeing how the computer refuses to play anything and everything.
My sound card can't possibly be fried or broken because I'm running a dual boot, and everything seems fine in the other OS.

Help, please?
Thanks :)

---

### Post by nullfactor on 2007-11-11
malilini -  What type of sound card do you have?  Open a terminal session and type the following command:
```

lspci |more
```

From the output, look for a line similar to:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
```

One thing you might try...  in the terminal, do the following:

```
sudo vi /boot/grub/menu.lst
```

Look for your kernel boot line and add the following to the end:
```

ACPI=off
```

Once that is done, the entire kernel boot line will look like the following:

```
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0dc8a5cf-cf6b-4f53-a839-a8b90511a90e ro quiet splash acpi=off
```

Hope this helps!  It worked for me, anyway.

---

### Post by malilini on 2007-11-11
nullfactor,

I have the same thing you have for lspci
but the method you suggested doesn't seem to work.

Thank you anyways.

---

### Post by nullfactor on 2007-11-11
malilini - Dumb question, but I'll ask anyway... did you reboot after making that change?  I forgot to add that in my reply.

---

### Post by malilini on 2007-11-11
I did, but there is the tiny (far dumber) chance I did it wrong.
Not the rebooting, but the adding to the kernel line.
Would it be a problem for you to walk me through step by step?

Thanks a lot for your effort, really :)

---

