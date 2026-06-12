---
title: "I got my blu-ray movies to play on Linux! (ATI Video Card)"
date: 2010-05-05
forum: Multimedia Software
---

### Post by MitchLeBlanc on 2010-05-05
Hey guys, so I got Blu-Ray to play on my computer today perfectly, no video lag, no color distortion, etc.

I just want to outline the steps I used, very briefly, in case it can help someone else!

My specs:

AMD Athlon X2 2400+
4GB Ram
ATI Radeon 4850
Creative xFi

First, in order to have a video player with hardware acceleration for my ATI card I had to compile a version of Mplayer-vaapi (where vaapi is the video acceleration api, I think). Before that though, I had to install libVA. I had some trouble compiling libVA from source, so I found a repository which had some binaries: [http://ubuntuupdates.org/ppas/24](http://ubuntuupdates.org/ppas/24)

I enabled that binary

```
sudo add-apt-repository ppa:nilarimogard/webupd8
```and then:

```

sudo aptitude update
sudo apt-get install libva1 libva-dev
```I then navigated to a page with some mplayer-vaapi tarbells and followed the intructions: [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/]("http://www.splitted-desktop.com/%7Egbeauchesne/mplayer-vaapi/")

Now we have our player setup!

I followed a guide on how to stream BluRay movies with MakeMKV: [http://themediaviking.com/software/bluray-linux/](http://themediaviking.com/software/bluray-linux/)

Once the file was streaming, I CD 'd into the directory where the complied mplayer-vaapi was relaxing. For me, that was /home/mitch/Source/mplayer-vaapi-20100414/mplayer-vaapi/

And to play the movie (I was playing Sunshine), the command which worked for me was:

```
./mplayer -fps 23.976 -cache 8192 -lavdopts threads=2 -fs -vo xv -va vaapi http://STREAMURLHERE
```The thread command is because I have a dualcore processor, you can drop that or adjust as necessary. Note that I had to play around with the track numbers of the stream, the MakeMKV guide says the stream url is: "http://localhost:51000/stream/title0.ts ", however with Sunshine, I found that title2.ts was actually the movie, the other numbers were bonus features and such.

Sorry for writing this quickly and perhaps poorly, but hopefully it helps someone!

---

