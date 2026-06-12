---
title: "Cant browse internet in 10.04"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by bluekage on 2010-06-25
Hey all,
Just upgraded my laptop to 10.04 today, finished successfully but after about an hour or two I lost my internet connection. Tried reconnecting but it kept refusing to, eventually after restarting it went through. However, even though Im connected it cant do anything internet related, no browsing, no package downloading, nothing. Everything seems to be fine with the other computers on the network, be they wired or wireless.

Does anyone know what would be causing this? Please provide any solutions in step-by-step, I love ubuntu but Im still not too good with it.

Thanks in advance guys!

---

### Post by AfrikaDietmar on 2010-06-25
What error message do you see when you try to open a page ?

If you go on "File" > check if there is a tick on "Work Offline". (I know that sounds stupid but you never know...)

Go on Edit > Firefox Preferences > Advanced > Network > Settings

Where is your radio button ? (For me its on "Use system proxy settings)
Try the other options and see if it works.

---

### Post by Iowan on 2010-06-25
Is your connection wired or wireless?

---

### Post by bluekage on 2010-06-25
AfrikaDietmar - Whenever I try to open a page firefox just comes back with

"Address Not Found - Firefox cannot find the server at www.url.com"

I know its not me mistyping the url, it does it for bookmarks too. It also seems like it doesnt even attempt to go to the site as the message pops up quite instantly.

Sadly offline mode was not ticked either, nor did trying any of the other proxy settings you mentioned.

Iowan - Wow, cant believe I didnt specify that, my laptop is on wireless.

Thanks for the replies though guys, any other ideas?

---

### Post by bluekage on 2010-06-25
Just a little new info, saw some people mentioning being able to pull sites up with their IP, but not their url, tried it myself but had no luck...

---

### Post by bluekage on 2010-06-25
More info, just booted into my windows laptops windows partition, no issues there.

---

### Post by bluekage on 2010-06-25
Ok, so Ive found a temporary solution,it was suggested to someone else who had the same problem that they do "sudo dhclient" in the terminal. Doing so does indeed get the internet up and running on my laptop, but it only lasts until I restart my computer, if anyone can come up with something more permanent I would be much obliged.

---

### Post by Iowan on 2010-06-25
Just to cover bases - if you right-click Network Manager icon, does it show "Networking enabled" box checked? Some threads reported that it sometimes got turned off.

---

### Post by bluekage on 2010-06-25
Nope, its still checked.

---

