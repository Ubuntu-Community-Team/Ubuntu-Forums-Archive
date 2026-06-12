---
title: "Disk Burning Problem"
date: 2011-11-01
forum: Multimedia Software
---

### Post by agardner791 on 2011-11-01
I have been trying to burn the Windows Developer Preview ISO file so I can install it beside Ubuntu. I have had no luck doing this however because every time I try to burn it says it is successful, however the disk always is blank. I have used K3B as well as Brasero and I have no idea what to do to solve this problem. Please help!

---

### Post by Rodney9 on 2011-11-01
You are burning an image, I presume.
Have you installed [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats") ? although I wouldn't have thought you would have to, just to burn, but worthwhile having anyway.

I would also look at this page for tips and help on burning in Ubuntu

  [https://help.ubuntu.com/community/CdDvd/Burning](https://help.ubuntu.com/community/CdDvd/Burning)

Rodney

---

### Post by enkay009 on 2011-11-01
Can you try mounting the ISO and checking it's contents?

This will establish whether the ISO is corrupt or not. It probably isn't corrupt but it doesn't hurt to double check.

---

### Post by agardner791 on 2011-11-02
Well I was not able to mount the image. All it included was a text file that said this:

"This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification.".

Does this mean I won't be able to burn the image or what because I"m not sure lol

This is getting really irritating didn't realize it would be this hard to burn.

---

### Post by enkay009 on 2011-11-02
Hmm... UDF shouldn't be a problem. I vaguely remember burning one in the past and I don't remember having problems. 

What does it say when you try to get it's file type with **file**? 

```
file myiso.iso
```... where *myiso.iso* is the ISO you're trying to burn.

---

