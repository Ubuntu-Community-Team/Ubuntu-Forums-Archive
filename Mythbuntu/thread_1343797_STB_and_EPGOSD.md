---
title: "STB and EPG/OSD"
date: 2009-12-02
forum: Mythbuntu
---

### Post by Chewiesw on 2009-12-02
I  use a STB and I can view TV. I use the STB remote to change channels at the moment .So far so good. But I have only one channel setup. I need to understand how the EPG and OSD will work if I use an external/manual  XMLTV source.As I only have one on channel is “tuned”

---

### Post by theophile on 2009-12-02
It should be obvious that the EPG/OSD won't work with your current setup. In order to do this properly, you will need to set up a way for your backend to control your STB. You can do this via firewire on some STBs or by ir blaster on others. Once you do this, you can create the proper channels and propagate the EPG. Then the OSD will work and you won't have to use the STB remote anymore.

---

### Post by Chewiesw on 2009-12-02
I thought as much but I am unsure what this means under input connections :External Channel command

"..change the channel for inputs which have an external turner such as a cable box. **THE FIRST ARGUMENT WILL THE CHANNEL NUMBER**"

I put \usr\local\bin\channel.sh 

where do I put the chanel number?

---

### Post by Chewiesw on 2009-12-02
from the log

```
009-12-02 22:18:21.793 TVRec(6): Changing from None to Watching WatchingLiveTV
2009-12-02 22:18:21.810 TVRec(6): HW Tuner: 6->6
/usr/local/bin/channel1.sh: 7: /usr/bin/v4l2-ctl: not found
2009-12-02 22:18:22.512 ret_pid(12078) child(12078) status(0x7f00)
2009-12-02 22:18:22.515 ChannelBase: external tuning program exited with error 127
2009-12-02 22:18:22.516 TVRec(6) Error: Failed to set channel to 4. Reverting to kState_None
2009-12-02 22:18:22.516 TVRec(6): Changing from Watching WatchingLiveTV to None
2009-12-02 22:18:28.159 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-02 22:18:36.530 I'm idle now... shutdown will occur in 1200 seconds.
```

---

### Post by theophile on 2009-12-02
> **Chewiesw said:**
> I thought as much but I am unsure what this means under input connections :External Channel command

"..change the channel for inputs which have an external turner such as a cable box. **THE FIRST ARGUMENT WILL THE CHANNEL NUMBER**"

I put \usr\local\bin\channel.sh 

where do I put the chanel number?

You don't. The backend will supply it for you. The help line is basically saying that if you are using a custom script, make sure it takes a channel number as its first argument.

---

### Post by theophile on 2009-12-02
> **Chewiesw said:**
> from the log

```
009-12-02 22:18:21.793 TVRec(6): Changing from None to Watching WatchingLiveTV
2009-12-02 22:18:21.810 TVRec(6): HW Tuner: 6->6
/usr/local/bin/channel1.sh: 7: /usr/bin/v4l2-ctl: not found
2009-12-02 22:18:22.512 ret_pid(12078) child(12078) status(0x7f00)
2009-12-02 22:18:22.515 ChannelBase: external tuning program exited with error 127
2009-12-02 22:18:22.516 TVRec(6) Error: Failed to set channel to 4. Reverting to kState_None
2009-12-02 22:18:22.516 TVRec(6): Changing from Watching WatchingLiveTV to None
2009-12-02 22:18:28.159 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-02 22:18:36.530 I'm idle now... shutdown will occur in 1200 seconds.
```
Line 7 of your channel change script references /usr/bin/v4l2-ctl which does not exist. Try testing your script manually from the command line before making MythTV use it.

---

