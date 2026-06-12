---
title: "b43-fwcutter help"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Freezing Hot on 2009-01-06
I downloaded b43-fwcutter for my compaq c500 as a .tar.gz file, then extracted it.

Now how do I move the darn file into the firmware folder?

---

### Post by pytheas22 on 2009-01-06
I think you're probably doing more work than you need to.  You should not need to install the b43 firmware from a .tar.gz file.  I know that the linuxwireless.org site tells you to do that, but those are generic instructions for all Linux distributions.  On Ubuntu, you can install the firmware simply by typing:
```

sudo apt-get install b43-fwcutter
```

and it will download and install the files for you into the proper location (provided you have an Internet connection; if you have no way to get online without wireless, let me know).

If this doesn't seem to work, you should make sure that the b43 firmware is applicable to you.  Do you have a Broadcom-based wireless card?  If you're not sure, please post the output of the command:
```

lspci -nn
```

---

### Post by Freezing Hot on 2009-01-06
> **pytheas22 said:**
> I think you're probably doing more work than you need to.  You should not need to install the b43 firmware from a .tar.gz file.  I know that the linuxwireless.org site tells you to do that, but those are generic instructions for all Linux distributions.  On Ubuntu, you can install the firmware simply by typing:
```

sudo apt-get install b43-fwcutter
```

and it will download and install the files for you into the proper location (provided you have an Internet connection; if you have no way to get online without wireless, let me know).

If this doesn't seem to work, you should make sure that the b43 firmware is applicable to you.  Do you have a Broadcom-based wireless card?  If you're not sure, please post the output of the command:
```

lspci -nn
```
I know it's a Broadcom card because I used to run Ubuntu from the live CD, and that is what I downloaded to make it work.

The thing is, I just loaded Ubuntu on that laptop, and I'm at the mall with no wireless on it. I'm using my fiance's Vista laptop to post this. I need to know how to download it on Vista and switch it to Ubuntu, if at all possible.

---

### Post by Ayuthia on 2009-01-06
You might try this link:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

It has instructions on how to download the packages you need to install it without a working internet connection in Ubuntu.

Hope that helps.

---

### Post by Freezing Hot on 2009-01-06
I'm just going to wait until we get home and do it the easy way. Until then, I'll have to use her laptop. :(

---

