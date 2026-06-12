---
title: "MythTV: Consistent video skipping... hardware or software?"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by quiller on 2007-10-30
I have a frontend/backend machine that's been running without fault for about a year and a half. There's the occasional lock-up or other problem, but a quick restart (rarely system, normally just the frontend) solves it. Lately, though, I've been getting a consistent and unavoidable skipping. This occurs with recorded programs, live TV and videos. The symptoms: video and audio play fine, then freeze for 2-5 seconds (differs each time). There's no visual artifacts, just a complete freeze for a few seconds, then right back to smooth play for 10-45 seconds. Load on the CPU is an average of 20%, max at 40-50% (if mythcommflag is running).

The frontend log always reports along the same lines:

```
2007-10-30 19:33:03.331 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:03.746 NVP: prebuffering pause
2007-10-30 19:33:31.927 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:35.215 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:38.446 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:38.744 NVP: prebuffering pause
2007-10-30 19:33:52.938 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:56.138 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:59.350 NVP: Timed out waiting for free video buffers.
2007-10-30 19:33:59.747 NVP: prebuffering pause
```
I've looked through the mailing lists and documentation, but nothing seems to help. I found [one article](http://www.mythtv.org/wiki/index.php/Troubleshooting:NVP:_Timed_out_waiting_for_free_video_buffers) which addresses this error specifically.

glx and OpenGL are both off -- no change. Moved /dev/rtc -- no change. I'm going to try the bios setting (if it exists), but need some help with this section:

> Adding "acpi_use_timer_override" as a kernel argument in my bootloader fixed the problem for good, as well as possibly "noapic" which I had in place for another reason.
I googled, but couldn't find any instructions. I'm familiar with the command line and Linux in general, but not to the point where I can dive into a task like this without some direction.

Finally, I wonder if this is strictly a software issue? At first I thought the hard drive holding recorded programs might be going south, but then videos (on a different physical drive) started exhibiting the same symptoms.

Can anyone recommend a good temp/load monitor to check if something is overheating? Perhaps other things to try and solve it via software/bios?

**Update 10/31**
I've exhausted all possibilities/recommendations that I can find (above article included). The machine isn't under heavy load, recorded programs and videos play fine on other frontends, and there's no over-heating. I even took the side panel off and stuck a 12" fan next to the box -- no change.

At this point I'm looking for anything. Could the video card be going crazy? Should I start swapping random hardware with new units?

Got a random, hey-this-might-be-related idea? I'm game for anything!

---

