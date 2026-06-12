---
title: "Downloading stops in 10 to 15 mins of locking the screen"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by raviepic3 on 2011-05-17
Hello people,

Everyday i initiated a download on my ubuntu pc and lock the screen and leave, i notice that the internet connection gets cut within 10 to 15 mins after i leave. I am connecting to internet via reliance data card - usb modem. what are the odds of my ubuntu responsible for this ?

---

### Post by jerrrys on 2011-05-17
is a high resource screen saver kicking in and killing the download?

---

### Post by puvijain on 2012-04-03
I facing the same problem. Could someone look into this. I'm in a college campus and using internet through a proxy. The net speed is slightly slow but decent when browsing and gives around 20-30kbps while  downloading. The download connection shows 0 b/s after a while from locking the screen.

---

### Post by CompBio on 2012-05-02
I have the same problem with a Fedora machine at school.  It may be confined to browser-based downloads.  If I use ftp or wget directly, I can put the download in background and log off and the job will run to completion.  If I access a website and use Firefox to download a file, it'll pause when I lock the screen.

Any chance you can use ftp or wget to do your file transfer?

---

### Post by lukeiamyourfather on 2012-05-02
Sounds like it might be USB auto suspend. When the system thinks a USB device is idle it will power down the port to save power. Do a search for disabling USB auto suspend and there will be some guides on it.

---

### Post by sefs on 2012-05-02
Here is a work-around that may work until you find a solution to the problem.

Install a download manager like uget (my preference) or gwget.

Then when firefox prompts you to save a file, then select the flashgot option and make sure your download manager of choice is selected such as uget/gwget/etc...

See attached image for example.

---

