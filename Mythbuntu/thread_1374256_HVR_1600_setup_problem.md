---
title: "HVR 1600 setup problem"
date: 2010-01-06
forum: Mythbuntu
---

### Post by tmcgary on 2010-01-06
Hello,
   I have been using mythbuntu for almost a year now, this is my first help! :frown:post. I have been trying to get clear-QAM 125 (HD) to work on Hauppauge HVR-1600 via the details here: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600).

My system specs are:
Dell Optiplex GX270 running Karmic (2.6.31)
2.4 Ghz Celeron Prescott
1 GB RAM
Turtle Beach Riveria sound card
Sparkle nVidia GeForce 8400GS 512 MB video card. I have selected VDPAU slim.
HVR-1600 (model 1101, see [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600))

The HVR-1600 analog tuner was working fine from my initial install of 9.10 and the digital tuner was providing a watchable signal but the audio sounded like a constant garbled clicking sound. I read the hvr-1600 wiki and thought updating the drivers might help this issue.

All was going well until I got to the step to copy the the cx18 firmware to the /lib/firmware directory ```
sudo cp cx18-firmware/*.fw /lib/firmware
```This gave me the error:
```
cp: cannot stat `cx18-firmware/*.fw': No such file or directory
```However when I follow this path I see many files in /lib/firmware that meet the cx18-firmware/*.fw description. When I enter```
 dmesg | grep cx18 
``` nothing happens the terminal just returns to a new line with the :/$.

Now when I select Watch TV from the frontend menu I get the error: MythTV has no capture cards defined, Please run the mythtv-setup program. When I use the backend setup and try to reconfigure the hvr-1600's analog tuner using IVTV MPEG-2 encoder card, no probed info is opened when I manually input /dev/video0 in for video device. Default input states: Could not open '/dev/' to probe its inputs.

lspci returns
```
01:08.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip                                                                     MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
```lspci -v returns
```
01:08.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip                                                                      MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. Device 7444
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
```It would seem that the drivers (and/or firmware) are gone or broken?? Any idea where I should go from here? Sorry for the long post, I wanted to be thorough with background information. Thanks!

Tom

---

### Post by gordintoronto on 2010-01-06
It appears that you don't know the format of a copy command.

If the command:
ls
displays a folder called cx-18-firmware, then you can issue the command:

sudo cp cx18-firmware/*.fw /lib/firmware

Otherwise, you need to cd (change directory) to get to that location.

It would be even more foolproof to
cd cx18-firmware
cp *.fw /lib/firmware

---

