---
title: "Misterious background downloads"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by Umkus on 2009-08-31
I've recently moved to Ubuntu from you-know-what-os. My internet connection is at 3mb/s. Last couple of days I've installed a netSpeed and a SystemMonitor gnome applets. Both of them are showing strange (and high!) network activities. Today it even became barely possible to browse the net. This occurs every time, immediately after the login screen.
How can I sniff/trace this traffic to an application or daemon which spawns it? Something is taking advantage of all the down link and I need to know how to resolve this.

Take a look at the [screenshot]("http://img440.imageshack.us/img440/1992/screenshot1o.png"). I haven't run any apps that might download anything. As soon as I login to my desktop the download speed is already at max.

Thanks ;)

---

### Post by tgeer43 on 2009-08-31
Is it only doing this for a short period after startup or is the problem more or less continuous?

While it's acting up enter this command in the terminal and post the output back to this thread.
```
sudo netstat -vep
```tgeer

---

### Post by Umkus on 2009-08-31
Thank you for the quick reply, tgeer43!
It is a permanent download, I'd call it ;) There was some fall in speed almost to the ground zero, though. But it lasted for just about 15 minutes.
The netstat output is too huge to paste it here, so it could be found on [pastebin]("http://pastebin.com/f77471c80").
There was a thread where a guy advised to use iftop for these kind of situations, so I've made  another [screenshot]("http://img511.imageshack.us/img511/3128/screenshot1m.png") with it. The line inside the black bar could be the guy I need to take care of.
But what does this mean anyway?

---

### Post by tgeer43 on 2009-08-31
It would be best if I can see the output of those two programs right after a cold boot and before you run any applications.

tgeer

---

### Post by Umkus on 2009-08-31
Okay! So I rebooted and logged into my desk but the sky-high download has already been there.
Here's output of [netstat]("http://pastebin.com/d2443e48d") and [iftop]("http://img523.imageshack.us/img523/8700/screenshot2q.png")'s screenshot just after the cold boot.

---

### Post by Gen2ly on 2009-08-31
netstat -putona

might be a little better as it will only show open ports.

---

### Post by Umkus on 2009-08-31
Gen2ly: Good hint, thanks!
Uptime is about 2 hours now and downloading seems to stop (till next time). Don't know the reason for all of this in the first place. Some people still sit under limited bandwidth ISP plans, by the way.

UPD: new morning, new ghostly downloads :-D

---

