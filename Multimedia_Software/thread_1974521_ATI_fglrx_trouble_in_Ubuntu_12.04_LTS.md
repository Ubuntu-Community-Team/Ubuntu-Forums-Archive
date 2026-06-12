---
title: "ATI fglrx trouble in Ubuntu 12.04 LTS"
date: 2012-05-06
forum: Multimedia Software
---

### Post by joehothebo on 2012-05-06
Hi everyone,

I have a little problem with the proprietary ATI driver for Ubuntu 12.04 LTS. I tried installing it both using the additional drivers as well as a manual installation both times I ended up in low graphics mode! I managed to get back into the Ubuntu GUI by removing the fglrx packages and resetting the xorg.conf but quite frankly I would really like to know the issue for this problem!
Some informations towards my HW:
Asper Aspire 3820TG
Intel Core i5-480M
AMD Radeon HD 6550M

Thanks a lot in advance and best regards!

Joe

---

### Post by ravb on 2012-05-13
I have the same issue, can anybody help?

---

### Post by Victicom on 2012-05-13
Follow these instructions carefully: 
 
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)  

At some point, you'll have to follow these instructions, too:   

[http://ubuntuforums.org/showthread.php?t=1969827](http://ubuntuforums.org/showthread.php?t=1969827)  

Please read carefully, it should work if you do.  I hope that helps :-)

---

### Post by Yellow Pasque on 2012-05-14
The problem is that you have a hybrid Intel/ATI GPU setup. I don't know the best solution offhand, but just installing fglrx probably isn't going to work.

---

### Post by lukeiamyourfather on 2012-05-14
Assuming the graphics hardware is a hybrid configuration (Intel integrated plus discreet AMD) check the BIOS for an option to use only the discreet graphics. Otherwise the FGLRX driver won't work.

---

### Post by roelforg on 2012-05-14
On my laptop, the post-release fglrx doesn't work (the other one does).
I ran
```

sudo aticonfig --initial=dual-head

```
the first time.
Logged back on.
And it worked.

---

### Post by Victicom on 2012-05-14
Yo,

If you read the links I sent you'll see there's some compatibility issues with fglrx/Catalyst and Kernel 3.2.

You need to install a patch before you build the .deb files, if you're installing manually. I wrote a full blown answer to his question, but this editor does not let me modify my answer for some reason.

Read the links, you'll see what I mean. Let me know if it works (It did for me).

---

