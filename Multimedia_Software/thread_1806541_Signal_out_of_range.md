---
title: "Signal out of range"
date: 2011-07-17
forum: Multimedia Software
---

### Post by Innova on 2011-07-17
I installed edubuntu 11.04 a couple months ago on the kids computer.  Everytime we would boot up, we received the signal out of range during the entire boot sequence.  However once the login screen showed up, we could see the desktop fine.

However, now it will not display anything from the time grub loads it is just Signal out of range.  I even let it sit for about 10 minutes.

I can boot from the live cd fine...but I'm not sure what to change.  

How can I fix this issue from the live cd?

---

### Post by Innova on 2011-07-18
I thought that I could copy the xorg.conf that the live cd uses to the hard drive.  However, there is no xorg.conf in /etc/X11.  I read somewhere that Ubuntu no longer uses this file?

---

### Post by CatKiller on 2011-07-18
> **Innova said:**
> I read somewhere that Ubuntu no longer uses this file?

It uses it if it's there, but it's not there by default.

Your problem's simply that you're using a resolution that your monitor doesn't support. Ctrl-Alt-F1 should get you a command line (hopefully your monitor can do that resolution) that will let you interact with your computer to fix it, at least.

If you post details of your graphics card & monitor and what you've tried so far, someone here might be able to help you fix it.

---

### Post by Innova on 2011-07-18
I tried the Ctrl-Alt-F1, and it doesn't do anything (it does work in the live cd however).

Also Ctrl-Alt-+ and Ctrl-Alt-- doesn't work either.

I am using an nForce 7025 onboard chipset ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813128469](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128469)).

The Monitor is a 15" 1280x1024 LCD.

Everything worked fine when first installed...it just stopped working yesterday.

---

### Post by Innova on 2011-07-19
Sorry, it is a Princeton Graphics 17" LCD Monitor.  Detects correctly in the edubuntu Live.

---

### Post by Innova on 2011-07-19
If I reinstall into the same partition without reformatting, with the /home directory be preserved?

---

### Post by psusi on 2011-07-19
> **Innova said:**
> If I reinstall into the same partition without reformatting, with the /home directory be preserved?

Yes, just make sure you use manual partitioning and uncheck the format box.

---

