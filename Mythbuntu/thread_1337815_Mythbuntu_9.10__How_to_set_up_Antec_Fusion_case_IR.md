---
title: "Mythbuntu 9.10:  How to set up Antec Fusion case IR and MCE remote control..."
date: 2009-11-25
forum: Mythbuntu
---

### Post by bradsthompson on 2009-11-25
Hi,

I worked through the How-to in the sticky section but cannot get the LCD/IR receiver on my Antec case to recognize commands from my MCE remote control (Logitech 880 programmed with MCE commands).  I am a total n00b at linux/Ubuntu and wasn't sure if I should be following the same instructions for 9.10 since they are for 8.10.  Installation gives me a choice between several different iMon displays from Soundgraph but I can't get any to work.  I seem to have ffdc version of the screen.

Can someone help get me started?

---

### Post by geobre on 2009-11-26
Hi,
Im not very experienced with myth either.. but I used myth control center to choose the:
Soundgraph iMON Antec Veris remote
That made it possible to get the lcd display etc to work. The other once didnt work, not even the Imon-pad remote, that I saw suggested some where..
Once the hardware in your case are working and your box accepts input from your remote (try with irw as in the guide you followed) you can find a lot of remote setups in /usr/share/lirc/remotes/ wich u can copy and replace in the /etc/hardware.conf, lircd.conf /home/user/.mythtv/lircrc and /home/user/.lirc


(U can also cheat, and choose the remote you use eg. mce in myth-control-center to get the settings for that remote, back up the files above, and then u choose the Imon remote to get lcd, ir-receiver and stuff to work. Once you done that you have to merge your backed up files with the new settings, so you keep the hardware part from Imon settings and the remote part from your mce settings. Hope it makes sence..) It worked for me at least, and in the settings files its not hard to se wich part goes for the remote, and wich is for the case (receiver and lcd). As I said, my experience with Myth is rather scarce, maybe someone else can help u out in a better way.

---

### Post by Neon Dusk on 2009-11-26
> **bradsthompson said:**
> Hi,

I worked through the How-to in the sticky section but cannot get the LCD/IR receiver on my Antec case to recognize commands from my MCE remote control (Logitech 880 programmed with MCE commands).  I am a total n00b at linux/Ubuntu and wasn't sure if I should be following the same instructions for 9.10 since they are for 8.10.  Installation gives me a choice between several different iMon displays from Soundgraph but I can't get any to work.  I seem to have ffdc version of the screen.

Can someone help get me started?

I'm using the Antec case with the iMon VFD (not the LCD) so this might not work for you.

You should have a file /usr/share/lirc/remotes/imon/lircd.conf.imon-mceusb that's for a MCE remote (or the Harmony using the MCE codes) with the Antec receiver.

To use this file :-
Edit /etc/lirc/hardware.conf and change
the REMOTE_LIRCD_CONF line to
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-mceusb"

Edit /etc/lirc/lircd.conf
and change the include line to
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-mceusb

restart lirc
sudo service lirc resart

run irw then press some buttons on the remote to see if they're recognised.

Note: The included lircd.conf.imon-mceusb didn't work for me so I did an irrecord to identify the codes and replaced lircd.conf.imon-mceusb with 

```

# brand:                       mceusb
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  mceusb
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x800F04
  gap          203990
  min_repeat      1
  toggle_bit_mask 0x8000

      begin codes
          Blue                     0x5E
          Yellow                   0x5D
          Green                    0x5C
          Red                      0x5B
          Teletext                 0x5A
#		  
		  Radio                    0x50
#		  
		  Subtitle                 0x4D
		  Audio                    0x4C
#
          Videos                   0x4A
          Pictures                 0x49
          RecTV                    0x48
          Music                    0x47
		  TV                       0x46
#		  
		  Aspect                   0x27
          Guide                    0x26
          LiveTV                   0x25
          DVD                      0x24
#	  
          Back                     0x23
          OK                       0x22
          Right                    0x21
          Left                     0x20
          Down                     0x1F
          Up                       0x1E
#
          Star                     0x1D
          Hash                     0x1C
#	  
          Replay                   0x1B
          Skip                     0x1A
          Stop                     0x19
          Pause                    0x18
          Record                   0x17
          Play                     0x16
          Rewind                   0x15
          Forward                  0x14
#	  
          ChanDown                 0x13
          ChanUp                   0x12
		  VolDown                  0x11
		  VolUp                    0x10
#	  
          More                     0x0F
		  Mute                     0x0E
          Home                     0x0D
          Power                    0x0C
#
          Enter                    0x0B
          Clear                    0x0A		 
#
          Nine                     0x09
          Eight                    0x08
          Seven                    0x07
          Six                      0x06
          Five                     0x05
          Four                     0x04
          Three                    0x03
          Two                      0x02
          One                      0x01
          Zero                      0x00
      end codes

end remote

```

---

