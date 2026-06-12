---
title: "Almost got it!  Small audio issue"
date: 2008-02-13
forum: Mythbuntu
---

### Post by uncle hammy on 2008-02-13
First off, thanks to everyone who has answered all my posts along the way as I try to get this going.  I know it seems that I have had endless questions, and a lot of them probably seemed dumb.  You all have been very accommodating.

I finally have the box running almost as good as I could have hoped for.  The only issue I have left is occasionally, the audio seems to start to get behind the video while viewing recordings, but not for the whole program.  For example, last night while watching Terminator, the entire program was absolutely excellent, until the last 10 minutes.  When suddenly the audio started cutting out for a few seconds, then would suddenly come back where it left off, but well behind the picture at that point....but somehow always mange to catch back up again...over and over.  I exited the recording, restarted it at the same position, and it went away.

I am using Gusty (I think??) 7.10 with all current updates.  I am using the onboard sound of my machine, The NVidia 7600 GS I use is PCI Express x16.  I have checked the extra audio buffering in settings.  I have checked to use priority threads.  I have unchecked use open gl for vertical sync, and also unchecked use video as timing base.  I am using Standard XvMC and Bobx2.  I have also unchecked "Allow commercial flagging and transcoding Jobs", because I have little need for either.

Does anyone have any other suggestions to help eliminate the problem?  One other question, "Use priority threads"...do I have to do anything else besides checking this to make it have any effect?  I have read something somewhere about rlimits, and being logged in as root....do I still have more work to do for this setting?

from [http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4)

> MythTV supports real-time scheduling of the video output thread. There are three ways to go about enabling this: You can use rlimits, you can use the realtime security module, or on older systems you can SUID the executable. Enabling real-time scheduling is optional, but can make the video display smoother, especially if you are decoding HDTV.
rlimits

The rlimits method is the preferred method and is included in Linux 2.6.12 and above. Unfortunately, you need PAM version 0.79 or above, which may not be supported by your distribution yet. Assuming anyone running mythfrontend is in the audio group and rlimits are supported, all you need to do is place this in your /etc/security/limits.conf

    *               -       rtprio     0
    *               -       nice       0
    @audio          -       rtprio     50
    @audio          -       nice       0



If I have to do this, how do I determine if I have PAM 0.79?  How do I determine if I am "in the audio group"?  How do I determine if "rlimits are supported"?

Thanks

---

