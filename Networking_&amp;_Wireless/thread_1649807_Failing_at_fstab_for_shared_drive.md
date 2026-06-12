---
title: "Failing at fstab for shared drive"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by anti-l33t on 2010-12-20
I suck at life, but I'm working on it.

I have an external HD attached to my desktop and setup as a shared resource.  I want to be able to access it from my laptop as well.  After much trying and drinking, I ended up with this in fstab:

> //crackbox/seagate /seagate -o

I'm not sure why that worked, but it did for a couple of weeks and then began giving me an error about not recognizing the file system type.  I've been reading everything I can find and trying to get it to work, and have come up with very little.  My fstab now contains this line instead of the above:

> //crackbox/seagate /seagate cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

Now, when I reload fstab with "sudo mount -a", I get this output:

> mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I feel like I'm missing something easy here.  Can anyone help me out?

---

### Post by anti-l33t on 2010-12-21
Anybody?  I've been playing around with different syntax options, but I'm no closer to a solution.  I'm wondering if my fstab input isn't the problem after all, but I'm still not sure where to look.

---

### Post by anti-l33t on 2010-12-24
So no ideas?  I don't know what else to try.

---

### Post by anti-l33t on 2011-01-07
I've officially run out of ideas.  Anyone out there?

---

### Post by PatchesTheCaveman on 2011-01-07
Run ```
sudo mount -a
``` again to reproduce that error.

Then run ```
tail -f /var/log/messages
```

You should see an error from mount.cifs.  Copy and paste it to a reply to this thread if you cannot fix it on your own.

---

### Post by anti-l33t on 2011-01-07
> **PatchesTheCaveman said:**
> Run ```
sudo mount -a
``` again to reproduce that error.

Then run ```
tail -f /var/log/messages
```

You should see an error from mount.cifs.  Copy and paste it to a reply to this thread if you cannot fix it on your own.

```
sudo mount -a
``` produces this: ```
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

```
tail -f /var/log/messages
``` gives me these items that I think are of interest.  There's more stuff, but it's not from CIFS, so I'm guessing it isn't what you want.

```
Jan  7 19:21:13 Cracktop kernel: [639667.021667] CIFS: Unknown mount option codepage
Jan  7 19:21:13 Cracktop kernel: [639667.021676] CIFS: Unknown mount option unicode
```

Thanks for your help.  I'm still learning this stuff.

---

### Post by PatchesTheCaveman on 2011-01-07
Remove ```
,codepage=unicode,unicode
``` from your fstab so it just reads:
```
//crackbox/seagate /seagate cifs guest,uid=1000,iocharset=utf8 0 0
```

Then try it again.

---

### Post by anti-l33t on 2011-01-07
> **PatchesTheCaveman said:**
> Remove ```
,codepage=unicode,unicode
``` from your fstab so it just reads:
```
//crackbox/seagate /seagate cifs guest,uid=1000,iocharset=utf8 0 0
```

Then try it again.

I made the change, but I get exactly the same error.

```
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by PatchesTheCaveman on 2011-01-08
What does ```
cat /var/log/messages | grep -i cifs
``` say?

---

### Post by anti-l33t on 2011-01-08
> **PatchesTheCaveman said:**
> What does ```
cat /var/log/messages | grep -i cifs
``` say?

Jan  3 19:11:26 Cracktop kernel: [330656.790141] CIFS: Unknown mount option codepage
Jan  3 19:11:26 Cracktop kernel: [330656.790150] CIFS: Unknown mount option unicode
Jan  4 18:34:01 Cracktop kernel: [377635.527874] CIFS: Unknown mount option codepage
Jan  4 18:34:01 Cracktop kernel: [377635.527883] CIFS: Unknown mount option unicode
Jan  7 19:21:13 Cracktop kernel: [639667.021667] CIFS: Unknown mount option codepage
Jan  7 19:21:13 Cracktop kernel: [639667.021676] CIFS: Unknown mount option unicode
Jan  7 20:01:11 Cracktop kernel: [642064.476151] CIFS: Unknown mount option codepage
Jan  7 20:01:11 Cracktop kernel: [642064.476157] CIFS: Unknown mount option unicode

---

