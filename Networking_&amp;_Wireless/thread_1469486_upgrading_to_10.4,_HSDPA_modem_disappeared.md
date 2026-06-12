---
title: "upgrading to 10.4, HSDPA modem disappeared"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by mpolito1969 on 2010-05-02
There was a bug in Ubuntu 9.10 that sometimes prevented me from using my UMTS connection (I reported bug #506620 on Launchpad).

Today I upgraded to Ubuntu 10.4, as it seemed the bug was solved, but the internet connection is now completely lost: my modem is no longer there.

Using dmesg I can see a modem is found and connected to ttyUSB0, ttyUSB1 and ttyUSB2, as it was before the upgrade, using lsmod I can see that 'option' module is there but the UMTS modem doesn't appear neither in the network manager applet nor using 'nm-tool' or 'ifconfig'.

I have rebooted several times having always the same result.

I have a built in GlobeTrotter HSdPA modem.

Any help?

Attached you find output from dmesg, lsmod and nm-tool.

Ciao,
Max

---

### Post by mpolito1969 on 2010-05-23
Just in case someone comes here with the same issue...

I solved the problem, thanks to Peteris Krisjanis from the Gnome Network Manager mailing list, by adding a line "option" to /etc/modules.

I don't know if this is a solution to the problem reported or just a workaround, but it works.

Ciao,
Max

P.S.
Ubuntu support is not so bad, broadly speaking, but when it comes to UMTS you'd be better shoot yourself in the head. I really can't understand.

I opened this thread

[http://ubuntuforums.org/showthread.php?p=9266274#post9266274](http://ubuntuforums.org/showthread.php?p=9266274#post9266274)

to discuss the issue but (as usual when there is "UMTS" in the title) I didn't get any reply.

---

### Post by mpolito1969 on 2010-05-23
What I wrote doesn't solve the problem.

I could connect yesterday in the evenining and today in the morning. Now, I don't know why, the modem has disappeared again.

I have rebooted six times my laptop without any success :(

Anyway, it costs so little that's worth give it a try, someone else might be more lucky than me.

Ciao,
Max

---

