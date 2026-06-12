---
title: "What can I use to make this &quot;Video Server&quot;"
date: 2010-08-10
forum: Multimedia Software
---

### Post by b0ot on 2010-08-10
I currently have a private network that I'm interested in setting a a "video server" on with the following capabilities: (currently running Ubuntu 10.04). One of the biggest problems I have is that some of my connections are very SLOW (around 200 kilobytes/sec) and possibly slower in other areas, and I would like a solution that is able to take this into account.

1.) I want it to be able to work cross platform with Windows machines. My current "server"
is running linux and I have a shared folder via Samba with my windows machines but everything is sent via tcp and there is no buffering when you try to play a video so it will not work for what I want.

2.) I want to be able to have every video/audio file in a file on my server available "on demand" for streaming. I want to be able to have multiple users be able to open different streams at the same time (although I should have a relatively small number of concurrent users max ~4 or so)

3.) I want to be able to have webcam or other streams from one remote computer to any other computer on the network with the option to have the stream stored to disk on my server. With my slow connection I need to be able to have the stream captured by the server.

Nice but not necessary: Some sort of front end to access the files

So far I have looked at:
Vlc - able to stream/capture one file but didn't seem able to do everything
flumotion - seems like it has a lot of potential and was able to get streaming from my server outwards, but no idea how I would be able to capture streams from remote computers to other remote computers. Also, the VoD part of this just flat out didn't work for me.
Zoneminder: Looked at briefly, installed but wasn't able to get running.

Any suggestions would be greatly appreciated I have had quite an unsuccessful hunt for a solution.

---

