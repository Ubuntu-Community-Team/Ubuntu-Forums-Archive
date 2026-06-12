---
title: "Ubuntu 10.10 cannot read DVD. I know it has been posted before, but neither of the an"
date: 2010-10-31
forum: Multimedia Software
---

### Post by pmbayon on 2010-10-31
I fixed VLC to point to the correct device /dev/sr0)
I executed sudo apt-get install ubuntu-restricted-extras
If I play a music CD instead of a movie DVD, it works correct, so the device must work
VLC and Movie Player work correctly with any video file in the computer.

If it helps, this is what the log says:

Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019744] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019752] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019759] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019769] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 d5 80 00 00 02 00
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019782] end_request: I/O error, dev sr0, sector 218624
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019788] quiet_error: 124 callbacks suppressed
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019792] Buffer I/O error on device sr0, logical block 54656
Oct 31 13:14:39 pablo-laptop kernel: [ 4079.019797] Buffer I/O error on device sr0, logical block 54657
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179664] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179675] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179685] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179700] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 05 77 14 00 00 02 00
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179722] end_request: I/O error, dev sr0, sector 1432656
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179732] Buffer I/O error on device sr0, logical block 358164
Oct 31 13:14:40 pablo-laptop kernel: [ 4079.179740] Buffer I/O error on device sr0, logical block 358165

Thanks in advance.

---

### Post by cascade9 on 2010-10-31
You need to install extra software(libDVDss) to play DVDs, not just ubuntu-restricted-extras. 

> **Installing libdvdcss**

 Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area. 
 
**Ubuntu 9.04, 9.10 and 10.04 (i386, amd64)**

 
[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]

 sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

 sudo /usr/share/doc/libdvdread4/install-css.shRebooting may be necessary. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by pmbayon on 2010-10-31
Thank you very much. It works fine. So easy...

---

### Post by cascade9 on 2010-11-01
Glad it helped ;)

---

