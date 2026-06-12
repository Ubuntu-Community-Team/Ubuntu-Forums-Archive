---
title: "HAMA remote config"
date: 2011-06-20
forum: Multimedia Software
---

### Post by Vevusio on 2011-06-20
being a linux newbie i painfully slowly managed to get my htpc/nas/git to run with ubuntu server and xbmc

everything seems fine now and (surprisingly) in xbmc the remote control works out of the box, what i'd like to do though is to map a shell script to a remote control (start) button when xbmc is not running

ultimately i want the START button on the remote to trigger a .sh that simply does "xinit xbmc"

i imagine i need some demon that runs in the background and reacts to key-events, however i could not find anything like this for the remote (most on the tutorials are on how to configure it for xbmc - which oddly just works for me)

my plan is to have the server auto-login upon start with an "xbmc" user (no login required, just logs in) that only has rights to the audio and video groups and has the remote-start-button-listener running to turn the media center on and off

any ideas are appreciated, ty

---

