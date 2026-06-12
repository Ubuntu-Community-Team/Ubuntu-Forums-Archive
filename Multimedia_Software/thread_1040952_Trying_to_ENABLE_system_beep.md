---
title: "Trying to ENABLE system beep"
date: 2009-01-16
forum: Multimedia Software
---

### Post by Masterofpsi on 2009-01-16
I know everyone hates the internal speaker's beep, but I would at least like the option to use it. No matter what I try, I can't seem to get to it.

```

echo -e '\a'

```

does nothing; neither does

```

beep

```.

I know that the bell itself works; when I still had Vista, it would beep whenever the battery was low, and it still beeps when I turn it on.

I un-blacklisted snd_pcsp in /etc/modprobe.d/blacklist, and have sudo modprobe'd it, but still nothing. Furthermore, when I try to modprobe pcspkr, I actually *can't*: I don't get an error message, but after modprobing it, lsmod doesn't show it.

My computer is a Toshiba Satellite A110. Does anyone know what the problem is?

---

### Post by alter1 on 2009-11-06
Same problem here (but no solution
[http://ubuntuforums.org/showthread.php?p=8238852](http://ubuntuforums.org/showthread.php?p=8238852)

---

### Post by Gustavo86 on 2010-01-13
The system beep sound is blacklisted in Ubuntu 9.10 Karmik Koala.

 You need to enable it manually with this command:

```
sudo modprobe pcspkr
```

But you need to do this everytime you startup Ubuntu 9.10

---

### Post by benerivo on 2010-01-13
> **Gustavo86 said:**
> The system beep sound is blacklisted in Ubuntu 9.10 Karmik Koala.

 You need to enable it manually with this command:

```
sudo modprobe pcspkr
```

But you need to do this everytime you startup Ubuntu 9.10

If the above works then you can edit a system file so that pcspkr works automatically on every boot. If you do...```
gksudo gedit /etc/modprobe.d/blacklist.conf
```then you can scroll to the end of this file and you will see a line which reads 'blacklist pcspkr'. Just remove this line, and save the file, and reboot.

---

### Post by Gustavo86 on 2010-03-11
It didn't work for me open **/etc/modprobe.d/blacklist.conf**, erase **"blacklist pcspkr"** and reboot my computer.

The only way that worked for me was with ```
sudo modprobe pcspkr
``` but you **don't have **to erase **"blacklist pcspkr"** in **blacklist.conf**, if you do, it won't work (weird, but true)

You can put **modprobe pcspkr** in **/etc/rc.local** before **"exit 0"** to start it every time your Ubuntu boot.

I hope this help.

PS: This in Ubuntu 9.10 Karmic Koala

---

