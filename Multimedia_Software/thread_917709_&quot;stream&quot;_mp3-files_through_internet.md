---
title: "&quot;stream&quot; mp3-files through internet"
date: 2008-09-12
forum: Multimedia Software
---

### Post by LarsEriksson on 2008-09-12
Hi.
When im at work i stream all music i am listening to from my computer at home through internet, i have a FTP-server setup on my Ubuntu server at home
At work i use a FTP-client([www.netdrive.net](www.netdrive.net)) that allows me to "mount" any FTP-server as a drive letter/normal local disc, so i just do that and listen to the .mp3-files like i would at home.
This solution is however _very_ slow, like browsing the FTP(in windows explorer) and it times out some times, even though alot of theese problems is client related i think that the nature of FTP is not so very good to use for streaming files and/or "static" connections.

So, is there anyone who knows of any alternatives to this solution, that might work better?
The requirements are that i should be able to use any music-player on my "client"(work) machine and not be forced to download any mp3-files to my "client"(work) machine.
The best would be if i could mount the fileserver's music-disc as a "normal" drive letter in windows, like i do now, but a faster and more stable solution.

---

### Post by eye208 on 2008-09-12
You can set up a streaming server with VLC. It's very simple, and it works like true web radio, not involving any shared network drives. Just add songs to VLC's playlist, then use the streaming wizard to configure the stream.

---

