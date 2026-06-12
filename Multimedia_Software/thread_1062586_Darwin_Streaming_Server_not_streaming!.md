---
title: "Darwin Streaming Server not streaming!"
date: 2009-02-07
forum: Multimedia Software
---

### Post by izziere on 2009-02-07
I have followed Howto's on installing DSS to the letter (famous last words?), uninstalled and then tried again.  Server is up and running but it does not stream:
```

sudo netstat -taunp | grep Darwin

tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      5200/DarwinStreamin
tcp        0      0 0.0.0.0:8001            0.0.0.0:*               LISTEN      5200/DarwinStreamin
tcp        0      0 0.0.0.0:554             0.0.0.0:*               LISTEN      5200/DarwinStreamin
tcp        0      0 0.0.0.0:7070            0.0.0.0:*               LISTEN      5200/DarwinStreamin
udp        0      0 127.0.0.1:6970          0.0.0.0:*                           5200/DarwinStreamin
udp        0      0 192.168.1.108:6970      0.0.0.0:*                           5200/DarwinStreamin
udp        0      0 127.0.0.1:6971          0.0.0.0:*                           5200/DarwinStreamin
udp        0      0 192.168.1.108:6971      0.0.0.0:*                           5200/DarwinStreamin

```

The DSS admin page shows multiple attempts at getting the sample file when I test using the following instructions from the guide:

  [I]To view a sample movie:
  Choose Open URL in New Player in the player File menu and enter, for example, the following URL:
  rtsp://hostname/sample_300kbit.mov
  where hostname is the host name or IP address of your server.[/I]

When I do this on a client, the quicktime player starts connecting and then hangs, but it does trigger a hit on the server access log.

If I try to navigate to the URL containing the video, it prompts a download, not a stream.  DSS not using Port 80, Apache is.

When I disable the server Quicktime client reports that service is not available.  When I re-enable it remarks 'not found'.  In the past I have found it hangs on 'switching transports' but not recently.

Any ideas or what other information is required for a diagnosis.  I don't like admitting defeat, but I am close!

Thanks

I

---

### Post by lwwakeup on 2009-07-23
Hello Izziere:
I am a newby and am having the same problem.   Did you ever find a solution?

When I try to connect to my server which is running Darwin, I use the rtsp://serveraddress:port/directory/filename just to ensure that streaming is working properly, and the server evidently sends some information to my client computer because the length of the video file is properly indicated if I move the Quicktime playhead on the client.  However, the Quicktime window does not expand to the size of the video and there is no video or audio.  Quicktime on the client just hangs indefinitely.  (The Client is running Windows XP Pro.)

By the way, I don't know what I did at 1 am, but Quicktime on one client began receiving the stream from the server.  But, only this one client.  I can't get any other computers in the network to receive the stream.  Very strange.  I did not install anything on the one computer that mysteriously starting working.  Wonder what happened?

Thanks in advance for any help!!  I would like to stream a few .mov files.  

lw

---

