---
title: "Spotify Linux using 12GB of RAM then crashes"
date: 2012-05-06
forum: Multimedia Software
---

### Post by pkkid on 2012-05-06
I have been using Spotify Linux for about a week now on Ubuntu 12.04.  Just today after starting Spotify I see my memory ramp up to use all 12GB (takes about 15s) in my system then crash out.  If I start Spotify from the command line I get the following:

```
00:01:55.039 I [breakpad.cpp:61] Registered Breakpad for product: spotify

00:01:55.039 I [translate.cpp:130] Reloading language file
00:01:55.041 I [breakpad.cpp:200] Searching for crashdumps: /home/mjs7231/.cache/spotify/*.dmp

00:01:55.170 A [CefModule.cpp:324] Check failed: g_cef_handle: 
00:01:55.211 I [offline_authorizer.cpp:307] Unable to login offline: no such user
00:01:55.327 I [ap:1787] Connecting to AP C1.spotify.com:4070
00:01:55.416 I [ap:1244] Connected to AP: 193.182.8.36:4070
third_party/tcmalloc/chromium/src/system-alloc.cc:423] SbrkSysAllocator failed.
third_party/tcmalloc/chromium/src/system-alloc.cc:423] MmapSysAllocator failed.
third_party/tcmalloc/chromium/src/system-alloc.cc:423] SbrkSysAllocator failed.
third_party/tcmalloc/chromium/src/system-alloc.cc:423] MmapSysAllocator failed.
Segmentation fault
```

---

### Post by kostkon on 2012-05-06
For a start, try deleting your ~/.cache/Spotify folder and restart spotify.

---

### Post by pkkid on 2012-05-07
> For a start, try deleting your ~/.cache/Spotify folder and restart spotify.
I tried this, and get the same result.  it takes about 15-20 seconds or so for the ram usage to hit its peek of 12GB.

One interesting thing I noticed is if the current memory consumption of other apps is very low, Spotify can actually start.  I notice the ram raise up to very close to 12GB then drop down again to about 6GB.  Spotify is able to start and I am able to jump into the settings.  I tried unchecking the "Crossfade Tracks" setting as that's all I can remember changing. However, upon clicking this option, Spotify's ram spiked past 12GB again and crashed.

I assume it's crashing out because I have no swap space for ram to hit once my HW memory is used.  However, Spotify shouldn't be using anything even close to this.

---

### Post by kostkon on 2012-05-07
> **pkkid said:**
> I tried this, and get the same result.  it takes about 15-20 seconds or so for the ram usage to hit its peek of 12GB.

One interesting thing I noticed is if the current memory consumption of other apps is very low, Spotify can actually start.  I notice the ram raise up to very close to 12GB then drop down again to about 6GB.  Spotify is able to start and I am able to jump into the settings.  I tried unchecking the "Crossfade Tracks" setting as that's all I can remember changing. However, upon clicking this option, Spotify's ram spiked past 12GB again and crashed.

I assume it's crashing out because I have no swap space for ram to hit once my HW memory is used.  However, Spotify shouldn't be using anything even close to this.
Close spotify and delete the ~/.config/Spotify folder to reset your preferences and see if that changes anything.

---

### Post by pkkid on 2012-05-07
This evening I uninstalled spotify-client, deleted my ~/.config/spotify folder, then reinstalled spotify-client. This seems to have resolved the memory issues (who knows for how long).

Thanks for the information.  I suppose things I should have really tried on my own before coming here. :D

---

