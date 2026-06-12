---
title: "Native Spotify for Linux"
date: 2010-10-12
forum: Multimedia Software
---

### Post by eddyojb on 2010-10-12
Hi all,

I'm struggling to get the native Spotify on Ubuntu 10.10 working. I haven't tried it on any other version so I'm not sure if it's exclusive to 10.10.

Basically, the application loads fine, until I hover over to the left-hand side bar (playlists etc), at which point it crashes and *poof* instantly closes down. I have no idea what the problem is. Otherwise it's a waste of an application but it just integrates better into my Ubuntu so would appreciate any ideas!

Ed

Additional Notes: Output from terminal:


edward@edward-VGN-NS20Z-S:~$ spotify

[1] 6721
02:14:30.472 I [offline_authorizer.cpp:156] Unable to login offline: no such user
02:14:30.769 I [ap:1387] Connecting to AP B3.spotify.com:4070
02:14:30.823 I [ap:937] Connected to AP: 78.31.12.9:4070
02:14:31.502 I [upnp:515] 192.168.0.1: got external ip 0x52021074
02:14:31.710 I [upnp:463] 192.168.0.1: mapping add ok
02:14:31.862 I [upnp:489] 192.168.0.1: Port 49544 mapped OK
[1]+  Done                    rm ~/.cache/spotify/offline.bnk
Segmentation fault


No real clues :(

---

### Post by lodravah on 2010-10-13
Yeah, I'm having the same issue. this seems to have helped some people: [http://getsatisfaction.com/spotify/topics/spotify_linux_preview_crashes_on_k_ubuntu_10_04_after_first_start_on_config_file_load](http://getsatisfaction.com/spotify/topics/spotify_linux_preview_crashes_on_k_ubuntu_10_04_after_first_start_on_config_file_load)

But not me :(

Still looking for some answers. Until then I run it in Wine.

-lodravah

Edit: Hey, seems as long as you avoid mousing over the left pane (especially the albumart-section) it works fine. So far the play/pause seems to work fine too as long as you carefully mouse up from the bottom of an unmaximized window. Now that was a sentence I have never written before :) Try it!

---

### Post by eddyojb on 2010-10-13
Yeh I noticed that too, using the tab button to navigate seems a bit senseless though when wine runs it fine!I was just expecting a bit more desktop integration with the native version but you can't even play local files! Though on wine you can play locally stored music through a mini-hack you can find kicking about, works great!

WINE all the way.

---

### Post by LakesideLoafer on 2010-10-14
Got exactly the same problem myself. Spotify Linux Preview has always worked flawlessly until I just upgraded from 10.04 to 10.10. Tried the various workarounds but none seem to work. :(

---

### Post by mandz on 2010-10-30
Update manager tells me of an update to the native Spotify client - 1.04.7... to 1.04.8... can't find any changelogs but perhaps this fixes compatibility with 10.10? 

If anyone has updated and is on 10.10 I'd be interested to know as this is one of the things stopping me from upgrading from 10.04!

---

### Post by antimirov on 2010-10-30
mandz,

Yes, this update fixes it.

---

### Post by mandz on 2010-10-31
Awesome, thanks for letting me know. I shall be upgrading.

---

