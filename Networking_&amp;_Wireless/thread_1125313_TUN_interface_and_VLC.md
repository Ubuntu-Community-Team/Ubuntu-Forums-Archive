---
title: "TUN interface and VLC"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by bruxodasilva on 2009-04-14
Hi!

I'm trying to streaming a video using VLC to a laptop.

I'm using click modular router, because the main point of this experience is to create a new protocol for multicast of video streaming. Click modular router intercept the packet that arrive at the wireless interface, do some king of processing and them delivers the packet to the kernel using the TUN interface. Then VLC should receive the packets and play the video.

The problem is that, although I can see through wireshark that click is passing the packets to TUN interface, VLC don't receive any packet... I already did: ```
chmod 0666 /dev/net/tun
``` but VLC continues not to receive packets.

That else do I need to do so that VLC can read packet from TUN interface?

I also try it on OpenSUSE, and everything just works...

Can you help?

Thanks in advance!

---

