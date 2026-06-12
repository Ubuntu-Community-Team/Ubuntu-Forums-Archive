---
title: "Channel surfing script"
date: 2010-06-29
forum: Multimedia Software
---

### Post by quequotion on 2010-06-29
I put together a shell script to surf channels with ivtv-tune and an xawtv channel map.

If you have a capture card, install **ivtv-utils** to get ivtv-tune.

Don't bother with xawtv, just install the scanner **scantv** and use it to make the file: ~/.xawtv

I also recommend to install NotifyOSDconfig (google the ppa). I set notifications to 1 second timeout to keep up with my channel surfing and be generally less annoying.

```
#! /bin/bash
# This script changes channels using ivtv-tune and an xawtv channel map, but xawtv is not required. 

# Get the last channel
CHANNEL=`cat ~/.tvchannelrc`

case "$1" in
	up) # Surf channel up if mapped.
		CHANGE="`expr $CHANNEL + 1`"
		echo $CHANGE > ~/.tvchannelrc
	;;
	down) # Surf channel down if mapped.
		CHANGE="`expr $CHANNEL - 1`"
		echo $CHANGE > ~/.tvchannelrc
	;;
	*) # Switch to named or numbered channel if mapped.
		CHANGE="$1"
	;;
esac

notify-send --icon=gtk-info --urgency=critical --expire-time=1000 "Channel $CHANGE" "`ivtv-tune -x $CHANGE`"
```

If you want to use this:
Save the above code as a text file:```
/usr/local/tvchannel
```Give it executable permission:
```
sudo chmod +x /usr/local/tvchannel
```

The best thing to do with this script is to assign it to some hotkeys. This way you can channel surf no matter what front end you use to watch the video stream; even when the video is in the background.

See included screenshots, changing the channel with hotkeys on a multi-media keyboard. I used WinKey+MediaKeyNext (aka Super+XF86AudioNext) and WinKey+MediaKeyPrevious (aka Super+XF86AudioPrev).

While typing this post I changed the channel a few times to get the two messages, "Signal Detected" and "Channel # not defined". Note the display of totem, behind the translucent firefox window, streaming video from PVR.

---

