---
title: "streamlink for live BBC stopped working."
date: 2017-10-19
forum: Multimedia Software
---

### Post by ajgreeny on 2017-10-19
I have been using streamlink for live streaming of BBC programmes since get-iplayer stopped working for live streams a while ago.

A few days ago it became necessary to use a BBC username and password added to the command, which I successfully did and then used the live streaming service, but since yesterday those are no longer accepted, even though I know they are correct, as I still login to the BBC's web pages with them.
Command used which was fine previously.
```
streamlink --bbciplayer-username *username* --bbciplayer-password *password* -p vlc --default-stream 544k_alt www.bbc.co.uk/iplayer/live/bbcone
```

I imagine this is a bit of a longshot, but has anyone else seen this problem and managed to solve the username/password failure?
The error I see is
```
[plugin.bbciplayer][error] Could not authenticate, check your username and password
error: No playable streams found on this URL: www.bbc.co.uk/iplayer/live/bbcone
```
The final error is not really correct as you can use a web-browser to go there and play in iPlayer but it uses too many resources on a low spec machine and is thus almost unusable.

---

