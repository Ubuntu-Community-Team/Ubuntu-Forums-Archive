---
title: "Wireless Problems with Broadcom 43xx &amp; Meerkat - FIX"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by eynestyne on 2010-10-24
Like a lot  of people out there, I have a Broadcom WLAN card. The 4311.
For some reason I cannot get it to work with Meerkat.
I tried all the options that are within my technical skills, but with no success.

After lots of googling and reading I concluded that the kernel was at fault.
So, I changed it. Now my WLAN is working perfectly.

Here is what I did.

1. I started off with a new install of Meerkat with all updates installed.

2. Then to here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.24.11-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.24.11-lucid/") and got the 2.6.32.24 kernel.

I downloaded three (3) files
  ```
linux-headers-2.6.32-0206322411_2.6.32-0206322411.201010200905_all
```
  ```
linux-headers-2.6.32-0206322411-generic_2.6.32-0206322411.201010200905_i386
```
  ```
linux-image-2.6.32-0206322411-generic_2.6.32-0206322411.201010200905_i386
```

I found that trying to install the 2nd and 3rd alone produced errors

3. Files were installed using GDebi Package Installer in the sequence listed above (Kubuntu)

4. Restart

5. Using KPackageKit I removed the 2.6.35 kernel (Kubuntu)

6. Restart.

7. Used the Additional Drivers app. to install the STA drivers.

8. Restart.

And thats it. Works Perfect for me.

More info.

My screen did a funky wrap around on my third restart.

Moving things around (open, maximize, minimize, drag, resize, etc) is a bit smoother with 2.6.35.

Kernel 2.6.36 has the some problem as 2.6.35. I tested this before going to 2.6.32 

----------------

Hope this helps someone.. Post back and share if it works for you or you encounter problems

---

