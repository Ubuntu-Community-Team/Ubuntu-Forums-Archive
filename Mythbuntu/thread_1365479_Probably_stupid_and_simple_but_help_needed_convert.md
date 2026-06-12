---
title: "Probably stupid and simple but help needed converting this hex for lirc"
date: 2009-12-27
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-12-27
I have a cyberlink remote that i am using within Mythbuntu.  I have managed to get most of the keys i need working but for some reason i have been unable to get hex dump working to map the extra keys.

I have found the list below of all the codes dumped from the remote, but they seem to be in the wrong format for the solution i have found (also below).  

Can someone who understands this stuff in a bit more detail give me an idea how to covert the first list into the format of the hex dump on the second list? 

First list (needs converting)

{KEY_HOME, {0x4,0x1,0x0,-1}},  
  {KEY_POWEROFF, {0x2,0x2,-1}},
  {KEY_RED, {0x4,0xffffff80,0x0,-1}},
  {KEY_GREEN, {0x4,0x8,0x0,-1}},
  {KEY_YELLOW, {0x4,0x10,0x0,-1}},
  {KEY_BLUE, {0x4,0x20,0x0,-1}},
  {KEY_LiveTV, {0x4,0x2,0x0,-1}},
  {KEY_Record, {0x3,0xffffff80,0x0,0x0,-1}},
  {KEY_Radio, {0x3,0x4,0x0,0x0,-1}},
  {KEY_SAP, {0x4,0x0,0x10,-1}},
  {KEY_Teletext, {0x4,0x0,0x20,-1}},
  {KEY_LastCH, {0x4,0x0,0x40,-1}},
  {KEY_Subtitle, {0x4,0x0,0x8,-1}},
  {KEY_Language, {0x4,0x0,0x2,-1}},
  {KEY_Angle, {0x4,0x0,0x1,-1}},
  {KEY_Back, {0x3,0x0,0x4,0x0,-1}},
  {KEY_Info, {0x3,0x0,0x0,0x2,-1}},
  {KEY_DVDMenu, {0x4,0x0,0x4,-1}},

Second list (the end result format)

          back                     0x8001009E

          Pause                    0x80010077

          volumeDown               0x80010072

          volumeUp                 0x80010073

          Record                   0x800100a7

          Guide                    0x80010082

          Mute                     0x80010071

          ChannelUp                0x80010192

          ChannelDown              0x80010193

          Play                     0x800100CF

Direct comparison between 2 of the keys (in case that helps)

         {KEY_Back,                {0x3,0x0,0x4,0x0,-1}},
          back                     0x8001009E (required format)

I am sure this can be done but i dont recognise the first format.  The second one just looks like a simple hex dump to me?

Thanks for the help/steers;

andy

---

### Post by nickrout on 2009-12-27
where are you getting the first format from? 

have you tried irrecord?

---

### Post by azmyth on 2009-12-27
I've never seen that format. I'd try irrecord to get the keys you need.

---

### Post by geekyhawkes on 2009-12-28
I havent seen irrecord, i was following this guide ([http://cjo20.net/remote.htm](http://cjo20.net/remote.htm)) but for some reason couldnt get hexdump to report anything, all that happens when i enter sudo hexdump /dev/input/event11  is that i get returned back to the bash prompt so the hex dump doesnt seem to do anything.  Anyone have an idea how i can get hexdump working?

---

### Post by nickrout on 2009-12-28
> **geekyhawkes said:**
> I havent seen irrecord, i was following this guide ([http://cjo20.net/remote.htm](http://cjo20.net/remote.htm)) but for some reason couldnt get hexdump to report anything, all that happens when i enter sudo hexdump /dev/input/event11  is that i get returned back to the bash prompt so the hex dump doesnt seem to do anything.  Anyone have an idea how i can get hexdump working?

Ahhh OK it is one of those remotes that emulate a keyboard.

So I ask again, where are you getting the first set from? (if hexdump is not working).

Also what is wrong with the set of key definitions that the author of the howto provides?

---

### Post by geekyhawkes on 2009-12-30
THe how to is fine but sadly it is missing a few of the extra keys.  I am following his howto but need to get a few extra buttons mapped and need the hex dump for them.

The original data that i wanted to convert was taken from this howto [http://linux.thaj.net63.net/cyberlinkusb/](http://linux.thaj.net63.net/cyberlinkusb/) out of the setup file.

I thought that would be simple to covert as the buttons are clearly labled, sadly it doesnt seem that simple

---

### Post by Neon Dusk on 2009-12-30
You could try the codes at [http://twe.awardspace.com/cyberlink/keys.h.html](http://twe.awardspace.com/cyberlink/keys.h.html)

i.e. back is decimal 158 
convert to hex 9e
Append the mask bits and you get: 0x8001009e

red is decimal 389
hex 185
Append the mask bits and you get: 0x80010185

I think the values you got from [http://linux.thaj.net63.net/cyberlinkusb/](http://linux.thaj.net63.net/cyberlinkusb/) are from part of a program used to directly capture the values from the USB device.

---

### Post by geekyhawkes on 2009-12-30
Perfect, thanks very much.  Excuse my ignorance but how do i convert decimal to hex? 

Thanks

---

### Post by Neon Dusk on 2009-12-30
You can do the conversion at various website such as [http://www.easycalculation.com/decimal-converter.php](http://www.easycalculation.com/decimal-converter.php)

---

### Post by nickrout on 2009-12-30
use the calculator that comes with ubuntu and choose View|Programming. Click on the 'decimal' radio button and enter the number. Click on the 'hex' radio button and your number is converted.

---

### Post by geekyhawkes on 2010-01-01
> use the calculator that comes with ubuntu and choose View|Programming. Click on the 'decimal' radio button and enter the number. Click on the 'hex' radio button and your number is converted

ace thankyou!  Should increase the waf if i can get all the remote buttons working

Strangly i still cannot get all of the buttons working, I cant get any of the coloured buttons at the top of the remote working (with any key setting) or the dvd menu button and lastch.  Any thoughts anyone?  I will upload my settings below in case anyone else buys this remote and it can save them some time (i picked it up for less than £6!!!)

---

### Post by geekyhawkes on 2010-01-02
Follow the main of the guide at this location;

[http://cjo20.net/remote.htm](http://cjo20.net/remote.htm)

The extra buttons i have setup are contained in the lircd.conf file;

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

begin remote

  name  CYBERLINK

  bits           32

  eps            30

  aeps          100

  one             0     0

  zero            0     0

  gap          135995

  toggle_bit_mask 0x0

      begin codes

          back                     0x8001009E

          Pause                    0x80010077

          volumeDown               0x80010072

          volumeUp                 0x80010073

          Record                   0x800100a7

          Guide                    0x80010082

          Mute                     0x80010071

          ChannelUp                0x80010192

          ChannelDown              0x80010193

          Play                     0x800100CF

          SkipFoward               0x800100A3

          SkipBack                 0x800100A5

          menu                     0x8001019A

          Fwdwind                  0x800100D0

          Rewind                   0x800100A8

	  home			   0x80010066
	
	  red			   0x80010185

	  green			   0x80010185

	  yellow		   0x800100E2

	  blue			   0x80010189

	  livetv		   0x80010179

	  SAP			   0x80010188

	  angle			   0x80010173

	  lastch		   0x80010195

      end codes

end remote


Then add the button mappins you want to the lircrc file, mine are;

begin
    remote = CYBERLINK
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = SkipBack
    config = Z
    repeat = 0
    delay = 0
end

begin 
    remote = CYBERLINK
    prog = mythtv
    button = SkipForward
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = menu
    config = m
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = back
    config = Escape
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = ChannelUp
    config = Page Up
    repeat = 0
    delay = 0
end

begin 
    remote = CYBERLINK
    prog = mythtv
    button = ChannelDown
    config = Page Down
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Fwdwind
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = VolumeDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = home
    config = "
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = red
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = green
    config = Y
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = yellow
    config = U
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = blue
    config = £
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = livetv
    config = $
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = SAP
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = angle
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = CYBERLINK
    prog = mythtv
    button = lastch
    config = H
    repeat = 0
    delay = 0
end



Restart lirc and all should be well.  I still cannot work out hy dvd menu, red,blue,yellow and green dont work.  Likewise for lastch, other than those the remote is working fine and myth now has a higher waf!

Thanks.

---

### Post by piginabox on 2010-03-08
Here's another thread [http://ubuntuforums.org/showthread.php?t=1214795]("http://ubuntuforums.org/showthread.php?t=1214795") with attached config files that include all the Cyberlink remote button's HEX codes.

That any help?

---

### Post by geekyhawkes on 2010-04-04
Just in case anyone else searches this to help them with their setup, you also have to add extra lines at the bottom of your licrc file for the mplayer (if you use mplayer to play your video files).  All i have added is play/pause.

---

