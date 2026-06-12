---
title: "Uninstall ndiswrapper"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by damitch on 2010-01-02
I started this as another thread, [http://ubuntuforums.org/showthread.php?t=1369287]("http://ubuntuforums.org/showthread.php?t=1369287"), but its morphed into a slightly different problem, I think.

Recap:

I installed the Ubuntu netbook remix on a Dell Inspiron 1011, then tried to get the wireless connection going.  At the time, I failed to understand that there was a good vendor's driver available, so I partly installed ndiswrapper, then found out about the Broadcomm STA driver.

I thought I had uninstalled ndiswrapper properly, but it seems it's not so.  It still shows up on a modprobe listing.

I have uninstalled all the *ndis* packages I could find; problem persists.

Any advice?  Thanks.

---

### Post by ajgreeny on 2010-01-02
Try purging the ndis applications you installed, as that may remove the module, but if not try this,  (from "man modprobe")
> -r --remove
              This option causes modprobe to remove, rather than insert a module.  If the modules
              it  depends  on  are  also  unused,  modprobe will try to remove them, too.  Unlike
              insertion, more than one module can be specified on the command line (it  does  not
              make sense to specify module parameters when removing modules).

              There  is  usually  no reason to remove modules, but some buggy modules require it.
              Your kernel may not support removal of modules.

---

### Post by damitch on 2010-01-03
I've tried that:
```
david@david-laptop:~$ sudo modprobe -r ndiswrapper
[sudo] password for david: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```
Since the -r option ignores configuration files, that warning message looks a bit strange, but I guess the application is nevertheless required to post it.

But anyhow, it didn't work.
```
david@david-laptop:~$ modprobe -l *ndis*
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/ubuntu/ndiswrapper/ndiswrapper.ko
david@david-laptop:~$ 
```

So.  If the kernel (the Linux kernel?) won't support removing modules, how do I safely reinstall the kernel?  Or is this something I could somehow prevent from happening at bootup?

---

### Post by bkratz on 2010-01-03
Might have found something useful

[http://ubuntuforums.org/showthread.php?t=507378](http://ubuntuforums.org/showthread.php?t=507378)

---

### Post by damitch on 2010-01-03
That did it, **bkratz**.  I used ```
locate ndiswrapper
``` to find those files and directories, removed them, and rebooted.  I'm now using the netbook.

Since it was a slightly botched install in the first place, it didn't look like there was any opportunity to make any uninstall command. I do understand that using uninstall would be much, much, much the preferred way to do this - but in this case, the hand-removal worked.

Thanks, all.

---

### Post by bkratz on 2010-01-03
Don't forget to go to the thread tools and mark as solved. Hopefully the other method will work better for you now.

Reread and it looks like it did---congratulations!

---

