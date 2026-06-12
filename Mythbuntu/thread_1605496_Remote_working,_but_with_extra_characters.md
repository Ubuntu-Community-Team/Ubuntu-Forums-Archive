---
title: "Remote working, but with extra characters"
date: 2010-10-25
forum: Mythbuntu
---

### Post by Spr0k3t on 2010-10-25
I'm not at home right now so I can't post the exact file details of my lirc configuration.  However, I am using an MCE remote which has worked for quite some time.  Just recently an update has rendered the remote almost useless.  Pressing a button (left) will perform multiple instances of "left".

I'll post an output of irw when I get home, but thought someone might know of a simple fix for the issue.

---

### Post by ian dobson on 2010-10-25
Hi,

OK, run irw and look at the codes it dumps. Something like:-

00000000000017b0 00 Pause Hauppauge_350
00000000000017b0 01 Pause Hauppauge_350
00000000000017b0 00 Pause Hauppauge_350
00000000000017b0 01 Pause Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 01 Vol+ Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
0000000000001791 01 Vol- Hauppauge_350

if you see more than one key press per real key press, then continue.

open the lirc configuration file (/etc/lirc/lircd.conf), at the bottom of the file there's a line include and a file name within ". Open the included file and delete all remotes apart from your one. For example I have a hauppage 350 remote and my config file looks like

```

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2
      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0

      end codes

end remote

```

Regards
Ian Dobson

---

### Post by Spr0k3t on 2010-10-25
K, opening up irw at the terminal, this is what I got from pressing the up and down keys three times each.

```
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 02 Up mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07be0 02 Down mceusb
^C

```

Looking at the file at /etc/lirc/lircd.conf pointed me to the file /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

I left mceusb and took out the mceusb_hauppauge and vista_mce.

Still the same results as above.

---

### Post by ian dobson on 2010-10-26
Hi,

Did you restart the system/lirc after changing? I had exactly the same problem and after editing/rebooting eveything was back to normal.

Regards
Ian Dobson

---

### Post by Spr0k3t on 2010-10-26
Yeah, I restarted lirc and verified the output.  Still no luck.

---

### Post by Spr0k3t on 2010-10-27
Fixed!  I followed these steps:

> Blacklist the kernel source drivers and use the old dkms built drivers.
-Well you already have lirc-sources-modules install and probably had this working on 10.04 or older version of ubuntu.
A. Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
Add>
blacklist mceusb
line to the file and save it.
B. Update initrmafs, #sudo update-initramfs -u -k all
C. reboot
D. Reconfigure lirc if its not already working.
#sudo dpkg-reconfigure lirc
On the Remote, Select "Windows Media Center Transceiver/Remote (All)
E. Thats it.
This is the method I chose after wrestling with button repeats on option 1. I use XBMC and could not figure out how to disable Ubuntu treating the remote as a keyboard device.

[http://ubuntuforums.org/showthread.php?t=1594799](http://ubuntuforums.org/showthread.php?t=1594799)

---

