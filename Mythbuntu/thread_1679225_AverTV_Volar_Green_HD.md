---
title: "AverTV Volar Green HD"
date: 2011-01-31
forum: Mythbuntu
---

### Post by riccardocioria on 2011-01-31
Hello to everyone...
I have buy some days ago a USB DVB receiver AverTV Volar Green HD.
I want to try it on mythbuntu, i follow some instructions (finded by Google) to install driver but i don't understand if the receiver is working or not.
I need your help to know how to configure the receiver if it is possible.

Thanks to everyone.

---

### Post by nhtrader on 2011-02-04
Just a heads up, I have a AverMedia Duet Tuner and I didn't get it to work.

Please be specific in future post regarding hardware and software (include model numbers, software used, which flavor of linux and version, how you installed MythTV)

First let's find out if your system sees your tuner.
enter terminal mode
enter command: lspci -v
scan output for your Tuner Card 
post output to forum

---

### Post by nickrout on 2011-02-04
It's usb, it won't show with lspci. 

More relevant would be lsusb, and the output of dmesg as you plug the device in. 

run ```
 dmesg >dmesgout.pre
lsmod >lsmodout.pre
```

This will save the dmesg buffer, and tell you what modules were present before you plug in.

Then plug the device in and then run ```
dmesg >dmesgout.post
lsmod>lsmodout.post
```

Now ```
diff dmesgout.pre dmesgout.post
```

will show you the result of plugging it in, and diff the lsmodout files to show modules that were loaded.

---

### Post by nhtrader on 2011-02-04
nickrout,

I apologize. Thanks for fixing this.

---

### Post by nickrout on 2011-02-04
no apologies needed :)

---

### Post by axel22 on 2011-02-08
Here's my output for the same card:

```
$ dmesg > dmesgout.pre
$ lsmod > lsmodout.pre
$ dmesg > dmesgout.post
$ lsmod > lsmodout.post
$ diff dmesgout.pre dmesgout.post 
855a856
> [ 6423.873272] usb 1-5: new high speed USB device using ehci_hcd and address 13

```

---

### Post by nickrout on 2011-02-08
> **axel22 said:**
> Here's my output for the same card:

```
$ dmesg > dmesgout.pre
$ lsmod > lsmodout.pre
$ dmesg > dmesgout.post
$ lsmod > lsmodout.post
$ diff dmesgout.pre dmesgout.post 
855a856
> [ 6423.873272] usb 1-5: new high speed USB device using ehci_hcd and address 13

```

how about ```
diff lsmodout.pre lsmodout.post
```

and ```
lsusb
```

are you sure these devices are supposed to work with linux?

---

### Post by axel22 on 2011-02-08
Thanks for your reply!

Nothing in lsmodout, but lsusb finds it:

```

$ diff lsmodout.pre lsmodout.post
$ lsusb
...
Bus 001 Device 013: ID 07ca:a835 AVerMedia Technologies, Inc. 
...

```

> **nickrout said:**
> 
are you sure these devices are supposed to work with linux?

Unfortunately, I do not know.

---

### Post by axel22 on 2011-02-08
> **axel22 said:**
> Unfortunately, I do not know.

But possibly not. Wine didn't detect the card, driver installation failed there. I'd give VMWare a shot, that should work.

---

### Post by nickrout on 2011-02-08
Except you can't run it in vmware if you want your mythbackend to access it!

---

### Post by axel22 on 2011-02-09
> **nickrout said:**
> Except you can't run it in vmware if you want your mythbackend to access it!

True, but at least I can run it through a different OS which accepts the drivers and use Unity to make it seem as if its a local Ubuntu app. :)

---

### Post by tsunglida on 2011-11-16
I have the same problem as you. And I am sure that AverTV Volar Green HD can't be supported to work with Linux. Because I asked Avermedia through the email.

---

