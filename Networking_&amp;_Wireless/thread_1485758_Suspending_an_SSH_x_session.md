---
title: "Suspending an SSH x session?"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2010-05-17
Recently I've been using the program screen to suspend console based programs I run through SSH. Recently, a friend of mine enlightened me with the "-X" parameter which allows me to run graphical programs on the SSH server.

So my question is, if I start a graphical program on the SSH server, is there a way to suspend it, like I do with screen, so that I can reconnect to it later?

I'm starting to think I might be crossing over into a full blown VNC server at this point, but I'm not sure.

Thanks!

---

### Post by ownaginatious on 2010-05-18
Anyone?

---

### Post by CharlesA on 2010-05-18
I don't know, but I would think it wouldn't work the same way, since all you are doing is forwarding X to a client instead of actually running it on the X server on the host machine.

I'd love to be proven wrong, but it sounds like VNC would be what you are looking for.

---

### Post by kevdog on 2010-05-18
Im not sure if the screen program run within the remote ssh session saves X options.  I think its terminal based.

---

### Post by wirelessmonkey on 2010-05-18
Don't use VNC, try freenx, it's much more secure, and it can save sessions!

---

