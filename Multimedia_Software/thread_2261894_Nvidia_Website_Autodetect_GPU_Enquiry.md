---
title: "Nvidia Website Autodetect GPU Enquiry"
date: 2015-01-21
forum: Multimedia Software
---

### Post by maravingian on 2015-01-21
HI All,

Probably a stupid question but I`d like to know more.

I was checking Nvidia`s website to see if my GeForce GT520 GPU was needing a driver update.  I clicked on "Autodetect my GPU" and it returned an error message advising me to update to Java 8.  I duly did so then rebooted my computer.  This time when I clicked again it was unable to recognise my GPU.  This lead me to thinking that Ubuntu does not allow core access to vital systems, and would therefore deny any attempt at reading my system information.

Would this be correct, or am I doing something wrong?

Any help appreciated.

Cheers

(My driver currently running is NVidia Binary Driver - version 331.113 from nvidia-331 (proprietary, tested), I do see NVidia Binary Driver - version 331.113 from nvidia-331-updates (proprietary). Am I using the right one?)

AMD FX(tm)-6300 Six-Core Processor × 6, 8GB RAM, 64bit Ubuntu

---

### Post by Yellow Pasque on 2015-01-21
What web browser are you using? Does it pass the basic Java test? [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
If it doesn't pass the test, then you probably don't have Java plugin installed or you're using Chrome/chromium, which don't support the Java plugin on Linux anymore.
At any rate, you shouldn't download drivers directly from the Nvidia site...

> version 331.113 from nvidia-331-updates (proprietary). Am I using the right one?)
Well, it supports your card, so it's "right" in that sense. If you insist on running the latest driver (346.35 at the moment), your best bet is to get it from here where it's prepackaged: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by maravingian on 2015-01-23
Thanks Temüjin.  I`ll give it a try

---

### Post by Nutria on 2015-01-23
> **maravingian said:**
> HI All,

Probably a stupid question but I`d like to know more.

I was checking Nvidia`s website to see if my GeForce GT520 GPU was needing a driver update.  I clicked on "Autodetect my GPU"

What's that web address?

I went to [http://www.nvidia.com/download/ScannForce.aspx?lang=en-us](http://www.nvidia.com/download/ScannForce.aspx?lang=en-us) and it just said, "We're sorry, the NVIDIA Smart Scan does not support your system at this time."

---

