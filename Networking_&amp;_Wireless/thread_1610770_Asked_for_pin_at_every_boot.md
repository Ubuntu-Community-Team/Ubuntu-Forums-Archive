---
title: "Asked for pin at every boot"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by alive1 on 2010-11-01
Hi,
Network manager asks me for my PIN to my 3g card every time I boot.. How do I stop this?
I tried entering the pin code in my Mobile Broadband connection settings, but it still asks!

Help?

edit: I've gotten a screenshot of the dialog box. See attached file.
This never happened before I upgraded to ubuntu 10.10.

---

### Post by alive1 on 2010-11-04
Nothing?

---

### Post by Peter09 on 2010-11-04
Right click on the network manager icon and select edit connections, go to the connection that is the problem. Ensure that the 'allow all users' box (or similar wording) is ticked.

---

### Post by linux18 on 2010-11-04
The only thing I can think of at the moment is to delete ~/.config reboot and choose "use unsafe storage" when you connect to the network. but this is a very uncoordinated idea that will mess up you configuration for a lot of things.

---

### Post by alive1 on 2010-11-04
Hi,
Thanks for the suggestion.
I just did what you said, but it still asks me for the PIN when I first boot up and log in.

Note that I am not trying to connect using this device. I haven't enabled auto-connect either. I just boot, log in, and get asked for the PIN every time I do so.

edit: I don't wanna delete my ~/.config either O_o

---

