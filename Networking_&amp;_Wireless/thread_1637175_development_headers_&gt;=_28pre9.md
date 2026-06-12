---
title: "development headers &gt;= 28pre9"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by nikkae on 2010-12-04
Does any one know:

How to check if 'development headers >= 28pre9' are installed?;

if 'development headers >= 28pre9' are installed, how can I make them functional?

---

### Post by chili555 on 2010-12-04
I am guessing a bit here because without examining the file you are working with or trying to compile, I assume, it's impossible to know for sure.

Frequently, it means the kernel headers matching your running kernel. In Ubuntu-speak, that means linux-headers-`uname -r`. Simply open up System > Administration > Synaptic and search for linux-headers-generic and install it and it's dependencies.

The >= 28pre9 part means for a kernel version of 2.6.28pre9 or newer. If you are running a recent version of Ubuntu, you have a much newer kernel.> how can I make them functional?If you are compiling a package, the Makefile will do all the work for you.

If you need further guidance, post back and we'll be happy to help you.

---

### Post by nikkae on 2010-12-04
I don't believe its impossible to find out if 'development headers >= 28pre9' are installed because I have access to every file on the file system, therefore I must be able to check.

'linux-headers-generic' is already installed on the computer in which I am experiencing this issue with.

> The >= 28pre9 part means for a kernel version of 2.6.28pre9 or newer

You would think the developer of this application I am compiling would specify that. I did a search on google.com for the term 'development headers' and couldn't find a definition of it.

I can't use a make file because I must first './configure', which is where this issue is occuring.

I am trying to compile and install NetworkerManager 0.8.2.

---

### Post by chili555 on 2010-12-04
> I don't believe its impossible to find out if 'development headers >= 28pre9' are installed because I have access to every file on the file system, therefore I must be able to check.I don't believe I said or implied that.> I can't use a make file because I must first './configure', which is where this issue is occuring.
Perhaps it's not referring to kernel headers, but the -dev files for something else. Please run ./configure again and post the last six lines before it errors out.> You would think the developer of this application I am compiling would specify thatI think a lot of developers have a rather elitist attitude along the lines that if you are compiling a tarball, you should know this stuff. If you don't know what that red switch is for on the panel of my Learjet, maybe you have no business in the left seat.

It's a fine line; hard-core grey-beards don't want to be condescended to, but newbies read this stuff and come away mad and frustrated.

---

### Post by nikkae on 2010-12-04
From my understanding of Ubuntu, its target market are those who don't know much computers but want an alternative to Microsoft Windows. If this really is the case then it should not be incorporating 'elitist' stuff.

I am trying to compile NetworkManager 0.8.2. The reason I need to upgrade NetworkManager 0.0.8 (which is what is used in Ubuntu 10.04 LTS) is because it lacks the ability to connect to WAN via PPPoE over WLAN - something that even Windows XP can do!! :@

I will get you those six lines and post them to you...

---

### Post by chili555 on 2010-12-04
wireless-tools, I bet. Please install libiw-dev and run ./configure again.

Isn't 0.8.2 a beta release? Are you sure you want to try a beta?

---

### Post by chili555 on 2010-12-04
> it lacks the ability to connect to WAN via PPPoE over WLANDo you mean make a PPPoE connection by wireless? I wasn't aware that wired vs. wireless made any difference in making a PPPoE connection. Do you have a citation?> it should not be incorporating 'elitist' stuff.It doesn't. A version of Network Manager configured for Ubuntu comes installed by default.

---

