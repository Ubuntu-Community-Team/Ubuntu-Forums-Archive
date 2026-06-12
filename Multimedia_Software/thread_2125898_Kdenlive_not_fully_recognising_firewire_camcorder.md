---
title: "Kdenlive not fully recognising firewire camcorder"
date: 2013-03-15
forum: Multimedia Software
---

### Post by nickdc on 2013-03-15
First, to avoid misunderstanding, the camcorder (Sony DVR-PC6E) is detected by Ubuntu (12.04) and operates smoothly via dvgrab from the terminal. It also is recognised immediately in Kino, which captures normally. But in Kdenlive, which I prefer to use, it connects momentarily, then immediately disconnects, without creating a preview. I can't find any evidence that Kdenlive recognises the camcorder. The only capture device picked up by the Cofig Wizard as Default video4linux device is my webcam, even after activating the check while the camcorder is connected and playing. Is it possible that, a) something in Kdenlive is blocking the information of the camcorder being connected from being passed from the OS to the application? and b) because Kdenlive is expecting to capture from the webcam, it makes a momentary start, then aborts because it's clearly not receiving the kind of data it expects? In the Capture configuration window I have firewire as the default device. Given that FFmpeg is not the default device, I'm not sure whether it matters what's set in its window, but I've tried unchecking Capture video (Video4Linux2), but it makes no difference. Since it's on this tab (FFmpeg) that the webcam is listed as a detected device, it occurs to me that maybe capture via firewire does not utilise video4linux, so I shouldn't expect it to show up here ... I'm out of my depth now, but experience and instinct tells me that I just need to give it a little teak somewhere and all will be well. Can some kind soul please help?

Just for additional info, my partner is running the same version of Kdenlive (0.9.4), also in Ubuntu 12.04 and on a very similar spec desktop pc, and on hers it works fine!

---

### Post by hzFVOW00pw on 2013-05-22
I can confirm. I have the exact same problem. Kdenlive 0.9.2 on Debian Jessie.

---

