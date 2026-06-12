---
title: "HDMI Audio Suddenly Stopped Working"
date: 2017-02-10
forum: Multimedia Software
---

### Post by AzurianArcher on 2017-02-10
My HDMI audio suddenly stopped working today, and I can't seem to figure out why. The HDMI display works fine, and I already checked that it is not my speakers and that nothing is muted. I am running Ubuntu 16.04 on a dell laptop. 

When I run pulseaudio in a terminal, it looks like it gets stuck doing a "rewind" when I do the sound test in the gnome settings panel. I'm not really sure how to interpret what I'm seeing though. I have a paste of the `pulseaudio -vvvv` output 

[http://pastebin.com/ZUi38XbE](http://pastebin.com/ZUi38XbE)

I also recorded a short video of what I am seeing because it is very strange. 

[https://www.youtube.com/watch?v=4zXXCc0P0a4](https://www.youtube.com/watch?v=4zXXCc0P0a4)

Here I use the gnome speaker test on both left and right speakers using HDMI and the internal laptop speakers (which work fine BTW). 

When you use the gnome-settings audio test, you can test "Front right" and "front left" speakers, and a nice woman says those words out of each side. While the woman is speaking (duration of the audio file they are using) the speaker icon turns blue. 

When I run this test over HDMI, I see the speaker turn blue and stay blue for a really long time while pulseaudio seems to be waiting on this rewind operation. The first button I press (left or right speaker) makes a loud pop noise, but after that there is no noise, just a hang with the speaker icon turning blue. When I test with the laptops internal audio, the speaker icon turns blue, plays the audio, and turns back to gray very quickly as the audio clip ends. You can see both of these events in the paste of the pulseaudio output. 

Again this just happened today, it was working fine last night, and I can't think of anything strange I was doing that might have caused this.

---

