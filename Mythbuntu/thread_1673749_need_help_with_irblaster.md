---
title: "need help with irblaster"
date: 2011-01-22
forum: Mythbuntu
---

### Post by crazyone on 2011-01-22
hi i have have been working on setting up a mythbuntu 10.10 media center for my house and am having a problem with the ir blaster i have. i got it from irblaster.info and it is a serail. the problem i am having is getting lirc setup with the info for it. i have been going off of [http://regx.dgswa.com/html/node/134](http://regx.dgswa.com/html/node/134) and it has been going great except i cant get the system to send any code. i jsut keep getting this error "
rob@media-center:~$ irsend SEND_ONCE DC50X 1
irsend: command failed: SEND_ONCE DC50X 1
irsend: hardware does not support sending
"

i have for my cable box a pace DC50X and am jsut confused on what the problem is. my hardware is as follows
amd phenom 2 x4 945 cpu
4gb ram
gigabyte ga-870a-ud3 mobo
9400gt video card
and a hauppauge winttv-hvr-1600
firefly rf remote


everything is running great in mythtv but i cant get the ir blaster to control the box. it isnt even sending a ir signal for some reason.  my lirc config is as follows



#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the ATI/NVidia/X10 RF Remote (userspace) remote:
#include "/usr/share/lirc/remotes/atiusb/lircd.conf.atilibusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Motorola Cable$
include "/usr/share/lirc/extras/transmitters/pace/pace.conf"



and the pace.conf file is 

# contributed by Mike Silliman
#
# brand: Pace
# supported devices: Pace DC50X (Comcast Digital Transport Adapter)
#
# Protocol: XMP-R
# Device: 62.16

begin remote
name DC50X
flags RAW_CODES
eps 30
aeps 100
gap 80412
begin raw_codes

name 1
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2656 210 763
210 763 210 763 210 894
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1578 210 1841
210 763 210 763 210 894
210 763 210 763 210

name 2
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2524 210 763
210 763 210 763 210 1026
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1446 210 1841
210 763 210 763 210 1026
210 763 210 763 210

name 3
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2393 210 763
210 763 210 763 210 1157
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1315 210 1841
210 763 210 763 210 1157
210 763 210 763 210

name 4
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2261 210 763
210 763 210 763 210 1315
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1157 210 1841
210 763 210 763 210 1315
210 763 210 763 210

name 5
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2130 210 763
210 763 210 763 210 1446
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1026 210 1841
210 763 210 763 210 1446
210 763 210 763 210

name 6
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1972 210 763
210 763 210 763 210 1578
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 894 210 1841
210 763 210 763 210 1578
210 763 210 763 210

name 7
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1841 210 763
210 763 210 763 210 1709
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 763 210 1841
210 763 210 763 210 1709
210 763 210 763 210

name 8
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1709 210 763
210 763 210 763 210 1841
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2787 210 1841
210 763 210 763 210 1841
210 763 210 763 210

name 9
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1578 210 763
210 763 210 763 210 1972
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2656 210 1841
210 763 210 763 210 1972
210 763 210 763 210

name 0
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2787 210 763
210 763 210 763 210 763
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1709 210 1841
210 763 210 763 210 763
210 763 210 763 210

name Enter
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1841 210 763
210 763 210 1026 210 1446
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 763 210 1841
210 763 210 1026 210 1446
210 763 210 763 210

end raw_codes
end remote


any help on getting the serial irblaster setup so it can atleast send a signal  that would be great.

---

### Post by larsolav on 2011-01-24
> **crazyone said:**
> ... it is a serail. 
...

#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the ATI/NVidia/X10 RF Remote (userspace) remote:
#include "/usr/share/lirc/remotes/atiusb/lircd.conf.atilibusb"

**#Configuration for the Microsoft Windows Media Center V2 (usb) : Motorola Cable$**
include "/usr/share/lirc/extras/transmitters/pace/pace.conf"


You say the transmitter is serial? In mythbuntu control center, can you select a serial transmitter in combination with your cable box? Then maybe that will prepare lirc_serial for you as they discuss in the link you provided in your post. Good luck!

---

### Post by crazyone on 2011-01-26
thanks for the response. sorry it took so long ot repsond got tired up with school work. but i ended up getting a usb blaster that is known to work.  ill try that after i get my master backend setup though for my other mythtv system i am hoping to setup.

---

