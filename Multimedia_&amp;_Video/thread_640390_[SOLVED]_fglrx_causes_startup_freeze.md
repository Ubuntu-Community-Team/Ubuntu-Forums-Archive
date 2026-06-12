---
title: "[SOLVED] fglrx causes startup freeze"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by zxscooby on 2007-12-14
When i try to use fglrx  my computer halts at "running local boot scripts"
my laptop is a Toshiba satellite with ati radeon mobility 7000, I had no problems with it untill
i upgraded to gutsy 7.10. xubuntu
ive found several posts with similar problems but no solution to mine.

---

### Post by zxscooby on 2007-12-15
I decided to use the open-source driver 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I now have direct rendering and my graphics card is functioning as it should.

---

### Post by weblordpepe on 2007-12-15
Do you find its slower? I sure do :(
Im using the restricted one, and while its faster I can't suspend.

---

### Post by acoustibop on 2007-12-15
That's because your card is not supported by any of the fglrx drivers, zxscooby.  I don't think you could have run it under the fglrx driver in Feisty, either.

---

### Post by zxscooby on 2007-12-17
Im quite positive i did , but the motherboard was replaced under warranty so it may be newer.

---

### Post by zxscooby on 2007-12-18
Yes its slow as hell, I can barely watch youtube clips without lag or freeze ups, where before it ran quite well, The problem is i got fglrx working with this card kinda by accident and i dont remember how. 
Where do i find the restricted driver? im not too worried about suspend.

---

### Post by zxscooby on 2007-12-18
> **weblordpepe said:**
> Do you find its slower? I sure do :(
Im using the restricted one, and while its faster I can't suspend.

Yes its slow as hell, I can barely watch youtube clips without lag or freeze ups, where before it ran quite well, The problem is i got fglrx working with this card kinda by accident and i dont remember how.
Where do i find the restricted driver? im not too worried about suspend.

---

### Post by weblordpepe on 2007-12-19
Did you install the ATI driver from the ATI website? If so you'll need to uninstall it before you can proceed with another driver. Its a right slag to uninstall. There's an uninstall script somewhere. You'll have to search for it.

I know what you're describing because I had that problem once. It was because the ATI thing was half installed and the Mesa thing was half installed and it was a mess.

The ATI installer totally screws up the restricted drivers manager.
the restricted driver can be found under System, then Administration, then Restricted Drivers Manager

---

### Post by zxscooby on 2007-12-19
I didnt use the ati one , i did it the ubuntu way from the community docs.
my resticted drivers manager only lists my wireless driver.

---

### Post by acoustibop on 2007-12-19
No, the Restricted Driver Manager wouldn't show an fglrx driver, zxscooby because, as I said, there isn't one that supports your card.

---

