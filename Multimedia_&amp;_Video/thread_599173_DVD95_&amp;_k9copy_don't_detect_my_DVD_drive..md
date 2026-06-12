---
title: "DVD95 &amp; k9copy don't detect my DVD drive."
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Bloodnut on 2007-11-01
I am new to Ubuntu and am trying to use DVD95 & or k9copy but both programs don't detect my DVD drive.How do I get them to detect my DVD drive? The drive is a Pioneer if that helps. Can anyone help as I do not want to use Windows at all if I can avoid it.

---

### Post by pay on 2007-11-01
What permissions does the drive have?```

ls -la /dev/CDROM #(where CDROM is the device for your system, ie hda)
```

---

### Post by Bloodnut on 2007-11-01
None that I know of.How do I find out?

---

### Post by Bloodnut on 2007-11-01
Sorry. Found the permissions and all are read only.

---

### Post by pay on 2007-11-01
Execute ```
ls -la /dev/hda #(or if that doesn't work hdc)

```and if you get something like > brw-rw---- 1 root disk 3, 0 Nov  1 13:33 /dev/hdathen run ```
sudo chmod a+rx /dev/hda
ls -la /dev/hda
```so you get > brwxrwxr-x 1 root disk 3, 0 Nov  1 13:33 /dev/hda

---

### Post by Bloodnut on 2007-11-01
I tried the above but still can't change the permissions to READ & WRITE.

---

### Post by pay on 2007-11-01
Post the output of ```
ls -la /dev/hda #or if thats not your cdrom change it:)
```please

---

### Post by Bloodnut on 2007-11-01
This is the result but as I have two burners I am not sure if this is correct.
brwxrwxr-x 1 root cdrom 22, 0 2007-11-01 16:53 /dev/hdc

---

