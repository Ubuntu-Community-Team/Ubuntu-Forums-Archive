---
title: "Can't Open JPG - Error interpreting JPEG image file"
date: 2014-12-03
forum: Multimedia Software
---

### Post by zhogan85 on 2014-12-03
My wife recently backed up her work computer to an external hard drive, but when I plug it in to my Ubuntu machine, I cannot open any of the jpgs and instead get the below error.

"Error interpreting JPEG image file (Not a JPEG file: starts with 0x53 0x61)"

Using the "file" command on the affected files, they are of type data. Is there anyway to open/repair these files?

I appreciate any help, we really want to get some of these photos back. Thanks

---

### Post by carl4926 on 2014-12-03
Backed up with what?
Not some cruddy camera software? What OS was used?

---

### Post by zhogan85 on 2014-12-04
The files were just copied from a Windows directory to an external hard drive manually (drag and dropped). All the other files she transferred are fine, only the jpgs seem affected.

---

### Post by carl4926 on 2014-12-04
And so are the originals gone?
Can windows open the files?

---

### Post by zhogan85 on 2014-12-04
The originals are gone yes, and windows can't open them either.

---

### Post by carl4926 on 2014-12-04
Is the file extension correct
Copy one to another location to fiddle with it, rename it etc...

---

### Post by zhogan85 on 2014-12-04
I've tried copying the files to a local copy and changing the extensions to various file types with no success. I still get variants of the initial error.

---

### Post by carl4926 on 2014-12-04
It's possible these files are corrupt due to the external device being removed incorrectly, by that I mean either before the transfer was entirely complete or the device was not safely removed.
Honestly, I'm grabbing at straws, since I never had a problem like this, least not since I dumped windows completely (must be 10yrs now).

I would try scandisk on the HDD from windows, just because. And be sure to always safely remove.

---

### Post by zhogan85 on 2014-12-04
I ran scandisk on the HDD and still get the same errors. The hard drive was safely removed initially, and all of the other files that were transferred are fine, its only the jpgs that are corrupted/having an issue. Any other ideas?

---

### Post by ajgreeny on 2014-12-04
I have occasionally seen similar files that will not open in, for example, gthumb or eog image viewer, but I have managed to open them in gimp, resave them, and they were then OK in any other application.

I have no idea why the original files were corrupt nor why gimp could open them.when other applications could not.

---

### Post by steeldriver on 2014-12-04
Have you tried looking at the first few bytes of the file to see if there's any recognisable header / exif info ? something like 

```

xxd -l 64 *somefile.jpg*

```

It might give a clue as to what happened

---

### Post by zhogan85 on 2014-12-04
Thanks ajgreeny, I had tried that too, but unfortunately no luck.

steedriver, I think you're on to something. It looks like they're encrypted with sophos. There are several rows of 4 digit numbers, with the following text to the far right.

SafeGuard FileEn
cryption..Copyri
ght 1998-2012 So
phos Group. All 
rights reserved.
 SafeGuard is a 
registered trade
mark of Sophos G

Do you know of a good way to decrypt this on Ubuntu? I have the password they were encrpyted with but don't have Sophos on this computer.

---

### Post by carl4926 on 2014-12-05
> **zhogan85 said:**
> Thanks ajgreeny, I had tried that too, but unfortunately no luck.

steedriver, I think you're on to something. It looks like they're encrypted with sophos. There are several rows of 4 digit numbers, with the following text to the far right.

SafeGuard FileEn
cryption..Copyri
ght 1998-2012 So
phos Group. All 
rights reserved.
 SafeGuard is a 
registered trade
mark of Sophos G

Do you know of a good way to decrypt this on Ubuntu? I have the password they were encrpyted with but don't have Sophos on this computer.

Why didn't you say they had been encrypted?

My suggestion is to ask Sophos

---

