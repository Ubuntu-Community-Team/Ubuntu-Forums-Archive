---
title: "Unable to play .FLV files using VLC or MPlayer"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by jd47 on 2007-03-25
Hi,

I'm unable to view .FLV files using either VLC or MPlayer although I can here sound. I've also tried to convert the .FLV files to mpeg using ffmpeg but this returns an error:

```
[flv @ 0xb7f1bc30]Unsupported video codec (4)
```

I'm running xubuntu 6.10. With the latest updates, I've searched the forums and installed all the codec's that were suggested. Any idea's anyone?

Thanks for your help,
Jon.

---

### Post by chriswyatt on 2007-03-25
They should work using VLC Media Player, VLC uses its own codecs I think.  Sometimes I find that certain VLCs don't play or cut out partway through with VLC.

---

### Post by louis_nichols on 2007-03-25
That is strange. It's interesting how, because things wotk for me, I never wondered why that is. My Totem behaves just like yours, but vlc displays the images too, when it comes to flv.

The question here is wether you have video from other files, with vlc. Files like avi, or wmv or something. My idea is that this might not be a flv-related issue, but rather something to do with the way the video output for vlc is set.

If you open vlc and go to Settings>Preferences>Video>Output modules, you can make a selection there (make sure the checkbox "Advanced options" in the bottom right of the screen is checked). That can make the difference. I know I had moments with only sound because of changing that option.

---

### Post by jd47 on 2007-03-25
Hi,

Thanks for the quick response.

I can play WMV, AVI and MPEG perfectly on both VLC and MPlayer. I've reinstalled both programs a few times with the same results and I've also tried gxine but that doesn't even try to play the file.

---

### Post by louis_nichols on 2007-03-25
What version of vlc are you using? Is it up-to-date? What is the output of the command

dpkg -l | grep vlc
?

---

### Post by jd47 on 2007-03-25
dpkg -l | grep vlc

```
root@jon-laptop:/home/jon# dpkg -l | grep vlc
ii  libvlc0                                    0.8.6-svn20061012.debian-1ubuntu1.1  multimedia player and streamer library
ii  mozilla-plugin-vlc                         0.8.6-svn20061012.debian-1ubuntu1.1  multimedia plugin for web browsers based on 
ii  vlc                                        0.8.6-svn20061012.debian-1ubuntu1.1  multimedia player and streamer
ii  vlc-nox                                    0.8.6-svn20061012.debian-1ubuntu1.1  multimedia player and streamer (without X su
ii  vlc-plugin-esd                             0.8.6-svn20061012.debian-1ubuntu1.1  Esound audio output plugin for VLC
root@jon-laptop:/home/jon# 
```

---

### Post by louis_nichols on 2007-03-25
Just as I feared. It's the exact same version I have, and I have no problems with flv files.

One last thing to ask: might it be the file? I mean, has this happened with more than one flv file? You should try downloading another one. It might just be a bad file (the error message you get doesn't suggest this, but it is the only other thing I can think of at this point.)

EDIT: another idea: you are using the svn version of vlc. Mine is the official one. So that might be another cause. I used to download the svn version too, but it was too unstable to make it worth the extra features (which I wasn't using anyway). So that might be another reason why it doesn't work for you. If the above doesn't work, I suggest you revert to the official one in the edgy repos and then try opening flv's again.

---

### Post by jd47 on 2007-03-25
Hi Louis,

You were right, it was the files I was downloading from [www.spikedhumor.com](www.spikedhumor.com) and they weren't working. I tried from [www.youtube.com](www.youtube.com) and they're working fine in both VLC and MPlayer!

Man I wasted some time on that one :) 

Thanks for your help,
Jon.

---

### Post by louis_nichols on 2007-03-25
Glad it's sorted ;)

---

