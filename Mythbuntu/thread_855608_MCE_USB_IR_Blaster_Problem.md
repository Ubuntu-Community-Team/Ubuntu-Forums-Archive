---
title: "MCE USB IR Blaster Problem"
date: 2008-07-10
forum: Mythbuntu
---

### Post by Tim L on 2008-07-10
I really like Mythbuntu but I can not get my MCEUSB IR Blaster to work. There is so much confusing information out there that someone new like me does not know where to turn. As a result I am going to try and get a definitive answer to an individual question.

Which is the correct command to type into the External channel change command field <I have already set up the script and know it works>:
1.change-channel-lirc.sh
2.change-channel-lirc
3../change-channel-lirc
4../change-channel-lirc.sh
5./usr/local/bin/change-channel-lirc
6./usr/local/bin/change-channel-lirc.sh

Please do not send me of to read this or that – I have already read everything and it has just confused me. I am running a standard combined front and back with NO EPG <I live in New Zealand and although they are available I am leaving that for another time> I am using a standard MCE 150 video card and USB remote, the one with the IR Blaster connected to the IR receiver box which plugs into the USB.

---

### Post by gfowler on 2008-07-10
> **Tim L said:**
> I really like Mythbuntu but I can not get my MCEUSB IR Blaster to work. There is so much confusing information out there that someone new like me does not know where to turn. As a result I am going to try and get a definitive answer to an individual question.

Which is the correct command to type into the External channel change command field <I have already set up the script and know it works>:
1.change-channel-lirc.sh
2.change-channel-lirc
3../change-channel-lirc
4../change-channel-lirc.sh
5./usr/local/bin/change-channel-lirc
6./usr/local/bin/change-channel-lirc.sh

Please do not send me of to read this or that – I have already read everything and it has just confused me. I am running a standard combined front and back with NO EPG <I live in New Zealand and although they are available I am leaving that for another time> I am using a standard MCE 150 video card and USB remote, the one with the IR Blaster connected to the IR receiver box which plugs into the USB.

Tim,
I infer a high level of frustration here.  I'll see if I can help a bit.
If your script name is change-channel-lirc.sh and resides in /usr/local/bin/ then the entry would be
  /usr/local/bin/change-channel-lirc.sh

At least mine is.

As an aside the only script I have seen with that name i.e. change-channel-lirc is a pearl script.  I banged my head on the wall for a few until I realised my typo; .sh and changed the ext to .pl.  

Of course that may not be your case.  

Jerry

---

### Post by Tim L on 2008-07-10
Jerry

Thanks that is exactly what I need. There is such confusion on the internet over such a simple point. I have found articles where it is written all the ways I listed.

Tim

---

