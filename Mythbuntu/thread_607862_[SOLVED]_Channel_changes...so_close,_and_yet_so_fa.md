---
title: "[SOLVED] Channel changes...so close, and yet so far. PVR-150 MCE, USB IR Blaster, Dir"
date: 2007-11-09
forum: Mythbuntu
---

### Post by linuxlibrarian on 2007-11-09
I have set up a Mythbuntu box for my husband... It's a scratchbuilt AMD 64 2.4 Ghz (single core), gig of ram, 250 gig sata hard drive, Biostar TForce 7050 M2 motherboard with onboard NVIDIA graphics, a wireless card of some variety and a Hauppauge PVR-150 MCE (the one with the usb IR blaster, and the black vista remote)

Honestly, it all works great. Except I can't change the channels on our DirecTV receiver using the IR Blaster/Remote. I have beat my head against the wall for the last two weeks.

Here's what I *do* know: IRW shows button presses, and the Mythbuntu set up responds well to every command EXCEPT channel changes. So I can use the remote to navigate around the Myth menus, I can pause live TV, I can traverse the Guide.

I know that the transmitter attached to the blaster that anchors on to the DirecTV receiver is working... (finally). The LED lights when I press the buttons, and I've even looked at it under the LCD of my digital camera to make extra sure. I am 99.99% sure it is placed correctly.... 

I am using the script that came with LIRC... the change-channel-lirc.pl script. Permissions seem appropriate, and the log (which I don't have handy now... but I can get) registers that channel changes are being attempted. Even the OSD changes... but when I press "Enter" or directly press in a number.... nothing happens (except the OSD changes... Not the actual channel)

So for kicks, I tried using the change-channel-lirc.pl script via the command line. I get this error:

/usr/bin/change-channel-lirc.pl  5

irsend unknown command 5

I *think* this is because my lircd.conf has the numbers written out "Five" "Six" "Eight"... However, I thought my lircrc was supposed to handle the mapping/conversion of the written out numbers to the numerals? 

I tried editing lircd.conf so that the written out numbers read this way:

instead of:
Five  (string of key codes)
I wrote:
5      (string of key codes)

But that only rendered my number buttons totally useless. :(

Any ideas why I'm getting this error? I copied the[ lircd.conf (and the lircrc) from this thread on the Hauppauge UK boards.]("http://www.hauppauge.co.uk/board/showthread.php?t=8048")

I tried to see if maybe the lircrc had a parsing error (like weird line breaks), but I don't know how to really tell.  

I figure even if this script snafu *isn't* why I can't change the channels, I've got to work it out before I know for sure that our DirecTV receiver stinks. ;) 

For what it's worth: DirecTV receiver is a Philips DSX 5250. Conveniently has NO serial, low speed data or USB port, so I *have* to use the ir blaster. Grrr.

Any ideas as to why irsend isn't recognizing numbers... I'd be greatly appreciative!

thanks!
shoe

---

### Post by linuxlibrarian on 2007-11-09
Okay, I figured it out... I changed the numbers in lircd.conf, lircrc, and had to make sure that both /etc/lircd.conf and /etc/lirc/lircd.conf were the same... (Go figure)

However, I still can't seem to change channels. Is it possible that the transmitter doesn't transmit the same frequency as my receiver is set to receive? Anyone gotten Mythbuntu to work with an IR blaster and an old Philips DirecTV box? Grrr.

shoe

---

### Post by superm1 on 2007-11-10
> **linuxlibrarian said:**
> Okay, I figured it out... I changed the numbers in lircd.conf, lircrc, and had to make sure that both /etc/lircd.conf and /etc/lirc/lircd.conf were the same... (Go figure)

However, I still can't seem to change channels. Is it possible that the transmitter doesn't transmit the same frequency as my receiver is set to receive? Anyone gotten Mythbuntu to work with an IR blaster and an old Philips DirecTV box? Grrr.

shoe

This is the mceusb2 based remote that you are referring to, correct?  There has been a lot of confusion with this remote for a lot of people (including myself).  I've only got it to work with one device of mine, unfortunately that isn't a direct tv receiver.

The lircd.conf that you are using, it should have two remotes in it: the mceusb2 one and the one for a direct tv receiver.

Lets see a copy of that to start, and make sure that nothing looks crazy about it.

Next, lets see the change-channel-lirc.pl that you are referring to.

If we can't nail the problem in either of those two files, then i have a more low tech possible solution.  We'll go into that after looking over these files.

---

### Post by linuxlibrarian on 2007-11-10
Hey! Thanks!

My lircd.conf is this, lifted verbatim off the Hauppauge UK forums:

```
########
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
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
# Radio, Print are only available on the HP Media Center remote control
#
#########
#
# Edited 24th May 2006 by pepsi_max2k (inaudible.co.uk)
#
# Updated button names & formatting
# for use with Hauppauge 1300 MCE Kit remote (RC 6 ir).
# 
#########


begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Power		0x00007bf3	# no e2,e3
	MyTV		0x00007bb9	# starts at af
	MyMusic		0x00007bb8	# starts at af
	MyPictures	0x00007bb6	# starts at af
	MyVideos	0x00007bb5	# starts at af
	Record		0x00007be8	# no e2,e3
	Stop		0x00007be6	# no e2,e3
	Pause		0x00007be7	# no e2,e3
	Play		0x00007be9	# no e2,e3
	Rewind		0x00007bea	# no e2,e3
	Forward		0x00007beb	# no e2,e3
	Replay		0x00007be4	# no e2,e3
	Skip		0x00007be5	# no e2,e3
	More		0x00007bf0	# no e2,e3
	Back		0x00007bdc	# no ba - d8
	Left		0x00007bdf	# no ba - d8
	Right		0x00007bde	# no ba - d8
	Up		0x00007be1	# no ba - d8
	Down		0x00007be0	# no ba - d8
	OK		0x00007bdd	# no ba - d8
	VolUp		0x00007bef	# no e2,e3
	VolDown		0x00007bee	# no e2,e3
	ChanUp		0x00007bed	# no e2,e3
	ChanDown	0x00007bec	# no e2,e3
	Home		0x00007bf2	# no e2,e3
	Mute		0x00007bf1	# no e2,e3
	RecordedTV	0x00007bb7	# starts at af
	Guide		0x00007bd9	# no ba - d8
	LiveTV		0x00007bda	# no ba - d8
	DVDMenu		0x00007bdb	# no ba - d8
	One		0x00007bfe	# no e2,e3
	Two		0x00007bfd	# no e2,e3
	Three		0x00007bfc	# no e2,e3
	Four		0x00007bfb	# no e2,e3
	Five		0x00007bfa	# no e2,e3
	Six		0x00007bf9	# no e2,e3
	Seven		0x00007bf8	# no e2,e3
	Eight		0x00007bf7	# no e2,e3
	Nine		0x00007bf6	# no e2,e3
	Zero		0x00007bff	# no e2,e3
	Star		0x00007be2	# no e2,e3
	Hash		0x00007be3	# no e2,e3
	Clear		0x00007bf5	# no e2,e3
	Enter		0x00007bf4	# no e2,e3
	Red		0x00007ba4	# no e2,e3
	Green		0x00007ba3	# no e2,e3
	Yellow		0x00007ba2	# no e2,e3
	Blue		0x00007ba1	# no e2,e3
	Teletext	0x00007ba5	# no e2,e3

#Following are unused with Hauppauge MCE remote.

	Radio		0x00007baf	# starts at af
	Print		0x00007bb1	# starts at af

      end codes

end remote
```

I guess I knew I needed the DirecTV receiver bit in there, but I'm a bit unsure *how* to get it in there. We do have a DirecTV remote (the RC24) working on the receiver that does have a lircd.conf configured for it... But it's all in raw codes.

So it looks like this:
```
# contributed by Cory Sharp <cssharp@mail.com>
# date 28 Jan 2007
#
# brand: DirecTV
# model no. of remote control: RC24
# devices being controlled by this remote: DirecTV H20 receiver
#
# Manufacturer code used for DirecTV: 00001 (DirecTV model D-10)
# Manufacturer code used for TV: 10000 (Supreme)
#
# To configure manufacturer codes for the remote, slide the switch to DirecTV
# or TV as appropriate, then hold mute and select until the LED blinks twice.
# Enter the five digit code -- success is indicated by two blinks after
# pressing the 5th digit.  Note: I could not find a TV code that enabled the
# tv-input button.
#
# The DirecTV RC24 RF protocol is currently unsupported by lirc.  If I
# understand it correctly: a zero bit is encoded a single 600us pulse or space,
# and a one bit is encoded as single 1200us pulse or space.  The initial button
# press has a 6000us pulse 1200us space header, and repeats have a 3000us pulse
# 1200us space header.  Buttons end in a 600us tail and have a 30000us gap.  A
# subset of the buttons emit a different code if held for about 42 repetitions,
# configured here as button names ending in -long.  Buttons specialized for the
# TV first triply emit a prelude button code in the DirecTV protocol, then the
# button code for the relevant TV.
#
# If LIRC supported this particular bit encoding, and if I understand the
# lircd.conf format correctly, this configuration would look something like:
#
# begin remote
#   gap 30000
#   header 6000 1200
#   repeat 3000 1200
#   ptrail 600
#   flags TIME_ENC
#   zero_duration 600
#   one_duration 1200
#   pre_data_bits 4
#   pre_data 0x0c
#   bits 12
#   begin codes
#     format 0x739
#     format-long 0x75a
#     ...
#   end codes
# end remote
#
# Note: I couldn't get lirc (version 0.8.1) to understand the 6000us header on
# the first button press, so the first button press is dropped, only repeats
# are recorded.

begin remote

  name  DirecTV_RC24
  flags RAW_CODES
  eps 30
  aeps 100

  gap 30000

      begin raw_codes

          name format
             3000    1200    1200    1200     600     600
              600    1200    1200    1200     600     600
             1200    1200    1200     600     600    1200
              600

          name format-long
             3000    1200    1200    1200     600     600
              600    1200    1200    1200     600    1200
              600    1200    1200     600    1200     600
              600

          name power
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
              600     600     600    1200     600    1200
              600

          name tv-power-on
             3000    1200    1200    1200     600     600
             1200     600     600     600     600     600
              600     600    1200    1200    1200     600
              600

          name tv-power-on-special
             2400     600     600     600    1200     600
             1200     600    1200     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name tv-power-off
             3000    1200    1200    1200     600     600
             1200     600     600     600     600     600
              600    1200    1200    1200    1200    1200
              600

          name tv-power-off-special
             2400     600    1200     600    1200     600
             1200     600    1200     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name rewind
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
             1200    1200     600     600    1200     600
              600

          name rewind-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600     600    1200     600     600     600
              600

          name play
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600

          name play-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
             1200     600     600    1200    1200    1200
              600

          name forward
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
              600     600     600     600    1200     600
              600

          name forward-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600    1200    1200     600     600    1200
              600

          name stop
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
              600    1200     600     600     600     600
              600

          name skip-back
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
             1200     600     600    1200     600     600
              600

          name skip-back-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
             1200    1200    1200     600    1200    1200
              600

          name skip-forward
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
             1200    1200     600    1200     600    1200
              600

          name skip-forward-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
              600     600     600    1200     600    1200
              600

          name pause
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
             1200     600     600     600     600    1200
              600

          name pause-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
             1200    1200    1200     600     600     600
              600

          name record
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
              600    1200     600     600    1200    1200
              600

          name record-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
             1200     600    1200     600    1200     600
              600

          name guide
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
              600     600     600     600     600     600
              600

          name guide-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
              600    1200     600    1200     600     600
              600

          name active
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
              600    1200     600     600     600    1200
              600

          name list
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
             1200     600     600     600    1200     600
              600

          name list-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
             1200    1200     600     600    1200    1200
              600

          name exit
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
             1200     600    1200    1200    1200    1200
              600

          name up
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
              600    1200    1200     600    1200    1200
              600

          name down
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
             1200     600    1200    1200     600     600
              600

          name left
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
             1200    1200    1200    1200     600    1200
              600

          name right
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
              600     600    1200    1200     600    1200
              600

          name select
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
              600    1200    1200    1200    1200     600
              600

          name back
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
             1200    1200     600     600     600     600
              600

          name menu
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
              600     600    1200     600    1200     600
              600

          name info
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
             1200     600     600    1200     600    1200
              600

          name info-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
              600     600     600     600    1200    1200
              600

          name red
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
              600    1200    1200     600     600     600
              600

          name red-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200     600
             1200     600    1200    1200    1200    1200
              600

          name green
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
             1200    1200    1200     600    1200     600
              600

          name green-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200    1200
              600     600     600     600     600     600
              600

          name yellow
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
             1200     600    1200     600     600    1200
              600

          name yellow-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200     600
             1200    1200     600     600     600     600
              600

          name blue
             3000    1200    1200    1200     600     600
              600    1200     600     600     600    1200
              600     600    1200     600    1200     600
              600

          name blue-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200    1200
              600    1200     600     600     600    1200
              600

          name volume-prelude
             3000    1200    1200    1200     600     600
              600    1200     600    1200    1200     600
              600    1200     600     600    1200    1200
              600

          name volume-up
             2400     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name volume-down
             2400     600    1200     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name mute
             2400     600     600     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name channel-up
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
              600    1200    1200     600    1200     600
              600

          name channel-down
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
             1200     600    1200     600    1200    1200
              600

          name prev
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
             1200    1200    1200    1200     600     600
              600

          name 1
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
              600    1200     600     600     600    1200
              600

          name 2
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
             1200     600     600     600    1200     600
              600

          name 3
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
             1200    1200     600     600    1200    1200
              600

          name 4
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
              600     600     600     600    1200    1200
              600

          name 5
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
              600    1200     600    1200     600     600
              600

          name 6
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
             1200     600     600    1200     600    1200
              600

          name 7
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
             1200    1200     600    1200    1200     600
              600

          name 8
             3000    1200    1200    1200     600     600
              600     600     600     600    1200     600
              600     600     600    1200    1200     600
              600

          name 9
             3000    1200    1200    1200     600     600
              600     600     600     600    1200     600
              600    1200     600    1200    1200    1200
              600

          name dash
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
             1200     600     600    1200    1200    1200
              600

          name 0
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
              600    1200     600    1200    1200     600
              600

          name enter
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
             1200    1200    1200     600     600     600
              600

      end raw_codes

end remote

```

I have tried cat'ing the files together, but either I did it wrong, or it didn't like something about the files, because I lost use of both remotes that way.

So I guess the question is, CAN I cat these two files together? If it is possible, how? And do I need another module loaded to make it run, or is using lirc_mceusb2 okay for them both? Is there another way to get the codes for the DirecTV receiver?

The channel change script I ended up having the most luck with was this:
```
#!/bin/sh
REMOTE_NAME=mceusb
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 
``` 

The script is executing fine now, the usb little box lights up, as does the little bug that attaches to the front of the satellite receiver. Alas, there is no channel change (although there is a change in the OSD and a change registered when I look at the output of mythfrontend -v channel)

Thanks for your help.... I'm sorta wondering if it's not time to upgrade the receiver (or heck, downgrade it) to a model that actually has a serial or usb port. We seem to have gotten stuck with the receiver time forgot... But now I've been presented with a challenge to get THIS receiver going, and I'm going to exhaust every possibility before conceding defeat. :)

thanks again!
shoe

---

### Post by superm1 on 2007-11-10
> **linuxlibrarian said:**
> Hey! Thanks!

My lircd.conf is this, lifted verbatim off the Hauppauge UK forums:

```
########
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
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
# Radio, Print are only available on the HP Media Center remote control
#
#########
#
# Edited 24th May 2006 by pepsi_max2k (inaudible.co.uk)
#
# Updated button names & formatting
# for use with Hauppauge 1300 MCE Kit remote (RC 6 ir).
# 
#########


begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

    Power        0x00007bf3    # no e2,e3
    MyTV        0x00007bb9    # starts at af
    MyMusic        0x00007bb8    # starts at af
    MyPictures    0x00007bb6    # starts at af
    MyVideos    0x00007bb5    # starts at af
    Record        0x00007be8    # no e2,e3
    Stop        0x00007be6    # no e2,e3
    Pause        0x00007be7    # no e2,e3
    Play        0x00007be9    # no e2,e3
    Rewind        0x00007bea    # no e2,e3
    Forward        0x00007beb    # no e2,e3
    Replay        0x00007be4    # no e2,e3
    Skip        0x00007be5    # no e2,e3
    More        0x00007bf0    # no e2,e3
    Back        0x00007bdc    # no ba - d8
    Left        0x00007bdf    # no ba - d8
    Right        0x00007bde    # no ba - d8
    Up        0x00007be1    # no ba - d8
    Down        0x00007be0    # no ba - d8
    OK        0x00007bdd    # no ba - d8
    VolUp        0x00007bef    # no e2,e3
    VolDown        0x00007bee    # no e2,e3
    ChanUp        0x00007bed    # no e2,e3
    ChanDown    0x00007bec    # no e2,e3
    Home        0x00007bf2    # no e2,e3
    Mute        0x00007bf1    # no e2,e3
    RecordedTV    0x00007bb7    # starts at af
    Guide        0x00007bd9    # no ba - d8
    LiveTV        0x00007bda    # no ba - d8
    DVDMenu        0x00007bdb    # no ba - d8
    One        0x00007bfe    # no e2,e3
    Two        0x00007bfd    # no e2,e3
    Three        0x00007bfc    # no e2,e3
    Four        0x00007bfb    # no e2,e3
    Five        0x00007bfa    # no e2,e3
    Six        0x00007bf9    # no e2,e3
    Seven        0x00007bf8    # no e2,e3
    Eight        0x00007bf7    # no e2,e3
    Nine        0x00007bf6    # no e2,e3
    Zero        0x00007bff    # no e2,e3
    Star        0x00007be2    # no e2,e3
    Hash        0x00007be3    # no e2,e3
    Clear        0x00007bf5    # no e2,e3
    Enter        0x00007bf4    # no e2,e3
    Red        0x00007ba4    # no e2,e3
    Green        0x00007ba3    # no e2,e3
    Yellow        0x00007ba2    # no e2,e3
    Blue        0x00007ba1    # no e2,e3
    Teletext    0x00007ba5    # no e2,e3

#Following are unused with Hauppauge MCE remote.

    Radio        0x00007baf    # starts at af
    Print        0x00007bb1    # starts at af

      end codes

end remote
```I guess I knew I needed the DirecTV receiver bit in there, but I'm a bit unsure *how* to get it in there. We do have a DirecTV remote (the RC24) working on the receiver that does have a lircd.conf configured for it... But it's all in raw codes.

So it looks like this:
```
# contributed by Cory Sharp <cssharp@mail.com>
# date 28 Jan 2007
#
# brand: DirecTV
# model no. of remote control: RC24
# devices being controlled by this remote: DirecTV H20 receiver
#
# Manufacturer code used for DirecTV: 00001 (DirecTV model D-10)
# Manufacturer code used for TV: 10000 (Supreme)
#
# To configure manufacturer codes for the remote, slide the switch to DirecTV
# or TV as appropriate, then hold mute and select until the LED blinks twice.
# Enter the five digit code -- success is indicated by two blinks after
# pressing the 5th digit.  Note: I could not find a TV code that enabled the
# tv-input button.
#
# The DirecTV RC24 RF protocol is currently unsupported by lirc.  If I
# understand it correctly: a zero bit is encoded a single 600us pulse or space,
# and a one bit is encoded as single 1200us pulse or space.  The initial button
# press has a 6000us pulse 1200us space header, and repeats have a 3000us pulse
# 1200us space header.  Buttons end in a 600us tail and have a 30000us gap.  A
# subset of the buttons emit a different code if held for about 42 repetitions,
# configured here as button names ending in -long.  Buttons specialized for the
# TV first triply emit a prelude button code in the DirecTV protocol, then the
# button code for the relevant TV.
#
# If LIRC supported this particular bit encoding, and if I understand the
# lircd.conf format correctly, this configuration would look something like:
#
# begin remote
#   gap 30000
#   header 6000 1200
#   repeat 3000 1200
#   ptrail 600
#   flags TIME_ENC
#   zero_duration 600
#   one_duration 1200
#   pre_data_bits 4
#   pre_data 0x0c
#   bits 12
#   begin codes
#     format 0x739
#     format-long 0x75a
#     ...
#   end codes
# end remote
#
# Note: I couldn't get lirc (version 0.8.1) to understand the 6000us header on
# the first button press, so the first button press is dropped, only repeats
# are recorded.

begin remote

  name  DirecTV_RC24
  flags RAW_CODES
  eps 30
  aeps 100

  gap 30000

      begin raw_codes

          name format
             3000    1200    1200    1200     600     600
              600    1200    1200    1200     600     600
             1200    1200    1200     600     600    1200
              600

          name format-long
             3000    1200    1200    1200     600     600
              600    1200    1200    1200     600    1200
              600    1200    1200     600    1200     600
              600

          name power
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
              600     600     600    1200     600    1200
              600

          name tv-power-on
             3000    1200    1200    1200     600     600
             1200     600     600     600     600     600
              600     600    1200    1200    1200     600
              600

          name tv-power-on-special
             2400     600     600     600    1200     600
             1200     600    1200     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name tv-power-off
             3000    1200    1200    1200     600     600
             1200     600     600     600     600     600
              600    1200    1200    1200    1200    1200
              600

          name tv-power-off-special
             2400     600    1200     600    1200     600
             1200     600    1200     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name rewind
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
             1200    1200     600     600    1200     600
              600

          name rewind-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600     600    1200     600     600     600
              600

          name play
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600

          name play-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
             1200     600     600    1200    1200    1200
              600

          name forward
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
              600     600     600     600    1200     600
              600

          name forward-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
              600    1200    1200     600     600    1200
              600

          name stop
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
              600    1200     600     600     600     600
              600

          name skip-back
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
             1200     600     600    1200     600     600
              600

          name skip-back-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
             1200    1200    1200     600    1200    1200
              600

          name skip-forward
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
             1200    1200     600    1200     600    1200
              600

          name skip-forward-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
              600     600     600    1200     600    1200
              600

          name pause
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600     600
             1200     600     600     600     600    1200
              600

          name pause-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200     600
             1200    1200    1200     600     600     600
              600

          name record
             3000    1200    1200    1200     600     600
              600     600    1200    1200     600    1200
              600    1200     600     600    1200    1200
              600

          name record-long
             3000    1200    1200    1200     600     600
              600     600    1200    1200    1200    1200
             1200     600    1200     600    1200     600
              600

          name guide
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
              600     600     600     600     600     600
              600

          name guide-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
              600    1200     600    1200     600     600
              600

          name active
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
              600    1200     600     600     600    1200
              600

          name list
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
             1200     600     600     600    1200     600
              600

          name list-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200     600
             1200    1200     600     600    1200    1200
              600

          name exit
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
             1200     600    1200    1200    1200    1200
              600

          name up
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
              600    1200    1200     600    1200    1200
              600

          name down
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
             1200     600    1200    1200     600     600
              600

          name left
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
             1200    1200    1200    1200     600    1200
              600

          name right
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
              600     600    1200    1200     600    1200
              600

          name select
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
              600    1200    1200    1200    1200     600
              600

          name back
             3000    1200    1200    1200     600     600
              600     600    1200     600     600    1200
             1200    1200     600     600     600     600
              600

          name menu
             3000    1200    1200    1200     600     600
              600     600    1200     600     600     600
              600     600    1200     600    1200     600
              600

          name info
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
             1200     600     600    1200     600    1200
              600

          name info-long
             3000    1200    1200    1200     600     600
              600     600    1200     600    1200    1200
              600     600     600     600    1200    1200
              600

          name red
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
              600    1200    1200     600     600     600
              600

          name red-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200     600
             1200     600    1200    1200    1200    1200
              600

          name green
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
             1200    1200    1200     600    1200     600
              600

          name green-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200    1200
              600     600     600     600     600     600
              600

          name yellow
             3000    1200    1200    1200     600     600
              600    1200     600     600     600     600
             1200     600    1200     600     600    1200
              600

          name yellow-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200     600
             1200    1200     600     600     600     600
              600

          name blue
             3000    1200    1200    1200     600     600
              600    1200     600     600     600    1200
              600     600    1200     600    1200     600
              600

          name blue-long
             3000    1200    1200    1200     600     600
              600    1200     600     600    1200    1200
              600    1200     600     600     600    1200
              600

          name volume-prelude
             3000    1200    1200    1200     600     600
              600    1200     600    1200    1200     600
              600    1200     600     600    1200    1200
              600

          name volume-up
             2400     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name volume-down
             2400     600    1200     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name mute
             2400     600     600     600     600     600
             1200     600     600     600    1200     600
              600     600     600     600    1200     600
              600     600     600     600     600     600
              600

          name channel-up
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
              600    1200    1200     600    1200     600
              600

          name channel-down
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
             1200     600    1200     600    1200    1200
              600

          name prev
             3000    1200    1200    1200     600     600
              600     600     600     600    1200    1200
             1200    1200    1200    1200     600     600
              600

          name 1
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
              600    1200     600     600     600    1200
              600

          name 2
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
             1200     600     600     600    1200     600
              600

          name 3
             3000    1200    1200    1200     600     600
              600     600     600     600     600     600
             1200    1200     600     600    1200    1200
              600

          name 4
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
              600     600     600     600    1200    1200
              600

          name 5
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
              600    1200     600    1200     600     600
              600

          name 6
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
             1200     600     600    1200     600    1200
              600

          name 7
             3000    1200    1200    1200     600     600
              600     600     600     600     600    1200
             1200    1200     600    1200    1200     600
              600

          name 8
             3000    1200    1200    1200     600     600
              600     600     600     600    1200     600
              600     600     600    1200    1200     600
              600

          name 9
             3000    1200    1200    1200     600     600
              600     600     600     600    1200     600
              600    1200     600    1200    1200    1200
              600

          name dash
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
             1200     600     600    1200    1200    1200
              600

          name 0
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
              600    1200     600    1200    1200     600
              600

          name enter
             3000    1200    1200    1200     600     600
              600     600     600    1200     600     600
             1200    1200    1200     600     600     600
              600

      end raw_codes

end remote

```I have tried cat'ing the files together, but either I did it wrong, or it didn't like something about the files, because I lost use of both remotes that way.

So I guess the question is, CAN I cat these two files together? If it is possible, how? And do I need another module loaded to make it run, or is using lirc_mceusb2 okay for them both? Is there another way to get the codes for the DirecTV receiver?

The channel change script I ended up having the most luck with was this:
```
#!/bin/sh
REMOTE_NAME=mceusb
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 
```The script is executing fine now, the usb little box lights up, as does the little bug that attaches to the front of the satellite receiver. Alas, there is no channel change (although there is a change in the OSD and a change registered when I look at the output of mythfrontend -v channel)

Thanks for your help.... I'm sorta wondering if it's not time to upgrade the receiver (or heck, downgrade it) to a model that actually has a serial or usb port. We seem to have gotten stuck with the receiver time forgot... But now I've been presented with a challenge to get THIS receiver going, and I'm going to exhaust every possibility before conceding defeat. :)

thanks again!
shoe

Okay glad you posted those.  Here's the deal.  For starters, can you revert your lircd.conf to the one that came with mythbuntu?  I'd like to verify it really works with that one.  As long as it does, then you can just open up both these files in a graphical editor (gedit,geany,leafpad,mousepad, etc)

Copy everythign in between the begin remote and end remote sections of the direct tv lircd.conf and place it after the end remote section of the system wide /etc/lirc/lircd.conf.

That change-channel script you need to change the remote name its referring to as well.  Make if the name of the direct tv remote (as per that config that you just pasted)

---

### Post by linuxlibrarian on 2007-11-10
Okay, I'm a little slow. :) It's the brain fog.

Here's what I did: 

I opened mythbuntu, configured the RC6 remote as per Mythbuntu Control Center...

THEN...
I took everything (including) the begin remote and and end remote, and pasted it after the final end remote in the original lircd.conf. 

So it looks like this:

```

begin remote

blah blah mceusb

end remote

begin remote

blah blah Directv_RC24

end remote
```

I saved it.

Then I went to the script, and put in the DirecTV_RC24... 

Should have /etc/lirc/hardware.conf been edited as well?

I restarted lirc, and I restarted mythbackend

My remote buttons (most of them) still worked, at least as far as punching in numbers. So that was good, but the channels still didn't change. I rebooted, in case restarting the services wasn't enough, but still no love.

I am wondering if I cut and pasted stray lines accidentally? Could that mess things up? Also wondering (moreso) if maybe I misunderstood and was supposed to put both remotes between one set of begin / end remote tags?

Thanks so much for your help with this. :)

take care
shoe

---

### Post by superm1 on 2007-11-10
> **linuxlibrarian said:**
> Okay, I'm a little slow. :) It's the brain fog.

Here's what I did: 

I opened mythbuntu, configured the RC6 remote as per Mythbuntu Control Center...

THEN...
I took everything (including) the begin remote and and end remote, and pasted it after the final end remote in the original lircd.conf. 

So it looks like this:

```

begin remote

blah blah mceusb

end remote

begin remote

blah blah Directv_RC24

end remote
```I saved it.

Then I went to the script, and put in the DirecTV_RC24... 

Should have /etc/lirc/hardware.conf been edited as well?

I restarted lirc, and I restarted mythbackend

My remote buttons (most of them) still worked, at least as far as punching in numbers. So that was good, but the channels still didn't change. I rebooted, in case restarting the services wasn't enough, but still no love.

I am wondering if I cut and pasted stray lines accidentally? Could that mess things up? Also wondering (moreso) if maybe I misunderstood and was supposed to put both remotes between one set of begin / end remote tags?

Thanks so much for your help with this. :)

take care
shoe
You've got it right with two separate begin/end blocks.  Try from the command line with that change script now and see if it works.

---

### Post by linuxlibrarian on 2007-11-10
Now *this* is interesting. When I try to change channels with the command line, the OSD doesn't pop up, nothing happens, and the log doesn't indicate an attempt was even made to change the channels.:confused:  

When I hit the remote, it does at least change the OSD (the banner comes up and says what I would be watching had the channel really changed) and the show I'm watching pauses, and the output of mythfrontend -v channel indicates that it did get a channel change command.

I tried changing ownership from root to my user/mythtv group... and then I just chmod 777 the script to see if maybe it was something set too restrictively, but the same thing happens... Nothing via command line (though the little bug on the ir blaster/receiver lights).

I hope that I'm doing this bit right too... I open myth via the terminal "mythfrontend -v channel"

Then when I try to change the channel, I alt-tab to another terminal window on the desktop and run the script with a channel argument... :confused:

Or is there a way to access the command line *in* Mythtv?

thanks
shoe

---

### Post by superm1 on 2007-11-10
> **linuxlibrarian said:**
> Now *this* is interesting. When I try to change channels with the command line, the OSD doesn't pop up, nothing happens, and the log doesn't indicate an attempt was even made to change the channels.:confused:  

When I hit the remote, it does at least change the OSD (the banner comes up and says what I would be watching had the channel really changed) and the show I'm watching pauses, and the output of mythfrontend -v channel indicates that it did get a channel change command.

I tried changing ownership from root to my user/mythtv group... and then I just chmod 777 the script to see if maybe it was something set too restrictively, but the same thing happens... Nothing via command line (though the little bug on the ir blaster/receiver lights).

I hope that I'm doing this bit right too... I open myth via the terminal "mythfrontend -v channel"

Then when I try to change the channel, I alt-tab to another terminal window on the desktop and run the script with a channel argument... :confused:

Or is there a way to access the command line *in* Mythtv?

thanks
shoe
The reason i was asking you to do the channel change via command line was so that you can debug that part of it first.  You need to make sure that it is working before you will be able to do it all inside myth.

---

### Post by linuxlibrarian on 2007-11-10
All righty then... Well,  even though the channel doesn't change in myth... 

The command line doesn't output any errors when I run the script... So I guess that bit *is* working?

Sorry for my obtuse---- obtuseness? Obtusity? It's been a long day. :)

thanks
shoe

---

### Post by linuxlibrarian on 2007-11-11
Superm1... YOU ARE THE MAN! 

I know exactly why, now, it wasn't working, and now, exactly why it IS. 

Thank you SOOO much.

It turns out, the RC24 remote codes from LIRC were a little off... So I used an old irrecord file I made of the remote that was changing the box (just the number keys, as the other keys made the whole thing crash)

When I mapped all the DirecTV number keys, I then did what you said to do with the lircd.conf files... I put the DirecTV remote after the MCEUSB, and then I updated the channel change script (I had to alter it a little since there is no "select" button.)

I restarted LIRC, I restarted mythbackend... Then I tried the new script on the command line... Lo and behold! Channels changed! The remote had the same effect!

My husband is now a happy camper... And since this was driving me bonkers for the better part of two weeks... I am THRILLED.

Mythbuntu rocks. :) Thanks again for your time!

shoe

---

