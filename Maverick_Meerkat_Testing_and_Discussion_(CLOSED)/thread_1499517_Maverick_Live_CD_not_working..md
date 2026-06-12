---
title: "Maverick Live CD not working."
date: 2010-06-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-06-02
Hi,

The live cd is not working it hangs up on the Plymouth when its loading.

Thanks.

---

### Post by jppr on 2010-06-02
there is now new version [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by donniezazen on 2010-06-02
> **jppr said:**
> there is now new version [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

Let me try it. Thanks.

---

### Post by jppr on 2010-06-02
> **jppr said:**
> there is now new version [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

broken too...

---

### Post by wilee-nilee on 2010-06-02
The 6-2-2010 version listed seems to be working.

---

### Post by sparker256 on 2010-06-02
> **wilee-nilee said:**
> The 6-2-2010 version listed seems to be working.

I also have the 6-2-2010 version working but the 6-1-2010 version hung with no response from the keyboard. I am using live USB using the Startup Disk Creator.

Bill

---

### Post by jppr on 2010-06-02
Yep, this works :) [http://cdimage.ubuntu.com/daily-live/20100602.2/](http://cdimage.ubuntu.com/daily-live/20100602.2/)

---

### Post by wilee-nilee on 2010-06-02
I know this is the 2nd day of the live cd release, but running on a laptop Dell inspiron 4100 with  a ATI Technologies Inc Radeon Mobility M6 LY ancient card I am using the full extra visual effects and getting a decent screen resolution with lots of choices. This old thing wont run Karmic or Lucid out of the box with other then a 800x600 resolution. Wow is all I can say, as far as usability as I type so far. ;)

---

### Post by wayneericgouin on 2010-06-02
Strange, the current live-cd gave me a vesafb error on startup and refused to boot.

---

### Post by rtalcott on 2010-06-02
Same problem here.... vesafb error on startup and refused to boot on 2 machines.
rt

---

### Post by wayneericgouin on 2010-06-02
I got it to work using the startup disk creator rather than using Unetbootin.

---

### Post by rtalcott on 2010-06-02
Thank YOU **wayneericgouin**!  That helped but I appear not to be hung at the purple screen and 5 dots...can't seem to get to the desktop...
rt

---

### Post by VMC on 2010-06-02
After zsync todays (June2) ISO, I finally got the ISO to boot up. It failed on *Install* but worked on *Try first* then install from desktop. Everything works so far.

Tomorrow should bring the Alpha installs.

---

### Post by Catharsis on 2010-06-02
The 6/1 daily-live has a kernel bug in aufs which produces a Kernel Oops that breaks boot into the live session. This was fixed in the 2.6.34-5.13 kernel, which is in the 6/2 daily-live, so from then on it should boot OK into a live session.

This is the reason why there weren't Desktop ISOs on the tracker yesterday. They're up now with the 6/2 image.

---

### Post by jppr on 2010-06-03
[http://cdimage.ubuntu.com/releases/maverick/alpha-1/](http://cdimage.ubuntu.com/releases/maverick/alpha-1/)

Live-cd is just same like was yesterdays live-cd and alternate is just same which was two days ago...

---

### Post by dhalbert on 2010-06-06
> **wayneericgouin said:**
> I got it to work using the startup disk creator rather than using Unetbootin.
Me, too.

I was unable to get Maverick Alpha 1 netbook to boot from two different USB sticks prepared with unetbootin-471 on Windows.

However, using usb-creator (System->Administration->Startup Disk Creator) worked fine.

The unetbootin attempts failed with errors about "inserting ramzswap" and "inserting vesafb". Unfortunately the errors go by too fast to catch all the details.

---

