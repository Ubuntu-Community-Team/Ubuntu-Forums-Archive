---
title: "Totem's Xine config file"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by gaelfx on 2007-07-13
Recently, I accidentally made Firefox always open Totem for any RMVB file that is sent my way. If anyone knows how to undo this, information would be greatly appreciated, however, this is not the topic of my thread.

I figured I would fix it so that Totem could play the RMVBs, since I had heard that it might be able to. I installed the Xine backend (which I must say is a far superior initial setup than GStreamer since it can actually use the "Play Disc" function in its menus), and still RMVB does not work, which is not surprising since it is a proprietary codec. After a little research I discovered I had to get the MPlayer codecs and edit Xine's config file. This task proved difficult because they do not tell you on Totem's website that Xine doesn't have its own config file, they only point you to Xine's website, which assumes that Xine DOES have its own config file. Long story short: To access the config file for Totem's Xine interface:

```
sudo gedit /.gnome2/totem_config
```

This is probably the same as the one for Totem's GStreamer, but that seems strange to me that the two backends are mutually exclusive. Couldn't they make two config files? At any rate, I made it look for my Real codecs in the appropriate folder and started up a stream from Firefox. It didn't work!

Back to Google, I found a bug report:
[Totem Xine Config File Bug]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/124726")
Which decries exactly the problem I'm having. Not surprising as this has been happening ever since I installed Ubuntu (its actually rather comforting at this point, I feel like I haven't royally screwed it up yet or anything). Well, I edited the file again (mine had also reverted upon starting Totem) and restarted the computer. I checked the file, and it had not been reverted, so I thought maybe it would work. In the words of Charles Bronson, "No dice." So I'm thinking to myself that this problem must be related to Totem loading some older config file (how else could it revert exactly to the pre-edited version?), but now I can't seem to find this older version of that file from which Totem reloads.

 Can anyone help me find it or figure out why/how Totem does this? I know you'll tell me to go to the launchpad bugs site and contribute, but my experience there is that these kinds of problems get little attention there.

---

### Post by gaelfx on 2007-07-16
Well, I found the solution to the first part of my problem in another post

```
gconf-editor
```

is used to change the handling of certain URL types. Go to Desktop->Gnome->url-handlers to change actions on rtsp:// pages, but the issue with Totem's config file persists. Does the same problem occur with GStreamer? Can anyone confirm/deny this? Really, any input would be welcomed.

---

### Post by rootie on 2007-07-16
Hey there,

I solved my RMVB problem by installing the Medibuntu codecs. [Check it out here]("https://help.ubuntu.com/community/Medibuntu/#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

---

### Post by gaelfx on 2007-07-16
Well, thanks for the info. I got the libraries and added the W64Codecs from Synaptic, but it still seems not to work. I'm going to try rebooting, but to be really honest, I'm not terribly hopeful. Good find though, Medibuntu has some interesting stuff in it, thanks!

---

### Post by gaelfx on 2007-07-17
I guess I should have read the beginning of the config file because it turns out you have to uncomment a line for it to become effective. However, the issue still remains that Totem believes it has no codecs for Real Video 4.0. Is this codec not available yet or am I doing something wrong here?

---

