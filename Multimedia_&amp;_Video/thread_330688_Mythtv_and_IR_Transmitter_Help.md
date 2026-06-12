---
title: "Mythtv and IR Transmitter Help"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by rubrboots on 2007-01-03
Hello I have been trying to setup a homebrew ir transmitter to change the channels on my STB for MythTv. I have had no luck with the transmitter but it may be due to my lack of linux experience. 

I have followed the guide for setting up an external channel changer
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

the last thing I think might fix my problem is the step:

->When configuring your tuner in mythtv-setup, be sure to set the external channel change script to  change-channel-lirc.pl

What exactly does this mean? I have entered "change-channel-lirc.pl" into the "External channel changer command:"box of the Input setup in the mythtv setup. Is this correct or am I missing something here?

All in all Myth appears to be working fine but when I change channels nothing happens, I have looked at the ir transmitter though an digital camera when it should be transmitting and there are NO flashes. Is there a way to get my transmitter to transmit on demand for testing purposes?

Any advice would be greatly appreciated.

---

### Post by superm1 on 2007-01-05
> **rubrboots said:**
> Hello I have been trying to setup a homebrew ir transmitter to change the channels on my STB for MythTv. I have had no luck with the transmitter but it may be due to my lack of linux experience. 

I have followed the guide for setting up an external channel changer
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

the last thing I think might fix my problem is the step:

->When configuring your tuner in mythtv-setup, be sure to set the external channel change script to  change-channel-lirc.pl

What exactly does this mean? I have entered "change-channel-lirc.pl" into the "External channel changer command:"box of the Input setup in the mythtv setup. Is this correct or am I missing something here?

All in all Myth appears to be working fine but when I change channels nothing happens, I have looked at the ir transmitter though an digital camera when it should be transmitting and there are NO flashes. Is there a way to get my transmitter to transmit on demand for testing purposes?

Any advice would be greatly appreciated.
Hi,

Okay, so if your seeing no flashes from your digital camera, outside diagnostics will be needed.

First off, is lircd running after attempting a transmission?  Lircd may crash on you due to lots of problems, so check and see if the process is still running.

Next off, check ```
dmesg
``` for any errors about lirc-serial and missing setserial options.  Make sure that the lirc_serial module is loaded per ```
lsmod
```If all of this looks good, you can force manual transmissions just like what the code in that perl script shows:

```
 irsend SEND_ONCE REMOTENAME COMMAND 
```

where REMOTENAME is the name of your remote in /etc/lirc/lircd.conf
and COMMAND is the button your trying to send.

Looking closer at the script, (this was taken directly from mythtv-0.20/contrib), and I think I see a bug in it.  Try editing it and changing the line

```
system ("rc SEND_ONCE $remote_name $channel_digit");
```
to be

```
        system ("irsend SEND_ONCE $remote_name $channel_digit");
```
and
```
system ("rc SEND_ONCE $remote_name ENTER");
```
to be
```
        system ("irsend SEND_ONCE $remote_name ENTER");
```

I will have to update the script to make sure it reflects this :)

---

