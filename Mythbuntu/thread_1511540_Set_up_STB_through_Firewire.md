---
title: "Set up STB through Firewire"
date: 2010-06-16
forum: Mythbuntu
---

### Post by chris225 on 2010-06-16
Hey im kinda a n00b when it come to this, i just installed mythbuntu and im trying to set up my Stb as the capture card it has a firwire port on it. its cabelvison Sa4250HD box. others says it works so that's not the issue. it just wont play the tv, its says [Please wait......} then goes back to main screen. i dk whats to do i hope its simple fix. iv done firewire test and every time p2p and broadcast fail. im not getting connection on either. if someone could help i would really appreciate it. iv read all the wiki hows and watched every video. please someone help.

Thanks

---

### Post by lank23 on 2010-07-11
I have verizon fios STB QIP-7100 connected via firewire, seems to work well on non-copy protected channels. Should be a similar set-up.

Post these outputs for starters to make sure there are no hardware issues

```

cat /var/log/syslog | grep ieee1394

```

```

lspci

```

```

plugreport

```

---

### Post by LowSky on 2010-07-12
hi Chris225, I have the same box. I ran into the issue with the box failing to connect.. You have to unplug and and let it boot up before the signal will come back.  If it still doens't work, call cablevision and ask them to enable the port or to replace your current box with one that does work.. if they say thats impossible remind them of the FCC rules that stat that they are required to give you one by law.

I can't get it to work with LiveTV no matter what, and recording TV with scheduling only works if the channel doens't have 5C encryption, which most do. the only open channels are the ones that you can get without a cablebox and even those can become encrypted if the network wishes it to be. Its really fun when one show will record just fine, but the next fails, and you then have to go through your watch list and delete empty files.

To get around all these problems, I ordered a Hauppauge HD PVR this weekend and plan I using it to record cable TV. Sure its an extra $200 out of my pocket but it give me control over what I want to record and not the cable company.

---

