---
title: "Remote"
date: 2008-01-28
forum: Mythbuntu
---

### Post by uncle hammy on 2008-01-28
I am thinking I am going ot have to get a new remote, but wanted to ask first.  

I purchased an "MCE Remote" on ebay, and when it arrived, I realized it was a cheap knockoff.  I can't even tell you who makes it, but the model number is apparently SRC-0149.  

I set up the remote control via the Myth Control Center, and selected Media Center New remote.  However, the only keys that seem to work are the arrow keys and the number keys.

When going to Edit Keys setup, and trying to enter bindings, it seems that almost all the buttons are recognized as ctrl+alt+"square" or alt+"square".  "square" is actually that, it's just a symbol that pops up.  Saving the bindings and viewing them reveals that is saved as ctrl+alt+? or alt+?.

Is there a way to try to work with this, or should I just pick up a new remote?

---

### Post by uncle hammy on 2008-01-28
I take part of that back....

here's the exact remote i was shipped....

[http://www.win-star.com/product/productshow.php?RootCAT=R07&CatID=116&ID=382](http://www.win-star.com/product/productshow.php?RootCAT=R07&CatID=116&ID=382)

---

### Post by stdPikachu on 2008-01-29
Hmm, squares and question marks typically mean that the font the app/terminal is using doesn't have a symbol for that character.

What happens when you run `irw` in a terminal and mash the keys a bit?

---

### Post by uncle hammy on 2008-01-30
> **stdPikachu said:**
> What happens when you run `irw` in a terminal and mash the keys a bit?
I get a "connection refused" error when trying to run irw.  I purchased an actual Microsoft 1039 remote, so I think this may end up being moot.  From what I read at mythtv.org, these remotes seem to be fully supported?

---

### Post by stdPikachu on 2008-01-30
I got a connection refused when I first tried LIRC, which was why I reconfigured my LIRC to use the dev/input drivers (see sig), although I have no idea if the MCE remotes work with it. COnnection refused usually means LIRC isn't running, or that there's a misconfiguration somewhere that stops it from working.

Can you post your /etc/lirc/lircd.conf and hardware.conf?

You can check it LIRC is running by doing `ps aux | grep lirc | grep -v grep` - if any lines are returned then LIRC is running OK.

---

### Post by uncle hammy on 2008-01-31
The new remote should be in tomorrow.  I have read people having a lot of issues with the knock off I have, even with Media Center....and it's supposed to be a Media Center remote.

If I have any problems with the new remote, I will post them in this thread.

Could you tell me, what exactly does the "Create Dynamic Button Mappings" option in the remote page of the Myth Control Center do?

---

### Post by uncle hammy on 2008-02-04
OK, the new remote arrived, and it is working MUCH better than the other.  Overall, it is acceptable, but I have about 7 buttons (Back, LiveTV, RecordedTV, DVDMenu, Clear, Star, Hash) not functioning.

If I go to the "Edit Keys" menu, and try to bind a command to any of these keys, nothing registers at the "awaiting key input" prompt.

irw is now working, and if I go there, all these keys register just fine when I mash them, displaying the proper button title, and input frequency.  Here's my /etc/lirc/lircd.conf file.  All the frequencies in here, seem to match up correctly to what was displayed in irw, though displayed differently. For example, in irw, Back was 000000037ff07bdc as opposed to 0x00007bdc in lircd.conf.  All buttons in irw started with 000000037ff07 and only the last three characters differed.

Here's my lircd.conf file

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

I noticed in /home/myuser/.lircrc and noticed that there were no entries for any of these buttons.  So I tried adding the following line to test ( I also added to /home/mythtv/.lircrc, just to be sure)...

```

begin
    remote = mceusb
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

```

Based on the rest of the file, as far as I can tell, this should have worked, but no luck.  All the other button mappings in the file worked exactly as described.  Here's my .lircrc file

```


begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

```

Any suggestions?

---

### Post by uncle hammy on 2008-02-05
OK, one last thing to add to this.  I have 2 .lircrc files...

one is ~/myuser/.lircrc
one is ~/mythtv/.lircrc (no . everywhere online I search for remote helo, I see people mentioning ~/**.**mythtv)

which on of these is the actual one that is used?  In the myth control center, I have set up to auto log into mythtv using "myuser".  I downloaded the .lircrc file from the mce remote wiki page, but I put it in ~/myuser, not ~/mythtv, perhaps that'smy issue?

---

### Post by newlinux on 2008-02-05
> **uncle hammy said:**
> OK, one last thing to add to this.  I have 2 .lircrc files...

one is ~/myuser/.lircrc
one is ~/mythtv/.lircrc (no . everywhere online I search for remote helo, I see people mentioning ~/**.**mythtv)

which on of these is the actual one that is used?  In the myth control center, I have set up to auto log into mythtv using "myuser".  I downloaded the .lircrc file from the mce remote wiki page, but I put it in ~/myuser, not ~/mythtv, perhaps that'smy issue?

MythTV's lircrc file needs to be in .mythtv directory of the user that you run mythfrontend as. If you run mythtv as "myuser" you need to have a file:

```
/home/myuser/.mythtv/lircrc
``` Most other programs (mplayer, vlc, etc.) will look for an lircrc configuration file at ```
/home/myuser/.lircrc
``` So what some  people do is link the two.

If I am reading your post correctly, you should put the file in ```
/home/myuser/.mythtv/lircrc
``` (ie ~myuser/.mythtv/lircrc). If I am reading it incorrectly and you run mythfrontend as the mythtv user replace myuser with mythtv.

---

### Post by uncle hammy on 2008-02-05
Seriously, I could kiss you :)

---

