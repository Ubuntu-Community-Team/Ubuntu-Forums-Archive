---
title: "wireless not working until logon"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by benbong on 2009-04-21
Hi Everyone,

I have a computer running ubuntu 9.04 x86_64 desktop edition (but I had exactly the same issue with 8.10 x86_64) that does not connect until someone is logged on, after that, everything is working fine.

Usually I access my computer via SSH from work to do some updates (especially now, with the 9.04 nearly out and all the bug fixes) then I reboot the computer and cannot access it anymore as I cannot logon directly.

I've done some research on the forum and founs some process for it . Actually I have in the rc.local:
```

ifup wlan0

```

That shoud launch the wlan0 at the end of the boot, but it does not seems to work.

my wlan0 has been configured using the gnome network manager (manually assigned IP using WPA2 connection).

I was just wondering if the only solution was to manually describe everything in the interfaces file?

Thank your very much for your help.

PS: I really think that in the gnome network manager, you should be able to select which interface to go up when the computer is started. It may be an option that I haven't seen.

---

### Post by dcottingham on 2009-04-23
I have the same problem and I hope one day I can find an answer.  One unsatisfactory approach is to set the computer to automatically log in a user at boot.  But with recent releases, it not only waits for login, but then pops up a dialog asking for the keyring password.  So I can't even get this bad solution to work.

I found the following page on this subject:
[http://www.ventanazul.com/webzine/articles/fix-wireless-connection-problem-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/fix-wireless-connection-problem-gutsy-gibbon)
but the solution is basically to rip out gnome network manager and replace it with something else.

I'm hoping to find something less drastic.

---

### Post by benbong on 2009-04-29
I've investigated and found this solution on that forum :
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Hope it'll help someone else.

---

