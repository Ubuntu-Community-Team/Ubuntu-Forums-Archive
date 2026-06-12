---
title: "Spotify native won't start"
date: 2011-07-31
forum: Multimedia Software
---

### Post by ukblacknight on 2011-07-31
Basically as it says in the title.  The second to last update about 6 or 7 weeks ago broke Spotify native.  I get the following error  message in the terminal:


```
tom@blacknight:~$ spotify
15:56:35.913 I [breakpad.cpp:36] Registered Breakpad for product: spotify

15:56:35.914 I [translate.cpp:117] Reloading all languages
15:56:35.914 I [fsevents:403] starting polling thread
15:56:35.931 I [breakpad.cpp:94] Searching for crashdumps: /home/tom/.cache/spotify/*.dmp

QDBusArgument: write from a read-only object
15:56:36.253 I [ap:1374] Connecting to AP B3.spotify.com:4070
15:56:36.288 I [upnp:517] 192.168.1.1: got external ip 0x51663686
15:56:36.292 I [ap:924] Connected to AP: 78.31.8.43:4070
15:56:36.300 I [upnp:465] 192.168.1.1: mapping add ok
15:56:36.306 I [upnp:491] 192.168.1.1: Port 21238 mapped OK
Segmentation fault
```

Has anyone else experienced this?  Anyone know of a fix?

Thanks in advance!

Ubuntu 11.04 x64 (classic desktop)

---

### Post by Bordee on 2011-08-12
I've been having problems with Spotify Native Linux Client crashing on me as well. Since the linux version is a preview version, it might be expected to have to grapple with bugs.

I found a work around that isn't pretty, but it gets the job done.

1. Delete the ~/.cache/spotify folder. You can either do this through nautilus, or through the terminal command rm -rf (be careful though).

2. Start Spotify in the terminal. You'll probably have to log in since that info has been forgotten.

3. The welcome to Spotify popup might block you from getting into Spotify. Unfortunately, there appears to be no way of clicking on the popup and closing it. To get around this, go to File > Exit in the Spotify menu.

4. Start Spotify again in the terminal. This time it remembers you login details, and it doesn't throw the popup at you. 

5. Use Spotify for however long you desire and exit. Now, try opening Spotify application without the terminal. If you're lucky, it should open and work. It might throw an error message and ask you if you want to send a crash report. Hit send or skip. It should let you into Spotify, however. 

6. Once Spotify launcher stops working, go back to step 1 and repeat.



Does anyone know a better workaround for this?

---

### Post by ukblacknight on 2011-08-13
> **Bordee said:**
> I've been having problems with Spotify Native Linux Client crashing on me as well. Since the linux version is a preview version, it might be expected to have to grapple with bugs.

I found a work around that isn't pretty, but it gets the job done.

1. Delete the ~/.cache/spotify folder. You can either do this through nautilus, or through the terminal command rm -rf (be careful though).

2. Start Spotify in the terminal. You'll probably have to log in since that info has been forgotten.

3. The welcome to Spotify popup might block you from getting into Spotify. Unfortunately, there appears to be no way of clicking on the popup and closing it. To get around this, go to File > Exit in the Spotify menu.

4. Start Spotify again in the terminal. This time it remembers you login details, and it doesn't throw the popup at you. 

5. Use Spotify for however long you desire and exit. Now, try opening Spotify application without the terminal. If you're lucky, it should open and work. It might throw an error message and ask you if you want to send a crash report. Hit send or skip. It should let you into Spotify, however. 

6. Once Spotify launcher stops working, go back to step 1 and repeat.



Does anyone know a better workaround for this?

I can't even get this to work :(  If it wasn't for the fact I use Spotify on my phone a lot, I'd have cancelled my subscription because of this.

---

