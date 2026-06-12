---
title: "Unstable video with a Logitech Quickcam Pro 9000"
date: 2009-04-25
forum: Multimedia Software
---

### Post by gee42 on 2009-04-25
I wasn't sure whether this should be under hardware or media/video so apologies in advance.

I have a Logitech Quickcam Pro 9000 and when I try to use Skype video the picture I send (and can see when using the video test feature in the 'video devices' option screen) is unstable. I can see an image but the picture breaks up in the horizontal plane jerking left and right many times a second.

In trying to resolve this I've tried testing with cheese, luvcview and Ekiga.

I could not get cheese to display the output from the camera: it took a few seconds to display anything and then displayed a test-card screen. Selecting 'video' and then 'recording' displayed a black screen for a second or so then back to the test-card display.

Lucview displays what I think is the same problem but much less pronounced; where the Skype video picture is jumping many times a second, the luvcview picture jumps every 1 to 2 seconds.

In Ekiga running a video echo test against sip:500@ekiga.net again shows a similar problem but even less pronounced than luvcview only breaking up every couple of seconds.

Could it be something to do with frame-rates?

Thinking it was the display side of the equation, some posts suggested that compiz could cause problems with unstable video but I've turned that off and even changed from the nvidia binaries to the open source binaries with no improvement.

One direction I started down was around the Video for Linux version in use but as a newbie I realised I was starting to get out of my depth. Changing the gstreamer-properties video settings gave different errors; setting the default plugin input on the video tab to v4l2, and selecting my device “UVC Camera (046d:0990)” and pressing the test button gives the error “Failed to construct test pipeline for 'Video for Linux 2 (v4l2)'”, but I realise I could be heading in the wrong direction and this irrelevant.

I'm hoping someone may have a solution, could give me a prod in the right direction, or has the same problem. BTW camera works fine in Windows XP.

Ubuntu 8.04
Skype v 2.0.0.72-1
Ekiga 2.0.12
luvcview 20070512-3
cheese 2.22.3
Logitech quickcam pro 9000

I intend to post this in the Skype and Logitech Linux forums and see what that throws up as well.

Thanks.

---

