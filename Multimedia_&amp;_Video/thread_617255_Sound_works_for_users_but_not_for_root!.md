---
title: "Sound works for users but not for root!"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by Zill on 2007-11-19
Kubuntu Dapper - All sound, including the k3b "fanfare", works fine for normal users.

However, when running sudo k3b to burn root backup archives, no sound is heard.

I have added root to the audio group in /etc/group but still no success.  Any other ideas please?

---

### Post by Qwerty_ on 2007-11-19
Why do you need sound on your root account?

---

### Post by Zill on 2007-11-19
Qwerty_:  I backup data with root permissions 700 to a separate partition.  I therefore must run sudo k3b to burn these files to disk.  k3b normally gives a useful "fanfare" to announce that the burn is completed but this does not work on my system when k3b is run as su.

---

### Post by Zill on 2007-11-19
This problem does seem to be specific to k3b.  I can play a wav file as su with the following cli command:
```
sudo play foo.wav
```

---

