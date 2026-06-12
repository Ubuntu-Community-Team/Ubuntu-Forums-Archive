---
title: "Mobile broadband, where to go?"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by marijke on 2011-03-31
Hi all,

We've just come back to the country and I am looking for mobile broadband on both our laptops. We've talked r to just about every company now and most look at me in a funny way when I mention linux, they never heard of it. So what should i do? Surely there are dongles that I can use. Which company would be best? I like vodafone as I already have my mobile with them.

I got a lenova and dh got an acer.both got the latest linux on it.

Thanks

---

### Post by Megaptera on 2011-03-31
> **marijke said:**
> Hi all, We've just come back to the country ...

Which country?
 In the UK I use "3" mobile broadband with Ubuntu no problems.

---

### Post by patryk77 on 2011-03-31
That is generally dependent on the Hardware, not the supplier.

I use a Huawei E1556 modem and it works fine in 10.10

In 10.04, I had to do [some minor tweaking](http://glog.procrasstination.com/index.php?/archives/18-HowTo-Prevent-Ubuntu-from-mounting-3G-modem-as-CD-ROM.html)

You can look at the [Usb_ModeSwitch page](http://www.draisberghof.de/usb_modeswitch/#hardware), that has some info on Modem support.

---

### Post by marijke on 2011-03-31
Didn't I log into the australian ubuntu forum? I'm sure it said .au when I clicked the link. Using the phone for this, not fun.

So I'd have to make sure the modem will work, which will most likely mean buying one outright, I guess. I doubt the modems supplied will work

---

### Post by patryk77 on 2011-03-31
> **marijke said:**
> I doubt the modems supplied will work

I find your lack of faith disturbing :P

Aside from the tweaking in Ubuntu 10.04, my modem worked out of the box.

If you have a 3G phone that supports thetering, you could possibly use that too; I used my Nokia N900 in Poland which worked flawlessly.

---

### Post by Mayank Bhagat on 2011-04-01
Just create a new connection , you may choose the networks given or choose manual where you just have to input access point name and its done

---

### Post by marijke on 2011-04-01
> **patryk77 said:**
> I find your lack of faith disturbing :P

Aside from the tweaking in Ubuntu 10.04, my modem worked out of the box.

If you have a 3G phone that supports thetering, you could possibly use that too; I used my Nokia N900 in Poland which worked flawlessly.


They only let me tether my phone if I'm on a plan. I'm on prepaid at the moment and you actually get more mb with it. 

But are you saying that it would be safe to buy any modem? There are drivers for all? And how would I get the right driver without internet?

---

### Post by patryk77 on 2011-04-01
> **marijke said:**
> But are you saying that it would be safe to buy any modem? There are drivers for all? And how would I get the right driver without internet?

Maybe not *any* modem, but if you look at the USB_ModeSwitch link I pasted it lists a bunch of them and their status. Any modem listed as working on there is a pretty safe bet.

As for the drivers, that would be the kernel's job, so while it may not recognize ALL modems, a great deal work out of the box with nothing to download.

---

