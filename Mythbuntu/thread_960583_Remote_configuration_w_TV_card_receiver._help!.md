---
title: "Remote configuration w/ TV card receiver. help!?"
date: 2008-10-27
forum: Mythbuntu
---

### Post by WoodsieLord on 2008-10-27
Hello,
I've got this Card & remote: [http://img399.imageshack.us/img399/4985/mkworldplustvhybridpcifg9.jpg](http://img399.imageshack.us/img399/4985/mkworldplustvhybridpcifg9.jpg)
(additional info at bottom)

All I did is launch the Mythbuntu Control Centre and checked "Enable a Remote Control". I've tried a few from the list, although my card is not listed among those.

The result is this: The remote "works". EVERYWHERE feels the same, I mean, in a terminal console, in the mythtv backend config or in live TV. Only a FEW buttons work, and they're BAD arranged/distributed. the "zero" key, sends an 8 (eight), the "Five" key, sends a "-" minus character. Volume down key, sends a 9 (nine). Maybe 2 or 3 keys more work like this. 

I've been reading for two days now. Every command I try makes no effect. I made changes in the hardware.conf (lirc) restarted the box, etc. ZERO means eight, nothing else.

· irrecord gets the "gap not found" classic error.
· calling irw will crash lircd with some configs.
· irw will "work" with some other configs. At least does not crash. I press Zero, 8 appears.
· I checked "Generate dynamic buton mappings". The same.
· I tried to stop lircd. Pressing Zero will bring 8 even with lircd stopped.
· Remote commands transmits fine. No random respones. Zero always gives eights, fives always gives minuses and so on..
· If I run "cat /dev/input/event8" I get a different string of bizarre characters for every button I press. I found only 3 buttons that do nothing like if they were dead. The codes look coherent (the same crap appears if I press the button more times). The d*mn remote&receiver are working! I should be able to get this working fine!

I don't ask for a single step solution. I request some directions, hints or tips. I don't know what the hell is going on here.

Thanks in advance.

[Additional information]
Tuner: Kworld Plus TV PCI. SAA7134HL Based. Phillips PAL tuner.
· my IR input device lists as "event8" if I run cat /proc/bus/input/devices . N: Name="saa7134 IR (Kworld Xpert TV PVR) (...) H: Handlers=kbd event8
· IR receiver is connected directly to the TV Card
Need more info? Let me know! I will try to follow and provide everything.

---

### Post by SiHa on 2008-10-27
Sounds to me like you have basic kernel support: you get a response even with lircd stopped, and changes to [lircd/hardware].conf, but it's badly screwed.

I've found that MCC doesn't always setup remotes properly, especially if they are mapped to an event rather than /dev/lirc0 or /dev/lirc/0.

Have a look at your hardware.conf, it should be something like this:

```
REMOTE="something or other"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event8"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
```

I'll bet that your device is pointing to /dev/lirc0?

The modules are the important bit - you could try adding lirc_gpio to the **REMOTE_MODULES** line - I just did a quick google, and came across [ [COLOR="Blue"]this[/COLOR]](http://www.lirc.org/html/table.html#@hw-tv-card) on lirc.org, and it mentions a kworld card, and also a lircd.conf for it.
To use this conf file, add the following to your **/etc/lirc/lircd.conf**:
```
include /usr/share/lirc/remotes/kworld/lircd.conf.kworld
```
...and comment out any others

As a last resort, you could try```
sudo dpkg-reconfigure lirc
```. You get a bigger choice of remotes than from within MCC, your KWORLD card may even be listed.

---

### Post by WoodsieLord on 2008-10-27
Thanks a lot for the reply,

> I'll bet that your device is pointing to /dev/lirc0?I've read a bit about this somewhere before. Indeed, by default it shows dev/lirc0. I tried once again switching to event8 with no luck.
Second, I tried to add lirc_gpio to the REMOTE_MODULES line. No changes.
Third, about the Kworld.conf file: I've seen that file before! I have a bit more to tell you about this files:

Leaving MythTV aside for a second, I have an 'IGOR' IR receiver via COM port in my Windows machine for several years now. I use my VCR remote with Girder to control Winamp music player. Why am I telling you this? Because I found something interesting. Girder has a little box which shows the detected/sensed IR code. What an interesting idea to test the TV card remote here and check for the IR codes!. I found out that a nice 75% of IR commands are the same for the "Kworld ATSC_110" Remote. At least, they look alike (some different characters at the beginning). The first kworld.conf files I've seen had completely different codes ( like 0x000000000000807F, while Girder says 61D600FF and the ATSC_110 says 0x00FF for the same button)

Long story short, I tried the ATSC_110 config but I'm still getting Eights instead of zeros.
Finally, I tried reconfiguring the lirc package several times with different cards and lastly, I tried to use the IGOR serial receiver/sensor. I couldn't get it to work.
When I tried to configure "Linux input device" (or something like that) in Lirc, the remote stopped working. Except for this, the other options always did the same.

Once again, Thanks a lot for your reply. I appreciate your time helping us out!

---

### Post by WoodsieLord on 2008-10-28
Update:

I've always been able to run **irrecord -H dev/input -d /dev/input/event8 test.file** where I'm asked to press and **hold** a random button. No matter which button I hold, a single dot appears and -as I stated in the first post- I get a GAP not found error.

**But**
I read somewhere about someone with the same sympthom, where he/she starts to press repeatedly a button instead of holding it. I tried this and I got an interesting result: ** I was able to finish the irrecord procedure.**. The most interesting part about this is that checking the "test.file" recently created it features the commands and some beautiful and non repeated codes like:
```
...
cero  0x0009
uno   0x00A7
dos   0x0002
...
```
etcetera. Just in case, I run this test three times and the codes for cero, uno and dos are always the same (cero is always 0x0009, uno 0x00A7, etc). This means irrecord works fine I guess!
The bad part, is that I'm still unable to make use of the file. I tried to include this new and incomplete 'test.file' example the way you suggested (in the /etc/lirc/lircd.conf file).

I'm still clueless. The only possibility I can think of, is that the SAA7134 TV card drivers come with its own IR 'interpreter' or something like that. That may explain why we feel there's something out there overriding whatever LIRC says. I'm not sure what can I do about now, but I'm sure I proved that the crazy remote/sensor work and that irrecord works fine.

...help! :)
thanks again.

---

### Post by SiHa on 2008-10-29
> I've always been able to run irrecord -H dev/input -d /dev/input/event8 test.file where I'm asked to press and hold a random button. No matter which button I hold, a single dot appears and -as I stated in the first post- I get a GAP not found error.

In the version of irrecord that comes with 8.04.1, that's exactly what it tells you to do. I guess this is to fix the problem you're having.

So you've recorded an file - you're almost home and dry.
Easiset thing to do is just rename this to **/etc/lirc/lircd.conf**

Now what do you get with irw? (don't forget to restart lirc first)```
sudo /etc/init.d/lirc restart
```

---

### Post by WoodsieLord on 2008-10-29
Woohaa, another step forward! It works, almost...! SiHa, **thanks** for your help. One last detail holds from success:

Once I underestood how this must be done, I run irrecord once more to capture all buttons. But I run out of luck. Irrecord doesn' react to the most useful arrow buttons. Also, the rewind & forward buttons are interpreted with the same code as numberes 1 and 2. (pressing 1 or rewind is the same, pressing 2 or forward is the same). Just in case I double checked Girder to see if those button pairs really have the same codes but they don't. I'm not as concerned byt the forward & rewind buttons as I am with the arrowed ones, which are more crytical...  What should I do about this?

---

### Post by SiHa on 2008-10-30
Can you post the file you get with irrecord, trying every button?
Can you also post what you get from Girder for all buttons?

It sounds like irrecord isn't correctly identifying the pre & post - data bits, the bits that frame each button press. I'm wondering if you could write your own lircd.conf, with a combination of the bits that irrecord has managed to capture, and the codes that you can get using Girder.

Other things to try:

Irrecord may not be able to identify the RC protocol of your remote, you can force it to use RC5/RC6/RC-MM.

There is an option in irrecord to record raw pulse / space data. I've never used it, and have no idea how LIRC actually uses that data, but that may be your only option. 

I can't remember the syntax, for these two, but check the manpages```
man irrecord
```('q' to quit).

---

### Post by WoodsieLord on 2008-10-30
> Can you post the file you get with irrecord, trying every button?
I'm afraid No. I mean, when I'm asked to hold "left" button, I get a no buttons pressed timeout and Irrecord finishes prematurely. So, I can show you the working buttons only :'(
> Can you also post what you get from Girder for all buttons?
Here we go. I dumped the Girder Codes manually in a TXT file.

_Girder codes:_
The 100% of the buttons WORK. As far as I can see every button has its very own code. The only fishy thing is that all the codes begin with 61D6. 
```
KW	61D630CF
>o	61D66897
power	61D6B847
num 1	61D600FF
num 2	61D6807F
num 3	61D640BF
num 4	61D6C03F
num 5	61D620DF
num 6	61D6A05F
num 7	61D6609F
num 8	61D6E01F
num 9	61D610Ef
num 0	61D650AF
Previ	61D6906F
mute	61D628D7
ç[]	61D67887
windo	61D6E817
home	61D6F807
back	61D6708F
LEFT	61D642BD
RIGHT	61D6C23D
UP	61D604FB
DOWN	61D6847B
ENTER	61D6D02F
CH+	61D608F7
CH-	61D68877
VOL+	61D6C837
VOL-	61D648B7
Time	61D69867
Stop	61D658A7
Record	61D6D827
e	61D6D22D
rewind	61D602FD
Play	61D622DD
forward	61D6827D
TX	61D644BB
((o))	61D6A857
[<->]	61D6F00F
snapsh	61D638C7
Zz	61D652AD
=·=.	61D612ED
A	61D6926D
B	61D618E7
C	61D6C43B
```
_my test.file (copied to lircd.conf)_
All the buttons captured here send functions to mythtv after a mythbuntu-lirc-generator run.
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Wed Oct 29 20:52:14 2008
#
# contributed by 
#
# brand:                       test.file
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  test.file
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          203989
  toggle_bit_mask 0x800100CF

      begin codes
          1                        0x00A7
          2                        0x0002
          3                        0x000B
          4                        0x0182
          5                        0x004A
          6                        0x0005
          7                        0x0008
          8                        0x00E2
          9                        0x0080
          0                        0x0009
          menu                     0x004E
          ch+                      0x0195
          ch-                      0x00CF
          vol+                     0x018B
          vol-                     0x000A
          enter                    0x0003
          rewind                   0x00A7
          forward                  0x0002
      end codes

end remote



```

> It sounds like irrecord isn't correctly identifying the pre & post - data bits, the bits that frame each button press. I'm wondering if you could write your own lircd.conf, with a combination of the bits that irrecord has managed to capture, and the codes that you can get using Girder.
I'm not sure if I'm following you here. You mean to add codes manually and try using the 61D6 prefix or something like that? Let me know what you mean and I'll try :)

> There is an option in irrecord to record raw pulse 
I've been trying to get this working but I have no luck this time. My irrecord command used to get my test.file above, is as follows:
**irrecord -H dev/input -d /dev/input/event7 test.file** (notice: I made a clean reinstall of mythbuntu a few days ago and now I have event7 :P )
If I try to add --force (or -f) I get an error telling me that I cannot use -d along with -f. So, I'm able to run **irrecord -H dev/input --force example.file** but...
When I'm asked to hold a button (press it repeatedly in newer versions) no dots appear, only "8" (eights) if I press the Zero but even if I do keep tapping "8" (zeros) I get a Gap not found error.
The file "example.file" is actually never created.

> Irrecord may not be able to identify the RC protocol of your remote, you can force it to use RC5/RC6/RC-MM.
I was hoping to find an option for irrecord that would allow me to force any of those protocols but I think there is no way to do this.

I hope You get something from the girder & irrecord codes :)
Once again, thanks for your help SiHa.

---

### Post by SiHa on 2008-10-30
OK, it looks like irrecord needs more work, let's leave that for a minute.

Well, from the details you gave in your first post, and the Girder codes, I think we're finally onto something. You say that when you press 5, you get a '-'. 

That's the important bit.

The Girder-reported code for '5' is **0x61D620DF**, in lircd.conf.kworld, the first definition has **0x00000000000020DF** for the '-' key. So, if you ignore the **61D6** (This is the pre_data, as defined in the header) they are the same! This also follows for the other keys you mentioned 0 & 8, Vol- & 9.

So, it looks like this configuration file has the RC info correct, but the codes are wrong. I've taken the codes you got from Girder and created a new file:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
# lircd.conf.kworld_plustv
# cobbled together by Simon Harrison (SiHa) using header info
# from lircd.conf.kworld, and codes supplied by someone else...
# 
# brand: kworld
# model no. of remote control: ?
# devices being controlled by this remote: PlusTV tuner card
#

begin remote

  name  kworld_plusTV
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       8853  4526
  one           533  1713
  zero          533   589
  ptrail        531
  repeat       8853  2281
  pre_data_bits   16
  pre_data       0x61D6
  gap          107839
  toggle_bit      0


      begin codes
	KW	0x00000000000030CF
	>o	0x0000000000006897
	power	0x000000000000B847
	1	0x00000000000000FF
	2	0x000000000000807F
	3	0x00000000000040BF
	4	0x000000000000C03F
	5	0x00000000000020DF
	6	0x000000000000A05F
	7	0x000000000000609F
	8	0x000000000000E01F
	9	0x00000000000010Ef
	0	0x00000000000050AF
	Previ	0x000000000000906F
	mute	0x00000000000028D7
	ç[]	0x0000000000007887
	windo	0x000000000000E817
	home	0x000000000000F807
	back	0x000000000000708F
	LEFT	0x00000000000042BD
	RIGHT	0x000000000000C23D
	UP	0x00000000000004FB
	DOWN	0x000000000000847B
	ENTER	0x000000000000D02F
	CH+	0x00000000000008F7
	CH-	0x0000000000008877
	VOL+	0x000000000000C837
	VOL-	0x00000000000048B7
	Time	0x0000000000009867
	Stop	0x00000000000058A7
	Record	0x000000000000D827
	e	0x000000000000D22D
	rewind	0x00000000000002FD
	Play	0x00000000000022DD
	forward	0x000000000000827D
	TX	0x00000000000044BB
	((o))	0x000000000000A857
	[<->]	0x000000000000F00F
	snapsh	0x00000000000038C7
	Zz	0x00000000000052AD
	=·=.	0x00000000000012ED
	A	0x000000000000926D
	B	0x00000000000018E7
	C	0x000000000000C43B
      end codes

end remote

```

Copy this into a file and save it as **lircd.conf.kworld_plustv**

Try putting this file somewhere, and pointing your lircd.conf to it, the file should look like this: ```
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

include /path/to/lircd.conf.kworld_plustv

```

Or simply save the file as **/etc/lirc/lircd.conf**

Check your hardware.conf is still correct - pointing to **/dev/input/event7**, and loading the correct modules. Restart lirc, and try IRW.

#fingers crossed# This has got to work...

EDIT: Just had a thought. You might want to check that /dev/input/event**n** isn't changing between boots. It can happen, and the fact that it has changed (although after a reinstall) suggests it might do again.

have a look here: [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) 'Making the LIRC device static'

---

### Post by WoodsieLord on 2008-11-02
quick reply: I'm afraid the new frankestein **lircd.conf.kworld_plustv** didn't work. No keys respond at all (irw). I've been working around but I'm still here. 
Also, I've downloaded the remotes files from lirc.org and tried the RC-5 profile with no luck. I really don't know what to do other than trying lots of profiles one by one. This is driving me crazy!. Sorry for my late response. Do you have any idea what I could try next?
I REALLY see your point. I mean why my 'button 5' gives a '-', why 'button 0' gives a '8', etc. The bad part is that I don't know where or what is checking/using what to work that way. I double checked my hardware.conf and lircd.conf files. I tried using "include" and also overwriting the lircd.conf file. I'm really clueless...

Also, I don't know why my only working (for now) irrecord command captures button presses with a different codeset if everything looks like the Girder codes are the real thing! (I wasn't convinced until you make me notice the 0 -> 8, 5 -> - (...) behaviour.

Indeed, my eventX is changing between boots. I'll check that! thanks :).

Thanks again for your help. I'll let you know if I get it working.

---

### Post by SiHa on 2008-11-03
> Also, I don't know why my only working (for now) irrecord command captures button presses with a different codeset if everything looks like the Girder codes are the real thing! (I wasn't convinced until you make me notice the 0 -> 8, 5 -> - (...) behaviour.
I think it's probably because irrecord is having a hard time identifiying the correct protocol, and is getting it wrong.

> my test.file (copied to lircd.conf)
All the buttons captured here send functions to mythtv after a mythbuntu-lirc-generator run.

Sorry - I missed that part. If these codes work in Myth, then irrecord must be doing something right. I just can't see any correlation between these codes and the Girder ones.

If all else fails, you could try making a homebrew serial receiver. I use the 'More advanced' version here: [http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html) on both my Mythboxes.

Apart from that, I'm out of ideas. Sorry.

---

### Post by armeniovale on 2008-11-03
Hi guys
I´m following this post with very high interest because i have the same situacion, in my Mythubuntu Media Center with a Kworld Plus TV PVR-7134SE card.

Now i'm trying to configure the remote control with a serial receiver, and th Irrecord comand. Perhaps, the Lircd.conf file generated con be useful for the problems above.

---

### Post by SiHa on 2008-11-04
Ooh, it might!
Although, I found with my Hauppauge card that the codes that I get with a serial receiver are completely different to the ones I get using the on-board receiver.
Here's hoping though - I'd love to get to the bottom of this one.

---

### Post by heldal on 2008-11-05
> **WoodsieLord said:**
> 
Indeed, my eventX is changing between boots. I'll check that! thanks :).


For more info on how to specify the device see:
[http://www.lirc.org/html/devinput.html](http://www.lirc.org/html/devinput.html)

A worse problem you may encounter is that recent versions of the x-server take input signals (kbd/mouse etc) via DBUS from the hardware abstraction layer (hald) which in turn hogs all input devices unless it's told otherwise. lirc will then write to the log that it is unable to get exclusive access to the device, and in my case (remote on a Hauppauge HVR4000) it failed to receive anything at all. Only a few keys (up/down/left/right/enter etc) which were handled through the X-server worked. In this case you'll have to locate the IR receiver in the output from lshal and create rule for hal to ignore the device. In my case I created /usr/share/hal/fdi/preprobe/20thirdparty/10-ignore-cx88-ir.fdi containing


```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
<device>
 <match key="info.product" contains_ncase="cx88 ir">
    <merge key="info.ignore" type="bool">true</merge>
 </match>
</device>
</deviceinfo>
```

Use the info.product string that matches your device (here "cx88 ir").

This problem may affect many, if not all, IR receivers that use the dev/input interface.

---

### Post by pamaho on 2008-11-06
Hi, i'm the same problem, but in fedora. Somebody can post your hardware.conf file?? I can not extend because my english is very bad. Thanks.

---

### Post by heldal on 2008-11-06
> **pamaho said:**
> Hi, i'm the same problem, but in fedora. Somebody can post your hardware.conf file?? I can not extend because my english is very bad. Thanks.

This example is for a Hauppauge remote but should adjust easily for most dev/input -type remotes.

Find the IR device in the output from "cat /proc/bus/input/devices". For the Hauppage one it reads:

I: Bus=0001 Vendor=0070 Product=6902 Version=0001
N: Name="cx88 IR (Hauppauge WinTV-HVR400"
P: Phys=pci-0000:06:02.0/ir0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc

The pattern "*/ir?" matches the physical device above regardless of the order in which input-drivers are loaded, and is used in hardware.conf that set:

REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="phys=*/ir?"

---

### Post by pamaho on 2008-11-06
Well, i post the content of my files:

My "hardware.conf" (in fedora "/etc/sysconfig/lirc"):

> 
# Note: in addition to these parameters, you need to have working    -*- sh -*-
# configuration file for lircd (and lircmd if enabled).

# Options to lircd(8).  Typically, this will be empty, as which driver to use
# should be speified using the LIRC_DRIVER variable below.
LIRCD_OPTIONS="-H dev/input -d /dev/input/event6"

# The infrared receiver (and/or transmitter) driver to be used by lircd(8),
# similar to passing "-H driver" to lircd(8).
# Run "/usr/sbin/lircd -H help" to get a listing of supported drivers.
DRIVER="dev/input"

# Which lirc device will be used by lircd(8).
# This is the same as passing "-d device" to lircd.
# An empty value will use the default /dev/lirc device.
DEVICE="/dev/input/event6"

# If "yes", the init script will try to start lircmd(8) too.
ENABLE_LIRCD="yes"
ENABLE_LIRCMD="no"

# Options to lircmd(8).
LIRCMD_OPTIONS=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd.conf"

My "lircd.conf":

> 
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

include /usr/share/lirc-remotes/kwolrd/lircd.conf.kworld_plustv


And my ".lircrc" (saved in my folder home):
> 
begin
    prog = irexec
    button = power
    config = tvtime &
    config = tvtime-command QUIT
end
# The following defines most of the common buttons found on a remote and
# what commads they would map to inside tvtime.
begin
    prog = irexec
    button = fullscreen
    config = tvtime-command TOGGLE_FULLSCREEN
begin
    prog = irexec
    button = mute
    config = tvtime-command TOGGLE_MUTE
end

# Menu navigation.
begin
    prog = irexec
    button = ch+
    config = tvtime-command UP
end
begin
    prog = irexec
    button = ch-
    config = tvtime-command DOWN
end
begin
    prog = irexec
    button = vol+
    config = tvtime-command RIGHT
    repeat = 2
end
begin
    prog = irexec
    button = vol-
    config = tvtime-command LEFT
    repeat = 2
end

begin
    prog = irexec
    button = recall
    config = tvtime-command CHANNEL_JUMP
end

begin
    prog   = irexec
    button = 1
    config = tvtime-command CHANNEL_1
end
begin
    prog   = irexec
    button = 2
    config = tvtime-command CHANNEL_2
end
begin
    prog   = irexec
    button = 3
    config = tvtime-command CHANNEL_3
end
begin
    prog   = irexec
    button = 4
    config = tvtime-command CHANNEL_4
end
begin
    prog   = irexec
    button = 5
    config = tvtime-command CHANNEL_5
end
begin
    prog   = irexec
    button = 6
    config = tvtime-command CHANNEL_6
end
begin
    prog   = irexec
    button = 7
    config = tvtime-command CHANNEL_7
end
begin
    prog   = irexec
    button = 8
    config = tvtime-command CHANNEL_8
end
begin
    prog   = irexec
    button = 9
    config = tvtime-command CHANNEL_9
end
begin
    prog   = irexec
    button = 0
    config = tvtime-command CHANNEL_0
end


I run irexec with the command "irexec --daemon". Please, help me. Is the only device that i can not configure. Sorry for my english.

---

### Post by WoodsieLord on 2008-11-07
Hehe I never thought that getting XMLTV was going to be easier than the remote but sure it is!:)

> A worse problem you may encounter is that recent versions of the x-server take input signals (kbd/mouse etc) via DBUS from the hardware abstraction layer (hald) which in turn hogs all input devices unless it's told otherwise. lirc will then write to the log that it is unable to get exclusive access to the device, and in my case (remote on a Hauppauge HVR4000) it failed to receive anything at all. Only a few keys (up/down/left/right/enter etc) which were handled through the X-server worked
Thanks for this info Hedal, I created the xml file as you stated but nothing changed after rebooting. I'm still getting eights if I press the 'zero' button. Also Irrecord does not recognize the tricky keys. 
By the way, if I run **irrecord -H dev/input --device=name='saa7134 ir*' lircd.conf** the device cannot be found (don't remember this exactly at this time, "*blahblah (is lirc running?)*")
(I checked my device name running **lshal | grep -i saa**. I get a info.product "saa7134 ir(Kworld PCI PVR BLA")

Anyways, I decided to go for the serial IR receiver. I got everything I need except the IR receptor itself and a wire to bring it to the case front... I hope I will be getting the parts soon. SiHa, how do you configure LIRC with this receiver? Looks like the "igor" version to me, although I'm not sure.

Thanks again, People :KS

---

### Post by SiHa on 2008-11-07
> Anyways, I decided to go for the serial IR receiver. I got everything I need except the IR receptor itself and a wire to bring it to the case front... I hope I will be getting the parts soon. SiHa, how do you configure LIRC with this receiver? Looks like the "igor" version to me, although I'm not sure.

I just run```
sudo dpkg-reconfigure lirc
```

Select "Homebrew Serial Receiver 16x50 compatible UART", and ttyS0 (for external) or ttyS1 (for internal). This takes care of disabling the kernel serial support as well.

---

### Post by heldal on 2008-11-08
> **WoodsieLord said:**
> Thanks for this info Hedal, I created the xml file as you stated but nothing changed after rebooting. I'm still getting eights if I press the 'zero' button. Also Irrecord does not recognize the tricky keys. 
By the way, if I run **irrecord -H dev/input --device=name='saa7134 ir*' lircd.conf** the device cannot be found (don't remember this exactly at this time, "*blahblah (is lirc running?)*")
(I checked my device name running **lshal | grep -i saa**. I get a info.product "saa7134 ir(Kworld PCI PVR BLA")


You don't need the HAL-rule in my example (for cx88 chipset) if you have a saa7134 IR-device. It is already handled in a file supplied with the lirc-package (the only dev/input device that seems OK wrt lirc and HAL).

The devices and names for use with lircd and in hardware.conf are found from /proc/bus/input/devices and not from lshal. If you check there (cat /proc/bus/input/devices) you'll probably find that you need to use uppercase "IR" in the name. I think lircd is case-sensitive for names. I don't have any saa7134 device to check.

---

### Post by WoodsieLord on 2008-11-13
I'm completely discouraged...

I've been looking for a TSOP1738 or compatible receiver through tens of electronical part stores all over the downtown. All I got was "I have no idea what is that" Not even compatible receivers.

Well, at this terrible scenario, I can always order some from USA or any store that sells this piece. But, first I thought I just might try my own serial receiver (the one I'm using with girder on Windows OS). No way. It just looks like its dead. Tried lot of presets for serial receivers (igor variant and other serials).
I wasn't able to even get any kind of garbage reaction with irrecord, irw, xev, nor cat /dev/lirc0.
This is so frustrating... not having XMLTV was ok, having to bear with "nuppel video" is somewhat acceptable but having no remote to watch TV, we all agree that this is not bearable right? :'(

It is also frustrating that every google search results return tons of 'guides' that include compiling downloading programming and lots of [linux intensive] knowledge. I've lost my patience, right now I'm wishing for a magic cage with a single button that will work fine stright out of the box without any configuration...

---

### Post by SiHa on 2008-11-13
I feel for you.

If you have an old VHS / DVD, you could try the one out of that?

In fact, my remote frontend is actually in an old DVD player case (don't ask why, it's a long story...), and I'm using the receiver that was originally in the case.

You'd need to check if it's 3V3 or 5V, and you'd have to hope it's 36/38KHz, although most are.

---

### Post by heldal on 2008-11-14
> **WoodsieLord said:**
> Hello,
· If I run "cat /dev/input/event8" I get a different string of bizarre characters for every button I press. 

Most dev/input IR-receivers will not work out of the box on 8.10. The problem is that HAL (hald) grabs all input-devices so that lircd is unable to get exclusive access to the event interface. The "garbage" you seen in a terminal-window is keycodes coming through the X-server which in turn (dafault on 8.10) gets its input though HAL.

Use lshal to identify your remote and create a rule for HAL to ignore the device. See /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi for a working example for the IR-receiver on saa7134 DTV-receivers.

The following exception was necessary for my Hauppauge HVR4000

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
<device>
 <match key="info.product" contains_ncase="cx88 ir">
    <merge key="info.ignore" type="bool">true</merge>
 </match>
</device>
</deviceinfo>
```

---

