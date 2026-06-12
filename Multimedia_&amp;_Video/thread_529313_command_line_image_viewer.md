---
title: "command line image viewer"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by Hawk__0 on 2007-08-19
Is there such an image viewer that you can use to display images IN the command line?
i want to be able to view my images from command-line ssh that are on my other computer, thanks

---

### Post by jpkotta on 2007-08-19
You can do X forwarding with SSH, and open an image viewer on the remote machine.  E.g. ```
ssh -X user@remote
```  X forwarding must be enabled on the SSH server.  This is slooow over the internet, but OK over a LAN.

---

### Post by Hawk__0 on 2007-08-19
sweet, thanks! even better!

---

### Post by ivantis on 2008-06-30
is there a command line image viewer, so that i could view images on windows, like with PuTTY?

---

