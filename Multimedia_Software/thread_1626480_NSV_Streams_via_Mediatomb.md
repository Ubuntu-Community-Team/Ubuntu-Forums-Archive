---
title: "NSV Streams via Mediatomb"
date: 2010-11-20
forum: Multimedia Software
---

### Post by hibliss on 2010-11-20
I had this setup and working before with some help, so I know it is possible.

I want to use Mediatomb to transcode a Shoutcast NSV stream on the fly so I can watch it on my Playstation. I know I can use both mencoder/mplayer and VLC for the transcoding.

I am running Ubuntu server 9.04 with the latest Mediatomb from the repo.

Thanks in advance.

---

### Post by Blues- on 2010-11-20
I'm doing exactly that on my server ..
but I'm using ffmpeg to transcode the sopcast stream ..

I can post my setup details if you want.

---

### Post by hibliss on 2010-11-20
I would love that. I can work with what you post.

---

### Post by Blues- on 2010-11-20
First of all .. make sure that ffmpeg and sp-sc (The sopcast cli binary) is installed.

1) Download the sopcast-start and sopcast-stop scripts I've created from here [http://konni.com/~konni/mediatomb/](http://konni.com/~konni/mediatomb/)
place the into /usr/local/bin and chmod +x

2) Do the same with the mediatomb-video-generic script and place it into /usr/local/bin and chmod +x.  You might need to adjust the script to where you have ffmpeg installed.
You can adjust the "threads" parameter to 2 if you have a dual core machine (my server is quad core) or take this directive out if you have an old cpu.

3) Edit the mediatomb config.xml, add "<transcode mimetype="video/sopcast-x-ms-wmv" using="video-generic"/>" into the "<mimetype-profile-mappings>" section, and add this
```
 <profile name="video-generic" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/usr/local/bin/mediatomb-video-generic" arguments="%in %out"/>
        <buffer size="24000000" chunk-size="1024000" fill-size="120000"/>
      </profile>

```
into the transcoding profiles and save the file.

4) Goto the mediatomb web ui, click on videos, click the plus sign to add new item, fill it out like this ..
```
 
 External Link (URL)
 Title: Sopcast
 URL: http://127.0.0.1:9999
 Protocol: http-get
 Class: object.item.videoItem	
 Description: Sopcast
 Mimetype: video/sopcast-x-ms-wmv
```

now you are all set ..
to watch sopcast via mediatomb ..
ssh to your box, type in "sopcast-start $url" where $url is the actual sopcast link .. 
then on your mediarenderer click the sopcast link and you should see the stream.

When you are finished wathing .. ssh again into your box and type in "sopcast-stop" to kill all sopcast streams (sp-sc) on the machine 

Cheers,
Blues-

---

