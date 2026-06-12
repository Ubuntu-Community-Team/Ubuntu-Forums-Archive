---
title: "downloading flv video from rtmp address"
date: 2009-10-05
forum: Multimedia Software
---

### Post by onemanclapping on 2009-10-05
Hey there,

I want to download this flv video:

rtmp://video2.rtp.pt/flv/RTPFiles&file=/informacao/campanhabiana_42024.flv

Does anyone know how can I do it?

I tried the UnPlug plugin for firefox, but it didn't download the flv file, but a ".ext" instead...

Thanks in advance,

- onemanclapping

---

### Post by FrostDust on 2009-10-05
wget will download a file from a given address and put it in your home folder. In your case, use:

```
wget rtmp://video2.rtp.pt/flv/RTPFiles&file=/informacao/campanhabiana_42024.flv
```

If you dislike using the terminal for this, you can install gwget, which is just a GUI frontend for wget.

---

### Post by onemanclapping on 2009-10-05
> **FrostDust said:**
> wget will download a file from a given address and put it in your home folder. In your case, use:

```
wget rtmp://video2.rtp.pt/flv/RTPFiles&file=/informacao/campanhabiana_42024.flv
```


Thank you very much for your help, but when I do that, I get:

```
omc@omc-ubuntu-laptop:~$ wget rtmp://video2.rtp.pt/flv/RTPFiles&file=/informacao/campanhabiana_42024.flv
rtmp://video2.rtp.pt/flv/RTPFiles: Unsupported scheme.
[1] 8327
[1]+  Exit 1                  wget rtmp://video2.rtp.pt/flv/RTPFiles
omc@omc-ubuntu-laptop:~$ 
```

what can I do? :/

---

### Post by FrostDust on 2009-10-05
Try, like suggested at [Stack Overflow]("http://stackoverflow.com/questions/1024632/rtmp-is-there-such-a-linux-command-line-tool"), this command:

```
vlc -I dummy rtmp://live.site.com/loc/45/std_fc74a6b7f79c70a5f60.mp3 \
    --sout file/ts:output.mpg vlc://quit
```

Obviously, you'd need vlc installed first.

If that doesn't work, you can try installing WINE and using it to run the Windows program [Orbit Downloader]("http://www.orbitdownloader.com/Use-as-RTMP-Downloader.htm"). Although [according to Wikipedia]("http://en.wikipedia.org/wiki/Orbit_Downloader") it has some browser-hijacking behaviors, that should at most only affect browsers you run under WINE.

---

### Post by onemanclapping on 2009-10-05
Thanks all for you help, but I ended up using windows and Flv Recorder, as seen [here]("http://www.downloadatoz.com/howto/save-record-capture-flv-video-audio-steaming-through-http-rtmp-protocol.html").

---

### Post by feeela on 2011-03-23
rtmpdump worked for me…

```
rtmpdump -r rtmp://artestras.fcod.llnwd.net/a3903/o35/MP4:geo/videothek/EUR_DE_FR/arteprod/A7_SGT_ENC_04_043064-000-A_PG_HQ_DE?h=e266e4b9566e25236c607d0f3def9cce -o OUTPUT_FILENAME_HERE.flv
```

---

### Post by berperikemanusiaan on 2012-03-30
Curl worked for me in Ubuntu 11.10 as of 30 March, 2012:

```
curl rtmp://url/directory1/directory2/filename.mp4  -o saved_filename_curl.mp4
```

Wget does not support rtmp.  VLC QT4 gui worked once, and failed at the command line.

---

### Post by mraandtux on 2012-03-30
Try playing it on VLC 2.0, and then recording it.
sudo add-apt-repository ppa:n-muench/vlc

---

### Post by scicode on 2012-09-26
> **berperikemanusiaan said:**
> Curl worked for me in Ubuntu 11.10 as of 30 March, 2012:

```
curl rtmp://url/directory1/directory2/filename.mp4  -o saved_filename_curl.mp4
```

Wget does not support rtmp.  VLC QT4 gui worked once, and failed at the command line.

thanks, perfect solution

you :guitar:

---

