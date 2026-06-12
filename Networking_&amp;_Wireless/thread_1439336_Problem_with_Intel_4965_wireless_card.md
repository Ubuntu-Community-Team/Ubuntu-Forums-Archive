---
title: "Problem with Intel 4965 wireless card"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by lateralus01 on 2010-03-26
I'm having some connection problems with my wireless card.  I have an intel 4965agn wireless card that uses the iwlwifi drivers.

```

mark@mark-laptop:~$ lspci | grep -i wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

My connection drops off completely for long periods of time.  If I ping the access point, packets are transmitted and received for about 5-10 seconds, then nothing is transmitted anywhere from 5 to 20 seconds, then packets are transmitted again, and the cycle repeats.

The problem isn't the access point or the environment; my wireless card works fine in Windows 7.

I've used Gentoo before with this card and I was able to get it working fine.  I had to download, compile, and install the drivers myself but it worked without any problems.  I think the kernel I was using was 2.6.28 and the specific module that my card used was iwl4965.  It's strange because that module isn't loaded, and nothing happens when I try to load it:

```

mark@mark-laptop:~$ sudo modprobe iwl4965
mark@mark-laptop:~$ sudo lsmod | grep iwl
iwlagn                109084  0 
iwlcore               112796  1 iwlagn
led_class               4096  1 iwlcore
mac80211              181140  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211
mark@mark-laptop:~$

```

I've added the latest firmware from intellinuxwireless.org to /lib/firmware but that didn't help anything; look at the timestamp to see the files that were already there:
```

mark@mark-laptop:/lib/firmware$ ls -l | grep iwl
-rw-r--r--  1 root root  335056 2009-11-30 05:29 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  149652 2009-11-30 05:29 iwlwifi-3945-1.ucode
-rwxr-xr-x  1 root root  150100 2009-11-30 05:29 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187608 2009-11-30 05:29 iwlwifi-4965-1.ucode
>>-rwxr-xr-x  1 root root  187972 2010-03-26 00:50 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2009-11-30 05:29 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2009-11-30 05:29 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2009-11-30 05:29 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  459992 2009-11-30 05:29 iwlwifi-6000-4.ucode

```

strange that the oldest version firmware in the directory was the one for my wireless card before I copied the newest version there...

Any Ideas?

Thanks,

lateralus01

---

### Post by Gorgapor on 2010-04-19
I am having very similar problems with an intel wireless card, in a thinkpad t410. It is being very flaky, and dropping out for minutes at a time.

Here's my lspci output:
```
03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
```

and my lsmod output:
```
$ sudo lsmod | grep iwl
iwlagn                121577  0 
iwlcore               124955  1 iwlagn
mac80211              238128  2 iwlagn,iwlcore
cfg80211              148386  3 iwlagn,iwlcore,mac80211
led_class               3732  3 thinkpad_acpi,iwlcore,sdhci

```

---

### Post by cfth on 2010-06-13
Did either of you ever find some kind of solution?

I'm having issues with the Intel 4965 also as detailed here:
[http://ubuntuforums.org/showthread.php?p=9453232](http://ubuntuforums.org/showthread.php?p=9453232)

---

