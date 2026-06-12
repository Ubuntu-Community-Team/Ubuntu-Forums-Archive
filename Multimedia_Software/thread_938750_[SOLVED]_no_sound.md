---
title: "[SOLVED] no sound"
date: 2008-10-05
forum: Multimedia Software
---

### Post by theozzlives on 2008-10-05
After upgrading my Ubuntu, I have no sound. Ubuntu don't recognize my built in card anymore.I don't know what kind of card it is as it's on the motherboard. I have a Compaq Deskpro C-132104. The sound worked before I don't understand why it don't now. I'm not new to computers but only have a year under my belt with Linux (old DOS guru). Any imput would be appreciated.

---

### Post by glotz on 2008-10-05
Seen this? [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Kevbert on 2008-10-05
Please post the terminal output of
```
lshw -C multimedia
```
Note that this command is case sensitive.

---

### Post by theozzlives on 2008-10-25
> **Kevbert said:**
> Please post the terminal output of
```
lshw -C multimedia
```
Note that this command is case sensitive.

that didn't help but I got the computer in the light and found the chip: ESS AudioDrive E51B69F 6308

---

### Post by Darphas on 2008-10-25
i have the same problem :s

---

### Post by theozzlives on 2008-10-26
after searching the Community DOCs, I found this little command "sudo modprobe snd-es18xx". It worked! My Compaq has sound again.

---

