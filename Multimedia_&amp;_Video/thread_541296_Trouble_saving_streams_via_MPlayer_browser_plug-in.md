---
title: "Trouble saving streams via MPlayer browser plug-in"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by thousandrobots on 2007-09-02
What is the correct procedure for saving streaming video to a file via the MPlayer plug-in for Firefox?

In /etc/mplayerplug-in.conf, i have:

download=1
dload-dir=$HOME/mplayer
keep-download=1
noembed=1

I have also added these same lines to ~/.mplayer/config, but I don't think it matters there.

I am using MediaPlayerConnectivity, as well.

The directory "mplayer" exists in my home directory, and is writable.

In the MediaPlayerConnectivity config, I have this setting for Windows Media:

/usr/bin/X11/gmplayer

I can play .asf streams just fine. However, I was hoping the above configuration would be enough to result in the streams automatically being dumped into a file in the specified directory. But that's not happening. What else do I need to do?

My set up:
Feisty
Mplayer
MediaPlayerConnectivity 0.8.3
Firefox 2.0.0.6

One more twist: 90% of the media streams I want to download are on a site that requires registration (cookies), which is why I was hoping I could get the browser plug-in to just dump the files, rather than relying on command line approaches.

I have done a bit of Googling and searching these threads, but haven't found anything that solves the problem. Any ideas?

Thanks.

(One thing I will try in the meantime is extracting URLs from the streams and dropping them into the command line, but given the cookie requirements for the sites, I am not sure that will do me much good.)

---

