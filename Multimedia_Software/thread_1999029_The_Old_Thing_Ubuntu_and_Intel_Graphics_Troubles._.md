---
title: "The Old Thing: Ubuntu and Intel Graphics Troubles. SUGGESTION! AT LEAST!"
date: 2012-06-07
forum: Multimedia Software
---

### Post by FelixKay on 2012-06-07
Hey Folks!

Always had troubles with my Intel processor and Intel On Board Graphics and Ubuntu.

Now, I found something that works pimping your "Intel Ubuntu" (it works with my computer at least).

Here We Go:

Install an Intel-Friendly Kernel, which is Linux Kernel 3.4.0!

My Specifications:

OS: Ubuntu 12.04 Precise
IMPORTANT - IMPORTANT: Chipset/Graphics: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562]
RAM: 1 GB
Subsystem: Fujitsu Technology Solutions D1521 Mainboard
Kernel driver in use: i915

Crappy Kernel: "3.2.0.24-something"
Good Kernel: "3.4.0-030400-generic-pae"

SOLUTION:

STEP 1
Download Precise Kernel File "[linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb")" from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/"). Be careful to take the right file (LINUX-IMAGE, GENERIC-PPA).

Or get it via terminal by typing  ***cd /tmp && wget -O linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb")*** .

STEP 2
Install it by doubleclicking the deb-file in the corresponding folder or via terminal:

1. Go to folder e. g.***  cd /tmp *** or***  cd*** ***~/Downloads***

2. Install it:  *** sudo apt-get install linux-image-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb***


STEP 3
Then restart.

Enjoy.

This SOLUTION is maybe not so elegant and unprofessional......but.....................
..........................................it seems to work (here).

Yours, Felix

---

