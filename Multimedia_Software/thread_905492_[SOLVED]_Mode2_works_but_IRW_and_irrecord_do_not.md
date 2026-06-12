---
title: "[SOLVED] Mode2 works but IRW and irrecord do not"
date: 2008-08-30
forum: Multimedia Software
---

### Post by helicoptergeek on 2008-08-30
I have been working on trying to get my mythbuntu 8.04 system to recognize my remote.  I am using the Philips OVU4003 (MCE) to receive the signal and a vizio universal remote to send the signal.  

I noticed that the philips would light up every time I pressed a button on the remote but could not get irw to recognize any signal input.  I finally found out about mode2 and that does register button presses on my remote.

I am new to ubuntu/mythbuntu and this is my first post.  I tried to find other threads but that proved unsuccessful.

Any help would be greatly appreciated.

---

### Post by helicoptergeek on 2008-08-31
I got it to work with a hack.  I found the universal code for an xbox360 controller and programmed my remote.  Then I downloaded the lircd.conf for the xbox360.

The command that I use is 
```

sudo irrecord -H dev/input -d /dev/input/event4 altlircd.conf

```

I understand the sudo and irrecord.  The altlircd.conf is the file the results get sent to.  If someone could explain the -H dev/input and the -d /dev/input/event4 I might be able to get this to work. 

While the current solution works, I would like to find a good irrecord tutorial because I am out of my depth.

---

### Post by helicoptergeek on 2008-09-01
Well I finally got it all to work.  For those that have not found (like me until today) there is a good how to install lirc.  It can be found at [https://help.ubuntu.com/community/InstallLirc/Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy").

With this use of that page I was able to sucessfully run and save irrecord.  For those interested, here are the results:
```

# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Mon Sep  1 13:50:49 2008
#
# contributed by 
#
# brand:               VIZIO
# model no. of remote: VIZIO Remote Control VUR8
#		       http://www.vizio.com/accessoryDetails.aspx?id=1430
# devices being controlled by this remote:
# 	TV:		VIZIO GV42L	Code: 11758
#	Game Consel:	XBOX 360	Code: 21708
#	MythTv:		MCEUSB Philips	Code: 20503

# IMPORTANT!
# Inorder to get this to work you need to program on of the buttons (DVD, 
# Audio, Cable) to 20503.  I did this so that controling the MythTv box would
# conflict with the Vizio TV.  
begin remote

  name  Vizio GV42L
  bits           32
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       8991  4437
  one           576  1660
  zero          576   539
  ptrail        559
  repeat       8961  2240
  gap          107369
  toggle_bit_mask 0x0

      begin codes
          1                        0xA25D807F
          2                        0xA25D40BF
          3                        0xA25DC03F
          4                        0xA25D20DF
          5                        0xA25DA05F
          6                        0xA25D609F
          7                        0xA25DE01F
          8                        0xA25D10EF
          9                        0xA25D906F
          0                        0xA25D50AF
          Input                    0xA25DE718
          -                        0xA25DA45B
          Menu                     0xA25D21DE
          Info                     0xA25D6897
          Guide                    0xA25D7B84
          Exit                     0xA25D44BB
          Ok                       0xA25D847B
          Up                       0xA25D01FE
          Down                     0xA25D817E
          Left                     0xA25D8A75
          Right                    0xA25DB24D
          Last                     0xA25DD42B
          Mute                     0x20DF906F
          Volume_Up                0x20DF40BF
          Volume_Down              0x20DFC03F
          Channel_Up               0xA25D01FE
          Channel_Down             0xA25D817E
          Pause                    0xA25D00FF
          Play                     0xA25DA857
          Stop                     0xA25D28D7
          Fast_Forward             0xA25DC837
          Rewind                   0xA25D9867
          Skip_Foward              0xA25D24DB
          Skip_Back                0xA25DC43B
          Rec                      0xA25D17E8
      end codes

end remote

```

---

### Post by bedek on 2010-06-09
I've just found on ebay "Philips USB IR Remote Receiver Media Centre OVU4003/00" and I'm not sure if I should buy it to use with Ubuntu 10.4 (for XBMC)

As I understand this is not by default supported under Ubuntu (it's not on the list of supported devices when installing lirc).

I also understand that there is way to run this device and it can work fully with lirc after loading proper configuration and modules (including remote control configuration etc.) ?

---

### Post by esplinter on 2010-09-29
Hi,

I am using this remote with xubuntu 10.04 and every button works out of the box.

When installing lirc (or doing dpkg-reconfigure lirc) you have to select "windows media center remote (all)" and everything works great.

---

### Post by bedek on 2010-09-30
My problem is that receiver seems to blink (which informs that it receives signal from remote) even when I'm not pressing any button on remote - is any of you have same problem with receiver ?

Here is photo of my receiver:
[http://attachments.techguy.org/attachments/112068d1185610264/ir-receiver-001.jpg](http://attachments.techguy.org/attachments/112068d1185610264/ir-receiver-001.jpg)

---

