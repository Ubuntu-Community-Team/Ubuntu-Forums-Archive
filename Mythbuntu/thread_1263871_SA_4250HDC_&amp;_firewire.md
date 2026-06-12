---
title: "SA 4250HDC &amp; firewire"
date: 2009-09-11
forum: Mythbuntu
---

### Post by bml137 on 2009-09-11
Problem: Unable to receive recordings from my SA 4250HDC over firewire.

Background: Was able to receive recordings from my SA 4250HDC over firewire from August 2008 through March 2009.

Something happened in late March that caused it to stop working.  I am still able to change the channel on 4250HDC box, but MythTV gets stuck after "L" when trying to lock on the channel.  I was never able to "retrieve packets" with mythprime before March or after.  So I can't use that for debugging purposes.

I haven't had an inkling of luck with the late March update to 8.10, an upgrade to 9.04 and with the current release of 9.10.  I read that the 2.6.31 kernel overhauls the firewire framework.  Is there some other way I could be retrieving information from the firewire port?

```
Host Adapter 0
==============

Node 0 GUID 0x00004c01000043fa
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x001cea9be65e0000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
        channel=0, data_rate=0, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2
```

Thanks,
Brian

---

### Post by bml137 on 2009-10-01
I discovered the issue.  The cable company decided to block the firewire output one day.  I called them up and they reset the firmware and everything is working again.

---

### Post by kendoori on 2009-10-01
Who is your cable provider? is it by chance Cablevision/Optimum Online? I don't have this set up yet, but I've been researching how to do this w/o using a tuner card or cable, and stumbled across the fact that you can attach to this cable box directly via firewire.

I'm be curious as to what your experience is? and also what kind of machine you are using to capture off of the cable box?

I'm thinking about building a quiet box to put in my bedroom..

Love to hear about your setup.

---

### Post by bml137 on 2009-10-03
My provider is WOW Cable.  I don't think the provider should be an issue, because the firewire port must be enabled by law.

If you want to test the new cable box before you install all of mythbuntu, just install mythprime.  By running this tool, you can see if your cable box is sending the video stream over the firewire.

You can download mythprime and build it yourself here ...
[https://wiki.ubuntu.com/majoridiot]("https://wiki.ubuntu.com/majoridiot")

---

### Post by bml137 on 2009-11-13
Looks like WOW Cable keeps blocking output from their cable box's firewire port.  After a couple weeks, it got blocked again.  They reset the box again and it worked for another 2 weeks.

After it was blocked again, I couldn't get them to open it up.  I called a couple times and the last guy said that the box wasn't even capable of outputting video and that it was "input only".  He said he had the manual for the box and that is what it said.  Nonetheless, I told him off, as that same box was outputting video for a year.  I told him that they uploaded a policy to the box that effectively blocked the firewire output.

Needless to say I will be dropping WOW today and getting Time Warner tomorrow.  They may not be better, but it will be cheaper (for at least a year).  Maybe their firewire will work too.

---

