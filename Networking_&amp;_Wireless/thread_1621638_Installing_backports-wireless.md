---
title: "Installing backports-wireless"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by asus701user on 2010-11-14
I am trying to sort out the very slow wireless connection on my eeepc701 and thought that possibly installing the linux-backports-modules-wireless-lucid application might solve it; but I cannot install it. I get this message:
[FONT=monospace]
[/FONT][FONT=Courier New]sudo apt-get install linux-backports-modules-wireless-lucid-generic
Reading package lists... Done
Building dependency tree       
[/FONT][FONT=Courier New]Reading state infor[/FONT][FONT=Courier New]mation... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.[/FONT] [FONT=Courier New]
  linux-backports-modules-wireless-lucid-generic: Depends: 
linux-backports-modules-compat-wireless-2.6.34-2.6.32-26-generic 
but it is not installable[/FONT]
E: Broken packages


How can I solve this? The error message doesn't make sense to me. Wireless
worked fine under the original Xandros OS.

Apologies for this being a very basic question.

Many thanks

---

### Post by FerretDefunct on 2010-11-23
Having the same troubles with "sudo apt-get install linux-backports-modules-wireless-*maverick*-generic" on my Eee PC 1005PE using Ath9k.

---

### Post by ThomasNovin on 2010-11-30
I also have this problem. I just posted to [email]linux-wireless@vger.kernel.org[/email] about this problem:

My post:

> Hello

This page, [http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu](http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu), should be updated to include Maverick/10.10.

If I just try to install as instructed for other versions:

sudo apt-get install linux-backports-modules-wireless-lucid-generic

I get:

E: Unable to locate package linux-backports-modules-wireless-lucid-generic

If I search backports*modules*wireless I find:

linux-backports-modules-wireless-2.6.35-22-generic - compat-wireless Linux modules for version 2.6.35 on x86/x86_64
linux-backports-modules-wireless-2.6.35-22-generic-pae - compat-wireless Linux modules for version 2.6.35 on x86
linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-generic - compat-wireless Linux modules for version 2.6.35 on x86/x86_64
linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-generic-pae - compat-wireless Linux modules for version 2.6.35 on x86
linux-backports-modules-wireless-maverick-generic - Backported wireless drivers for generic kernel image
linux-backports-modules-wireless-maverick-generic-pae - Backported wireless drivers for generic kernel image

So the only package good for installing without having to re-install every kernel change is linux-backports-modules-wireless-maverick-generic, however that package is not installable.

$ sudo apt-get install linux-backports-modules-wireless-maverick-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-backports-modules-wireless-maverick-generic : Depends: linux-backports-modules-wireless-2.6.35-23-generic but it is not installable
E: Broken packages

Something is broken in Ubuntu it seems?

Rgds

---

### Post by ThomasNovin on 2010-11-30
Got a reply.

> 
On 11/30/2010 09:35 AM, Thomas Novin wrote:
> Hello
> 
> This page,
> [http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu](http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu), should be updated to include Maverick/10.10.
> 
> If I just try to install as instructed for other versions:
> 
> sudo apt-get install linux-backports-modules-wireless-lucid-generic
> 
> I get:
> 
> E: Unable to locate package
> linux-backports-modules-wireless-lucid-generic

I added the package names for Ubuntu 10.10 into the wiki. The Ubuntu
guys changed the name of the package but the meta package is still
depending on the old names, this is a Ubuntu bug. (see:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/681727](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/681727) )

Hauke

Edit: So basically, everyone with this problem go to [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/681727](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/681727) and follow the progress. Press 'Affects me' and maybe it will be fixed a little faster.

Edit2: Btw, install linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-generic while waiting for the fix and you'll have a working setup with the current kernel.

---

