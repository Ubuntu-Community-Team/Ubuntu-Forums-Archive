---
title: "AMD64 css encryption problem"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by mindless1973 on 2007-09-03
Hi,

It seems that my AMD64 Ubuntu has some problem with css-encrypted DVDs. I am not able to rip them.

After some tries and reading a few forum articles I am now able at least to watch them using totem with xine backend. However, I am not able to watch them in VLC.

Ripping is also not possible. Altough I don't have problems ripping unecrypted DVDs using Acidrip or dvd::rip, but encrypted ones won't work with both of the ripping tools.

I checked my installed libraries, but could not find the libdvdcss or libdvdcss2 package in the AMD64 repository. I only found the libdvdread3 package. However, I don't know if that really is what I need.

any help?

Thanks,

bye
Marcus.

---

### Post by RomeReactor on 2007-09-04
Hi. Please read [this first]("https://help.ubuntu.com/community/RestrictedFormats"). If after reading that you still want libdvdcss2, you need the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

To add the Medibuntu repositories and install the necessary packages, [look here]("http://ubuntuforums.org/showthread.php?p=3300453#post3300453"). Note that the last package in the third command line (w32codecs) is for the 32 bit architecture; if you want to be able to play wmv files in Ubuntu 64 bit, change the last package from **w32codecs** to **w64codecs**.

---

### Post by mindless1973 on 2007-09-04
Thanks!

The missing Medibuntu repository was the problem. After adding it to my software sources, I could install the necessary library and codecs.

Also thanks for the tip with the w64codecs package!

bye
Marcus.

---

