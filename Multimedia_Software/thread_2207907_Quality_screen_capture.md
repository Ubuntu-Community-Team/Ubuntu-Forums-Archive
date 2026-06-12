---
title: "Quality screen capture"
date: 2014-02-25
forum: Multimedia Software
---

### Post by SimonHGR on 2014-02-25
Hi, I'm struggling with screen capture. I need to get either an uncompressed, or at least very high quality, screen capture of a 1280x720 pixel region of my screen at 30 fps. I have an i7 CPU and 16GB RAM so I think the hardware should be more than sufficient. Here's what I've tried, and why it hasn't worked.

1) I found instructions on using ffmpeg with x11grab. The instructions are immensely complicated and didn't match the version of ffmpeg that's current, and I don't understand it nearly enough to work out how to fix it. In my efforts, I did discover (I believe) that I don't have a libx256 codec. I think I've heard of this codec,and I think it might be one of the high quality ones, so perhaps I want to fix that no matter what.

2) I tried "simplescreenrecorder" which worked a treat, except it was recording directly into memory, and only wrote the file when it finished (and used a single thread / CPU core to do it), so it was filling my 16GB RAM very quickly and I need to be able to record essentially continously (probably not more than 20 minutes, most of the time, but nevertheless)

3) I have manged to get avconv jto grab the screen, but it compresses it with a horrible algorithm that is useless to me from a quality perspective. I think this is just a matter of education: there are so many options that I don't know which knobs I should fiddle with. My minimal command was simply "avconv -f alsa -i default -f x11grab -i :0.0 /tmp/out.mpg". As I recall I did find the options to make it record a different region of the screen, but the quality was the major problem

4) I tried a program called ardesia, which looked like the best thing since sliced bread, as it appeared that it would simultaneously solve both this problem, and the problem of how I could annotate my screen. Unfortunately, on this installation (Ubuntu 13.10, x64) it doesn't work at all. Once a "pen" has been selected, it becomes impossible to change tools, and the pen doesn't actually write on the screen in a visible way (there's a brief flash of the drawings that were made just as the program shuts down). If anyone can tell me how to get this working, that would be absolutely the ideal from my perspective.

Any help anyone can offer? The folks at my publisher keep nagging me to use Camtasia on windows, but I think I'd rather chew my own leg off first, so I really want to make this work if I possibly can.

I guess if I can do any of the following I'm good to go:

1) get ardesia to work (probably the preferred option if it's high quality video)
2) find an avconv or ffmepg command that uses a high quality compression or no compression
3) anything else that meets the goal of creating screen-capture type presentations with the necessary quality

Cheers,
Simon

---

### Post by SimonHGR on 2014-02-25
I made some progress, I discovered how to install libx264:

sudo apt-get install libx264
sudo apt-get install libavcodec-extra-53

(I think the first one is actually a command line tool, and might not be necessary, but I can't tell)

And I discovered a command line that seems to grab good quality screen video using avconv.

avconv -f x11grab -r 25 -s 1280x720 -i :0.0+100,100 -vcodec libx264 -pre lossless_ultrafast -threads 0 test.mkv

This doesn't have audio, but I think I might have a lead for that.

So, I guess my biggest problem still is screen annotation, for which ardesia would be perfect, if I could make that work...

---

### Post by SimonHGR on 2014-02-25
Another step forward. This managed to grab the audio from my microphone too (though I believe I had previously tweaked the settings in the regular system settings -> audio to enable that)

avconv -f alsa -i pulse -f x11grab -r 30 -s 1280x720 -i :0+100,100  -vcodec libx264 -pre:0 lossless_ultrafast -threads 0 video.mkv

this one I also modified to 30 frames per second (the -r30 after x11grab) and to offset the capture area down and right by 100px to get it away from my machine's menus. Thats the +100,100 in -i:0+100,100.

So, all I could wish for now is a working ardesia, or some other tool to allow me to do on-screen annotations, highlighting, things like that.

Any suggestions?

---

### Post by SimonHGR on 2014-03-19
Desperation led me to create my own. It,s written in Java, so has a good chance of working anywhere. Help yourself if you are also stuck.

[https://github.com/SimonHGR/java-annotate](https://github.com/SimonHGR/java-annotate)

---

