---
title: "mt-daapd, mediatomb, ffmpeg and libavcodec"
date: 2009-10-18
forum: Multimedia Software
---

### Post by cavetroll on 2009-10-18
Hi there

I have a problem and I hope somebody can help me out.
I`m running Ubuntu 9.04 server 64-bit. I recently compiled and installed mediatomb0.12 using this guide: [http://wiki.flexion.org/InstallingMediaTomb012.html](http://wiki.flexion.org/InstallingMediaTomb012.html)
It took some time to compile and get ffmpeg to work. I had to remove the libraries libavcodec, libavcodec52 and libavutil49 prior to compiling ffmepg as the latest source would not work with the one from the repositories. So far so good. Everything worked fine.
I then re-installed a service called mt-daapd which can publish a specific folder to appear as a Shared Library in iTunes. This package depends on libavcodec, libavcodec52 and libavutil49. Those libs get installed in /usr/lib. As soon as they are there, ffmpeg is broken. I get this error message: ffmpeg: symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet
I really don`t know what`s going on as it points to the correct lib in /usr/local/lib. There must be a problem with library linking or something, I guess. I`m no Ubuntu expert, but shouldn`t it be possible for local libs to co-exist with system wide libs? When I uninstall libavcodec libs from /usr/lib and re-install ffmpeg, it is working again. But that automatically removes mt-daapd.
I guess the same would happen if I`d install any other package (like vlc...) that is dependent on those libav*-libs in /usr/lib
Can you see my dilemma? This is driving me nuts as I can`t find a solution for this. How can I tell mt-daapd to use the libraries in /usr/local/lib and don`t install its dependencies?

Any help or advice would be highly appreciated.
Thanks

---

### Post by cavetroll on 2009-10-20
*Bump*
So nobody can tell me how to compile mt-daapd to use the local libraries...? Really sad... :(
Or is there an alternative service that does a similar thing to mt-daapd...?

---

### Post by buntunoob on 2009-10-22
I pulled this from [http://wiki.fireflymediaserver.org/Quickstart_Tarball](http://wiki.fireflymediaserver.org/Quickstart_Tarball)
 
If your id3tag headers or libraries are not in /usr/include and /usr/lib, then you must use the --with-id3tag= to help the configure system locate those. For example, on Mac OSX, using libid3tag installed from fink, the id3tag headers are in /sw/include, and the libraries are in /sw/lib. The appropriate configure command would be "./configure --with-id3tag=/sw". You might also want to install libid3tag-devel to have this header file.

---

### Post by cavetroll on 2009-10-31
Thanks for your reply. I managed to install the tarball version. Unfortunately this version is a bit older than the one that comes with the Ubuntu 9.04 repositories. I would really like to install an up-to-date version. Does anyone know where I can find the sourcecode to compile mt-daapd on 9.04 myself? I also haven't been able to get the tarball version to run as a service on startup.
Thanks

---

### Post by Remix_88 on 2009-12-08
Hi,

I'm the guy from Flexion.Org.

I'm just rebuilding my Mediatomb and Firefly servers. I'll be updating my wiki in the coming days with the full details of what I've done.

That said, I have based my new servers on Karmic because the mt-daapd package (and others I've looked at) are now aware of the ffmpeg extra/unstripped libraries. 

Compiling Mediatomb from source on Karmic is much easier since all the build dependencies can be met from -dev packages in the official repos :-)

Regards, Martin.

---

### Post by cavetroll on 2009-12-08
Hi Martin

Many thanks for your reply. That sounds great! I'll update my box!
Here's looking forward to reading your new blog posts ;)

Regards
Tom

---

### Post by buntunoob on 2009-12-08
@Remix a Huge TY for your Howto...

---

