---
title: "Need help in running Darwin Streaming Server on ubuntu"
date: 2007-06-27
forum: Multimedia Production
---

### Post by yinglcs2 on 2007-06-27
Hi,

I am trying to run Darwin Streaming Server on ubuntu.  Here is what I did:
1. execute 'DarwingStreamingServer'
2. check if port 554 is being listened:
```

netstat -na | grep 554
tcp        0      0 0.0.0.0:554             0.0.0.0:*               LISTEN     
```

3. try to hit it with vlc:
```

$ ./vlc rtsp://127.0.0.1:554/sample_300kbit.mp4
```

But i get this error:

```
[00000313] live555 demuxer error: Failed to connect with rtsp://127.0.0.1:554/sample_300kbit.mp4
[00000314] main access error: no access2 module matched "rtsp"
[00000312] main input error: open of `rtsp://127.0.0.1:554/sample_300kbit.mp4' failed: could not create access: no access2 module matched "rtsp"
[00000311] main interface error: option errors-dialog does not exist
End Inside libvlc_InternalAddIntf
```


Can you please tell me why I cant' see the sample from Darwin?
Thank you.

---

### Post by dillbertdabomb on 2007-07-04
Wish I could help, but I get a messsage saying that the user qtss couldent switch so it doesn;t start

---

### Post by SmallAxe on 2007-07-05
Can you please tell me why I cant' see the sample from Darwin?
Thank you.

        -yinglcs2:

        Couple of quick questions: 1. What version of Darwin are you  running?

                                                   2. What version of VLC?

                                                   3. When you installed VLC was it from source or Binary package?

       (just tried setting this up in house, got it to work, installed as root instead of su)

---

### Post by shuaibe on 2007-07-06
Have you installed VLC with --enable-live555 & --enable-realrtsp support ?

I have another problem: Iam able to stream the sample files on the Darwin Streaming Server but when i add my own files, which are hinted, RTSP DESCRIBE returns 404 Not Found! Iam also using VLC on the client side. Any suggestions ?

---

### Post by emartinez on 2007-07-06
yinglcs2,

Quick question, did you install DSS from a binary package in the repositories, or from source?
If it was from the repos I would recommend uninstalling that package, and installing the latest Darwin build from source, just make sure you install it using sudo, or as root.

dilbertdabomb,

Are your movies in the /usr/local/movies and is the ownership and permissions similar to the other QT sample files in that directory?

---

