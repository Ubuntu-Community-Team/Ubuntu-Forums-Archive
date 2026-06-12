---
title: "Intel Corporation WiFi Link 5100 not detecting any network"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by Hunding on 2011-10-12
I know this has been answered somewhere, but I just cannot seem to find it. I recently acquired a new laptop as my old one with Ubuntu 6.10 just finally gave up and went away. RIP

I have installed Ubuntu 11.04 through wubi from the windows 7 pro that was pre-installed with my new laptop. I was going to remove the windows partition but I have not been able to get my wireless to work from ubuntu. 

Here is the output from:

lspci -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]

I've attached the output in a txt format from:

dmesg | grep iwl 

the output is very long.

Any help is greatly appreciated, even if it is something as simple as a [http://www.lmgtfy.com](http://www.lmgtfy.com) ;)

---

### Post by chili555 on 2011-10-12
You have a very unhappy wireless device there; for example, from your dmesg:> [   13.180900] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.131568] iwlagn 0000:01:00.0: [COLOR="Red"]**Hardware error detected.**[/COLOR]  Restarting.
[   21.131577] iwlagn 0000:01:00.0: Loaded firmware version: 8.83.5.1 build 33692
[   21.131592] iwlagn 0000:01:00.0: Start IWL Error Log Dump:
<snip>
[   26.090150] iwlagn 0000:01:00.0: Could not load the INST uCode section
[   26.090157] iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110
[   31.090153] iwlagn 0000:01:00.0: Could not load the INST uCode section
[   31.090158] iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110
[   36.090049] iwlagn 0000:01:00.0: Could not load the INST uCode section
[   36.090056] iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110I am Googling and you might do the same.

In the meantime, let's see if your firmware files are intact. Please show us:```
ls -al /lib/firmware | grep ucode
md5sum /lib/firmware/iwlwifi-5000-5.ucode
```Fascinating.

---

### Post by Hunding on 2011-10-12
```
ls -al /lib/firmware | grep ucode
-rw-r--r--  1 root root  335056 2010-11-18 14:20 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  337520 2011-04-06 13:29 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 2011-01-24 13:45 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  150100 2010-11-18 14:20 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-11-18 14:20 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-11-18 14:20 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-11-18 14:20 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2011-03-03 08:03 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-11-18 14:20 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2010-11-18 14:21 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 07:07 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 07:07 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2010-11-18 14:20 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-13 19:00 iwlwifi-6050-5.ucode

```

```
md5sum /lib/firmware/iwlwifi-5000-5.ucode
d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
```

I don't even know where to begin to google this honestly. I have followed probably five different threads in attempting to resolve this issue. I hate to say this, but it does seem to work under windows 7 pro. Maybe I should find an ndiswrapper?

---

### Post by chili555 on 2011-10-12
> I don't even know where to begin to google this honestly.I'd start here:> iwlagn Could not load the INST uCode section
Unable to set up bootstrap uCode: -110It's definitely a unique problem.

You could certainly try ndiswrapper. If there is another underlying problem, it may or may not solve it.

May I see your entire dmesg? Please do:```
dmesg > hunding.txt
zip hunding.zip hunding.txt
```Attach the file hunding.zip to your reply.

Your firmware results look perfect. Nothing to fix there.

---

### Post by Hunding on 2011-10-12
here is the output...

I will have a look and see what I can find as well.

thanks for the help Chilli555

---

