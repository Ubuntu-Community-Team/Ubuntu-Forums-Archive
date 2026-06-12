---
title: "Ethernet connection not working after each boot"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by chrismyers on 2006-06-03
My ethernet connection worked fine with Breezy, but since I did a fresh install of Dapper I have had connection problems.

After a reboot I have to run "Networking", Deactivate Eth0 & then Activate it.

Its a little irritating. Anyone know of a fix?

My network card details follow:

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at d2000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c000 [size=8]
        Capabilities: [44] Power Management version 2


Thanks in advance :D

---

### Post by jvictor on 2006-06-03
Seems like a DHCP problem with dapper. Trya  static IP if u have the luxury of doing so

---

### Post by chrismyers on 2006-06-03
[QUOTE=jvictor]Seems like a DHCP problem with dapper. Trya  static IP if u have the luxury of doing so[/QUOTE]

I think you're right. Good point, but I'd prefer to find a fix before reverting to a workaround though.

---

### Post by tom56 on 2006-06-03
I have the same problem... [http://ubuntuforums.org/showthread.php?t=187758](http://ubuntuforums.org/showthread.php?t=187758)
Look there and I've (sort of) pinpointed the cause.

Haven't found a solution yet though ](*,)

EDIT: Forgot to mention, I seem to have the exact same card ("0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)). Could be that?

---

### Post by RizSilverthorn on 2006-06-04
I also have the same onboard network card with the same issue and temporary resolution. Maybe a pattern is appearing? Unfortunately I do not have the rights to assign a static IP (corporate network).

---

### Post by jvictor on 2006-06-05
looks like a bug report has to be filed.

---

### Post by tom56 on 2006-06-05
I already added a comment to one which I think is the same, here...
[https://launchpad.net/distros/ubuntu/+bug/42608](https://launchpad.net/distros/ubuntu/+bug/42608)

---

### Post by phoenix_1983 on 2006-06-06
I also have the same problem...

I found that changing the IPV6 settings eased some of the burden... however apt-get still isn't working.  My sources list is fine..

I've tried teh black_list trick and that hasn't made apt-get work.

I keep getting time outs when trying to use apt-get.  I can ping au.archive.ubuntu.com with 0 packet loss.... i'm stumped!!!

---

### Post by enigmamachine42 on 2006-06-08
i have found that when my wireless (ath0) and ethernet (eth0) are both active, linux will automatically reset the default gateway device to eth0 when i reboot.  no idea why.

---

### Post by chrismyers on 2006-06-14
[QUOTE=jvictor]Seems like a DHCP problem with dapper. Trya  static IP if u have the luxury of doing so[/QUOTE]

I finally decided to set a static IP. I've never had the problem since.

Thanks for your help.

I'd still like to find a fix for allowing me to use DHCP (if anyone is reading this).

Once again, Cheers.

---

### Post by gala on 2006-06-14
I also had the same problem, tried every solution found in forums, but no success. DOWNGRADED to BREEZY.

---

### Post by 4rc on 2006-06-15
Yes, I have the same hardware and the same problem. This started happening after I dist-upgraded to dapper. It's quite easy to fix this, by manually deactivating and activating again, but it's very annoying to do that every time I boot (I'm dualbooting so I have to do it often).

If someone finds a solution please post it here!

---

### Post by Aigars on 2006-06-17
[http://download.nvidia.com/XFree86/nforce/1.0-0306/KnownProblems](http://download.nvidia.com/XFree86/nforce/1.0-0306/KnownProblems).

---

### Post by sicofante on 2006-06-17
[QUOTE=Aigars][http://download.nvidia.com/XFree86/nforce/1.0-0306/KnownProblems](http://download.nvidia.com/XFree86/nforce/1.0-0306/KnownProblems).[/QUOTE]
This URL doesn't work here (HTTP Error 404 - File or directory not found.)

---

### Post by Aigars on 2006-06-18
[http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)

STEP 4: Review the Known Problems for any special installation instructions required by your platform.

---

### Post by eswar on 2006-07-17
Oh.. even i have the same problem.  
In my Toshiba- A80-154 Satellite laptop, I have Marvell-Yukon ethernet card. 
 Moreover, I have a static IP, but still i have the problem.  

I tried the blacklisting also.  But it didn't work out!

It is terribly irritating, can't do even updates and upgrades.
 
any thoughts?! :-k 

Thanks in advance!

---

### Post by tom56 on 2006-07-18
> **Aigars said:**
> [http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)

STEP 4: Review the Known Problems for any special installation instructions required by your platform.

I don't think that's it, given that I had no problems on Breezy.

If everyone who has this problem comments on the bug with their hardware details and error messages, the cause of the issue might be revealed and someone could begin work on a fix.

[https://launchpad.net/distros/ubuntu/+bug/42608](https://launchpad.net/distros/ubuntu/+bug/42608)

---

### Post by ezphilosophy on 2006-07-18
> **chrismyers said:**
> My ethernet connection worked fine with Breezy, but since I did a fresh install of Dapper I have had connection problems.

After a reboot I have to run "Networking", Deactivate Eth0 & then Activate it.

Its a little irritating. Anyone know of a fix?

My network card details follow:

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at d2000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c000 [size=8]
        Capabilities: [44] Power Management version 2


Thanks in advance :D

I have the same problem.  Quite annoying.

[http://www.ubuntuforums.org/showthread.php?t=207318](http://www.ubuntuforums.org/showthread.php?t=207318)

Can't seem to find a fix.

---

### Post by ezphilosophy on 2006-08-06
Well, I just want to give this thread a *bump*.  I still haven't found a fix and the problem is really irritating.  Why should I have to go into network settings each time I turn on my computer, then disable then enable the eth0 just to get on the internet?!

Why was there no problem in Breezy but now there is in Dapper?  What could the big change be?

What more, is that out of all the threads with this problem (there are many), no one has a solution other than giving yourself a static IP.

Please, Ubuntu Gurus, help us solve this problem!

---

### Post by Nesnej Trick on 2006-08-06
I have the same problem with our new family computer. What also seems to work is to set a static IP to a bogus address, save, reopen and re-set to DHCP. This problem appears to be somehow related to NVidia Nforce network controlers, since I don't have that problem on my own computer, which has the ethernet controler integrated in the Intel IHC5 chipset.

---

### Post by eeried on 2007-01-11
Are you still having the same problem?

I'm trying to find an Asus motherboard that works fine with Dapper or Edgy, and I thought ASUSTeK K8N4-E SE (NVIDIA nForce4 4X) looked all right.

---

