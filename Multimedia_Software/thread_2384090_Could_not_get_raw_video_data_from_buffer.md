---
title: "Could not get raw video data from buffer"
date: 2018-02-02
forum: Multimedia Software
---

### Post by narekkrean11 on 2018-02-02
My Os version is Ubuntu 16.04 LTS  and LibVlc version is 2.2.2-5. I have  a c++ project using LibVlc I am buffering audio and video data and then  read it from buffer. I want to get raw data that is why i use RV24 or  RV32 Video codecs in my program but video data does not come. For  example when I use Video codec SVQ1 I get some video data. This problem  comes from LibVlc version and it works on Ubuntu 14.04 but not on 16.04.I asked this question in VideoLan forums and in Stackoverflow but still have no answer. Is there any idea how this issue could be  fixed. Thanks in advance I will appreciate any help.```
int StreamGrabberSetMedia(VlcStreamGrabber * pGrabber, libvlc_media_t * pMedia, bool paceControl)
{
    char vcodec[] = "RV32";
    char acodec[] = "s16l";
    char pszOptions[1024] = {0};
    libvlc_event_manager_t * pEventManager = NULL;

    if (pGrabber == NULL || pMedia == NULL) return VLC_ENOITEM; 

    sprintf_s( 
        pszOptions,
        1024,
        ":sout=#transcode{"
             "vcodec=%s,"
             "acodec=%s,"
             "threads=2,"
        "}:smem{"
            "%s,"
            "audio-prerender-callback=%lld,"
            "audio-postrender-callback=%lld,"
            "video-prerender-callback=%lld,"
            "video-postrender-callback=%lld,"
            "audio-data=%lld,"
            "video-data=%lld"
        "}",
        vcodec,
        acodec,
        (paceControl ? "time-sync" : "no-time-sync"),
        (long long int)(intptr_t)(void*) &AudioPrerender,
        (long long int)(intptr_t)(void*) &AudioPostrender,
        (long long int)(intptr_t)(void*) &VideoPrerender,
        (long long int)(intptr_t)(void*) &VideoPostrender,
        (long long int)(intptr_t)(void*) pGrabber,
        (long long int)(intptr_t)(void*) pGrabber
    );
}
```

---

### Post by mörgæs on 2018-02-03
Hi, welcome to the fora.

> **narekkrean11 said:**
> This problem  comes from LibVlc version and it works on Ubuntu 14.04 but not on 16.04.

Have you tried how it works in a live boot of 17.10.1?

---

### Post by narekkrean11 on 2018-02-09
Thanks for answer but i need this to work on 16.04 i write some program which must work on all Ubuntu versions

---

### Post by mörgæs on 2018-02-11
On the way to 'need to work' you have to gather knowledge and narrow down the problem. 

That could for example come from trying various other releases

---

### Post by narekkrean11 on 2018-02-12
Oh i now where the problem comes from...when i buffer the video i encode  it and when i want to read it from buffer i decode it. In program I use  libVlc api and  when VLC compiles function smem does not work correctly when i use RGB on Ubuntu 16.04(they change sours code and in this Ubuntu version VLC compiles the other way) this problem could be fixed by VideoLan developers or  by Ubuntu developers

---

### Post by mörgæs on 2018-02-13
> **narekkrean11 said:**
> ...this problem could be fixed by VideoLan developers or  by Ubuntu developers

...or the problem could already be fixed in a recent Ubuntu release.

---

