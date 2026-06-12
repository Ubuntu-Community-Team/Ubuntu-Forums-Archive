---
title: "New Mythbuntu install, can't get Hauppauge remote to work"
date: 2014-12-27
forum: Mythbuntu
---

### Post by todd-4 on 2014-12-27
More remote control problems…  Sorry, it seems like this problem is scattered all over and every answer is different.  None that I’ve found work for me…

New to Linux, not sure where to start troubleshooting.  Have done hours of google searching, tried about everything I can find (although sorry but I haven’t been documenting those attempts so I’m not quite sure EVERYTHING I’ve tried…)  This is just not as easy as it seems it should be…

Much as I hate to (being a guy) I have to stop and ask for directions.

I’ve got a Mythbuntu box running Ubuntu 14.04.1 and Myth 0.27 v 0.27.4-27-g40506c2.  Pretty much everything appears to be working fine except I can’t get it to respond to an infrared remote.

I’ve got three tuner cards, all Hauppauge –a PVR-150 (MCE version, no remote input jack), an HVR-1600 and an HVR-2250.

The remote receiver is plugged into the HVR-1600, but I’ve tried plugging it into the 2250 with no change in results.

Before converting to Myth, this was a Win 8 box running SageTV in the same hardware configuration, and remote functions worked fine.  That’s why I’m using the 1600’s remote input, because it was working fine there.

I’ve done the “simple setup” – I have Myth Control Centre installed, I’ve gone to the Infra-red settings and set it up at times for all three choices.  The obvious one – “USB & Serial Remote support via LIRC”, which is what everyone on the web seems to point to, as well as the “No additional remote support” and “Use Android or IOS phone”.

FYI, I do have Mythmote on my phone, and it does work as a remote.  I just don’t want the entire family to have to have a phone around to work the TV…  I’d like it to work from the standard Hauppauge remote – which I think is called the “silver 45 button remote” by everyone.

In the “USB & Serial Remote support” I’ve chosen “Enable a remote control” and there tried every version of Hauppauge remote listed. 

After switching each I’ve tried “generate dynamic button mappings” each time.

I’ve tested the results both immediately and also (for good measure) rebooting each time.

I just can’t get the darn thing to respond to ANYTHING on the remote.

Yes, I know the batteries are good.  I’m a TV tech.  I know how to see the IR output on a remote, and I have a repeater/detector that flashes a visible LED when it gets input besides..  And I know the repeater works because I have other equipment in the “equipment closet” that works fine (and, again, it’s the same setup I was using for years with Win and Sage…)

I know my troubleshooting is kind of scattershot – because I really have no idea what the step-by-step flow of everything should be, what is handled by Myth, the kernel, lirc, etc…

The troubleshooting I’ve done is very similar to this post here:

[http://askubuntu.com/questions/178356/tracing-ir-to-hauppage-remote-on-mythbuntu-12-04](http://askubuntu.com/questions/178356/tracing-ir-to-hauppage-remote-on-mythbuntu-12-04)

Like this person, if I [FONT=courier new]ls /dev/l*[/FONT] I get no lirc0 (or any lirc…)

Like this person, if I [FONT=courier new]cat /proc/bus/input/devices[/FONT] I get a listing for various audo and video output devices, but nothing that looks like an IR receiver.

Like this person, if I look at [FONT=courier new]/etc/lirc/hardware.conf[/FONT] I get (below) something that looks pretty “normal” from what I’ve read.

[FONT=courier new]#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""[/FONT]

If I run IRW, I get “no such file or directory”.  Which seems to be a problem…

Dmesg gives me…

[FONT=courier new]$ dmesg | grep irc
[    7.769330] lirc_dev: IR Remote Control driver registered, major 250[/FONT]

If I try to start lirc manually I get:

[FONT=courier new]todd@avserver:~$ sudo service lirc start

 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
find: `/sys/class/rc/*/': No such file or directory[/FONT]

Which,, from what I read, seems to tie back to the part that the system doesn’t have an IR device under /dev/lirc0

One suggestion seems to try looking at

[FONT=courier new]tail –f /var/log/kern.log[/FONT]

after pushing buttons, but I get nothing there that seems to tie to the remote.

I do have an .lircrc file in my home directory, it says….

[FONT=courier new]#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa[/FONT]

And [FONT=courier new]~/.lirc/mythtv[/FONT] looks like a file full of button mapping commands.

I’ve tried installing lirc manually (sudo apt-get install lirc) but the system just tells me I have the latest.

There’s some talk about some configuration options in lirc – like there’s supposed to be a GUI interface where you pick your remote – but I can’t get anything like that to come up.  There are various suggestions on command lines to run lirc to configure the system, I can’t quote them right now but I’ve tried them all and nothing comes up.

If I knew that was the problem I’d keep going down that path, but EVERYTHING I read seems to indicate MythTV should “just work” with the Hauppauge remotes.  I’m not trying anything unusual…!
 
What can I check next?

Thanks in advance for any help, Merry Christmas!

---

### Post by todd-4 on 2014-12-31
Just checking in.... Anyone?  If there's anything else I can do to troubleshoot this there's nothing I'd rather spend my New Years' Day doing.... (!)

---

### Post by Lester_Burnham on 2014-12-31
Hi Todd,

The only thing I can add before having a read up on hauppauge remotes plugged directly to the TV card. I have no experience with their workings, only with MCE usb style remotes.
When running irw, it is lower case. I have made the misleading mistake of writing it in uppercase in posts before, so it would stand out instead of using the code tags.
It seems your problem is  more at the hardware level at the moment anyway.

Lester

---

### Post by t-charrett on 2015-01-01
Hi, I was looking at the forum today before doing an upgrade on my mythbuntu 12.04 machine with a NovaT 500 remote, this caught me out last time I installed, I think you now need to select "linux input layer" in the control center. I have some very short notes on the last install but I haven't tried these yet with 14.04, but I was going to try and install tomorrow and will post again if this doesn't help you.


From my 12.04 install notes...


1)Remote is now done thorugh new linux ir-keymaps
In mythbuntu control center select linux input layer
In /etc/lirc/hardware.conf enter correct event/device 
(use $dmesg | grep input  or $cat /proc/bus/input/devices   to find device)

$sudo nano /etc/lirc/hardware.conf


section from my 12.04 config:
> 
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:03:06.2-usb-0:1-event-ir"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
#"devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""





2) Edit lircd.conf file to remove 32bit legacy remote from file:


$ cd /usr/share/lirc/remotes/devinput
$ nano lircd.conf.devinput


remove from: "# generated by devinput.sh (obsolete 32 bit version)"


3)shutdown (not reboot), restart  & test.


key press delay/period
----------------------
use ir-keytable to set delay/period for both remotes (I have two ir recievers) in case they switch.
edit /etc/rc.local
add:
$ ir-keytable -s rc0 -D 100 -P 125
$ ir-keytable -s rc1 -D 100 -P 125


test: 
$ sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1383247047.538472: event MSC: scancode = 2ba115b7
1383247047.538479: event key down: KEY_IMAGES (0x01ba)
1383247047.538481: event sync
1383247047.787465: event key up: KEY_IMAGES (0x01ba)
1383247047.787470: event sync

---

### Post by khPWXxF on 2015-01-06
I tried to use that remote when I first bought my T500 tuner back in 2009.  I was unsuccessful – I learned lots of reasons (in addition to inexperience) why it wouldn't work but clearly didn't get all – I bought a Microsoft compatible and was a happier bunny.  
   
  For what it's worth I'll list the issues/myths which I came across, but it was in a different decade and with different Hauppauge tuner:
   
  1.  Some reported that the small jack plug at the end of the receiver lead was obstructed by the metal plate at the back of the board.  Hole in plate not big enough.
   
  2.  The T500 loads microcode ONLY on a cold start.  ie after power removal from the computer.  A plain reboot leaves 'stale code' which will not reflect changes in config (such as turning amplifier on), and is even intolerant of changing display from HDMI to VGA.  I don't know whether your Hauppauges are the same – a full power cycle after any changes is worth a try.
   
  3.  Mine seemed to be more reliable at 30cm range rather than 200cm.  Suggests bad hardware??
   
  4.  With 9.04 there was an issue which I've not seen with either 12.04 or 14.04 and the ms compatible but I'll mention it.
  Mythbuntu control centre (MCC) has a section for selecting the remote.  I needed to find out which 'event' it was using and provide that in MCC, but it only prompted for it if you deleted then set the remote again.
  You find out the event with cat /proc/bus/input/devices.
   Having said all that, this was some years ago (time really flies when you play with mythtv!) and mythbuntu has improved IR support dramatically.
   
  5.  As far as I can work out, the files you need to look at (and presumably are set up by MCC) are:
  > [FONT=&amp]/etc/lirc/hardware.conf[/FONT][FONT=&amp]  = Where is this hardware?[/FONT]
  > [FONT=&amp]/etc/lirc/lircd.conf[/FONT][FONT=&amp]     = specifies include file(s) saying how pulses should be interpreted.  eg [some ones and zeros with this spacing] mean the 'Record' button.[/FONT]
  [FONT=&amp]You can have multiple includes – I have the MS remote and my TV remote there.[/FONT]
  
  
  [FONT=&amp]If those files are right then irw should give sensible results.[/FONT]
  
  [FONT=&amp]Next, [/FONT]
  > [FONT=&amp]~/.mythtv/lircrc[/FONT][FONT=&amp]     = a link to ~/.lirc/mythtv [/FONT]
  
  [FONT=&amp]That tells the system that when it sees (say) the 'Record' button it should pump 'R' into mythtv but that if I press the power button it should start a script.    The button names are case sensitive.[/FONT]
  
  Of course, that ~ is really your home directory - /home/phil/ in my case.
   
  Finally, in mythtv setup there are 'keybindings'.  These say things like 'when in schedule screen, interpret R as record'.  If you change them then you will need to change your 'user manual'.
   
  hth and good luck!
  Phil

---

### Post by todd-4 on 2015-01-20
Lester - thanks, I do run irw in lower case, my mistake in typing it in upper, thanks for pointing that out though.

First, for all in troubleshooting this I've discovered that if I do a 

[FONT=courier new]cat /proc/bus/input/devices[/FONT]

the resulting listing shows no sign of any remote.

If I then

[FONT=courier new]sudo modprobe ir-kbd-i2c[/FONT]

I see the following entry added to the devices file 

[FONT=courier new]I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="i2c IR (Hauppauge HVR-1600)"
P: Phys=i2c-7/7-0071/ir0
S: Sysfs=/devices/virtual/rc/rc0/input16
U: Uniq=
H: Handlers=kbd event13 
B: PROP=0
B: EV=100013
B: KEY=10afc312 214201700000000 0 118000 41a800004801 9e16c000000000 10000ffc
B: MSC=10[/FONT]

and after I've done this - VIOLA - i then get at least SOME response to the remote.

Once I do this, I get a response out of MythTV when I press the arrow keys (up, down, left, right) or number keys (1, 2, ... 9, 0) on the remote.  I can not only see this reflected in the Myth UI, but it also controls elements of the Ubuntu desktop (if I'm in that) and if I then run irw I get output!

[FONT=courier new]todd@avserver:~$ irw
^[[A^[[C^[[B^[[D[/FONT]

HOWEVER, no response to any other keys on the remote.

Now... before one says "your remote is bad", keep in mind..

A)  I'm a TV technician... I do know a bit about troubleshooting remotes.. (!)
B)  The machine I'm running this on is dual-boot with a Win8 partition that is running SageTV (which is what I did for a DVR before Myth).  If I boot that partition up and load Sage, Sage responds to this exact same remote - using this exact same hardware - just fine, all keys...
C)  I have TWO remotes, both behave exactly the same in Myth...
D)  I know for a fact that both remotes ARE putting out IR when the non-functional keys are pressed, not only because SageTV responds fine in Win8, but because I have an IR detector....

So... 99.99999% certain the problem is not the remote, the remote receiver (being not plugged in or just not working) OR the Hauppauge card not passing the remote signals on...

With that behind us, I also found out that this new "devices" entry made by my running modprobe does not persist from one boot to the other.  If I reboot Mythbuntu, I lose that entry - and have to run modprobe again to get it there.

I don't understand this behavior, because as long as I do NOT reboot, I see the entry in the devices file no matter how many times I open and close it - it MUST be saved to the file, you would think.  I cannot save changes to this file, however, permissions do not allow this (even as sudo).  I can "save as" a copy to my home directory, though.  

I'm thinking if that problem can't be solved I can probably do something in startup to automatically run modprobe when rebooted.  Seems odd to have to do that workaround, but, whatever...  I'm only pointing it out here in case it's some indication that something, somewhere, is going wrong.

Now, back to the issue at hand..

I tried to follow t-charret's suggestions but nothing really looks the same as my installation and I'm not sure how to interpret.  For example, when he says to modify /etc/lirc/hardware.conf to enter the correct event/device, is that:

[FONT=courier new]/devices/virtual/rc/rc0/input16[/FONT]

As shown above?  Also, the "REMOTE_LIRCD_CONF" line in mine does not resemble his so I'm not sure what to put there.

I stopped there on his suggestions because I had too many variables and did not know what to change first...

I got farther through khPWXxF's suggestions...

1 through 3 are hardware issue related, I've eliminated them.

4 relates to the lack of the remote event in the devices file, addressed above.

5, I checked hardware.conf, which shows

[FONT=courier new]#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""[/FONT]

Which baffles me because I don't think my device is /dev/lirc0, but yet i AM getting a response to the remote - just partial...

[FONT=courier new]/etc/lirc/lircd.conf [/FONT]

Gives me...

[FONT=courier new]#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"[/FONT]

I checked, and [FONT=courier new]/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge[/FONT] gives a long list of remote configurations, some of which don't even have codes for the arrow keys - sample of the first section in this file is below.
[FONT=courier new]
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100
  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote[/FONT]

and, just for the heck of it, I modified every entry in the file for the left arrow to change it to end in all zeros, figuring that would disable my left arrow SOMEHOW, but even after a reboot (and re-running modprobe as above) I still had the left arrow, so I assume it's getting that keymapping elsewhere...

and if I look at [FONT=courier new]~/.mythtv/lircrc[/FONT]

I get a file that looks like it's defining every key used by the remote, including all the buttons on my remote that do not work.  Sample below.

[FONT=courier new] LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Go
    config = Return
    repeat = 0
    delay = 0
end

[/FONT]Again, here I tried changing a value (the left arrow key) and saving it (I think I left it blank) and when I rebooted and ran modprobe the left arrow worked normally, even though this file still showed that entry blank.

I feel like I'm running around in circles because I really don't understand exactly what the flow is supposed to be - even though it seems to have been defined pretty well for me with all the help here, it just seems like MY system is pulling it's configurations from "somewhere else" rather than what is being outlined here.

Question I can see to try to resolve in an orgainzed way....

1)  How do I get the[FONT=courier new] /proc/bus/input/devices[/FONT] file to retain the remote event listing without having to run modprobe every time I reboot?
2)  In my config, what should the [FONT=courier new]/etc/lirc/hardware.conf[/FONT] file say about my input device and configuration file?
3)  Is [FONT=courier new]/etc/lirc/lircd.conf [/FONT]the source of "what button does what?" it just seems to point to another file ([FONT=courier new]/usr/share/lirc/extras/more_remotes/lircd.conf.hauppauge[/FONT])  Why would I not just point to this file directly?
4)  Within the [FONT=courier new]lircd.conf.hauppauge[/FONT] file referred to above, there are a bunch of separate remote listings - why are there more than one, and what determines which one is used?

I feel like if I can work through THAT trail I can then modify the [FONT=courier new]lircd.conf.hauppauge[/FONT] file to make my remote work.... maybe?

Wow.  It would be nice if just picking "Hauppauge TV Remote" in Mythbuntu Control Centre just made my Hauppauge remote work!

---

### Post by todd-4 on 2015-02-04
Just bumping this a bit.  All details are above, but what I'm really looking for is simply some direction to go in to try and troubleshoot further...  I'm at a dead end with my understanding of the system, and must be missing something...

---

### Post by khPWXxF on 2015-02-05
My T500 and my Hauppage 'stick' IR receivers both appear in ' [COLOR=#000000][FONT=courier new]cat /proc/bus/input/devices' without doing anything with modprobe (even if I don't use them).  Not your setup exactly but the same stable.
[/FONT][/COLOR]
Have you done a [COLOR=#000000][FONT=courier new]'cold' boot recently? ie close down, unplug computer from power socket, press 'start' to discharge capacitors (or wait a short while) then power on again?
The T500 remembers old settings over a warm boot and sulks if you change anything (eg swap HDMI to VGA) - maybe yours are the same. They could even still have the windows settings!
[/FONT][/COLOR][COLOR=#000000][FONT=courier new]If it still fails, then you're looking at drivers perhaps?
[/FONT][/COLOR][COLOR=#000000][FONT=courier new]
I also see
[/FONT][/COLOR]```
phil@myth:~$ ls -l /dev/l*
crw------- 1 root root 250,   0 Feb  5 09:35 /dev/lirc0
lrwxrwxrwx 1 root root       15 Feb  5 09:35 /dev/lircd -> /run/lirc/lircd
[.. more omitted ..]

```
but that's inconclusive as I rely on an MC remote.

The reference to T500 in your hardware.conf looks odd.  Is that your remote?  Two tone colours?

[COLOR=#000000][FONT=courier new]If all else fails, ms compatible remotes with usb IR receivers are very cheap and work great!

Phil
 [/FONT][/COLOR]

---

### Post by todd-4 on 2015-02-05
> **khPWXxF said:**
> Have you done a [COLOR=#000000][FONT=courier new]'cold' boot recently? ie close down, unplug computer from power socket, press 'start' to discharge capacitors (or wait a short while) then power on again?

The T500 remembers old settings over a warm boot and sulks if you change anything (eg swap HDMI to VGA) - maybe yours are the same. They could even still have the windows settings![/FONT][/COLOR][COLOR=#000000][FONT=courier new]

I don't cold boot often - it's a 24/7 media server - but I can try that.  I don't have a T500 - this remote is actually coming through an HVR-1600 card, but what the heck, anything's worth trying!

[/FONT][/COLOR][COLOR=#000000][FONT=courier new]> **khPWXxF said:**
> If it still fails, then you're looking at drivers perhaps?

I suppose I could think of that, but given the fact that I can get it to use the arrow keys that would seem to indicate the driver is working...
[/FONT][/COLOR][COLOR=#000000][FONT=courier new]
> **khPWXxF said:**
> I also see
[/FONT][/COLOR]```
phil@myth:~$ ls -l /dev/l*
crw------- 1 root root 250,   0 Feb  5 09:35 /dev/lirc0
lrwxrwxrwx 1 root root       15 Feb  5 09:35 /dev/lircd -> /run/lirc/lircd
[.. more omitted ..]

```
but that's inconclusive as I rely on an MC remote.

The reference to T500 in your hardware.conf looks odd.  Is that your remote?  Two tone colours?

No, I have a standard Hauppauge "silver" remote.  I forget how many buttons.  In the course of this I've tried every choice available in the Control Centre configuration of the system, I may have left it on T500 just because it made no difference which configuration I used, since only the arrow keys work in all of them.  I assume I should be using the more generic "Hauppauge TV Remote" choice.


[COLOR=#000000][FONT=courier new]> **khPWXxF said:**
> If all else fails, ms compatible remotes with usb IR receivers are very cheap and work great!

Sure, I could do that, but this is a challenge... I KNOW it's possible, there are just all kinds of people out there who claim they just installed Mythbuntu, picked the remote, and it "just worked".  

I'm using this in part to learn a bit more about Linux.  Reminds me of my old DOS days, when you could muck around in config files if you wanted to...


Right now, given that it all works - for the arrow keys - I feel SOOOO close to a solution.  Like I'm making a jigsaw puzzle and there's just ONE piece that fell under the table...  I feel like if I could just know for a fact exactly which configuration file - from which location - was feeding the system the definition of the remote's keys then that would fix it, but since the arrow keys work and I've modified every config file I can find with no change, I've got to think I'm just not hitting the right file...

Thanks, maybe I WILL have to go to a USB remote, but I'm hoping not.[/FONT][/COLOR]

---

