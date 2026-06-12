---
title: "Just me, or is Xorg a PIG!"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by wkulecz on 2006-09-07
Just installed i386 Ubuntu 6.06 on AMD X2 3800+ with GeForce 5500 video card.  Video/DVD playback is close to useless with xawtv having Xorg take 50-80% CPU depending on window size, and Xine has Xorg take 85% CPU!

I have an image processing application that I initially started on Knoppix 4, when I moved to Fedora Core 5 the change from XFree86 to Xorg had the same poor performance as Ubuntu shows.  But the Fedora folks quickly had a fix.

Ubuntu Xorg server 10.2 and 10.4 both have the same poor performance.  Fortunately I was late enough getting started to have missed the 10.3 fiasco.

I wanted to use Ubuntu for the workstations (five initially) as it should be easier for the users to learn and maintain, was tedious for me to get the gcc etc. tools installed (first distribution I've seen without basic compiler tools out of the box!) but I only have to do this once.  Needless to say, this issue is a showstopper for me.

Also I need to disable all screensavers and blanking etc., but Ubuntu's Xorg server seems to be ignoring my "ServerFlags" section Option "StandByTime" "0" etc. that I've added to the xorg.conf file.  (I know I'm in the right place becasue I had to change the default screen depth to 16 for my code to run).

If I don't find a quick solution, I'll have to forget about Ubuntu and go thru the hassle of setting up FC5 everywhere or go back to Knoppix 4 (great initially but too easy to self-destruct with any upgrades or additions).  Knoppix 5 has switched to Xorg and has the same unusable video performance issue!  What was nice about Knoppix 5 is I could boot the DVD, plug in a memory stick with my code, do make clean; make and run my application.  But too may dropped frames (although not as bad as Ubuntu!) to be useful because Xorg server is hogging the cpu.  At least with Knoppix 5 I knew it wouldn't work in half an hour instead of wasting most of a day as I have with Ubuntu.

I know its not a hardware issue as this was my FC5 box initially until I moved the hard drive to another system with a case more condusive to my development needs.

--wally.

---

### Post by tseliot on 2006-09-07
Wierd... did you try installing the nvidia driver?

---

### Post by skymt on 2006-09-07
You should make sure you have proper (closed source) drivers installed, and use Xv output for video.

---

### Post by wkulecz on 2006-09-07
The nv driver worked fine with Fedora Core 5 once they fixed the bug in the Xorg server.

Here is the thread I started on the Fedora Core forum when I discovered the issue on AMD-64:
[http://fedoraforum.org/forum/showthread.php?t=103211&page=2&pp=15](http://fedoraforum.org/forum/showthread.php?t=103211&page=2&pp=15)

Turns out the problem existed on i386 as well.  The Fedora team had a fix already, it just wasn't generally out.  AMD-64 builds required updated NV driver as well, as I recall, the i386 NV driver did not need updating

Perhaps Ubuntu developers could be put in touch with the folks from FC5 to fix this issue.

I'd prefer to stick with open source drivers. But there seems to be good info on this forum about installing the proprietary drivers, so I'll give it a try tomorrow before I go back to FC5.
I like FC 5, but I know it is more hassle for me to install and think it'll be tougher for the users of my image processing system to deal with.

--wally.

---

### Post by wkulecz on 2006-09-08
I believe the bug that messes up the shared memory data transfers between the applications and the Xserver is in the Xorg server.

There were a couple of differences in the module options in the xorg.conf file between Ubuntu and FC5.  Int10 is loaded in Ubuntu, but not FC5 and dbe is loaded in FC5 but not Ubuntu.

Making Ubuntu xorg.conf options match had no effect.

In the Xorg.0.log files I could see no differences in any of the version numbers although the build date on FC5 was 06 April 2006
while Ubuntu is 16 March 2006.

Now I'm off to the wiki.x.org to see if this problem is logged there yet.

I'll try the Proprietary drivers this afternoon but I'll take bets it makes no difference.

Too bad it looks like I'll be giving up on Ubuntu, it'd be a good system for my users if it didn't have this showstopper problem.

--wally.

PS, re: the blanking not turning off, there is another monitor sleep control in system->preferences->powerManagemnet that needs to be set to "never" which seemed to be overriding the xorg.conf options.

---

### Post by wkulecz on 2006-09-08
Happy to report that installing the Proprietary NVIDIA glx drivers is a work-around to fix this issue.

--wally.

---

