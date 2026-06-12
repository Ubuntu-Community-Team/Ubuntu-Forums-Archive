---
title: "Video timing method: USleep with busy wait"
date: 2008-03-02
forum: Mythbuntu
---

### Post by 4dognight on 2008-03-02
Video timing method: USleep with busy wait

I get this in my frontend log each time i switch channels.
Anyone know what this means, and is it a problem?

---

### Post by laga on 2008-03-02
[http://www.mythtv.org/wiki/index.php/Frame_display_timing](http://www.mythtv.org/wiki/index.php/Frame_display_timing)

---

### Post by 4dognight on 2008-03-02
> **laga said:**
> [http://www.mythtv.org/wiki/index.php/Frame_display_timing](http://www.mythtv.org/wiki/index.php/Frame_display_timing)

It doesn't realy explain how to choose between RTC and usleep. I tried using xvmc but it failed, and ended up using usleep.

I thought it might explain my errors about prebuffering pause, but Im still in the dark about those errors.

---

### Post by LarsGa on 2008-04-17
I'll second that.

While the wiki article explains frame timing very well, it does not explain how to tell mythtv which method to use.

---

### Post by laga on 2008-04-17
You can't tell MythTV which method to use. It automagically tries to choose the best method available on your system... In mythbuntu-control-centre in Hardy, there's an option to enable RTC video timing.

---

