---
title: "SSH X11 forwarding quirk in Ubuntu 11.10"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by michael111 on 2011-10-20
Hi all!

I'm trying to log into a remote server using the "ssh -X" command using GNOME Terminal 3.0.1, but i'm having problems running firefox. When I enter the command "firefox" or even the actual path ("/home/michael/firefox-linux/firefox-bin") I get my local installed firefox instead of the remote application.
"xcalc" works so I know that the X forwarding is working.

How do I solve this?

Thanks.

---

### Post by wstrauss on 2011-10-20
I'm having the same problem. Firefox over X forward opens my locally installed firefox.

---

### Post by homeyclaus on 2011-10-25
Executing Firefox with -no-remote option will force it to not try to talk with an existing Firefox window/process.

See [http://manpages.ubuntu.com/manpages/hardy/en/man1/gnome-moz-remote.1.html](http://manpages.ubuntu.com/manpages/hardy/en/man1/gnome-moz-remote.1.html)

---

