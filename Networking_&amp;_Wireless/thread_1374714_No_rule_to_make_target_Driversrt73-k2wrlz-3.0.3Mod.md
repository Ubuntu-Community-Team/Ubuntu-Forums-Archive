---
title: "No rule to make target Drivers/rt73-k2wrlz-3.0.3/Module"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by canter690 on 2010-01-07
Hi 

Am trying to install the rt73 drivers and am getting the following error message 

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** No rule to make target `Drivers/rt73-k2wrlz-3.0.3/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

Any ideas ?

Thought I had installed the linux headers properly but not sure.

Thanks

---

### Post by Project PWNED on 2010-01-07
I had that same problem yesterday and the TP-Link USB card I had ended up supporting injection out of the box, so I didn't mess with it further. Is this what you're trying to do?

---

### Post by canter690 on 2010-01-08
Yeah but my TPlink doesn't seem to do injection.  Am on 9.10.  

Perhaps I am doing something else wrong - but back to the question at hand .... how do I get the driver to compile ?

---

### Post by chili555 on 2010-01-08
Do you have the package *build-essential* installed? Please do so and try again.

---

### Post by canter690 on 2010-01-09
Yeah. Its installed.  Seems like I have installed just about every header development and linux kernel package as well but am open to more suggestions.

---

### Post by pdc on 2010-01-09
often folks are following a guide to help them install

can you tell us what guide you used please?

I installed the drivers for rt73 for a Dick Smith USB wireless device

I posted what worked for me here

[http://ubuntuforums.org/showthread.php?t=1281183](http://ubuntuforums.org/showthread.php?t=1281183)

is anything here of use to you?

---

### Post by canter690 on 2010-01-09
I used tpark's guide in the following post although I have looked a a few others this is the primary one.

[http://forum.aircrack-ng.org/index.php?topic=1824.255](http://forum.aircrack-ng.org/index.php?topic=1824.255)

I guess the TPlink device should be the same as the Dick Smith device given they are both rt73 based so I will try your instructions and see how they go...

Thanks for all your prompt help so far.

---

### Post by canter690 on 2010-01-09
GOT IT!

Followed these instructions 
[http://ubuntuforums.org/showthread.php?t=1215251](http://ubuntuforums.org/showthread.php?t=1215251)

Think my problem was I was just doing a make in the Module directory.  When I used dkms to load it everything just worked.  Device now injecting.

Thanks for all your help.

---

