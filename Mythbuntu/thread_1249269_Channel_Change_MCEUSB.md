---
title: "Channel Change MCEUSB"
date: 2009-08-25
forum: Mythbuntu
---

### Post by sirbanks on 2009-08-25
I have Googled and searched this to death with no success and hope someone can help me out. Using Mythbuntu 9.04 with MCE Remote and transmitter and Scientific Atlanta 3250 cable box. Remote works mostly after Myth install, but Scientific Atlanta 3250 will not change channels. Problem is not the code to change channels (at least not yet), problem is that the IR transmitter is not being activated. I know I need a channel change script and this is where it gets really confusing. I have found numerous scripts on the net but none work. I have created my own, made it executable and placed in /usr/local/bin and then referenced it in the MythTV backend, but all that happens is that when I select "Watch TV", the screen blanks for a second and then goes back to the menu. If I remove the reference, then I can watch TV fine, just cannot control cable box (the internal tuner channel change works fine). I'm thinking the problem is the channel change script but am getting nowhere. Any help is appreciated!

---

### Post by hackmeister on 2009-08-25
First things first. Are you able to change channels from the command line? Do you have your cable box properly defined in lircd.conf? I wrote the how-to for the Motorola DCT700 cable box:
[https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script?highlight=%28dct700%29](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script?highlight=%28dct700%29)

If the box is properly defined you should be able to change channels and get the on screen display from your cable box to pop up. What happens when you type 'irw' in the commandline and start hitting keys? You should see the key press popup on the commandline. Check out the section "Testing the Remote definition and blaster". Once you can do that you can proceed to the channel changing script.

---

### Post by sirbanks on 2009-08-26
Thanks for getting back to me. I have looked at your instructions and they have helped me get a long way. Where I am hanging up is with the transmitter. I used the MCEUSB link in your instructions and under "IR Blasting" followed those instructions. I added the code for "MCEUSB" to the lircd.conf file and tested it OK. But when I try to enter $[FONT=monospace] [/FONT]irsend SET_TRANSMITTERS 1 (or 2 for that matter) I get the following error:
irsend: command failed: SET_TRANSMITTERS 1
irsend: hardware does not support sending

The blaster does not attempt to send a signal. However, the problem with the blank screen for a few seconds when the "Watch TV" selection is chosen in MythTV is gone and now the TV comes up as normal. Only when I change channels, it changes in the internal tuner and not the blaster. Again, thanks for your help.

---

### Post by sirbanks on 2009-08-26
OK, more info. irsend LIST returns a list of commands. Anytime I try irsend SEND_ONCE XXXX I get the error irsend: command failed: SEND_ONCE SAE8000 info
irsend: hardware does not support sending

I may have a screwed lircd.conf file. Here is my file:

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (old version MicroSoft USB ID) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box transmitter:
include "/usr/share/lirc/transmitters/scientificatlanta/general.conf"

#Everything after this was added 8/26/2009 by me.

#
# this config file was automatically generated
# using lirc-0.6.6(sir) on Wed Mar 24 22:28:59 2004
#
# Modified by Stephane Lavergne <stephane|iMars.com>:
#    Base frequency is 56kHz, irrecord was otherwise right on.
#
# contributed by 
#
# brand:                       Scientific Atlanta
# model no. of remote control: AT8400
# devices being controlled by this remote: Explorer 8000
#

begin remote

  name  SAE8000
  bits           22
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       3397  3372
  one           827  2557
  zero          827   855
  ptrail        827
  gap          101386
  toggle_bit      0

  frequency 56000

      begin codes
          power                    0x000000000037C107
          guide                    0x000000000036C127
          menu                     0x000000000036F920
          info                     0x000000000036213B
          select_up                0x000000000036812F
          select_down              0x000000000037A10B
          select                   0x0000000000366133
          select_left              0x000000000037810F
          select_right             0x0000000000364137
          select_page+             0x000000000036D924
          select_page-             0x000000000037D904
          exit                     0x0000000000366932
          settings                 0x0000000000373918
          A                        0x000000000037E902
          B                        0x000000000036193C
          C                        0x000000000037191C
          vol+                     0x000000000036093E
          vol-                     0x000000000037091E
          ch+                      0x0000000000377111
          ch-                      0x000000000036F121
          mute                     0x000000000036892E
          fav                      0x000000000037F101
          last                     0x000000000036E123
          rew8secs                 0x000000000037C906
          list                     0x000000000036C926
          live                     0x000000000036B129
          rew                      0x000000000037291A
          ff                       0x000000000036293A
          play                     0x000000000037990C
          stop                     0x0000000000365934
          pause                    0x0000000000374117
          rec                      0x0000000000375914
          1                        0x000000000036113D
          2                        0x000000000037111D
          3                        0x000000000036912D
          4                        0x000000000037910D
          5                        0x0000000000365135
          6                        0x0000000000375115
          7                        0x000000000036D125
          8                        0x000000000037D105
          9                        0x0000000000363139
          asterisk                 0x000000000037E103
          0                        0x0000000000373119
          pound                    0x000000000036B928
          pip_power                0x000000000037B908
          pip_swap                 0x0000000000367930
          pip_move                 0x0000000000377910
          pip_ch+                  0x000000000036E922
          pip_ch-                  0x000000000037F900
          video_source             0x0000000000376113
      end codes

end remote

#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

#
# RC-6 config file
#
# source: [http://home.hccnet.nl/m.majoor/projects__remote_control.htm](http://home.hccnet.nl/m.majoor/projects__remote_control.htm)
#         [http://home.hccnet.nl/m.majoor/pronto.pdf](http://home.hccnet.nl/m.majoor/pronto.pdf)
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              200000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
    Blue          0x00007ba1
    Yellow          0x00007ba2
    Green          0x00007ba3
    Red          0x00007ba4
    Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

I am very confused about whether this file should include info for my remote control (HP MCE) or the Scientific Atlanta Cable Box or both. I have tried no code, MCE only, SA only and now both. The HP remote control works (except for the BACK button which I wished acted like the keyboard ESC key). I just cannot get a rise out of the USB transmitter. I have read everything I can find, but it gets quite confusing with the different files in different locations. Again, thanks for any assistance you can provide.

---

### Post by sirbanks on 2009-08-31
Bumping after a few days. I feel like this is probably old news to most, but I have absolutely not been able to find the solution. I stumbled across one tidbit that said that the MCEUSB (OLD) did not support IR transmitters? I tried the MCEUSB, but my remote will not function with that. Is the Firefly kit easier to setup? Advice appreciated.

---

### Post by Zennmaster on 2009-09-02
I am having the exact same problem. I'll be watching this thread anxiously, and will post anything I may find!

---

### Post by hackmeister on 2009-09-02
> **sirbanks said:**
> 
I am very confused about whether this file should include info for my remote control (HP MCE) or the Scientific Atlanta Cable Box or both. I have tried no code, MCE only, SA only and now both. The HP remote control works (except for the BACK button which I wished acted like the keyboard ESC key). I just cannot get a rise out of the USB transmitter. I have read everything I can find, but it gets quite confusing with the different files in different locations. Again, thanks for any assistance you can provide.

lircd.conf contains the codes for your satellite/cable box. The .lircrc file contains the remote key associations with your applications used by Myth. If the remote is working and you can navigate your menus you're done with the receiving part of the equation.

So at this point can you change the channels from the command line or are you still getting the message about not being able to transmit?

---

### Post by sirbanks on 2009-09-02
Hackmeister, thanks for getting back to me. Yes, the remote is still working although some buttons do not do what I would like: this is a different topic for a different discussion, however. It works well enough. Pertaining to the transmitter however, I never was able to get the transmitter to transmit. I continued to get the error that the hardware was not supported. After weeks of working on this and reading everything I could find, twice, I finally backed up and went a new direction, one that I would recommend if possible: use the Fireware connection. I have a firewire port on my SA 3250HD cable box and I was able to download, compile and use obtained code to change my channels. Just got it working this morning and so far I am pleased. I strongly recommend to anyone fighting this problem to see if your cable box has a firewire port and then use this option if possible. It worked for me. Info is on mythtv.org. Thanks again for all the help, but I've given up on IR transmitter at this point. On to other items!

---

### Post by hackmeister on 2009-09-02
> **sirbanks said:**
> Pertaining to the transmitter however, I never was able to get the transmitter to transmit. I continued to get the error that the hardware was not supported. After weeks of working on this and reading everything I could find, twice, I finally backed up and went a new direction, one that I would recommend if possible: use the Fireware connection. 

Which model mce was this? I have 2 older ones that worked pretty easily in Mythbuntu, LinHES and Mythdora. I wonder if it's the newer models that are having problems? Maybe you had a bad unit?

---

### Post by Zennmaster on 2009-09-03
Congrats to sirbanks for finding a workable alternative!  I don't think that option will work for me, so if anyone is still willing to think about this one, I'll pick up the baton.

Hackmeister: the unit I am using is actually the HP OVU400102/71, which has a R6 marking on it, and is supposed to use thesame drivers as the new MCE. 

It seems very odd that this combination just "Don't Work"...

---

### Post by hackmeister on 2009-09-04
> **Zennmaster said:**
> the unit I am using is actually the HP OVU400102/71, which has a R6 marking on it, and is supposed to use the same drivers as the new MCE. 
Mmm I've heard that the HP MCE remotes can be a little touchy. Read this thread on the mythtv-users mailing list:
[http://mythtv.org/pipermail/mythtv-users/2009-September/263463.html](http://mythtv.org/pipermail/mythtv-users/2009-September/263463.html)

Is that the one you have?

---

### Post by Zennmaster on 2009-09-04
> **hackmeister said:**
> 
[http://mythtv.org/pipermail/mythtv-users/2009-September/263463.html](http://mythtv.org/pipermail/mythtv-users/2009-September/263463.html)

Is that the one you have?

That would be the one. That exchange inspired me to try the other driver (mceusb2 vs mceusb), to no avail.  My lircd.conf file is just the one generated by the lirc setup utility, with the dct700 code cut and pasted in from your very useful howto.  

Still quite baffled!

---

