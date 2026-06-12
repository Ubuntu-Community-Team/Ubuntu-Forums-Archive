---
title: "NX nomachine: 1. No sound, 2. Copy files locally?"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by fisheater on 2010-01-11
Hi all

This post  is two part:

1.NX from no machine works very well. Suggested to me by a forum member, it was very easy to set up for a novice. I now can use my laptop to VPN/SSH into my desktop and keep my files more organized!

Second part is technical questions.
1.Getting sound to work in NX by nomachine 3.4.0-5: I have searched and not found much that worked. Under services I have selected 'Enable Multimedia Support' and no sound comes though my VPN session. I would like to listen to my MP3s when away on the road.

2.Getting files out of my virtual session: When I log my laptop (client) into my desktop (server) I can use my files and programs without any problem. How can I get a file from my desktop (server) onto my laptop (client) so I can print it locally? At present it seems 'stuck' in my virtual session of my desktop. The workaroud is to email smaller files to myself, but big files are a problem.

Thanks!

FE

---

### Post by pricetech on 2010-01-11
I'm logging in with a winders machine as the client and the sound is working for me.  I did check the Enable Multimedia Support, but didn't change anything else.

There's a guide on the No Machine website with pointers to making file sharing work, but I haven't had time to fully test it.

[http://www.nomachine.com/ar/view.php?ar_id=AR08D00413](http://www.nomachine.com/ar/view.php?ar_id=AR08D00413)

Good luck with it.

---

### Post by fisheater on 2010-01-11
You are a wealth of info!

I hadn't thought of trying the connection in a winXP box, and it was a success. That means the server end of things are working ok. I will keep digging into why my 9.04 client doesnt get sound.

No success yet with getting a file out of the VPN desktop onto my laptop. Will update as things change.

Ty

FE

---

### Post by pricetech on 2010-01-12
I probably wouldn't pursue that.  From what I can tell the file sharing isn't wrapped in SSH so it would be no more secure that ordinary winders file sharing, which may be fine on a LAN, but not over the Internet.

I know somebody who's really good at this stuff.  I'll pick his brain and get back to you.

It's probably not rocket surgery, I've just never done it.

---

### Post by pricetech on 2010-01-12
winscp for winders works for me.  Piece of cake to set up and it automagically connects me to my home directory on my Hardy desktop.  It includes a key generator too.

---

### Post by pricetech on 2010-01-12
SFTP under Ubuntu was a piece of cake also.

Places - Connect to Server.  Choose the SSH option and fill in the blanks.  You'll be prompted for your password.

That's internal as I haven't tried it from home, but I see no reason it won't work.

Have fun.

---

