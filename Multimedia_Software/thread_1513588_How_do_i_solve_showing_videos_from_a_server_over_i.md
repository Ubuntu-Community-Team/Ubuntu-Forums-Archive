---
title: "How do i solve showing videos from a server over internet?"
date: 2010-06-19
forum: Multimedia Software
---

### Post by nickeh on 2010-06-19
Hi! 

I have a file server running at home, now I'm away for the summer. I started to think if i have to download my multi media files or is there some good way to stream it? 

I'm a bit limited, the only protocol I've opened ports for is SSH and http. When i mount it through ssh and try to watch video the player acts as if it was a local file, wich is expected. But with limited outgouing bandwith from the server the video doesn't take long till it starts to freeze. 

So, what I'm looking for is either how to set upp a media player with bigger buffers or if i could use XBMC or anything and connect through ssh?

What are your suggestions on how the best way is to play media files from the server?

---

### Post by xzero1 on 2010-06-20
You must reduce the bitrate of your video files. Since you have control over your server I would approach it like this:

On the server :
Original video file -> ffmpeg transcode / reduce bitrate -> temp video file

The most efficient temp file codec is probably h264. I might try mp4 as the container.

Once the server process is started, play the *temp video file* on your client. Of course, this assumes your server is fast enough do the transcode on the fly. Note that some file formats need a more of the temp file completed before starting playback. I might be able to help you with the server command line if you give me the source file type and required bit rate.

Update1:
BTW, although it might not sound right, to make the video look better you might also want to *reduce* the resolution a bit, since higher resolution files require higher bitrates for a given quality. This can be done with the correct ffmpeg parameters.

Update2:
I decided to set up an ssh server and try out this idea. It works fairly well on my local network. First I set up a batch file to do the transcode:

I put this in /usr/local/bin ...:
You may need to modify it to your needs. I just want to give you an idea of what might work. I used mpeg4 as the codec because it was already installed and might be easier to decode on my slow eepc. You might want to leave off the redirection code for a while so you can see how fast the transcoding is proceeding. Note you probably want to reduce the -b 2000k for the internet or local network.

```
#!/bin/bash
rm /dev/shm/TeMp.ts
rm /dev/shm/fflog
ffmpeg -i $1 -vcodec mpeg4 -acodec copy -ac 2 -ab 64k -s 320x200 -b 2000k  ~/TeMp.ts 2>~/fflog
```

...Then I log onto the server via ssh command line, goto the folder with the video and execute the above with the video file as its argument.

Now without logging out, I log on again via the ssh gui i.e. Places-> connect to server, right click on the TeMp.ts and play it with gnome-mplayer. There will probably be gitches here and there but it seems to work ok. Interestingly, you can seek on the file.

If you really have a bad connection, then just start the copying TeMp.ts to your client computer and then play the local file. Whatever you try, let us know how it works out.):P

---

### Post by nickeh on 2010-06-24
Tried your script adjusting only bitrate I needed to go down to 500k so the quality was too low. This is when just streaming. 

The server only has 1 mbit up. But where I am staying for the summer i have 100mbit down so i think that the easy way is to download the things i want to see from other sources and then do a big merge with the server when i come home. Space is somewhat limited on my laptop so might have to upload some stuff over night to the server every now and then... 

Need to look if i can change from expensive ADSL to cheap broadband. It's a shame not all apartmenthouses are connected to a good internet connection =/

---

