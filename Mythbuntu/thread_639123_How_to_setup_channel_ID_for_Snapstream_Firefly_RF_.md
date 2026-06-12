---
title: "How to setup channel ID for Snapstream Firefly RF remote R1000"
date: 2007-12-12
forum: Mythbuntu
---

### Post by williammanda on 2007-12-12
I have two Snapstream Firefly RF remotes and they both accept all channel IDs. So both remotes worked on both computers. This presented a problem since the remote in the livingroom would change channels on the computer in the living room and the bedroom. I found a link that explained how to separate the remotes thus giving each their own channel ID.

[http://www.mythtv.org/pipermail/mythtv-users/2005-November/108619.html](http://www.mythtv.org/pipermail/mythtv-users/2005-November/108619.html)

I didn't exactly follow the instructions to the letter so here is what I did:

1. I added this code to my /etc/modprobe.d/aliases

```
alias char-major-57-* esp
alias char-major-58-* esp
[B][B]alias char-major-61 lirc_atiusb
options lirc_atiusb unique=1 debug=1 mask=0x0010[/B][/B]
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
```

There are two key parameters to understand:

unique
0=accept all channel IDs
1=accept only channel IDs set by the mask parameter

mask
This sets your channel ID. Example: my setup uses channel ID 5 which is mask-0x0010.
The Snapstrean Firefly RF remote has 16 channel IDs and they are as follows:
Channel ID  Mask
1                 0x0001
2                 0x0002
3                 0x0004
4                 0x0008
5                 0x0010
6                 0x0020
7                 0x0040
8                 0x0080
9                 0x0100
10               0x0200
11               0x0400
12               0x0800
13               0x1000
14               0x2000
15               0x4000
16               0x8000

Lastly I want to note that the debug parameter is also enabled to help identify the channel ID in the sys log. This doesn't need to be there for the remote to work but it helps to my sure your remote is setup properly. You can remove it after you have finished.

2. I setup my remote control to match the channel ID by:
Pressing and holding the firefly button until it blinks then I release the the button. When it finishes blinking and the led is on, I select (using the number buttons) the corresponding channel ID. Which in my case was channel 5. Then I press and release the firefly button to end the setup. If all was correct, you should see the led blink the number of times that equals your channel ID.

3. Re-boot your computer.

4. Open the sys log. I open it by selecting System>Administration>System log.
Select sys log and scroll down. Press any key on the remote and will see something similar to this:

```
[CODE]Dec 12 20:07:26 AMD kernel: [  173.162661] lirc_atiusb[2]: **accept channel 5**
Dec 12 20:07:26 AMD kernel: [  173.184459] lirc_atiusb[2]: data received 14 ab 96 40  (ep=0x81 length=4)
Dec 12 20:07:26 AMD kernel: [  173.184464] lirc_atiusb[2]: accept channel 5
```[/CODE]

"accept channel 5" tells me that my remote control is setup for channel 5. If you get any other number, go the step for setting up your remote to the correct channel ID.

5. Stop lirc.

```
sudo /etc/init.d/lirc stop
```

Use irrecord to create a new lircd.conf file. You can not use the old one, the codes will be different.

```
sudo irrecord -d /dev/lirc0 lircd.conf
```

Then copy / move the lircd.conf file to /etc/lirc

```
sudo mv lircd.conf /etc/lirc
```

restart lirc

```
sudo /etc/init.d/lirc start
```

or reboot your computer.

6. Test out your remote control. If you need more help with lirc refer to this link:

[https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)

Good Luck!

---

### Post by santhony on 2009-12-30
Does anyone have any Snapstream Firefly codes that have been programmed from irrecord?

I can't get irrecord to complete, thus I cannot use different channels on my firefly remote....  I have 4 sets of them...

---

### Post by williammanda on 2009-12-30
If you are referring to the lirc.conf file that is created here is a link.

[http://ubuntuforums.org/showpost.php?p=7413632&postcount=5]("http://ubuntuforums.org/showpost.php?p=7413632&postcount=5")

---

### Post by santhony on 2009-12-31
Thanks Wilammanda!

I've finally figured out the Snapstream Firefly and setting up with different channels.  I had to reverse engineer and now can tell you what the codes are for any channel and any key.

I need to post my work so no one ever again has to figure this out...

I think I'll post this in a new thread.

Anyone who needs Snapstream Firefly codes, feel free to ask me.

Thanks!!

---

### Post by santhony on 2010-05-20
I'll try and divulge the work I have done with setting up the Channel ID's on the snapstream firefly.  I actually have 3 of them.. so i reverse engineered the codes to get them to work together and not interfere with each other.

Let me start with my files, only two are needed.
ffch1.conf (placed under /etc/modprobe.d)
lircd.conf (placed under /etc/lirc)

To start you need to tell Firefly which channel to listen on, otherwise the default is to listen on all 16 channels.

Here's how this is done.  This is a file, placed under the "/etc/modprobe.d" folder, that is in UBUNTU.

You can call the file whatever you like, as long as you use the naming convention, "filename.conf". It must have the .conf extension!

The file under my /etc/modprobe.d is "ff1.conf"

Hence to edit it, I type:
sudo gedit /etc/modprobe.d/ff1.conf

# /etc/modprobe.d/ffch1.conf
# options to enable/disable various features of the
# lirc_atiusb kernel module.
# To see which options are available, run "modinfo lirc_atiusb | grep parm".
#
# My output:
#   parm:           debug:Debug enabled or not (default: 0) (bool)
#   parm:           mask:Set channel acceptance bit mask (default: 0xFFFF) (int)
#   parm:           unique:Enable channel-specific codes (default: 0) (bool)
#   parm:           repeat:Repeat timeout (1/100 sec) (default: 10) (int)
#   parm:           mdeadzone:rw2 mouse sensitivity threshold (default: 0) (int)
#   parm:           emit_updown:emit press/release codes (rw2): 0:don't (default), 1:emit 2 codes only, 2:code for each button (int)
#   parm:           emit_modekeys:emit keycodes for aux1-aux4, pc, and mouse (rw2): 0:don't (default), 1:emit translated codes: one for mode switch, one for same mode, 2:raw codes (int)
#   parm:           mgradient:rw2 mouse: 1000*gradient from E to NE (default: 500 => .5 => ~27 degrees) (int)
#
# Mask values can be:
# Channel Mask
#       1 0x0001
#       2 0x0002
#       3 0x0004
#       4 0x0008
#       5 0x0010
#       6 0x0020
#       7 0x0040
#       8 0x0080
#       9 0x0100
#      10 0x0200
#      11 0x0400
#      12 0x0800
#      13 0x1000
#      14 0x2000
#      15 0x4000
#      16 0x8000
#
# Accept only channel 1
 options lirc_atiusb debug=1 unique=1 mask=0x0001


It's only the actual last line that does the work, the rest is just explanation and info.

You'll need to reboot after updating this file or adding it to the /etc/modprobe.d folder... I'm sure there is a command to restart it, but I'm not sure what it is at this time.

My next reply will cover the lirc.conf file.

---

### Post by santhony on 2010-05-20
The ffch1.conf file applies a mask to the codes recieved from the Firefly Remote.  So now we need to update the lirc.conf file so it can actually match up the received codes to a command.

Actually tho, the default code that comes with the Firefly should have the Channel 1 codes in there by default.  So for your first firely, all you should have to do is apply the mask so it will not listen to any other remotes using channel id other than 1. 


So for a Firefly Remote on Channel 1, using my ff1.conf, masking file.
My lirc.conf looks like:

sudo gedit /etc/lirc/lirc.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(lirc_atiusb) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#Snapstream Firefly Default Channel 1

begin remote

name Snapstream Firefly
bits 40
eps 30
aeps 100
one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014628D0000
1 0x00000014E20D0000
2 0x00000014E30E0000
2 0x00000014638E0000
3 0x00000014648F0000
3 0x00000014E40F0000
4 0x00000014E5100000
4 0x0000001465900000
5 0x0000001466910000
5 0x00000014E6110000
6 0x00000014E7120000
6 0x0000001467920000
7 0x0000001468930000
7 0x00000014E8130000
8 0x00000014E9140000
8 0x0000001469940000
9 0x000000146A950000
9 0x00000014EA150000
0 0x00000014EC170000
0 0x000000146C970000
BACK 0x000000146B960000
BACK 0x00000014EB160000
ENT 0x00000014ED180000
ENT 0x000000146D980000
VOL+ 0x000000145E890000
VOL+ 0x00000014DE090000
VOL- 0x000000145D880000
VOL- 0x00000014DD080000
MUTE 0x000000145F8A0000
MUTE 0x00000014DF0A0000
FIREFLY 0x0000001455800000
FIREFLY 0x00000014D5000000
CH+ 0x00000014608B0000
CH+ 0x00000014E00B0000
CH- 0x00000014618C0000
CH- 0x00000014E10C0000
INFO 0x0000001483AE0000
INFO 0x00000014032E0000
OPTION 0x0000001484AF0000
OPTION 0x00000014042F0000
UP 0x000000146F9A0000
UP 0x00000014EF1A0000
LEFT 0x00000014729D0000
LEFT 0x00000014F21D0000
DOWN 0x0000001477A20000
DOWN 0x00000014F7220000
RIGHT 0x00000014749F0000
RIGHT 0x00000014F41F0000
OK 0x00000014739E0000
OK 0x00000014F31E0000
MENU 0x00000014719C0000
MENU 0x00000014F11C0000
EXIT 0x0000001475A00000
EXIT 0x00000014F5200000
REC 0x00000014FC270000
REC 0x000000147CA70000
PLAY 0x00000014FA250000
PLAY 0x000000147AA50000
STOP 0x00000014FD280000
STOP 0x000000147DA80000
REW 0x00000014F9240000
REW 0x0000001479A40000
FWD 0x00000014FB260000
FWD 0x000000147BA60000
PREV 0x00000014002B0000
PREV 0x0000001480AB0000
PAUSE 0x00000014FE290000
PAUSE 0x000000147EA90000
NEXT 0x00000014FF2A0000
NEXT 0x000000147FAA0000
MUSIC 0x00000014DB060000
MUSIC 0x000000145B860000
PHOTOS 0x00000014DA050000
PHOTOS 0x000000145A850000
DVD 0x00000014D9040000
DVD 0x0000001459840000
TV 0x00000014D8030000
TV 0x0000001458830000
VIDEO 0x00000014DC070000
VIDEO 0x000000145C870000
HELP 0x00000014D6010000
HELP 0x0000001456810000
MOUSE 0x00000014022D0000
MOUSE 0x0000001482AD0000
A 0x00000014EE190000
A 0x000000146E990000
B 0x00000014F01B0000
B 0x00000014709B0000
C 0x00000014F6210000
C 0x0000001476A10000
D 0x00000014F8230000
D 0x0000001478A30000

end codes

end remote

The ONLY thing that changes between the lirc.conf codes for Firefly channel ID 1 and lirc.conf Firefly channel ID 2 is a couple of characters in the middle of the code.  But it has a rythym, a constant.  You will actually add the mask to a portion of the Channel 1 code.


Here is the lirc.conf for Firefly Channel ID 2

#Snapstream Firefly Channel 2

begin remote

name Snapstream Firefly
bits 40
eps 30
aeps 100
one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014728D1000
1 0x00000014FE20D1000
2 0x00000014F30E0000
2 0x00000014738E0000
3 0x00000014748F0000
3 0x00000014F40F0000
4 0x00000014F5100000
4 0x0000001475900000
5 0x0000001476910000
5 0x00000014F6110000
6 0x00000014F7120000
6 0x0000001477920000
7 0x0000001478930000
7 0x00000014F8130000
8 0x00000014F9140000
8 0x0000001479940000
9 0x000000147A950000
9 0x00000014FA150000
0 0x00000014FC170000
0 0x000000147C970000
BACK 0x000000147B960000
BACK 0x00000014FB160000
ENT 0x00000014FD180000
ENT 0x000000147D980000
VOL+ 0x000000146E890000
VOL+ 0x00000014EE090000
VOL- 0x000000146D880000
VOL- 0x00000014ED080000
MUTE 0x000000146F8A0000
MUTE 0x00000014EF0A0000
FIREFLY 0x0000001465800000
FIREFLY 0x00000014E5000000
CH+ 0x00000014708B0000
CH+ 0x00000014F00B0000
CH- 0x00000014718C0000
CH- 0x00000014F10C0000
INFO 0x0000001493AE0000
INFO 0x00000014132E0000
OPTION 0x0000001494AF0000
OPTION 0x00000014142F0000
UP 0x000000147F9A0000
UP 0x00000014FF1A0000
LEFT 0x00000014829D0000
LEFT 0x00000014021D0000
DOWN 0x0000001487A20000
DOWN 0x0000001407220000
RIGHT 0x00000014849F0000
RIGHT 0x00000014041F0000
OK 0x00000014839E1000
OK 0x00000014031E1000
MENU 0x00000014819C0000
MENU 0x00000014011C0000
EXIT 0x0000001485A00000
EXIT 0x0000001405200000
REC 0x000000140C270000
REC 0x000000148CA70000
PLAY 0x000000140A250000
PLAY 0x000000148AA50000
STOP 0x000000140D280000
STOP 0x000000148DA80000
REW 0x0000001409240000
REW 0x0000001489A40000
FWD 0x000000140B260000
FWD 0x000000148BA60000
PREV 0x00000014102B0000
PREV 0x0000001490AB0000
PAUSE 0x000000140E290000
PAUSE 0x000000148EA90000
NEXT 0x000000140F2A0000
NEXT 0x000000148FAA0000
MUSIC 0x00000014EB060000
MUSIC 0x000000146B860000
PHOTOS 0x00000014EA050000
PHOTOS 0x000000146A850000
DVD 0x00000014E9040000
DVD 0x0000001469840000
TV 0x00000014E8030000
TV 0x0000001468830000
VIDEO 0x00000014EC070000
VIDEO 0x000000146C870000
HELP 0x00000014E6010000
HELP 0x0000001466810000
MOUSE 0x00000014122D0000
MOUSE 0x0000001492AD0000
A 0x000000140E190000
A 0x000000148E990000
B 0x00000014001B0000
B 0x00000014809B0000
C 0x0000001406210000
C 0x0000001486A10000
D 0x0000001408230000
D 0x0000001488A30000

end codes

end remote

---

### Post by williammanda on 2010-05-20
> **santhony said:**
> The ffch1.conf file applies a mask to the codes recieved from the Firefly Remote.  So now we need to update the lirc.conf file so it can actually match up the received codes to a command.

Actually tho, the default code that comes with the Firefly should have the Channel 1 codes in there by default.  So for your first firely, all you should have to do is apply the mask so it will not listen to any other remotes using channel id other than 1. 


So for a Firefly Remote on Channel 1, using my ff1.conf, masking file.
My lirc.conf looks like:

sudo gedit /etc/lirc/lirc.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(lirc_atiusb) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#Snapstream Firefly Default Channel 1

begin remote

name Snapstream Firefly
bits 40
eps 30
aeps 100
one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014628D0000
1 0x00000014E20D0000
2 0x00000014E30E0000
2 0x00000014638E0000
3 0x00000014648F0000
3 0x00000014E40F0000
4 0x00000014E5100000
4 0x0000001465900000
5 0x0000001466910000
5 0x00000014E6110000
6 0x00000014E7120000
6 0x0000001467920000
7 0x0000001468930000
7 0x00000014E8130000
8 0x00000014E9140000
8 0x0000001469940000
9 0x000000146A950000
9 0x00000014EA150000
0 0x00000014EC170000
0 0x000000146C970000
BACK 0x000000146B960000
BACK 0x00000014EB160000
ENT 0x00000014ED180000
ENT 0x000000146D980000
VOL+ 0x000000145E890000
VOL+ 0x00000014DE090000
VOL- 0x000000145D880000
VOL- 0x00000014DD080000
MUTE 0x000000145F8A0000
MUTE 0x00000014DF0A0000
FIREFLY 0x0000001455800000
FIREFLY 0x00000014D5000000
CH+ 0x00000014608B0000
CH+ 0x00000014E00B0000
CH- 0x00000014618C0000
CH- 0x00000014E10C0000
INFO 0x0000001483AE0000
INFO 0x00000014032E0000
OPTION 0x0000001484AF0000
OPTION 0x00000014042F0000
UP 0x000000146F9A0000
UP 0x00000014EF1A0000
LEFT 0x00000014729D0000
LEFT 0x00000014F21D0000
DOWN 0x0000001477A20000
DOWN 0x00000014F7220000
RIGHT 0x00000014749F0000
RIGHT 0x00000014F41F0000
OK 0x00000014739E0000
OK 0x00000014F31E0000
MENU 0x00000014719C0000
MENU 0x00000014F11C0000
EXIT 0x0000001475A00000
EXIT 0x00000014F5200000
REC 0x00000014FC270000
REC 0x000000147CA70000
PLAY 0x00000014FA250000
PLAY 0x000000147AA50000
STOP 0x00000014FD280000
STOP 0x000000147DA80000
REW 0x00000014F9240000
REW 0x0000001479A40000
FWD 0x00000014FB260000
FWD 0x000000147BA60000
PREV 0x00000014002B0000
PREV 0x0000001480AB0000
PAUSE 0x00000014FE290000
PAUSE 0x000000147EA90000
NEXT 0x00000014FF2A0000
NEXT 0x000000147FAA0000
MUSIC 0x00000014DB060000
MUSIC 0x000000145B860000
PHOTOS 0x00000014DA050000
PHOTOS 0x000000145A850000
DVD 0x00000014D9040000
DVD 0x0000001459840000
TV 0x00000014D8030000
TV 0x0000001458830000
VIDEO 0x00000014DC070000
VIDEO 0x000000145C870000
HELP 0x00000014D6010000
HELP 0x0000001456810000
MOUSE 0x00000014022D0000
MOUSE 0x0000001482AD0000
A 0x00000014EE190000
A 0x000000146E990000
B 0x00000014F01B0000
B 0x00000014709B0000
C 0x00000014F6210000
C 0x0000001476A10000
D 0x00000014F8230000
D 0x0000001478A30000

end codes

end remote

The ONLY thing that changes between the lirc.conf codes for Firefly channel ID 1 and lirc.conf Firefly channel ID 2 is a couple of characters in the middle of the code.  But it has a rythym, a constant.  You will actually add the mask to a portion of the Channel 1 code.


Here is the lirc.conf for Firefly Channel ID 2

#Snapstream Firefly Channel 2

begin remote

name Snapstream Firefly
bits 40
eps 30
aeps 100
one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014728D1000
1 0x00000014FE20D1000
2 0x00000014F30E0000
2 0x00000014738E0000
3 0x00000014748F0000
3 0x00000014F40F0000
4 0x00000014F5100000
4 0x0000001475900000
5 0x0000001476910000
5 0x00000014F6110000
6 0x00000014F7120000
6 0x0000001477920000
7 0x0000001478930000
7 0x00000014F8130000
8 0x00000014F9140000
8 0x0000001479940000
9 0x000000147A950000
9 0x00000014FA150000
0 0x00000014FC170000
0 0x000000147C970000
BACK 0x000000147B960000
BACK 0x00000014FB160000
ENT 0x00000014FD180000
ENT 0x000000147D980000
VOL+ 0x000000146E890000
VOL+ 0x00000014EE090000
VOL- 0x000000146D880000
VOL- 0x00000014ED080000
MUTE 0x000000146F8A0000
MUTE 0x00000014EF0A0000
FIREFLY 0x0000001465800000
FIREFLY 0x00000014E5000000
CH+ 0x00000014708B0000
CH+ 0x00000014F00B0000
CH- 0x00000014718C0000
CH- 0x00000014F10C0000
INFO 0x0000001493AE0000
INFO 0x00000014132E0000
OPTION 0x0000001494AF0000
OPTION 0x00000014142F0000
UP 0x000000147F9A0000
UP 0x00000014FF1A0000
LEFT 0x00000014829D0000
LEFT 0x00000014021D0000
DOWN 0x0000001487A20000
DOWN 0x0000001407220000
RIGHT 0x00000014849F0000
RIGHT 0x00000014041F0000
OK 0x00000014839E1000
OK 0x00000014031E1000
MENU 0x00000014819C0000
MENU 0x00000014011C0000
EXIT 0x0000001485A00000
EXIT 0x0000001405200000
REC 0x000000140C270000
REC 0x000000148CA70000
PLAY 0x000000140A250000
PLAY 0x000000148AA50000
STOP 0x000000140D280000
STOP 0x000000148DA80000
REW 0x0000001409240000
REW 0x0000001489A40000
FWD 0x000000140B260000
FWD 0x000000148BA60000
PREV 0x00000014102B0000
PREV 0x0000001490AB0000
PAUSE 0x000000140E290000
PAUSE 0x000000148EA90000
NEXT 0x000000140F2A0000
NEXT 0x000000148FAA0000
MUSIC 0x00000014EB060000
MUSIC 0x000000146B860000
PHOTOS 0x00000014EA050000
PHOTOS 0x000000146A850000
DVD 0x00000014E9040000
DVD 0x0000001469840000
TV 0x00000014E8030000
TV 0x0000001468830000
VIDEO 0x00000014EC070000
VIDEO 0x000000146C870000
HELP 0x00000014E6010000
HELP 0x0000001466810000
MOUSE 0x00000014122D0000
MOUSE 0x0000001492AD0000
A 0x000000140E190000
A 0x000000148E990000
B 0x00000014001B0000
B 0x00000014809B0000
C 0x0000001406210000
C 0x0000001486A10000
D 0x0000001408230000
D 0x0000001488A30000

end codes

end remote

OK if that is the way you would like to handle it. But for most people that aren't computer programmers...editing one file and using irw is very simple.

---

### Post by dborn on 2010-05-20
Hi, I'm the one who contacted Steve for this info and he graciously decided to make it publicly available here as opposed to privately responding to me.

Thanks Steve, I appreciate your generosity and yes, I am a programmer! ;)

Daniel

---

### Post by santhony on 2010-05-20
The remote codes are in HEX, so to count in HEX, it goes like this:

0 1 2 3 4 5 6 7 8 9 A B C D E F 
which is equivalent to counting in our standard Decimal
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15.

So HEX actually has 15 char 0-F, where are standard Decimal system has 0-9.


If you start by comparing the HEX codes, you will see:

ffid1 1 0x00000014628D0000
      1 0x00000014E20D0000

ffid2 1 0x00000014728D1000
      1 0x00000014FE20D100

ffid1 2 0x00000014E30E0000
      2 0x00000014638E0000

ffid2 2 0x00000014F30E0000
      2 0x00000014738E0000

ffid1 ENT 0x00000014ED180000
      ENT 0x000000146D980000

ffid2 ENT 0x00000014FD180000
      ENT 0x000000147D980000

Counting from right to left, the eighth position has been incremented by 1.  I think my First few lines, MAXI and CLOSE may be off.. no wonder they haven't been working for me on my FFID2.. lol

So just to put this all in perspective, you can forecast what ffid3 would be for ENT.  I can't recall if you simply add a a to that eight position or if you add the MASK #....  If I had my third FF setup right now, I would know.

so FFID3 ENT may look like this, if we increment by 1....
ffid3 ENT 0x000000140D180000
      ENT 0x000000148D980000.

Also note that there are two codes for each key.... Not sure why, but if you don't have the two alternating codes.. your remote will need double key presses to respond.

I'm attaching my working config files for ff1 and ff2.



ffid3

---

### Post by santhony on 2010-05-20
Here's My config files uploaded.

Please let me know any comments/updates or questions..

Thanks

---

### Post by santhony on 2010-05-20
No problem at all Dan.. Always happy to help.

I wrote up my posts in between breakfast with my kids, so hopefully I haven't confused anything up and all makes sense...

Feel free with any questions or further explanations.

Let me know how you make out.

---

### Post by jlr2000 on 2010-10-12
> **santhony said:**
> Here's My config files uploaded.

Please let me know any comments/updates or questions..

Thanks

Thanks so much for sharing your findings.  I just got my Snapstream Firefly remote working with ubuntu minimal/xbmc using this how to:

[http://wiki.xbmc.org/?title=Snapstream_Firefly](http://wiki.xbmc.org/?title=Snapstream_Firefly)

I quickly realized the problem of having 5 Firefly remotes in the house.  All the other setups are windows and I could easily change channel IDs.  Based on the link above for xbmc can anyone give me some direction on how to apply this thread's information on unique channel ids in xbmc?  I've brand new to linux and feel pretty good about getting this far, but I need help getting over the next hurdle....setting up multiple xbmc boxes with unique channel IDs for Firefly.

Any help or direction is greatly appreciated.  Again thanks for the information here, I feel all the parts are here, I just need help getting it all together.

Thanks.

---

### Post by jlr2000 on 2010-10-12
Okay, now that I think about this some more I think if I simply take the codes that
santhony provided on the previous page and replace them with the codes from the xbmc wiki page:

```
begin remote
	name Snapstream
	bits 16
	eps 30
	aeps 100 
	one 0 0
	zero 0 0
	pre_data_bits 8
	pre_data 0x14
	post_data_bits 16
	post_data 0x0
	gap 235978
	toggle_bit_mask 0x80800000
	begin codes
		Play 0x7AA5
		Pause 0x7EA9
		Stop 0xFD28
		Fwd 0xFB26
		Rew 0x79A4
		Left 0x729D
		Right 0xF41F
		Up 0x6F9A
		Down 0xF722
		OK 0x739E
		CH+ 0xE00B
		CH- 0x618C
		EXIT 0x75A0
		MENU 0xF11C
		OPTION 0x042F
		INFO 0x83AE
		Next 0x7FAA
		Prev 0x002B
		MAXIMIZE 0x81AC
		Firefly 0xD500
		Rec 0xFC27
		VOL+ 0x5E89
		VOL- 0xDD08
		MUTE 0x5F8A	
		CLOSE 0xD702
		Video 0xDC07
		Music 0xDB06
		Photos 0x5A85
		TV 0x5883
		A 0x6E99
		B 0xF01B
		C 0x76A1
		D 0xF823
		0 0xEC17
		1 0x628D
		2 0xE30E
		3 0x648F
		4 0xE510
		5 0x6691
		6 0xE712
		7 0x6893
		8 0xE914
		9 0x6A95
		BACK 0x6B96
		DVD 0xD904
		Help 0x5681 
		Mouse 0x022D
		ENT 0xED18
	end codes
end remote
```

So if I try to modify this lircd.conf as such:
```

begin remote
	name Snapstream
	bits 16
	eps 30
	aeps 100 
	one 0 0
	zero 0 0
	pre_data_bits 8
	pre_data 0x14
	post_data_bits 16
	post_data 0x0
	gap 235978
	toggle_bit_mask 0x80800000
	begin codes
		Play 0x00000014FA250000
                Play 0x000000147AA50000
		Pause 0x00000014FE290000
                Pause 0x000000147EA900000x7EA9
                Stop ......
                Stop ......and so on....
```

Does that make sense?  From what I understand from reading all the posts I've found, by using a 
unique channel id in effect you are using "unique" remote, which is why you need
the unique codes.  I *THINK* this is what is being said and why the only
lircd file out there is for ALL channels.  I'll keep working on this, as I said
I have 5 Firefly remotes and would like each setup to work.  I'll have to keep re-reading
santhony's explanation on how the codes are generated....first couple of 
passes it went over my head, but it was late...

If anyone can tell me if I'm on the right path here or not I'd appreciate it 
very much.

Thanks!

---

### Post by jlr2000 on 2010-10-12
All I did was add the "ff1.conf" file as santhony suggested so that ubuntu only listened on 1 channel:

```
# /etc/modprobe.d/ffch1.conf
# options to enable/disable various features of the
# lirc_atiusb kernel module.
# To see which options are available, run "modinfo lirc_atiusb | grep parm".
#
# My output:
#   parm:           debug:grin:ebug enabled or not (default: 0) (bool)
#   parm:           mask:Set channel acceptance bit mask (default: 0xFFFF) (int)
#   parm:           unique:Enable channel-specific codes (default: 0) (bool)
#   parm:           repeat:Repeat timeout (1/100 sec) (default: 10) (int)
#   parm:           mdeadzone:rw2 mouse sensitivity threshold (default: 0) (int)
#   parm:           emit_updown:emit press/release codes (rw2): 0:don't  (default), 1:emit 2 codes only, 2:code for each button (int)
#   parm:           emit_modekeys:emit keycodes for aux1-aux4, pc, and  mouse (rw2): 0:don't (default), 1:emit translated codes: one for mode  switch, one for same mode, 2:raw codes (int)
#   parm:           mgradient:rw2 mouse: 1000*gradient from E to NE (default: 500 => .5 => ~27 degrees) (int)
#
# Mask values can be:
# Channel Mask
#       1 0x0001
#       2 0x0002
#       3 0x0004
#       4 0x0008
#       5 0x0010
#       6 0x0020
#       7 0x0040
#       8 0x0080
#       9 0x0100
#      10 0x0200
#      11 0x0400
#      12 0x0800
#      13 0x1000
#      14 0x2000
#      15 0x4000
#      16 0x8000
#
# Accept only channel 1
 options lirc_atiusb debug=1 unique=1 mask=0x0001
```And that worked with the Firefly lirc.conf file from the XBMC wiki page.  I think this is so since santhony said "the default codes should work for channel 1". This worked for making only Firefly Channel 1 active.  Now I'm trying to setup another box with a Firefly remote as channel ID 2.  This seems to a bit more difficult.

In santhony's example he needed 2 lines for each button press, but in my setup only 1 was needed.  I tried to take the working lircd.conf file and increment each code by one where santhony states "8th from the right".  In my file the leading and trailing digits are not there, but you can tell the code is the same.  When I tried to increment each line by 1 in hex and save it, it wasn't recognized.  

I'll keep trying, hopefully if anyone has any ideas they will let me know and when I get it figured out I'll post back for others....

---

### Post by santhony on 2010-10-14
Good Morning !!

Hey I received your message jlr2000.. No problem at all.. I can dig up my work from figuring out the codes so you can extract the codes for your 5 frontends.  I'll see if i can find it today..  From what I remember tho, it's a repeating pattern for certain positions in the key codes.

Feel free to pick at me for any other information, I'm surprised your able to make sense of my work...lol...:)

Has anyone tried using the Snapstream Firefly on the newly released Maverick?

I got a quick look at it last nite and looks like the setup is going to be different.  The traditional method for configure LIRC for it, I think, has been fully deprecated(no longer used).  It appears to be now loaded thru FUSE, User Space File System, which is all very new to me.

If anyone has any thoughts or suggestions, please let me know.

I have three frontends using the Snapstream Firefly that I need to get running.

---

### Post by santhony on 2010-10-14
Just a quick note on where I started my work on the Snapstream Firefly.

Not sure if you all have found this already....

[http://www.mythtv.org/wiki/Snapstream_Firefly](http://www.mythtv.org/wiki/Snapstream_Firefly)

---

### Post by jlr2000 on 2010-10-14
Thanks Santhony....

I'm still trying to figure this out...but haven't had much luck.  The main difference in my setup is I'm running ubuntu minimal with XBMC (not MythTV like everyone else in these forums it seems).  On my main HTPC I have the Firefly working, I have it set to channel ID "1" and it works beautifully.  As mentioned before I used the XBMC wiki information to copy/create the lircd.conf file.  Also in XBMC there is no lircc file, the "keypress translation" seems to be in another file for XBMC.  The only thing I did differently from the wiki setup was to include a /etc/modprobe.d/ff1.conf file that only "listens" on channel 1. That is all working.

On the second HTPC I'm setting up I did the same things except I changed the channel to "2" in /etc/modprobe.d/ff2.conf and I also changed the lircd.conf codes, incrementing them by 1 in hex as you described.  I've read quite a few other posts with codes for channels 5 and 9 and when I check the codes they are consistent with the changes I'm making so I believe I got that part down.  On the second PC the remote isn't working at all...if I tail the syslog I can see my "accept ID 2" or something like that so I know the system "sees" the keypress.  If I try to run "irw" nothing shows up.  I even tried "irrecord" but that did not capture any keypresses.  The only other difference that I can think of was that for my main HTPC I used a custom script to load the os (made for the Zotac MAG nettop) and the second HTPC I just used XBMC Live from CD to install the OS (both ubuntu minimal) and xbmc to harddisk.  I don't think there are differences but who knows.  The fact that the second HTPC box "sees" the keypresses in the syslog is encouraging...just need to figure out the rest.

Thanks again for any help, just wanted to give the details of my testing....

---

### Post by santhony on 2010-10-14
I actually found the thread where I explained... or at least tried to explain the lircd.conf codes for each firefly channel.

[http://ubuntuforums.org/showthread.php?t=639123](http://ubuntuforums.org/showthread.php?t=639123)

Here is a little of the thread that I believe explains it.

In a nutshell, you will increment the eighth position,counting right to left.

Lets use the code for ENT as an example.(there's two codes for each key)

For FF CH1 it is:
ENT 0x00000014ED180000
ENT 0x000000146D980000

For FF CH2 it is: 
ENT 0x00000014FD180000
ENT 0x000000147D980000

For FF CH3 it should be:
ENT 0x000000140D180000  -- The 8th position increments to 0 (wraps to beginning of counting in HEX).
ENT 0x000000148D980000  -- The 8th position increments to 8.


I have to pull my master spread sheets from ARCHIVE's, I'll see to restore them in the morning.

Again, Check this thread for further details:
[http://ubuntuforums.org/showthread.php?t=639123](http://ubuntuforums.org/showthread.php?t=639123)

---

### Post by santhony on 2010-10-14
> **jlr2000 said:**
> Thanks Santhony....

I'm still trying to figure this out...but haven't had much luck.  The main difference in my setup is I'm running ubuntu minimal with XBMC (not MythTV like everyone else in these forums it seems).  On my main HTPC I have the Firefly working, I have it set to channel ID "1" and it works beautifully.  As mentioned before I used the XBMC wiki information to copy/create the lircd.conf file.  Also in XBMC there is no lircc file, the "keypress translation" seems to be in another file for XBMC.  The only thing I did differently from the wiki setup was to include a /etc/modprobe.d/ff1.conf file that only "listens" on channel 1. That is all working.

On the second HTPC I'm setting up I did the same things except I changed the channel to "2" in /etc/modprobe.d/ff2.conf and I also changed the lircd.conf codes, incrementing them by 1 in hex as you described.  I've read quite a few other posts with codes for channels 5 and 9 and when I check the codes they are consistent with the changes I'm making so I believe I got that part down.  On the second PC the remote isn't working at all...if I tail the syslog I can see my "accept ID 2" or something like that so I know the system "sees" the keypress.  If I try to run "irw" nothing shows up.  I even tried "irrecord" but that did not capture any keypresses.  The only other difference that I can think of was that for my main HTPC I used a custom script to load the os (made for the Zotac MAG nettop) and the second HTPC I just used XBMC Live from CD to install the OS (both ubuntu minimal) and xbmc to harddisk.  I don't think there are differences but who knows.  The fact that the second HTPC box "sees" the keypresses in the syslog is encouraging...just need to figure out the rest.

Thanks again for any help, just wanted to give the details of my testing....


You must be close.. There's a few things you can try.
What I would try first is....  If you type from command prompt.. IRW, you should see an output in the console for each button press... If you do.. then your almost there...  Your /etc/modprobe.d/ffch2.conf is correct, and it's just not matching up to the lircd.conf...

Also be sure to have the FF remote configured for channel 2.

If above doesn't work.
Can you set up the box to respond to FFCH1?  You should be able to replicate what you did on station FFCH1 on the station you want to be FFCH2.

In my other posts, I did attach FFCH2 codes... I'm reattaching them to be sure you have the correct codes.

Remember you have to restart lirc every time you make a change to it.
In Ubuntu, the command is "sudo /etc/init.d/lirc restart" , without the quotes.

Let me know how you make out.. I'll be back in touch.

FYI.. These newer attached codes only have one entry per key press.. Someone else was able to figure that one out.....But these are what I use for my current two Front Ends..  I'm also needing a third station now...

---

### Post by jlr2000 on 2010-10-21
> **santhony said:**
> You must be close.. There's a few things you can try.
What I would try first is....  If you type from command prompt.. IRW, you should see an output in the console for each button press... If you do.. then your almost there...  Your /etc/modprobe.d/ffch2.conf is correct, and it's just not matching up to the lircd.conf...

Also be sure to have the FF remote configured for channel 2.

If above doesn't work.
Can you set up the box to respond to FFCH1?  You should be able to replicate what you did on station FFCH1 on the station you want to be FFCH2.

In my other posts, I did attach FFCH2 codes... I'm reattaching them to be sure you have the correct codes.

Remember you have to restart lirc every time you make a change to it.
In Ubuntu, the command is "sudo /etc/init.d/lirc restart" , without the quotes.

Let me know how you make out.. I'll be back in touch.

FYI.. These newer attached codes only have one entry per key press.. Someone else was able to figure that one out.....But these are what I use for my current two Front Ends..  I'm also needing a third station now...
Sorry I haven't responded, got caught up in life again....

Anyway, so I removed everything I had done, I went back and did everything in the XBMC Wiki for the firefly remote using the codes on the wiki and instructions and it all works.  If I try to replace my working lircd.conf file with the information in your chan1 lircd file (changing the name from "Snapstream_Firefly" to "Snapstream" it doesn't work, and that just doesn't make sense to me.  If you notice the XBMC wiki codes for lircd are much "shorter" than what you have.  It's frustrating because it seems so close....I'll keep trying but wanted to give an update.
Thanks.

---

### Post by jlr2000 on 2010-10-21
SUCCESS!!

Okay, as I mentioned before I followed the XBMC Wiki for the Snapstream remote and got it working.  I think tried to swap the lircd.conf file with santhony's chan1 file.  I didn't think it was working but I found it it WAS working, but the button mappings in the XBMC "translation" file were off because it used upper and lower case letters such as "Play" when santhony's lircd has "PLAY".  SOME of the button names were the same and I noticed movement and then tried IRW which of course now worked great.  So I took santhony's chan2 lircd and changed the names to match my XBMC "translation" file, changed the FF remote to use chan2, changed the "only listen to this channel" file to channel 2, rebooted  and BAM! It WORKED!  I still need to work out the codes for other channels (I have 5 remotes total in the house).

THANKS SO MUCH AGAIN FOR SHARING YOUR INFORMATION, especially SANTHONY for his posts and help.

:P

---

### Post by jlr2000 on 2010-10-22
One last bit of information for those looking or for when I come back to set up another channel :)

When incrementing the codes for keys in hex, you need to increment in TWO places:

    Up        0x00000014[COLOR=Red]8[/COLOR]F9A[COLOR=Red]2[/COLOR]000
    Left      0x00000014[COLOR=Red]9[/COLOR]29D[COLOR=Red]2[/COLOR]000
    Down    0x00000014[COLOR=Red]9[/COLOR]7A2[COLOR=Red]2[/COLOR]000
    Right     0x00000014[COLOR=Red]9[/COLOR]49F[COLOR=Red]2[/COLOR]000

The codes above are from my lircd.conf file for Firefly Channel 3.  I first had trouble setting this up because I thought I only needed to increment the character after "14" by the next hex value (see previous page for how to count in hex).  My mistake was that the 4th from last digit ALSO needed to be incremented to the next hex value.  If you look at santhony's chan1 and chan2 files side by side this become evident....alas the "pattern" he spoke about (but on two levels).

Chan1
    Up      0x00000014[COLOR=Red]6[/COLOR]F9A[COLOR=Red]0[/COLOR]000
Chan2
    Up      0x00000014[COLOR=Red]7[/COLOR]F9A[COLOR=Red]1[/COLOR]000
Chan3
    Up      0x00000014[COLOR=Red]8[/COLOR]F9A[COLOR=Red]2[/COLOR]000

...and so on....

Again, hope this helps someone else out....

---

### Post by williammanda on 2010-12-17
> **santhony said:**
> Has anyone tried using the Snapstream Firefly on the newly released Maverick?

I got a quick look at it last nite and looks like the setup is going to be different.  The traditional method for configure LIRC for it, I think, has been fully deprecated(no longer used).  It appears to be now loaded thru FUSE, User Space File System, which is all very new to me.

If anyone has any thoughts or suggestions, please let me know.


Has anyone gotten multiple remotes working under mythtv .24?

---

### Post by santhony on 2010-12-17
I will be trying today...  I'll let you know how I make out..

---

### Post by santhony on 2010-12-19
The good news is the Snapstream Firefly works with Myth out of the box with Channel ID 1.

If you go thru the Mythbuntu-Control-Centre and use the IR setup, choosing, 
ATI/NVidia/X10 RF Remote(userspace).

I believe for the other channel ID's to work, the default toggle bit needs to be incremented, "toggle_bit_mask 0x80800000".

Does anyone have the increment pattern for this reverse engineer?

Anyone not seeing channel 1 Working after using Mythbuntu-Control-Centre Infrared selections, we can walk you thru it..

---

### Post by santhony on 2010-12-19
I still haven't cracked the toggle bit yet.. But I did find the codes for each channel ID..

You must increment the number after 14 by 1 for each Channel ID# increase.

So the next Channel ID, which would be channel ID 2,  for MAXI from the Sample code below is:

MAXI     0x00000014112C0000


SAMPLE CODE from Channel ID 1.
  begin codes
    MAXI     0x00000014012C0000
    CLOSE    0x0000001457820000
    1        0x00000014628D0000
    2        0x00000014638E0000
    3        0x00000014648F0000
    4        0x0000001465900000
    5        0x0000001466910000
    6        0x0000001467920000
    7        0x0000001468930000

I currently have 3 Frontends, so I'll post up Channel ID's 1, 2 and 3 when finished.

I'm sure there's and easier way just by changing the toggle bits..

---

### Post by williammanda on 2010-12-27
> **santhony said:**
> I still haven't cracked the toggle bit yet.. But I did find the codes for each channel ID..

You must increment the number after 14 by 1 for each Channel ID# increase.

So the next Channel ID, which would be channel ID 2,  for MAXI from the Sample code below is:

MAXI     0x00000014112C0000


SAMPLE CODE from Channel ID 1.
  begin codes
    MAXI     0x00000014012C0000
    CLOSE    0x0000001457820000
    1        0x00000014628D0000
    2        0x00000014638E0000
    3        0x00000014648F0000
    4        0x0000001465900000
    5        0x0000001466910000
    6        0x0000001467920000
    7        0x0000001468930000

I currently have 3 Frontends, so I'll post up Channel ID's 1, 2 and 3 when finished.

I'm sure there's and easier way just by changing the toggle bits..

Any updates?

---

### Post by santhony on 2010-12-27
I currently have 3 different channel ID's working for 3 different frontends.

I'll post up those lircd.conf files.

To describe the process in a nutshell, in getting the Firefly to work in 10.10.  From Mythbuntu Control Centre, select the ATI/NVidia/X10 RF Remote(userspace).

Check off the two boxes, "Generate dynamic button mappings" and "Generate frontend restart mapping(Power followed by Clear)

From there, the firefly should be working with channel ID#1.  The next channel ID will be to increment the character after 14.  Also you will need a mask to be sure your frontend only accepts channels from the Channel ID you want.  That is a modeprobe.d conf file... I'll post those up as well..

---

### Post by williammanda on 2010-12-27
I tried to use irrecord and failed. Has anyone else been able to do so? Here is a post with the details:

[http://ubuntuforums.org/showpost.php?p=10248635&postcount=8]("http://ubuntuforums.org/showpost.php?p=10248635&postcount=8")

---

### Post by williammanda on 2011-01-13
> **santhony said:**
> Also you will need a mask to be sure your frontend only accepts channels from the Channel ID you want.  That is a modeprobe.d conf file... I'll post those up as well..

Any updates on the modprobe.d file?

---

### Post by santhony on 2011-01-13
> **williammanda said:**
> Any updates on the modprobe.d file?

Yes, the modprobe.d has to have a file so that the firefly only listens on the specific channel you want it too... otherwise the other remotes will change it..

I'll post up my modprobe.d configs in the morning.

---

### Post by williammanda on 2011-01-18
Any updates?

---

### Post by santhony on 2011-01-18
Sorry about that... been  a long week... here's my /etc/modeprobe.d/ffchx.conf files..

Just remove the ".txt" portion from the file name and place it in the /etc/modprobe.d/ folder.  

You can adjust the Mask value as detailed in the file to match the channel ID of the frontend's firefly for additional channel ID's.

Let me know if this all makes sense, I can further explain.

Have a good one!

---

### Post by santhony on 2011-01-18
Hopefully I grabbed all the correct files..lol

---

### Post by williammanda on 2013-01-27
The need arised for multiple Snapstream firefly remotes again using 12-10. In reviewing the past two approaches, I found the current way to make the multiple remotes work. 

I 1st tried using santhony's approach but found that the ffch.conf file was no longer needed. The lirc_atiusb module has changed to atilibusb and is a driver in the hardware.conf. Also I found that the current lird.conf file was working for channel id 9. When I tried to use irrecord, it failed as in the past attempts. So I was left with using the current lircd.conf which I adjusted it to create another for channel id 8. Here are the two lircd.conf files which have details instructions to implement multiple remotes:

```
# Channel 8 with single entries for the buttons
#
# Modified 1-27-13
#
# Follow these 3 steps to setup multiple Snapstream Firefly RF remotes with Mythbunu 12-10. 
#
# 1. Select/use the ATI/NVidia/X10 RF Remote (userspace) remote (for hardware.conf).
#
# 2. Setup remote control to match the channel ID:
Press and hold the firefly button until it blinks then release. When it finishes blinking and the led is on, select (using the number buttons) the corresponding channel ID. Which in my case was channel 8. Press and release the firefly button to end the setup. If all was correct, you should see the led blink the number of times that equals your channel ID.
#
# 3. To change the button codes to match the channel id of the remote: (I couldn't get irrecord to work so I used this method)
# Change the charactor to the right of the "x" by one hexidecimal number
# Example: channel 8 MAXI 0x712C , channel 9 0x812C, channel 10 0x912C
#
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(atilibusb) on Mon Nov 24 14:58:45 2008
#
# contributed by 
#
# brand: Snapstream Firefly R1000
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          147992
  min_repeat      3
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x712C
          CLOSE                    0x4702
          1                        0x520D
          2                        0x530E
          3                        0x540F
          4                        0x5510
          5                        0x5611
          6                        0x5712
          7                        0x5813
          8                        0x5914
          9                        0x5A15
          0                        0x5C17
          BACK                     0x5B16
          ENT                      0x5D18
          VOL+                     0x4E09
          VOL-                     0x4D08
          MUTE                     0x4F0A
          FIREFLY                  0x4500
          CH+                      0x500B
          CH-                      0x510C
          INFO                     0x732E
          OPTION                   0x742F
          UP                       0x5F1A
          LEFT                     0x621D
          DOWN                     0x6722
          RIGHT                    0x641F
          OK                       0x631E
          MENU                     0x611C
          EXIT                     0x6520
          REC                      0x6C27
          PLAY                     0x6A25
          STOP                     0x6D28
          REW                      0x6924
          FWD                      0x6B26
          PREV                     0x702B
          PAUSE                    0x6E29
          NEXT                     0x6F2A
          MUSIC                    0x4B06
          PHOTOS                   0x4A05
          DVD                      0x4904
          TV                       0x4803
          VIDEO                    0x4C07
          HELP                     0x4601
          MOUSE                    0x722D
          A                        0x5E19
          B                        0x601B
          C                        0x6621
          D                        0x6823
      end codes

end remote
```

```
# Channel 9 with single entries for the buttons
#
# Modified 1-27-13
#
# Follow these 3 steps to setup multiple Snapstream Firefly RF remotes with Mythbunu 12-10. 
#
# 1. Select/use the ATI/NVidia/X10 RF Remote (userspace) remote (for hardware.conf).
#
# 2. Setup remote control to match the channel ID:
Press and hold the firefly button until it blinks then release. When it finishes blinking and the led is on, select (using the number buttons) the corresponding channel ID. Which in my case was channel 8. Press and release the firefly button to end the setup. If all was correct, you should see the led blink the number of times that equals your channel ID.
#
# 3. To change the button codes to match the channel id of the remote: (I couldn't get irrecord to work so I used this method)
# Change the charactor to the right of the "x" by one hexidecimal number
# Example: channel 8 MAXI 0x712C , channel 9 0x812C, channel 10 0x912C
#
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(atilibusb) on Mon Nov 24 14:58:45 2008
#
# contributed by 
#
# brand: Snapstream Firefly R1000
# model no. of remote control: 
# devices being controlled by this remote:
#


begin remote

  name  lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          147992
  min_repeat      3
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x812C
          CLOSE                    0x5702
          1                        0x620D
          2                        0x630E
          3                        0x640F
          4                        0x6510
          5                        0x6611
          6                        0x6712
          7                        0x6813
          8                        0x6914
          9                        0x6A15
          0                        0x6C17
          BACK                     0x6B16
          ENT                      0x6D18
          VOL+                     0x5E09
          VOL-                     0x5D08
          MUTE                     0x5F0A
          FIREFLY                  0x5500
          CH+                      0x600B
          CH-                      0x610C
          INFO                     0x832E
          OPTION                   0x842F
          UP                       0x6F1A
          LEFT                     0x721D
          DOWN                     0x7722
          RIGHT                    0x741F
          OK                       0x731E
          MENU                     0x711C
          EXIT                     0x7520
          REC                      0x7C27
          PLAY                     0x7A25
          STOP                     0x7D28
          REW                      0x7924
          FWD                      0x7B26
          PREV                     0x802B
          PAUSE                    0x7E29
          NEXT                     0x7F2A
          MUSIC                    0x5B06
          PHOTOS                   0x5A05
          DVD                      0x5904
          TV                       0x5803
          VIDEO                    0x5C07
          HELP                     0x5601
          MOUSE                    0x822D
          A                        0x6E19
          B                        0x701B
          C                        0x7621
          D                        0x7823
      end codes

end remote
```

---

### Post by sabhain on 2013-09-04
First off, thanks so much for all the leg work on this.  I've used this thread numerous times to fix / install my Firefly's.

I'm back here trying to get the firefly working again in 12.04 LTS, and I'm wondering what becomes of the two lines that we used to use in the modprobe aliases.conf file:

```
alias char-major-61 lirc_atiusb
options lirc_atiusb unique=0 debug=0 mask=0x0040
```

The mask in line 2 was the one that set the channel for the remote receiver.  How is that accomplished now?  Is it entirely within the lircd.conf files?

Thanks so much for all your efforts.

---

### Post by williammanda on 2013-09-04
> **sabhain said:**
> First off, thanks so much for all the leg work on this.  I've used this thread numerous times to fix / install my Firefly's.

I'm back here trying to get the firefly working again in 12.04 LTS, and I'm wondering what becomes of the two lines that we used to use in the modprobe aliases.conf file:

```
alias char-major-61 lirc_atiusb
options lirc_atiusb unique=0 debug=0 mask=0x0040
```

That file isn't used anymore and I'm not sure why it was removed. Also irrecord doesn't work as well. The combination of both limitations resulted in the alternate method.

> The mask in line 2 was the one that set the channel for the remote receiver.  How is that accomplished now?  Is it entirely within the lircd.conf files?


Yes it is entirely in the lircd.conf file. You will need to set the ID per the instructions:
# 3. To change the button codes to match the channel id of the remote: (I couldn't get irrecord to work so I used this method)
# Change the charactor to the right of the "x" by one hexidecimal number...the number is in bold print
# Example: channel 8 MAXI 0x**7**12C , channel 9 0x**8**12C, channel 10 0x**9**12C

One of my remotes has a couple of buttons that are going bad....might get another if possible or look at an alternative.

---

### Post by sabhain on 2013-09-05
Does irw work for you still?

I'm having a devil of a time with this.  I've inserted your hardware.conf & lircd.conf and set my remote to ch8 to test this out.  Like you I have a couple of these around.  At the moment, I had been running them on 7 and 10 .. but that's a small detail.

I learned a long time ago that the name of the remote in each file was critical.  If there wasn't match up, then it was hard (maybe impossible) to get the .lircrc file to correctly interpret the commands.

I can't get to that point though.  I get a clean restart of LIRC, but IRW shows no activity.  I've even tried to chase it around a little by changing the remote ID, but no luck so far.

I'm working on an upgrade to 12.04 LTS from something much older.  I have the older running in parallel with a diskless boot (sigh) and am doing the new on small local SSDs.

For completeness, I've attached the files as I have them now.  Perhaps I'm missing something obvious that you'll see.  The trouble with this thing is that we fight it every 4 or 5 years, win the battle and forget the strategy for next time.

Thanks for your time and help.

/etc/lirc/hardware.conf:
```
REMOTE="firefly_ch8"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.ch8firefly"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

/etc/lirc/lircd.conf:
```
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

#Configuration for the ATI/NVidia/X10 RF Remote (userspace) remote:
include "/usr/share/lirc/remotes/atiusb/lircd.conf.ch8firefly"
```

/usr/share/lirc/remotes/atiusb/lircd.conf.ch8firefly:
```
# Channel 8 with single entries for the buttons
#
# Modified 1-27-13
#
# Follow these 3 steps to setup multiple Snapstream Firefly RF remotes with Mythbunu 12-10. 
#
# 1. Select/use the ATI/NVidia/X10 RF Remote (userspace) remote (for hardware.conf).
#
# 2. Setup remote control to match the channel ID:
# Press and hold the firefly button until it blinks then release. When it finishes blinking and the led is on, select (using the number buttons) the 
corresponding channel ID. Which in my case was channel 8. Press and release the firefly button to end the setup. If all was correct, you should see t
he led blink the number of times that equals your channel ID.
#
# 3. To change the button codes to match the channel id of the remote: (I couldn't get irrecord to work so I used this method)
# Change the charactor to the right of the "x" by one hexidecimal number
# Example: channel 8 MAXI 0x712C , channel 9 0x812C, channel 10 0x912C
#
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(atilibusb) on Mon Nov 24 14:58:45 2008
#
# contributed by 
#
# brand: Snapstream Firefly R1000
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  firefly_ch8 
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          147992
  min_repeat      3
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x712C
          CLOSE                    0x4702
          1                        0x520D
          2                        0x530E
          3                        0x540F
          4                        0x5510
          5                        0x5611
          6                        0x5712
          7                        0x5813
          8                        0x5914
          9                        0x5A15
          0                        0x5C17
          BACK                     0x5B16
          ENT                      0x5D18
          VOL+                     0x4E09
          VOL-                     0x4D08
          MUTE                     0x4F0A
          FIREFLY                  0x4500
          CH+                      0x500B
          CH-                      0x510C
          INFO                     0x732E
          OPTION                   0x742F
          UP                       0x5F1A
          LEFT                     0x621D
          DOWN                     0x6722
          RIGHT                    0x641F
          OK                       0x631E
          MENU                     0x611C
          EXIT                     0x6520
          REC                      0x6C27
          PLAY                     0x6A25
          STOP                     0x6D28
          REW                      0x6924
          FWD                      0x6B26
          PREV                     0x702B
          PAUSE                    0x6E29
          NEXT                     0x6F2A
          MUSIC                    0x4B06
          PHOTOS                   0x4A05
          DVD                      0x4904
          TV                       0x4803
          VIDEO                    0x4C07
          HELP                     0x4601
          MOUSE                    0x722D
          A                        0x5E19
          B                        0x601B
          C                        0x6621
          D                        0x6823
      end codes
```

---

### Post by williammanda on 2013-09-05
Please try this hardware.conf file in place of yours: (please don't change the remote name)

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia/X10 RF Remote (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atilibusb"
REMOTE_LIRCD_ARGS="--release"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

and use one of the lircd.conf files. Start out with channel 1 on the remote while running mythtv or using irw (yes it does work for me) to test and work your way up the channels until one works. 
Thanks

---

### Post by sabhain on 2013-09-05
Awesome.  Thanks for the help and patience.  Your channel 8 setup worked immediately for me.  That helps me greatly with the WAF.

New life for my Fireflys .. very cool.

---

### Post by williammanda on 2013-09-17
While trying out newer versions of Ubuntu, newer than 12.10, I found out a couple of things:
1. Mythbuntu control center does work (my understanding it will by 14.04)
2. The driver that snapstream firefly remote uses is supplied via the kernel.

So I'm not worried about Mythbuntu control center but the kernel driver for the remote does present a couple of hurdles. The prior installation methods up to 12.10 for lirc doesn't work due to the new kernel driver and udev. What occurs in 13.04 and up is that the remote is considered a keyboard and not allowed use by lirc. You can view this via the xorg log, the remote is a keyboard and a mouse.

```
[    24.818] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input12/event12"
[    24.818] (II) XINPUT: Adding extended input device "X10 WTI RF receiver mouse" (type: MOUSE, id 8)
[    24.818] (II) evdev: X10 WTI RF receiver mouse: initialized for relative axes.
[    24.819] (**) X10 WTI RF receiver mouse: (accel) keeping acceleration scheme 1
[    24.819] (**) X10 WTI RF receiver mouse: (accel) acceleration profile 0
[    24.819] (**) X10 WTI RF receiver mouse: (accel) acceleration factor: 2.000
[    24.819] (**) X10 WTI RF receiver mouse: (accel) acceleration threshold: 4
[    24.819] (II) config/udev: Adding input device X10 WTI RF receiver mouse (/dev/input/mouse1)
[    24.819] (II) No input driver specified, ignoring this device.
[    24.819] (II) This device may have been added with another device file.
[    24.819] (II) config/udev: Adding input device X10 WTI RF receiver (/dev/input/event11)
[    24.819] (**) X10 WTI RF receiver: Applying InputClass "evdev keyboard catchall"
[    24.819] (II) Using input driver 'evdev' for 'X10 WTI RF receiver'
[    24.819] (**) X10 WTI RF receiver: always reports core events
[    24.819] (**) evdev: X10 WTI RF receiver: Device: "/dev/input/event11"
[    24.819] (--) evdev: X10 WTI RF receiver: Vendor 0xbc7 Product 0x8
[    24.819] (--) evdev: X10 WTI RF receiver: Found keys
[    24.819] (II) evdev: X10 WTI RF receiver: Configuring as keyboard
[    24.819] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/rc/rc0/input11/event11"
[    24.820] (II) XINPUT: Adding extended input device "X10 WTI RF receiver" (type: KEYBOARD, id 9)
[    24.820] (**) Option "xkb_rules" "evdev"
[    24.820] (**) Option "xkb_model" "pc105"
[    24.820] (**) Option "xkb_layout" "us"
```

So this gives us a couple of options depending on whether you have just one remote or more than one remote, meaning one or multiple mythtv setups (not multiple remotes on one mythtv setup). I will go over both options based on the number of remotes.

If you have one remote:

Keyboard Option setup
You can use all the options if you have one remote but if you have more than one remote, please skip this option. Currently the keyboard method can't tell if there is more than one remote.
This option will set your remote up as a keyboard. This method has it pro's and con's: 1. Easier setup 2. Repeat function built in 3. Only works on the current focused window 4. Not as configurable as lirc.

1. Install ir-keytables. Please do not load lirc or if it is installed, uninstall it.
2. Copy the following snapstream_firefly file to /lib/udev/rc_keymaps. (Rename the current file snapstream_firefly to snapstream_firefly.old)

```
# table snapstream_firefly, type: OTHER
0x2c KEY_W
0x02 KEY_ESC
0x0d KEY_1
0x0e KEY_2
0x0f KEY_3
0x10 KEY_4
0x11 KEY_5
0x12 KEY_6
0x13 KEY_7
0x14 KEY_8
0x15 KEY_9
0x17 KEY_0
0x16 KEY_ESC
0x18 KEY_ENTER
0x09 KEY_F11
0x08 KEY_F10
0x0a KEY_F9
0x0b KEY_UP
0x0c KEY_DOWN
0x00 KEY_VENDOR
0x2e KEY_I
0x2f KEY_OPTION
0x1d KEY_LEFT
0x1f KEY_RIGHT
0x22 KEY_DOWN
0x1a KEY_UP
0x1e KEY_ENTER
0x1c KEY_M
0x20 KEY_ESC
0x27 KEY_R
0x25 KEY_P
0x28 KEY_STOP
0x24 KEY_PAGEUP
0x26 KEY_PAGEDOWN
0x29 KEY_P
0x2b KEY_HOME
0x2a KEY_END
0x06 KEY_AUDIO
0x05 KEY_IMAGES
0x04 KEY_DVD
0x03 KEY_TV
0x07 KEY_VIDEO
0x01 KEY_F1
0x2d KEY_MODE
0x19 KEY_A
0x1b KEY_B
0x21 KEY_C
0x23 KEY_D
```

3. Reboot your computer or use sudo ir-keytable -w /lib/udev/rc_keymaps/snapstream_firefly
4. Now your remote will act like a keyboard but limited to the keys that are used in Mythtv.

If you have more than one remote or if you would like to use this option if you have one remote: 

Standard lirc Option setup:
This option is like the installations of 12.10 and before and allows you to use the channel ID as stated in the previous posts.

1. Install lirc if not already installed.
2. Use the supplied hardware.conf via the installation or one from the prior posts in this thread.
3. Use one of the lircd.conf files supplied by this thread ie channel ID 8 or 9.
4. Repeat steps 2 & 3 on another mythtv setup but using a lircd.conf with different channel ID.
5. Setup/copy Mythtv/Lircrc file. Copy the following file to ~/.mythtv/Lircrc (or this could be a symlink to ~/.Lirc/mythtv), ~/.Lirc/mythtv and ~/.Lircrc (this one is the include file with Mythbuntu).

```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton
#
# Modified again to use the Firefly remotes unique buttons by Ryan Schmitz
#
#
# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.
#
# You can set the jump point commands in Mythweb under Settings > Key Bindings as follows:
# F8 Main Menu
# F3 Program Guide
# F5 TV Recording Playback
# F7 Play DVD
# F6 MythGallary
# F4 Play Music
# F2 MythVideo


begin
prog = mythtv
button = FIREFLY
repeat = 0
config = F8
end

begin
prog = mythtv
button = TV
repeat = 0
config = F5
end

begin
prog = mythtv
button = VIDEO
repeat = 0
config = F2
end

begin
prog = mythtv
button = MUSIC
repeat = 0
config = F4
end

begin
prog = mythtv
button = PHOTOS
repeat = 0
config = F
end

begin
prog = mythtv
button = DVD
repeat = 0
config = F7
end

begin
prog = mythtv
button = HELP
repeat = 0
config = F1
end

begin
prog = mythtv
button = UP
repeat = 5
config = Up
end

begin
prog = mythtv
button = DOWN
repeat = 5
config = Down
end

begin
prog = mythtv
button = LEFT
repeat = 5
config = Left
end

begin
prog = mythtv
button = RIGHT
repeat = 5
config = Right
end

# Channel Up
begin
prog = mythtv
button = CH+
repeat = 5
config = Up
end

# Channel Down
begin
prog = mythtv
button = CH-
repeat = 5
config = Down
end

# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

# OK/Select
begin
prog = mythtv
button = ENT
config = Space
end

# Stop
begin
prog = mythtv
button = Stop
config = I
end

# Escape/Exit/Back
begin
prog = mythtv
button = BACK
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = CLOSE
config = Esc
end

# Escape/Exit/Back
begin
prog = mythtv
button = EXIT
config = Esc
end

# Play
begin
prog = mythtv
button = PLAY
repeat = 0
config = P
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 0
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 0
config = |
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = REW
repeat = 5
config = PgUp
end

# Rewind (10 sec default)
begin
prog = mythtv
button = FWD
repeat = 5
config = PgDown
end

# Skip forward (10 min default)
begin
prog = mythtv
button = NEXT
repeat = 5
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = PREV
repeat = 5
config = Home
end

# Record
begin
prog = mythtv
button = REC
repeat = 0
config = R
end

# Delete
begin
prog = mythtv
button = A
repeat = 0
config = D
end

# Decrease play speed
begin
prog = mythtv
button = B
repeat = 0
config = J
end

# double speed watch
begin
prog = mythtv
button = C
repeat = 0
config = J
end

# Bring up Time stretch
begin
prog = mythtv
button = D
repeat = 0
config = Y
end

change tuners
begin
prog = mythtv
button = OPTION
repeat = 0
config = Y
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = MENU
repeat = 0
config = M
end

# Scroll up
begin
prog = mythtv
button = VOL+
repeat = 5
config = F11
end

# Scroll down
begin
prog = mythtv
button = VOL-
repeat = 5
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = INFO
repeat = 0
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = MAXI
repeat = 0
config = W
end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 0
config = 0
end

begin
prog = mythtv
button = 1
repeat = 0
config = 1
end

begin
prog = mythtv
button = 2
repeat = 0
config = 2
end

begin
prog = mythtv
button = 3
repeat = 0
config = 3
end

begin
prog = mythtv
button = 4
repeat = 0
config = 4
end

begin
prog = mythtv
button = 5
repeat = 0
config = 5
end

begin
prog = mythtv
button = 6
repeat = 0
config = 6
end

begin
prog = mythtv
button = 7
repeat = 0
config = 7
end

begin
prog = mythtv
button = 8
repeat = 0
config = 8
end

begin
prog = mythtv
button = 9
repeat = 0
config = 9
end

```

6. Blacklist the kernel driver.
   A. Open terminal and enter lsmod. You should see something like this:

```
rc_snapstream_firefly    12535  0 
ati_remote             18603  0 
nfs_acl                12837  1 nfsd
rc_core                27718  3 ati_remote,rc_snapstream_firefly
```

   B. Using superuser edit /etc/modprode.d/blacklist.conf and add blacklist ati_remote to the bottom of the file.
7. Reboot your computer(s) and use your remote(s) with Mythtv.

If you have one remote:

Udev/Lirc Option setup:
 This option is a combination of the keyboard and standard lirc options. I'm not sure I understand why anyone would use the method but someone can enlighten me. This option doesn't allow for channel ID's. 

1. Follow the Keyboard option installation.
2. Install lirc if not already installed.
3. Use the following hardware.conf and acquire the REMOTE_DEVICE at /dev/input/by-id.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream Firefly"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-X10_WTI_RF_receiver-event-if00"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support.
#DISABLE_KERNEL_SUPPORT="true"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

4. Use the following lircd.conf.

```
# generated by devinput.sh
begin remote
        name            Snapstream firefly devinput
        bits            16
        eps             30
        aeps            100
        pre_data_bits   16
        pre_data        0x0001
        post_data_bits  32
        post_data       0x00000001
        gap             132799
        toggle_bit      0

	begin codes
		KEY_0			11
		KEY_102ND		86
		KEY_1			2
		KEY_2			3
		KEY_3			4
		KEY_4			5
		KEY_5			6
		KEY_6			7
		KEY_7			8
		KEY_8			9
		KEY_9			10
		KEY_A			30
		KEY_AB			0x196
		KEY_ADDRESSBOOK		0x1ad
		KEY_AGAIN		129
		KEY_ALTERASE		222
		KEY_ANGLE		0x173
		KEY_APOSTROPHE		40
		KEY_ARCHIVE		0x169
		KEY_AUDIO		0x188
		KEY_AUX			0x186
		KEY_B			48
		KEY_BACK		158
		KEY_BACKSLASH		43
		KEY_BACKSPACE		14
		KEY_BASSBOOST		209
		KEY_BATTERY		236
		KEY_BLUE		0x191
		KEY_BLUETOOTH		237
		KEY_BOOKMARKS		156
		KEY_BREAK		0x19b
		KEY_BRIGHTNESS_CYCLE	243
		KEY_BRIGHTNESSDOWN	224
		KEY_BRIGHTNESSUP	225
		KEY_BRIGHTNESS_ZERO	244
		KEY_BRL_DOT10		0x1fa
		KEY_BRL_DOT1		0x1f1
		KEY_BRL_DOT2		0x1f2
		KEY_BRL_DOT3		0x1f3
		KEY_BRL_DOT4		0x1f4
		KEY_BRL_DOT5		0x1f5
		KEY_BRL_DOT6		0x1f6
		KEY_BRL_DOT7		0x1f7
		KEY_BRL_DOT8		0x1f8
		KEY_BRL_DOT9		0x1f9
		KEY_C			46
		KEY_CALC		140
		KEY_CALENDAR		0x18d
		KEY_CAMERA		212
		KEY_CAMERA_FOCUS	0x210
		KEY_CANCEL		223
		KEY_CAPSLOCK		58
		KEY_CD			0x17f
		KEY_CHANNEL		0x16b
		KEY_CHANNELDOWN		0x193
		KEY_CHANNELUP		0x192
		KEY_CHAT		216
		KEY_CLEAR		0x163
		KEY_CLOSE		206
		KEY_CLOSECD		160
		KEY_COFFEE		152
		KEY_COMMA		51
		KEY_COMPOSE		127
		KEY_COMPUTER		157
		KEY_CONFIG		171
		KEY_CONNECT		218
		KEY_CONTEXT_MENU	0x1b6
		KEY_COPY		133
		KEY_CUT			137
		KEY_CYCLEWINDOWS	154
		KEY_D			32
		KEY_DASHBOARD		204
		KEY_DATABASE		0x1aa
		KEY_DEL_EOL		0x1c0
		KEY_DEL_EOS		0x1c1
		KEY_DELETE		111
		KEY_DELETEFILE		146
		KEY_DEL_LINE		0x1c3
		KEY_DIGITS		0x19d
		KEY_DIRECTION		153
		KEY_DIRECTORY		0x18a
		KEY_DISPLAY_OFF		245
		KEY_DISPLAYTOGGLE	0x1af
		KEY_DOCUMENTS		235
		KEY_DOLLAR		0x1b2
		KEY_DOT			52
		KEY_DOWN		108
		KEY_DVD			0x185
		KEY_E			18
		KEY_EDIT		176
		KEY_EDITOR		0x1a6
		KEY_EJECTCD		161
		KEY_EJECTCLOSECD	162
		KEY_EMAIL		215
		KEY_END			107
		KEY_ENTER		28
		KEY_EPG			0x16d
		KEY_EQUAL		13
		KEY_ESC			1
		KEY_EURO		0x1b3
		KEY_EXIT		174
		KEY_F10			68
		KEY_F11			87
		KEY_F12			88
		KEY_F13			183
		KEY_F14			184
		KEY_F15			185
		KEY_F1			59
		KEY_F16			186
		KEY_F17			187
		KEY_F18			188
		KEY_F19			189
		KEY_F20			190
		KEY_F21			191
		KEY_F22			192
		KEY_F23			193
		KEY_F24			194
		KEY_F2			60
		KEY_F			33
		KEY_F3			61
		KEY_F4			62
		KEY_F5			63
		KEY_F6			64
		KEY_F7			65
		KEY_F8			66
		KEY_F9			67
		KEY_FASTFORWARD		208
		KEY_FAVORITES		0x16c
		KEY_FILE		144
		KEY_FINANCE		219
		KEY_FIND		136
		KEY_FIRST		0x194
		KEY_FN			0x1d0
		KEY_FN_1		0x1de
		KEY_FN_2		0x1df
		KEY_FN_B		0x1e4
		KEY_FN_D		0x1e0
		KEY_FN_E		0x1e1
		KEY_FN_ESC		0x1d1
		KEY_FN_F		0x1e2
		KEY_FN_F10		0x1db
		KEY_FN_F1		0x1d2
		KEY_FN_F11		0x1dc
		KEY_FN_F12		0x1dd
		KEY_FN_F2		0x1d3
		KEY_FN_F3		0x1d4
		KEY_FN_F4		0x1d5
		KEY_FN_F5		0x1d6
		KEY_FN_F6		0x1d7
		KEY_FN_F7		0x1d8
		KEY_FN_F8		0x1d9
		KEY_FN_F9		0x1da
		KEY_FN_S		0x1e3
		KEY_FORWARD		159
		KEY_FORWARDMAIL		233
		KEY_FRAMEBACK		0x1b4
		KEY_FRAMEFORWARD	0x1b5
		KEY_FRONT		132
		KEY_G			34
		KEY_GAMES		0x1a1
		KEY_GOTO		0x162
		KEY_GRAPHICSEDITOR	0x1a8
		KEY_GRAVE		41
		KEY_GREEN		0x18f
		KEY_H			35
		KEY_HANGEUL		122
		KEY_HANJA		123
		KEY_HELP		138
		KEY_HENKAN		92
		KEY_HIRAGANA		91
		KEY_HOME		102
		KEY_HOMEPAGE		172
		KEY_HP			211
		KEY_I			23
		KEY_INFO		0x166
		KEY_INSERT		110
		KEY_INS_LINE		0x1c2
		KEY_ISO			170
		KEY_J			36
		KEY_K			37
		KEY_KATAKANA		90
		KEY_KATAKANAHIRAGANA	93
		KEY_KBDILLUMDOWN	229
		KEY_KBDILLUMTOGGLE	228
		KEY_KBDILLUMUP		230
		KEY_KEYBOARD		0x176
		KEY_KP0			82
		KEY_KP1			79
		KEY_KP2			80
		KEY_KP3			81
		KEY_KP4			75
		KEY_KP5			76
		KEY_KP6			77
		KEY_KP7			71
		KEY_KP8			72
		KEY_KP9			73
		KEY_KPASTERISK		55
		KEY_KPCOMMA		121
		KEY_KPDOT		83
		KEY_KPENTER		96
		KEY_KPEQUAL		117
		KEY_KPJPCOMMA		95
		KEY_KPLEFTPAREN		179
		KEY_KPMINUS		74
		KEY_KPPLUS		78
		KEY_KPPLUSMINUS		118
		KEY_KPRIGHTPAREN	180
		KEY_KPSLASH		98
		KEY_L			38
		KEY_LANGUAGE		0x170
		KEY_LAST		0x195
		KEY_LEFT		105
		KEY_LEFTALT		56
		KEY_LEFTBRACE		26
		KEY_LEFTCTRL		29
		KEY_LEFTMETA		125
		KEY_LEFTSHIFT		42
		KEY_LINEFEED		101
		KEY_LIST		0x18b
		KEY_LOGOFF		0x1b1
		KEY_M			50
		KEY_MACRO		112
		KEY_MAIL		155
		KEY_MAX			0x2ff
		KEY_MEDIA		226
		KEY_MEDIA_REPEAT	0x1b7
		KEY_MEMO		0x18c
		KEY_MENU		139
		KEY_MESSENGER		0x1ae
		KEY_MHP			0x16f
		KEY_MINUS		12
		KEY_MODE		0x175
		KEY_MOVE		175
		KEY_MP3			0x187
		KEY_MSDOS		151
		KEY_MUHENKAN		94
		KEY_MUTE		113
		KEY_N			49
		KEY_NEW			181
		KEY_NEWS		0x1ab
		KEY_NEXT		0x197
		KEY_NEXTSONG		163
		KEY_NUMERIC_0		0x200
		KEY_NUMERIC_1		0x201
		KEY_NUMERIC_2		0x202
		KEY_NUMERIC_3		0x203
		KEY_NUMERIC_4		0x204
		KEY_NUMERIC_5		0x205
		KEY_NUMERIC_6		0x206
		KEY_NUMERIC_7		0x207
		KEY_NUMERIC_8		0x208
		KEY_NUMERIC_9		0x209
		KEY_NUMERIC_POUND	0x20b
		KEY_NUMERIC_STAR	0x20a
		KEY_NUMLOCK		69
		KEY_O			24
		KEY_OK			0x160
		KEY_OPEN		134
		KEY_OPTION		0x165
		KEY_P			25
		KEY_PAGEDOWN		109
		KEY_PAGEUP		104
		KEY_PASTE		135
		KEY_PAUSE		119
		KEY_PAUSECD		201
		KEY_PC			0x178
		KEY_PHONE		169
		KEY_PLAY		207
		KEY_PLAYCD		200
		KEY_PLAYER		0x183
		KEY_PLAYPAUSE		164
		KEY_POWER		116
		KEY_POWER2		0x164
		KEY_PRESENTATION	0x1a9
		KEY_PREVIOUS		0x19c
		KEY_PREVIOUSSONG	165
		KEY_PRINT		210
		KEY_PROG1		148
		KEY_PROG2		149
		KEY_PROG3		202
		KEY_PROG4		203
		KEY_PROGRAM		0x16a
		KEY_PROPS		130
		KEY_PVR			0x16e
		KEY_Q			16
		KEY_QUESTION		214
		KEY_R			19
		KEY_RADIO		0x181
		KEY_RECORD		167
		KEY_RED			0x18e
		KEY_REDO		182
		KEY_REFRESH		173
		KEY_REPLY		232
		KEY_RESERVED		0
		KEY_RESTART		0x198
		KEY_REWIND		168
		KEY_RFKILL		247
		KEY_RIGHT		106
		KEY_RIGHTALT		100
		KEY_RIGHTBRACE		27
		KEY_RIGHTCTRL		97
		KEY_RIGHTMETA		126
		KEY_RIGHTSHIFT		54
		KEY_RO			89
		KEY_S			31
		KEY_SAT			0x17d
		KEY_SAT2		0x17e
		KEY_SAVE		234
		KEY_SCALE		120
		KEY_SCREEN		0x177
		KEY_SCROLLDOWN		178
		KEY_SCROLLLOCK		70
		KEY_SCROLLUP		177
		KEY_SEARCH		217
		KEY_SELECT		0x161
		KEY_SEMICOLON		39
		KEY_SEND		231
		KEY_SENDFILE		145
		KEY_SETUP		141
		KEY_SHOP		221
		KEY_SHUFFLE		0x19a
		KEY_SLASH		53
		KEY_SLEEP		142
		KEY_SLOW		0x199
		KEY_SOUND		213
		KEY_SPACE		57
		KEY_SPELLCHECK		0x1b0
		KEY_SPORT		220
		KEY_SPREADSHEET		0x1a7
		KEY_STOP		128
		KEY_STOPCD		166
		KEY_SUBTITLE		0x172
		KEY_SUSPEND		205
		KEY_SWITCHVIDEOMODE	227
		KEY_SYSRQ		99
		KEY_T			20
		KEY_TAB			15
		KEY_TAPE		0x180
		KEY_TEEN		0x19e
		KEY_TEXT		0x184
		KEY_TIME		0x167
		KEY_TITLE		0x171
		KEY_TUNER		0x182
		KEY_TV			0x179
		KEY_TV2			0x17a
		KEY_TWEN		0x19f
		KEY_U			22
		KEY_UNDO		131
		KEY_UNKNOWN		240
		KEY_UP			103
		KEY_UWB			239
		KEY_V			47
		KEY_VCR			0x17b
		KEY_VCR2		0x17c
		KEY_VENDOR		0x168
		KEY_VIDEO		0x189
		KEY_VIDEO_NEXT		241
		KEY_VIDEOPHONE		0x1a0
		KEY_VIDEO_PREV		242
		KEY_VOICEMAIL		0x1ac
		KEY_VOLUMEDOWN		114
		KEY_VOLUMEUP		115
		KEY_W			17
		KEY_WAKEUP		143
		KEY_WIMAX		246
		KEY_WLAN		238
		KEY_WORDPROCESSOR	0x1a5
		KEY_WWW			150
		KEY_X			45
		KEY_XFER		147
		KEY_Y			21
		KEY_YELLOW		0x190
		KEY_YEN			124
		KEY_Z			44
		KEY_ZENKAKUHANKAKU	85
		KEY_ZOOM		0x174
		KEY_ZOOMIN		0x1a2
		KEY_ZOOMOUT		0x1a3
		KEY_ZOOMRESET		0x1a4
		BTN_0			0x100
		BTN_1			0x101
		BTN_2			0x102
		BTN_3			0x103
		BTN_4			0x104
		BTN_5			0x105
		BTN_6			0x106
		BTN_7			0x107
		BTN_8			0x108
		BTN_9			0x109
		BTN_A			0x130
		BTN_B			0x131
		BTN_BACK		0x116
		BTN_BASE		0x126
		BTN_BASE2		0x127
		BTN_BASE3		0x128
		BTN_BASE4		0x129
		BTN_BASE5		0x12a
		BTN_BASE6		0x12b
		BTN_C			0x132
		BTN_DEAD		0x12f
		BTN_DIGI		0x140
		BTN_EXTRA		0x114
		BTN_FORWARD		0x115
		BTN_GAMEPAD		0x130
		BTN_GEAR_DOWN		0x150
		BTN_GEAR_UP		0x151
		BTN_JOYSTICK		0x120
		BTN_LEFT		0x110
		BTN_MIDDLE		0x112
		BTN_MISC		0x100
		BTN_MODE		0x13c
		BTN_MOUSE		0x110
		BTN_PINKIE		0x125
		BTN_RIGHT		0x111
		BTN_SELECT		0x13a
		BTN_SIDE		0x113
		BTN_START		0x13b
		BTN_STYLUS		0x14b
		BTN_STYLUS2		0x14c
		BTN_TASK		0x117
		BTN_THUMB		0x121
		BTN_THUMB2		0x122
		BTN_THUMBL		0x13d
		BTN_THUMBR		0x13e
		BTN_TL			0x136
		BTN_TL2			0x138
		BTN_TOOL_AIRBRUSH	0x144
		BTN_TOOL_BRUSH		0x142
		BTN_TOOL_DOUBLETAP	0x14d
		BTN_TOOL_FINGER		0x145
		BTN_TOOL_LENS		0x147
		BTN_TOOL_MOUSE		0x146
		BTN_TOOL_PEN		0x140
		BTN_TOOL_PENCIL		0x143
		BTN_TOOL_QUADTAP	0x14f
		BTN_TOOL_RUBBER		0x141
		BTN_TOOL_TRIPLETAP	0x14e
		BTN_TOP			0x123
		BTN_TOP2		0x124
		BTN_TOUCH		0x14a
		BTN_TR			0x137
		BTN_TR2			0x139
		BTN_TRIGGER		0x120
		BTN_WHEEL		0x150
		BTN_X			0x133
		BTN_Y			0x134
		BTN_Z			0x135
	end codes
end remote

# generated by devinput.sh (obsolete 32 bit version)
begin remote
        name            devinput
        bits            16
        eps             30
        aeps            100
        pre_data_bits   16
        pre_data        0x8001
        gap             132799
        toggle_bit      0

	begin codes
		KEY_0			11
		KEY_102ND		86
		KEY_1			2
		KEY_2			3
		KEY_3			4
		KEY_4			5
		KEY_5			6
		KEY_6			7
		KEY_7			8
		KEY_8			9
		KEY_9			10
		KEY_A			30
		KEY_AB			0x196
		KEY_ADDRESSBOOK		0x1ad
		KEY_AGAIN		129
		KEY_ALTERASE		222
		KEY_ANGLE		0x173
		KEY_APOSTROPHE		40
		KEY_ARCHIVE		0x169
		KEY_AUDIO		0x188
		KEY_AUX			0x186
		KEY_B			48
		KEY_BACK		158
		KEY_BACKSLASH		43
		KEY_BACKSPACE		14
		KEY_BASSBOOST		209
		KEY_BATTERY		236
		KEY_BLUE		0x191
		KEY_BLUETOOTH		237
		KEY_BOOKMARKS		156
		KEY_BREAK		0x19b
		KEY_BRIGHTNESS_CYCLE	243
		KEY_BRIGHTNESSDOWN	224
		KEY_BRIGHTNESSUP	225
		KEY_BRIGHTNESS_ZERO	244
		KEY_BRL_DOT10		0x1fa
		KEY_BRL_DOT1		0x1f1
		KEY_BRL_DOT2		0x1f2
		KEY_BRL_DOT3		0x1f3
		KEY_BRL_DOT4		0x1f4
		KEY_BRL_DOT5		0x1f5
		KEY_BRL_DOT6		0x1f6
		KEY_BRL_DOT7		0x1f7
		KEY_BRL_DOT8		0x1f8
		KEY_BRL_DOT9		0x1f9
		KEY_C			46
		KEY_CALC		140
		KEY_CALENDAR		0x18d
		KEY_CAMERA		212
		KEY_CAMERA_FOCUS	0x210
		KEY_CANCEL		223
		KEY_CAPSLOCK		58
		KEY_CD			0x17f
		KEY_CHANNEL		0x16b
		KEY_CHANNELDOWN		0x193
		KEY_CHANNELUP		0x192
		KEY_CHAT		216
		KEY_CLEAR		0x163
		KEY_CLOSE		206
		KEY_CLOSECD		160
		KEY_COFFEE		152
		KEY_COMMA		51
		KEY_COMPOSE		127
		KEY_COMPUTER		157
		KEY_CONFIG		171
		KEY_CONNECT		218
		KEY_CONTEXT_MENU	0x1b6
		KEY_COPY		133
		KEY_CUT			137
		KEY_CYCLEWINDOWS	154
		KEY_D			32
		KEY_DASHBOARD		204
		KEY_DATABASE		0x1aa
		KEY_DEL_EOL		0x1c0
		KEY_DEL_EOS		0x1c1
		KEY_DELETE		111
		KEY_DELETEFILE		146
		KEY_DEL_LINE		0x1c3
		KEY_DIGITS		0x19d
		KEY_DIRECTION		153
		KEY_DIRECTORY		0x18a
		KEY_DISPLAY_OFF		245
		KEY_DISPLAYTOGGLE	0x1af
		KEY_DOCUMENTS		235
		KEY_DOLLAR		0x1b2
		KEY_DOT			52
		KEY_DOWN		108
		KEY_DVD			0x185
		KEY_E			18
		KEY_EDIT		176
		KEY_EDITOR		0x1a6
		KEY_EJECTCD		161
		KEY_EJECTCLOSECD	162
		KEY_EMAIL		215
		KEY_END			107
		KEY_ENTER		28
		KEY_EPG			0x16d
		KEY_EQUAL		13
		KEY_ESC			1
		KEY_EURO		0x1b3
		KEY_EXIT		174
		KEY_F10			68
		KEY_F11			87
		KEY_F12			88
		KEY_F13			183
		KEY_F14			184
		KEY_F15			185
		KEY_F1			59
		KEY_F16			186
		KEY_F17			187
		KEY_F18			188
		KEY_F19			189
		KEY_F20			190
		KEY_F21			191
		KEY_F22			192
		KEY_F23			193
		KEY_F24			194
		KEY_F2			60
		KEY_F			33
		KEY_F3			61
		KEY_F4			62
		KEY_F5			63
		KEY_F6			64
		KEY_F7			65
		KEY_F8			66
		KEY_F9			67
		KEY_FASTFORWARD		208
		KEY_FAVORITES		0x16c
		KEY_FILE		144
		KEY_FINANCE		219
		KEY_FIND		136
		KEY_FIRST		0x194
		KEY_FN			0x1d0
		KEY_FN_1		0x1de
		KEY_FN_2		0x1df
		KEY_FN_B		0x1e4
		KEY_FN_D		0x1e0
		KEY_FN_E		0x1e1
		KEY_FN_ESC		0x1d1
		KEY_FN_F		0x1e2
		KEY_FN_F10		0x1db
		KEY_FN_F1		0x1d2
		KEY_FN_F11		0x1dc
		KEY_FN_F12		0x1dd
		KEY_FN_F2		0x1d3
		KEY_FN_F3		0x1d4
		KEY_FN_F4		0x1d5
		KEY_FN_F5		0x1d6
		KEY_FN_F6		0x1d7
		KEY_FN_F7		0x1d8
		KEY_FN_F8		0x1d9
		KEY_FN_F9		0x1da
		KEY_FN_S		0x1e3
		KEY_FORWARD		159
		KEY_FORWARDMAIL		233
		KEY_FRAMEBACK		0x1b4
		KEY_FRAMEFORWARD	0x1b5
		KEY_FRONT		132
		KEY_G			34
		KEY_GAMES		0x1a1
		KEY_GOTO		0x162
		KEY_GRAPHICSEDITOR	0x1a8
		KEY_GRAVE		41
		KEY_GREEN		0x18f
		KEY_H			35
		KEY_HANGEUL		122
		KEY_HANJA		123
		KEY_HELP		138
		KEY_HENKAN		92
		KEY_HIRAGANA		91
		KEY_HOME		102
		KEY_HOMEPAGE		172
		KEY_HP			211
		KEY_I			23
		KEY_INFO		0x166
		KEY_INSERT		110
		KEY_INS_LINE		0x1c2
		KEY_ISO			170
		KEY_J			36
		KEY_K			37
		KEY_KATAKANA		90
		KEY_KATAKANAHIRAGANA	93
		KEY_KBDILLUMDOWN	229
		KEY_KBDILLUMTOGGLE	228
		KEY_KBDILLUMUP		230
		KEY_KEYBOARD		0x176
		KEY_KP0			82
		KEY_KP1			79
		KEY_KP2			80
		KEY_KP3			81
		KEY_KP4			75
		KEY_KP5			76
		KEY_KP6			77
		KEY_KP7			71
		KEY_KP8			72
		KEY_KP9			73
		KEY_KPASTERISK		55
		KEY_KPCOMMA		121
		KEY_KPDOT		83
		KEY_KPENTER		96
		KEY_KPEQUAL		117
		KEY_KPJPCOMMA		95
		KEY_KPLEFTPAREN		179
		KEY_KPMINUS		74
		KEY_KPPLUS		78
		KEY_KPPLUSMINUS		118
		KEY_KPRIGHTPAREN	180
		KEY_KPSLASH		98
		KEY_L			38
		KEY_LANGUAGE		0x170
		KEY_LAST		0x195
		KEY_LEFT		105
		KEY_LEFTALT		56
		KEY_LEFTBRACE		26
		KEY_LEFTCTRL		29
		KEY_LEFTMETA		125
		KEY_LEFTSHIFT		42
		KEY_LINEFEED		101
		KEY_LIST		0x18b
		KEY_LOGOFF		0x1b1
		KEY_M			50
		KEY_MACRO		112
		KEY_MAIL		155
		KEY_MAX			0x2ff
		KEY_MEDIA		226
		KEY_MEDIA_REPEAT	0x1b7
		KEY_MEMO		0x18c
		KEY_MENU		139
		KEY_MESSENGER		0x1ae
		KEY_MHP			0x16f
		KEY_MINUS		12
		KEY_MODE		0x175
		KEY_MOVE		175
		KEY_MP3			0x187
		KEY_MSDOS		151
		KEY_MUHENKAN		94
		KEY_MUTE		113
		KEY_N			49
		KEY_NEW			181
		KEY_NEWS		0x1ab
		KEY_NEXT		0x197
		KEY_NEXTSONG		163
		KEY_NUMERIC_0		0x200
		KEY_NUMERIC_1		0x201
		KEY_NUMERIC_2		0x202
		KEY_NUMERIC_3		0x203
		KEY_NUMERIC_4		0x204
		KEY_NUMERIC_5		0x205
		KEY_NUMERIC_6		0x206
		KEY_NUMERIC_7		0x207
		KEY_NUMERIC_8		0x208
		KEY_NUMERIC_9		0x209
		KEY_NUMERIC_POUND	0x20b
		KEY_NUMERIC_STAR	0x20a
		KEY_NUMLOCK		69
		KEY_O			24
		KEY_OK			0x160
		KEY_OPEN		134
		KEY_OPTION		0x165
		KEY_P			25
		KEY_PAGEDOWN		109
		KEY_PAGEUP		104
		KEY_PASTE		135
		KEY_PAUSE		119
		KEY_PAUSECD		201
		KEY_PC			0x178
		KEY_PHONE		169
		KEY_PLAY		207
		KEY_PLAYCD		200
		KEY_PLAYER		0x183
		KEY_PLAYPAUSE		164
		KEY_POWER		116
		KEY_POWER2		0x164
		KEY_PRESENTATION	0x1a9
		KEY_PREVIOUS		0x19c
		KEY_PREVIOUSSONG	165
		KEY_PRINT		210
		KEY_PROG1		148
		KEY_PROG2		149
		KEY_PROG3		202
		KEY_PROG4		203
		KEY_PROGRAM		0x16a
		KEY_PROPS		130
		KEY_PVR			0x16e
		KEY_Q			16
		KEY_QUESTION		214
		KEY_R			19
		KEY_RADIO		0x181
		KEY_RECORD		167
		KEY_RED			0x18e
		KEY_REDO		182
		KEY_REFRESH		173
		KEY_REPLY		232
		KEY_RESERVED		0
		KEY_RESTART		0x198
		KEY_REWIND		168
		KEY_RFKILL		247
		KEY_RIGHT		106
		KEY_RIGHTALT		100
		KEY_RIGHTBRACE		27
		KEY_RIGHTCTRL		97
		KEY_RIGHTMETA		126
		KEY_RIGHTSHIFT		54
		KEY_RO			89
		KEY_S			31
		KEY_SAT			0x17d
		KEY_SAT2		0x17e
		KEY_SAVE		234
		KEY_SCALE		120
		KEY_SCREEN		0x177
		KEY_SCROLLDOWN		178
		KEY_SCROLLLOCK		70
		KEY_SCROLLUP		177
		KEY_SEARCH		217
		KEY_SELECT		0x161
		KEY_SEMICOLON		39
		KEY_SEND		231
		KEY_SENDFILE		145
		KEY_SETUP		141
		KEY_SHOP		221
		KEY_SHUFFLE		0x19a
		KEY_SLASH		53
		KEY_SLEEP		142
		KEY_SLOW		0x199
		KEY_SOUND		213
		KEY_SPACE		57
		KEY_SPELLCHECK		0x1b0
		KEY_SPORT		220
		KEY_SPREADSHEET		0x1a7
		KEY_STOP		128
		KEY_STOPCD		166
		KEY_SUBTITLE		0x172
		KEY_SUSPEND		205
		KEY_SWITCHVIDEOMODE	227
		KEY_SYSRQ		99
		KEY_T			20
		KEY_TAB			15
		KEY_TAPE		0x180
		KEY_TEEN		0x19e
		KEY_TEXT		0x184
		KEY_TIME		0x167
		KEY_TITLE		0x171
		KEY_TUNER		0x182
		KEY_TV			0x179
		KEY_TV2			0x17a
		KEY_TWEN		0x19f
		KEY_U			22
		KEY_UNDO		131
		KEY_UNKNOWN		240
		KEY_UP			103
		KEY_UWB			239
		KEY_V			47
		KEY_VCR			0x17b
		KEY_VCR2		0x17c
		KEY_VENDOR		0x168
		KEY_VIDEO		0x189
		KEY_VIDEO_NEXT		241
		KEY_VIDEOPHONE		0x1a0
		KEY_VIDEO_PREV		242
		KEY_VOICEMAIL		0x1ac
		KEY_VOLUMEDOWN		114
		KEY_VOLUMEUP		115
		KEY_W			17
		KEY_WAKEUP		143
		KEY_WIMAX		246
		KEY_WLAN		238
		KEY_WORDPROCESSOR	0x1a5
		KEY_WWW			150
		KEY_X			45
		KEY_XFER		147
		KEY_Y			21
		KEY_YELLOW		0x190
		KEY_YEN			124
		KEY_Z			44
		KEY_ZENKAKUHANKAKU	85
		KEY_ZOOM		0x174
		KEY_ZOOMIN		0x1a2
		KEY_ZOOMOUT		0x1a3
		KEY_ZOOMRESET		0x1a4
		BTN_0			0x100
		BTN_1			0x101
		BTN_2			0x102
		BTN_3			0x103
		BTN_4			0x104
		BTN_5			0x105
		BTN_6			0x106
		BTN_7			0x107
		BTN_8			0x108
		BTN_9			0x109
		BTN_A			0x130
		BTN_B			0x131
		BTN_BACK		0x116
		BTN_BASE		0x126
		BTN_BASE2		0x127
		BTN_BASE3		0x128
		BTN_BASE4		0x129
		BTN_BASE5		0x12a
		BTN_BASE6		0x12b
		BTN_C			0x132
		BTN_DEAD		0x12f
		BTN_DIGI		0x140
		BTN_EXTRA		0x114
		BTN_FORWARD		0x115
		BTN_GAMEPAD		0x130
		BTN_GEAR_DOWN		0x150
		BTN_GEAR_UP		0x151
		BTN_JOYSTICK		0x120
		BTN_LEFT		0x110
		BTN_MIDDLE		0x112
		BTN_MISC		0x100
		BTN_MODE		0x13c
		BTN_MOUSE		0x110
		BTN_PINKIE		0x125
		BTN_RIGHT		0x111
		BTN_SELECT		0x13a
		BTN_SIDE		0x113
		BTN_START		0x13b
		BTN_STYLUS		0x14b
		BTN_STYLUS2		0x14c
		BTN_TASK		0x117
		BTN_THUMB		0x121
		BTN_THUMB2		0x122
		BTN_THUMBL		0x13d
		BTN_THUMBR		0x13e
		BTN_TL			0x136
		BTN_TL2			0x138
		BTN_TOOL_AIRBRUSH	0x144
		BTN_TOOL_BRUSH		0x142
		BTN_TOOL_DOUBLETAP	0x14d
		BTN_TOOL_FINGER		0x145
		BTN_TOOL_LENS		0x147
		BTN_TOOL_MOUSE		0x146
		BTN_TOOL_PEN		0x140
		BTN_TOOL_PENCIL		0x143
		BTN_TOOL_QUADTAP	0x14f
		BTN_TOOL_RUBBER		0x141
		BTN_TOOL_TRIPLETAP	0x14e
		BTN_TOP			0x123
		BTN_TOP2		0x124
		BTN_TOUCH		0x14a
		BTN_TR			0x137
		BTN_TR2			0x139
		BTN_TRIGGER		0x120
		BTN_WHEEL		0x150
		BTN_X			0x133
		BTN_Y			0x134
		BTN_Z			0x135
	end codes
end remote

```

5. Setup/copy Mythtv/Lircrc file (follow step 5 of the standard lirc option setup) after modifying. I don't have a pre-made file but you will need to change the button names using the snapstream_firefly rc_keymap file.

FROM:
# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

TO:
# OK/Select
begin
prog = mythtv
button = KEY_ENTER
config = Space
end

I am looking into if it would be possible to change the keyboard option to allow for channel ID.

---

