---
title: "ndiswrapper problems"
date: 2005-02-17
forum: Networking &amp; Wireless
---

### Post by chbenito on 2005-02-17
I'm trying to get my wireless card working. I've read the ndiswrapper how-to. I've loaded the drivers. I've tried to load the module.

Unfortunately, when I try to load the module, I get this:

root@blue:~ # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-3-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I'm scratching my head. The driver should load, but it doesn't want to. Hmm.

Anyone know what my problem might be?

---

### Post by MrTrumpets on 2005-02-17
I see that you're using the root terminal.. even when I setup ndiswrapper, I had to use the "sudo" command first... I don't know why.. I just did.

If that's not the corrent answer, then you'll probably need someone with more linux knowledge.  :)

GL!

---

### Post by chbenito on 2005-02-18
I actually tried it both ways. It behaves the same when I use sudo from a normal terminal.

---

### Post by faqpete on 2005-02-18
Hi!
What kernel version do you use? I get the same errormessages like you when using kernel 2.6.10 or higher - when using 2.6.8 I've no problems with ndiswrapper!
Give it a try and use a lower kernelversion ;-)
faqpete

---

