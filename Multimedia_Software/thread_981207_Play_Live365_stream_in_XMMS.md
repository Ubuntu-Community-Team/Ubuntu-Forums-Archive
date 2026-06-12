---
title: "Play Live365 stream in XMMS"
date: 2008-11-13
forum: Multimedia Software
---

### Post by tgalati4 on 2008-11-13
Hello all,

I couldn't find this posted anywhere else.  Streamtuner is not supported anymore and it doesn't parse Live365 streams or Shoutcast streams anymore.

One can play [www.live365.com](www.live365.com) streams in firefox using a flash player-9 or greater.

If you have an older machine and want a low-overhead music stream, then you can use xmms to play the stream.  For instance a Pentium 1, 166 MHz, 64 MB HP Omnibook 5700CT running DSL.

The trick is getting the stream address.

At the bottom of the [www.live365.com](www.live365.com) site there is a "Listen Settings" tab.

In that tab are settings for Web Player Options:  Choose Additional Options "Show"

Choose MP3 Desktop player.

Click the ad filters to reduce the chatter.

Perform a search on an artist and select a stream.  You will get a "play.pls" file.  Save this file and rename with a meaningful radio name.

For example quartet_radio.pls

Open with xmms and enjoy.  Install w32codecs (if legal in your area) to decode the mp3pro streams.

The stream is kind of ugly:

```

[playlist]
NumberOfEntries=1
File1=http://www.live365.com/play/312423?auth=d2e64adc243071ac76a6d8d103a6afb3-1226634525-quartet4ever&tag=live365&token=0a7a717a7cdfd5ca61340c6f9f8119b5-4819130080400000&sid=**.**.250.25-1226512941889198&lid=803-usa&from=pls



```

Hope this reduces the agony units for playing internet radio on older machines.

---

