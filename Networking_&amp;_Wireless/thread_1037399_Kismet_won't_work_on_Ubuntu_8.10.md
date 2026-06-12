---
title: "Kismet won't work on Ubuntu 8.10"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by mattbasc on 2009-01-11
I am using Kismet 2008 05 R1. I tried installing using a package manager and using by compiling from source but I am getting the same error.

My kernel version is 2.6.24-21-generic.

I am using iwl3945 as my capture source type.

I have tried all the other similar ones: ipw3945, ipwlivetap. But they do not work.

The error I get when attempting "sudo kismet" is:

FATAL: channel get ioctl failed 95:Operation not supported
Done.

I have read that this means that I need to change my drivers. But I have up-to-date iwlwifi drivers (which contain the file iwl3945) in the kernel directory.
> 
PROBLEM: Fatal error enabling monitor mode, 'monitor' ioctl not available
      Some capture sources use a private ioctl, 'monitor', to enable rfmon.
      If Kismet is unable to find this ioctl, it means that the wrong 
      interface was specified, the wrong capture type is being used, or 
      most commonly, the drivers you are using have not been patched or the
      patched drivers are not being loaded.
      Be sure to download any patches needed for the drivers you are using, 
      and make sure that no other copies of those drivers exist in your
      /lib/modules/kern-version/ directory.  You may need to restart pcmcia-cs
      if your wireless card was already running when you installed the patched
      drivers.
    FIX: Provide the correct interface and ensure that the patched drivers are
      loaded.


---

### Post by S4L4Z on 2009-03-19
this is mine..i configure the kismet.conf in /etc/kismet. i assume my wifi card is the same with u since u are using iwl3945. below are part of the configuration, i just edited the "suiduser" part and the "source" part.maybe try to get the newest kismet and update ur ubuntu.works fine with me.try it out:)


p/s: using ubuntu 8.10(kernel 2.6.27-ll generic), on lenovo ibm thinkpad T60, Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux

```
# User to setid to (should be your normal user)
suiduser=salax

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,wlan0,iwl3945wifi

```

---

