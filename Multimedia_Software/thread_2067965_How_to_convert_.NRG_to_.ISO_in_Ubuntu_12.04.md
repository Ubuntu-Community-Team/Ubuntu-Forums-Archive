---
title: "How to convert .NRG to .ISO in Ubuntu 12.04"
date: 2012-10-08
forum: Multimedia Software
---

### Post by myromance123 on 2012-10-08
Hey there,
Hopefully I've posted this in the correct section. Please move this if I have not, apologies in advance.

I have a copy of a disc in .nrg format given to me from a Windows computer. I believe they used Nero to make this file format. What tool/software can I use to convert this .nrg to a .iso file in Ubuntu 12.04?

I wish to be able to mount it, or at least extract its contents to a folder. The archive manager doesn't recognize .nrg, which is why I ask here.

Thanks in advance for any form of help!

---

### Post by westie457 on 2012-10-08
Hello

nrg2iso or iat should work. Both are in the repositories.

---

### Post by myromance123 on 2012-10-08
Thank you very much westie457 for your swift and helpful reply!

nrg2iso did not work, it returned:
```
It seems that tlod-soe.nrg is already an ISO 9660 image
```

However, iat did work.
For anyone who later reads this. Open the Ubuntu Software Center, type in iat and install that package. Then run a terminal, cd to the directory where your .nrg file is.

Once there,
```
iat  input_file [output_file.iso]
```

For my case, the file name was tlod-soe.nrg. So, it was
```
iat tlod-soe.nrg State.iso
```
I named the iso file State.

Now the archive manager is able to extract the .iso, or I can even mount it. I had also tried Format Junkie, but it didn't properly convert the file. 

Thanks once again Westie457 :)

---

### Post by westie457 on 2012-10-08
Sometimes to convert a file you can change the extension. It won't always work and if it does not just change it back.

---

