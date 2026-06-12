---
title: "YouTube videos start and stop"
date: 2009-12-13
forum: Multimedia Software
---

### Post by Oldhacker on 2009-12-13
Recently, using Firefox 3.5.5, videos on YouTube keep starting and stopping incessantly. This has gone beyond the point of annoyance. Just out of curiosity, I tried playing the same video that I had given up on with Opera 10.10. It played normally, without any starting, waiting and stopping all the way through!

This proves that the problem lies within Firefox (Shiretoko) and not elsewhere in Ubuntu. Have others experienced this problem?

---

### Post by waynefoutz on 2009-12-13
It's running fine for me. I'm not running that Shiretoko build though. Try getting firefox 3.5.5 with Ubuntzilla. [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) That way you'll get a version of firefox that autoupdates like the windows version does. I don't know if that will fix your problem, but my flash is working fine.

---

### Post by Ghost|BTFH on 2009-12-13
Crazy question - did you bother to let it load before hitting play?  I'm not certain, but I believe Firefox's default buffer for video play-back may be a little bit conservative for when the servers are loaded.

Cheers,
Ghost

---

### Post by Oldhacker on 2009-12-14
No, I do not let it load before hitting play. The loading sometimes takes so long that I could fall asleep while waiting. ;-)

---

### Post by Oldhacker on 2009-12-15
I followed the instructions that you gave to installing a new edition of Firefox 3.5.5 using Ubuntuzilla. It installed fine but the new Firefox does not connect to the web at all!

Is there something further that I have overlooked?

Thanks

---

### Post by Oldhacker on 2009-12-15
Digging a little more, I went to about:config and Set the network.dns.disableIPv6 setting to true

That was the stumbling block for getting online again.
Now, to start testing the other functions with this version of Firefox to see what problems are solved (or added.)

---

