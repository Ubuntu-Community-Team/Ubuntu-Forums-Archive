---
title: "vsftpd pasv problem"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by rattlehead on 2010-01-23
When upgrading a media server to Karmic, vsftpd suddenly stopped working. The system was behind the router, and I had it set up to connect on a different port and use PASV. I had set up the router to forward all the necessary ports, and set up the vsftp config to only use that range. I knew this setup worked, because it was the same config since it's worked for years with Hardy.

The problem occurs when logging in; it works fine behind the router, but not from outside (which tricks you into thinking its the router... don't be fooled!) It logs in, but you get a 500 error and no directory listing.

I looked around and I see this same problem occurring sporadically, especially with Karmic. Some of the solutions I've seen posted seem a little convoluted; even a shell script that constantly kicks vsftpd back into line.

After a week of troubleshooting this, I figured I'd share my solution: it's not your fault.

The version of vsftp that is in the Karmic repos is 2.2.0; this has a known bug about PASV connections. I just got the new 2.2.2 pre-release and compiled it, dropped it in, and it worked fine from the get-go.

So, you just can't use 2.2.0 or 2.2.1, but you can rollback to 2.1.2 (I've been told) or grab the 2.2.2 pre-release, and it'll work.

---

