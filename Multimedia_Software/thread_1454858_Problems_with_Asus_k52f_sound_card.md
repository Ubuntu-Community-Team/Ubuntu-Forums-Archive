---
title: "Problems with Asus k52f sound card"
date: 2010-04-15
forum: Multimedia Software
---

### Post by tpsvca on 2010-04-15
Hello, there

I'm using Lucid 10.04 beta on Asus k52f with core i3. The problem is when i plugged in my headphones I still hear sound through my laptop speakers

---

### Post by tpsvca on 2010-04-16
> **tpsvca said:**
> Hello, there

I'm using Lucid 10.04 beta on Asus k52f with core i3. The problem is when i plugged in my headphones I still hear sound through my laptop speakers

Well, Hello! Somebody can help me?

---

### Post by tpsvca on 2010-04-23
> **tpsvca said:**
> Well, Hello! Somebody can help me?
cammon guys... Can anyone give me solution?

---

### Post by Yellow Pasque on 2010-04-23
Please post output of:
```
aplay -l
```

---

### Post by tpsvca on 2010-04-24
> **Temüjin said:**
> Please post output of:
```
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks in advanced

---

### Post by lidex on 2010-04-24
Hmm. Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by tpsvca on 2010-04-25
> **lidex said:**
> Hmm. Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

uname -a:
Linux tpca-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*:
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

Exact model Asus k52F


Thank you

---

### Post by demetrius2009 on 2010-04-25
Here is my result

dima@dima-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dima@dima-laptop:~$ uname -a
Linux dima-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
dima@dima-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
dima@dima-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
dima@dima-laptop:~$

---

### Post by demetrius2009 on 2010-04-25
Still no luck with sound from external speakers wneh headphones plugged in  with my Asus K52Jr laptop

---

### Post by lidex on 2010-04-25
Guys, I'm seeing a lot of issues with this particular codec and no real answers. I would at this point suggest upgrading alsa. Use the alsa-upgrade link in my sig. Follow this post to get the latest version:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by jsevi83 on 2010-04-25
I already upgraded ALSA to 1.0.23, but it doesn't solve anything. My speakers still sound when headphones are plugged, and I don't have sound through hdmi.

Does anybody have found a solution for this?


/proc/asound/card0/codec#0
Codec: Conexant ID 5069


/proc/asound/card0/codec#3
Codec: Intel G45 DEVIBX

---

### Post by peril2 on 2010-04-26
Have just purchased a K52F sx0032v and put 10.04 on it (9.10 wouldn't work). No problem with line-out or microphone, but HDMI audio wouldn't work. Played with various ALSA options (/etc/modprobe.d/alsa-base.conf) to no avail.

Found [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer) which enabled me try find the required configuration change to make it work (in my case, Card0, Codec3, Node06, amp-out val[1] unchecked). However, this was only the running configuration being changed so didn't survive rebooot.

Then found this post: [http://ubuntuforums.org/showpost.php?p=7027502&postcount=16](http://ubuntuforums.org/showpost.php?p=7027502&postcount=16) I downloaded Sanath's scripts and played with them until I could get them to make the specific change I needed, then installed them as per the post. Here is my version of Sanath's script (note that I have no prior experience with ALSA, HDA or python so don't expect me to answer any questions):
```
#!/usr/bin/python
#import gobject
#import pango

from dircache import listdir
from hda_codec import HDACodec, HDA_card_list, \
                      EAPDBTL_BITS, PIN_WIDGET_CONTROL_BITS, \
                      PIN_WIDGET_CONTROL_VREF, DIG1_BITS, GPIO_IDS

def main():
  try:
    codec = HDACodec(0, 3)
  except OSError, msg:
    if msg[0] == 16:
      print "Codec is busy..."
    return
  codec.analyze()
  n = codec.get_node(6)
  n.amp_vals_out.set_value(0,128)
#  n.set_active_connection(1)
  
  return 

if __name__ == '__main__':
  main()
```

---

### Post by tpsvca on 2010-04-26
Hello, can anybody help us? peril2 silution didn't work:

adding the line: options snd-hda-intel model=asus(or asus-mode3) on "/etc/modprobe.d/alsa-base.conf" not working

---

### Post by Yellow Pasque on 2010-04-26
Run the alsa-info.sh script and post to the alsa-devel list if no one on these forums can help.

---

### Post by jsevi83 on 2010-04-27
I just found a solution to mute the speakers when headphones are plugged in. See this thread, post 131

[http://ubuntuforums.org/showthread.php?t=1043568&page=14](http://ubuntuforums.org/showthread.php?t=1043568&page=14)

I only compiled using g++ instead of gcc

---

### Post by boofly on 2011-01-27
Had the same problem. Installing linux-backports-modules-alsa-maverick-generic fixed this for me!

---

