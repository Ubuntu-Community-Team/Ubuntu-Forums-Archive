---
title: "mythfrontend stops responding to inputs during recording playback"
date: 2008-08-10
forum: Mythbuntu
---

### Post by newlinux on 2008-08-10
I have a frontend that stops responding to the remote control and the keyboard during recording playback. If I don't press any keys on the remote or keyboard for a few minutes, it will stop responding to the next keypress for about a minute and then it will usually buffer up a couple of the keypresses and then I can use the keyboard or remote again. This only happens during recording playback. It hasn't happened in mythvideo (using the internal player with mythvideo) or in the mythfrontend menus. I didn't see anything in the logs that was suspicious. I'll turn up the verbosity but does anyone have any ideas?

I should add, I can still use the keyboard on the during this freeze (alt-tab will switch windows) so it isn't the whole desktop environment freezing. This is running in gnome.

---

### Post by newlinux on 2008-08-11
Well, I have also found this happens on another one of my frontends, once again only on recordings...

Any pointers would be helpful

---

### Post by newlinux on 2008-08-18
bump - anyone got any ideas on this? It really has me baffled - especially the fact that it only happens during liveTV or recordings, but not anywhere in the menus or during playback of mythvideo files. The video looks fine, nothing appears in the logs... this happens on two different frontends. And sometimes it doesn't take a few minutes of viewing - it happens in less than a minute. So it isn't just long inactivity that leads to it either.

---

### Post by newlinux on 2008-09-05
Okay, I've tried changing playback profiles - still have the problem, I've tried changing OSDs, still have this issue. One thing I did find is that it seems that basically the OSD freezes. One time it happened when the info screen was displaying - it stopped responding to any keys, and left the OSD info screen on (instead of fading it away after 3 seconds) until it responded to keystrokes again.

Still would be happy to get any suggestions...

---

### Post by rubrboots on 2008-09-10
Im having a very similar problem, usually a few minutes into a show, control is lost, sometimes the audio will lose sync when this happens, and other times the mouse pointer will appear in the center of the screen when control is lost. After a minute or so keyboard/remote control returns. 

I have looked at the frontend and backend logs but they really dont mean much to me. I have tried changing the commercial detection settings, but the problem persists. Is there a way to disable commercial detection?

Now my frontends have suddenly started to stutter/skip when recordings are played back (videos are fine though). I really like ubuntu on my desktop machine, however I am now considering a switch back to Knoppmyth for all my mythboxes.:confused::confused::confused:

---

### Post by netslacker on 2008-09-11
This problem seems to plague a few people, not really sure why.  I have the same issue and have been posting to a thread called "delayed response to remote"... or something like that.  But it is exactly the scenario that is described in this thread.

This is what I can tell you, during the delay remote and keyboard actions are queued, then, the system will suddenly execute all of the inputs all at once.  It is very annoying.

I can also tell you that while the problem is persisting that the Xorg process is pegged (97~100% cpu) on my dual core system. While it is pegged, the system will not respond to remote or keyboard inputs.  Once the pegging stops, the inputs are executed.  The Xorg process also, typically, runs around 2-5% on my system, but for some reason will spike to 100% for a period and it is during this period that the events are queued.

On mythtv.org there is a simple one-line sentence that mentions the issue and says that lowering the Xorg process priority will help to resolve it, but that has never done anything for me.  I have tried mythbuntu 8.04.1 64bit and am now running ubuntu 8.04.1 32bit and then applied the mythtv installs, problem exists/existed in both installs.  

I was debating trying knoppmyth to get the problem resolved as well.

---

### Post by newlinux on 2008-09-11
I'll check my Xorg process cpu utilization the next time this happens to verify that for me too. But still, why on liveTV/recording playback but not mythvideo using the internal player?

You're right - this issue really kills the WAF, especially when my previous build worked so well...

---

### Post by uopjohnson on 2008-09-18
I just did a fresh install of my two front ends and this problem has come up suddenly.  I thought it might be a lirc issues, but it happens with keyboard and telnet inputs as well.  Exact same symptoms playback continues, input gets queued and then executed all at once between 30seconds and 1 minute later. The hang can happen anytime after the recording starts,
Found this thread on mythtv users:
[http://www.gossamer-threads.com/lists/mythtv/users/348526](http://www.gossamer-threads.com/lists/mythtv/users/348526)
No solution though.  I will keep an eye on xorg next time.

---

### Post by uopjohnson on 2008-09-19
cross posting this since there are two open threads with this issue:
xorg was pegged at 97% when watching recordings.  Read that hear, or in another thread and confirmed it on my system.  This seemed like it might be the cause of the problem so I looked around for that and found a solution, at least for me.  I added
```
Option "UseEvents" "on"
```
to the Device section of xorg.cong and my Xorg cpu usage went down to 3% and I have had no problems with the remote tonight.
Give it a try, maybe it will work for you.  It seems to be an nvidia speicific fix, so it may not fix all problems.

---

### Post by newlinux on 2008-09-19
thanks, I'll give that a try when I get home tonight. All of my frontends that have the problem are indeed nvidia frontends. I rarely use my Intel GPU frontend but I've never noticed the problem there. And it occurs to me that I used to have this option on in previous installations.

---

### Post by netslacker on 2008-09-19
I only return to this forum to see if there is an answer to this problem so I will definitely give this a try when I get home tonight.  Thanks for the post...

---

### Post by uopjohnson on 2008-09-19
If it works post back.  Seems like this option should be set by default so I will file a bug report.

---

### Post by netslacker on 2008-09-19
I added the 'Option "UseEvents" "on"' to my xorg.conf tonight and it appears to have resolved the issue.  This is so far only about 30 mins of use but before I made the change the problem was pretty persistent and so far - so good.

I'll post again after a day or so...

---

### Post by newlinux on 2008-09-23
two days into testing for me on two different frontends, so far so good...

---

### Post by newlinux on 2008-09-27
I'm officially declaring my problem fixed. Haven't had it since adding the option.

---

### Post by netslacker on 2008-09-29
I too am officially declaring my problem as resolved.  Since adding the following snipped to the Xorg.conf file my delays to the remote have cleared up.  I am mucho happy now (so is wife!).

```

Option "UseEvents" "on"

```

---

### Post by Mr. Flibble on 2008-10-25
I realize that this is an AOL Style "Me Too" response, but I was having this exact same issue until I stumbled upon this thread. In my case, it was destroying the "WAF" as well.

Adding the line to my xorg.conf fixed the issue.

Note, I also figured out, in my case how to immediately replicate the issue without fail for those that are bug hunting.

If I start watching live TV, then hit the "Start" button on my MCE v2 Remote, hit "ok" to select the program guide, and then press "up" more than 2X, the input immediately freezes.

However, as mentioned, the addition to the conf file fixed the issue after restarting X.

---

### Post by Mr. Flibble on 2008-10-27
Murphy's law of course has reared it's ugly head. The problem is back, it was merely coincidence that I thought the problem was licked by adding the line to the "display" section of X. :(

Looking at other forums, it seems that it is a legitimate bug. Looks like it is in Myth, and not just MythBuntu.

Note, this is occurring on the front end that is on the same system as the back end, and is directly hooked into my TV. The system should be more than powerful enough to run the front and back ends.

Nothing appears in the logs, and htop shows no meaningful change in CPU usage.

---

### Post by uopjohnson on 2008-10-27
If you aren't seeing the CPU spike then you probably have a different problem.  My freeze was *always* accompanied by a cpu spike. Sorry it didn't help.

---

### Post by ajhtiredwolf on 2008-11-04
Should my remote be listed as a device in the xorg.conf? I have a few device sections. the remote is an mceusb2.

---

### Post by oobe-feisty on 2008-11-05
> **ajhtiredwolf said:**
> Should my remote be listed as a device in the xorg.conf? I have a few device sections. the remote is an mceusb2.


no it should not if it is in the xorg.conf  then its a problem with hal misconfiguring your hardware and will cause your remote not to function correctly

---

### Post by entourage on 2008-11-05
I appear to be having the same issue, however mine seems to have a twist.  
I can watch any channel (live or recorded) as long as it's not 1080i.  If it is, within a few seconds my CPU spikes to 100% and I have to force a reboot.

I just updated from 8.04 to 8.10 so I'm certain this has something to do with it.  I'm just not sure what.

I tried the "Option" "UseEvents" "on" but it appears as though I already had that in my xorg.conf 
```
"Option"     "UseEvents"    "1"
```

I can post logs if needed, but I wanted to see if anyone had any initial ideas?

I'm running 1080p, Athlon X2 2.6, 2GB RAM, 320GB HDD, onboard nVidia 7050

[EDIT] I checked my playback settings and it was set to the CPU+ profile.  I changed this to the NORMAL profile and can now playback without issue.  (I figured I'd leave this entry for others who upgrade and experience this issue)

---

### Post by leprasmurf on 2008-12-29
Just to throw in my $.02, I was having this very frustrating problem and came across this thread.  Since implementing the aforementioned fix, we have not had a problem since.  Thanks!

---

### Post by ahood on 2009-07-04
> **uopjohnson said:**
> cross posting this since there are two open threads with this issue:
xorg was pegged at 97% when watching recordings.  Read that hear, or in another thread and confirmed it on my system.  This seemed like it might be the cause of the problem so I looked around for that and found a solution, at least for me.  I added
```
Option "UseEvents" "on"
```
to the Device section of xorg.cong and my Xorg cpu usage went down to 3% and I have had no problems with the remote tonight.
Give it a try, maybe it will work for you.  It seems to be an nvidia speicific fix, so it may not fix all problems.

Thank you uopjohnson for this fix!

I recently upgraded from Mythbuntu 7.10 to 8.04 and encountered the problem described by Newlinux user (see above post). The remote I use is the grey Hauppauge A415-HPG that came with my PVR-350.

---

