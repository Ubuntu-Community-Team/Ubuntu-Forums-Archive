---
title: "Serial IR --&gt; DirecTV satellite box"
date: 2007-12-18
forum: Mythbuntu
---

### Post by tegwilym on 2007-12-18
I just got my Mythbuntu up and running on my computer and tv.  It works great, but just trying to figure out the next step.  I can watch and record through my DirecTV receiver just fine, but the computer can't control the satellite box. 

I just got one of these serial to IR cables from Ebay and am trying to set up the lirc thing now.  I've fooled with this for hours and am pretty lost on how I do this.  I've been reading a lot of sites, but have to be careful for the ones that are telling how to use the remote to control the comptuer - I'm not doing that (yet).  I want to have the computer change the channels on the box with the IR.
I got this serial cable - [http://www.irblaster.info/](http://www.irblaster.info/)

Any ideas or even better, any GOOD easy to understand HowTo sites?  I assume that the lirc is installed on this already, but not sure.

Help!

Thanks, 
Tom

---

### Post by OffAxis on 2007-12-19
[LIST=1]
[*]Download this file
```
sudo wget http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb
```
[*]Install it
```
sudo dpkg -i lirc_0.8.3~pre1-0ubuntu1_i386.deb 
```

[*] Make sure the codes for your box are listed in /etc/lirc/lircd.conf

        you can look here for the appropriate codes here:
[http://lirc.sourceforge.net/remotes/]("http://lirc.sourceforge.net/remotes/")


[*]Restart lircd if you updated your lircd.conf
```
sudo /etc/init.d/lirc restart
```
[/LIST]
Don't let the term 'remote' throw you. Think of it as 'remote devices', not just remote controls.
The same file (lircd.conf) is used to receive ir signals (FROM remote controls) and transmit ir signals (TO set top boxes)

There's an excellent document on external channel changing here:
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer]("https://help.ubuntu.com/community/MythTV_External_Channel_Changer")

and on LIRC in general here:
[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

---

### Post by tegwilym on 2007-12-19
Awesome! 
I'll give that a try tonight.  I like that it's all related to the Ubuntu stuff.  I kept running into a site that mentioned apt-get, and the next line down it had an "RPM" command.  That just kept confusing me.

Yeah, I was kind of assuming that remotes and remote devices shouldn't be too bad.  I just need to duplicate the channel changing signal from one like this - [http://lirc.sourceforge.net/remotes/rca/D770.jpg](http://lirc.sourceforge.net/remotes/rca/D770.jpg)

from my Serial --> IR transmitter that I'll dangle in front of the receiver.  If I can get the computer to at least change the channels, I'll be a happy former Windows user!  :)

I'll post my results....or more questions after I try that out.  Thanks again for the response!

Tom

---

### Post by tegwilym on 2007-12-19
Wouldn't this LIRC thing already be installed with Mythbuntu?  
I do get the "Lirc not configured" message when I bring up a command line, so at least it seems to know that.   
Although, I think it has version 8.2 and you mentioned 8.3, so an update shouldn't hurt.  
I'll just have to try it and see.


Tom

---

### Post by OffAxis on 2007-12-19
whoops!
I left out step #5.

5. The channel changing script.

What I've listed (1-4) will get lirc up and going. You can test it with 
[B]
irsend LIST "" ""[/B]
which will list the availabe remote devices (as defined by lircd.conf)


**irsend SEND_ONCE [name of your remote device] 3**

will attempt to send the signal for channel 3 to your remote device.

those two commands interact with LIRC directly. Mythtv will use a script to run the SEND_ONCE command (and a pause in between number presses if necessary), and a press of the 'ENTER' key if necessary.
There are two well used and well documented ones in the 'External Channel Changing' link in my previous post, as well as the necessary permissions for the file, so I'll just direct you there.

---

### Post by tegwilym on 2007-12-19
Thanks!  I'll post my results.  Hopefully I'll be flipping through channels.  Ha!
Tom

---

### Post by OffAxis on 2007-12-19
try running 
```
lircd -v
```
and see what version comes up.

> Wouldn't this LIRC thing already be installed with Mythbuntu? 
yes. The problem is the version; .8.2 doesn't have serial support implemented properly, .8.3(cvs or pre-release) does.

> I do get the "Lirc not configured" 
that's referring to the /etc/lircd.conf file, as in it either doesn't exist or doesn't list any sections for 'remote'.

---

### Post by OffAxis on 2007-12-19
Oh.
And one more thing (isn't there always?)
I'm not sure if mythbuntu disables kernel support of the serial driver or not (I haven't tried a serial device on a proper mythbuntu install).

There's a section in this document that details how to disable it:
[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

---

### Post by tegwilym on 2007-12-19
Yeah, always more.
I did read that page and I think I got it set up for com1 as in that example.  I need to double check my bios settings to make sure that is the port that is set.
I've never played with serial port in Linux yet, but have a lot of experience with this stuff in Windows, so hopefully not too strange!

Tom


> **OffAxis said:**
> 

There's a section in this document that details how to disable it:
[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

---

### Post by teet on 2007-12-19
Just FYI...

I have that same serial ir blaster and I got it working in gutsy.  The lirc_serial module in the lirc 0.8.2 packages that comes with gutsy are busted and don't work.  That's why you have to install the lirc 0.8.3 pre version.

Hopefully mythbuntu will have a 1-click setup for this IR blaster in hardy.

-teet

---

### Post by foxspam on 2007-12-19
Mmm, how I love ubuntu! Long live canonical :D

Cally Leeming

---

### Post by tegwilym on 2007-12-19
Ignore....where is the delete?

---

### Post by tegwilym on 2007-12-19
Darn.  I get a Bad Gateway error on the first part with the wget.  

--19:01:24--  [http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb](http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb)
           => `lirc_0.8.3~pre1-0ubuntu1_i386.deb'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 502 Bad Gateway
19:01:24 ERROR 502: Bad Gateway.


Know of another place to get the file?  I'm looking around.....

Tom

---

### Post by tegwilym on 2007-12-19
> **tegwilym said:**
> Darn.  I get a Bad Gateway error on the first part with the wget.  


Tom


...found it. Server down for maint.  I'll try again later.

---

### Post by tegwilym on 2007-12-20
Ok, I got the lirc 0.8.3 installed and running.  I think I have a serial port issue now since I don't get a signal out of the emitter.

I found a neat trick on another site that you can check the emitter.  Just point a digital camera at the IR emitter and look at the digital viewfinder.  You'll see it blink when it works.  Neat!

So, I'm getting nothing out of the IR emitter at the end of the serial cable.  Checked the com ports in BIOS and left port 1 turned on, and disabled com 2 for starters.

I only have one serial 9 pin on the back of this computer so there isn't much to screw up there - other than the configuration.

Hmmm....reading more...

Tom

---

### Post by teet on 2007-12-20
when compiling the lirc 0.8.3 module, I had to choose "software generated signal" (or something like that) in the ./configure.  I also remember that this thing is NOT "igor somethings variant".

Check out this thread:  [http://ubuntuforums.org/showthread.php?t=592415](http://ubuntuforums.org/showthread.php?t=592415)

sorry for being so cryptic...I'm away from my desktop right now (at the folks house for christmas).

-teet

---

### Post by OffAxis on 2007-12-20
I believe that's the 
**Home-brew (16x50 UART compatible serial port)** option, which is right above the
**Home-brew (Igor Cesko's variant) (16x50 UART compatible serial port)** option in the list.

There's one further down the list that may work as well, the 
**Irman / UIR** option.

```
sudo dpkg-reconfigure lirc
```
to view or change your selection.

---

### Post by tegwilym on 2007-12-20
> **OffAxis said:**
> 
**irsend SEND_ONCE [name of your remote device] 3**

will attempt to send the signal for channel 3 to your remote device.

those two commands interact with LIRC directly. Mythtv will use a script to run the SEND_ONCE command (and a pause in between number presses if necessary), and a press of the 'ENTER' key if necessary.
There are two well used and well documented ones in the 'External Channel Changing' link in my previous post, as well as the necessary permissions for the file, so I'll just direct you there.

A little confused about this part.  I used the D770 settings and I'm not getting the nagging message that "lirc not set up" anymore.  I also can start and stop the service ok.  On the SEND_ONCE test, what do I use for the [name] part?  I looked in the file and saw different names for each remote feature.....vcr1, vcr1, sat...etc.  Is that what I put in there?

I think I need to back up a little bit and confirm I got the serial port working at least and getting something out of the IR emitter, then move forward with the configuration of the lirc.  

...Unbutu is getting a lot easier all the time, but I think there is still a ways to go with the serial port setup.  

Tom

---

### Post by tegwilym on 2007-12-20
Ok one more question...

On the serial setup, I try the procedure that is mentioned here - [https://help.ubuntu.com/community/Install_Lirc_Gutsy#head-11f21cd416f984d51b87dc9dca2c21b890bf82d5](https://help.ubuntu.com/community/Install_Lirc_Gutsy#head-11f21cd416f984d51b87dc9dca2c21b890bf82d5)


But find that the part about setting up the serial port settings is confusing.



         [B]Choose manual
                Modify /var/lib/setserial/autoserial.conf
                * *[COLOR="Red"] Add (or modify if its there already) (switch to ttyS1 if your using that instead)[/COLOR]*
          
                           /dev/ttyS0 uart none[/B]

This part is confusing.  Do I replace the line that starts with /dev/ttyS0 with the line above?  Or just do the 'uart none'?  

How about a sample of the lirc file that is configured with Com port 1 that shows the setup that works?

Ok, enough for now.  I'll keep playing with this.  I'm sure I'm making this more complicated than I should.  :)

T.

---

### Post by OffAxis on 2007-12-20
> I used the D770 settings and I'm not getting the nagging message that "lirc not set up" anymore.
The message stops with the creation of the lircd.conf file.


> This part is confusing. Do I replace the line that starts with /dev/ttyS0 with the line above? Or just do the 'uart none'?

Either or.
I think it comes off as confusing because the the path MAY have been auto-detected depending on when you installed setserial and if you had it enabled in the bios.

Anyway, I'd just comment it out and add the new line. Something like:

```
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
#/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
#/dev/ttyS1 uart 16550A port 0x02f8 irq 3 baud_base 115200 spd_normal skip_test
**/dev/ttyS0 uart none**

```

---

### Post by tegwilym on 2007-12-20
> **OffAxis said:**
> The message stops with the creation of the lircd.conf file.



Either or.
I think it comes off as confusing because the the path MAY have been auto-detected depending on when you installed setserial and if you had it enabled in the bios.

Anyway, I'd just comment it out and add the new line. Something like:

```
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you 
do not do this, this file may be overwritten automatically the next 
time you upgrade the
# package.
#
#/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
#/dev/ttyS1 uart 16550A port 0x02f8 irq 3 baud_base 115200 spd_normal skip_test
**/dev/ttyS0 uart none**

```

Ok, I did have that set right then, but no IR still.

I was looking at another site and found this - 
```
setserial /dev/ttyS2 -v autoconfig
If the resulting message shows a uart type such as 16550A, then you're OK. If instead it shows "unknown" for the uart type, then there is supposedly no serial port at all at that I/O address. Some cheap serial ports don't identify themselves correctly so if you see "unknown" you still might have a serial port there.
```


I got "unknown" when I tried this on my computer.
Won't the port get set properly if I just do the "automatic" option rather than "manual"?

---

### Post by OffAxis on 2007-12-20
back to the lirc part...
> I looked in the file and saw different names for each remote feature.....vcr1, vcr1, sat...etc. Is that what I put in there?
not quite.

try 
```
irsend LIST "" ""
```

This will come back with a list of the valid remotes from lircd.conf.

Take that name and feed it back into irsend (exactly as it appears in the file), replacing the first ""

```
irsend LIST D770 ""
```

and that will list all the codes & keys mapped for that device (once again from the lircd.conf, this time from the remote-specific part).

So you take the remote name, a valid key, and run those through irsend SEND_ONCE
something like
```
irsend SEND_ONCE D770 5
```
which will use the D770 device's remote section to send the code for 5.

Running all this stuff through irsend just makes sure that lirc understands what you think it understands.

---

### Post by OffAxis on 2007-12-20
Did you have the port enabled in the bios when you installed 'setserial'?

It should have generated a path in the /var/lib/setserial/autoserial.conf file.

> Won't the port get set properly if I just do the "automatic" option rather than "manual"?
I have no idea.
Worth a shot, eh?:)

> 
I was looking at another site and found this -
Code:

setserial /dev/ttyS2 -v autoconfig
If the resulting message shows a uart type such as 16550A, then you're OK. If instead it shows "unknown" for the uart type, then there is supposedly no serial port at all at that I/O address. Some cheap serial ports don't identify themselves correctly so if you see "unknown" you still might have a serial port there.


I got "unknown" when I tried this on my computer.

Did you modify the device path to match yours?

---

### Post by tegwilym on 2007-12-20
> **OffAxis said:**
> back to the lirc part...

rsend LIST "" ""

This will come back with a list of the valid remotes from lircd.conf.

```
irsend SEND_ONCE D770 5
```
which will use the D770 device's remote section to send the code for 5.

Running all this stuff through irsend just makes sure that lirc understands what you think it understands.

In my case I just get
```
irsend:could not connect to socket
irsend:Connection refused
```

I put the D770 code into the lircd.conf file.  But nothing shows up when I do the irsend.  So I can't even take the next step to the irsend LIST D770 "".

I still think I have a serial port problem that I need to get through first. 

Tom

---

### Post by OffAxis on 2007-12-20
> I still think I have a serial port problem that I need to get through first. 
definitely.

what does 
```
 dmesg | grep -i lirc 
```
give you?

---

### Post by tegwilym on 2007-12-20
I'm actually doing this on my work machine right now, but when I did it on my Mythtv box last night I DID get something in there about the ports.  Nothing on this computer here, I screwed something up.  I'll just have to try this again when I get home  tonight.  I'm getting a few more ideas to try at least. 

Tom

---

### Post by tegwilym on 2007-12-20
> **OffAxis said:**
> definitely.

what does 
```
 dmesg | grep -i lirc 
```
give you?

Getting closer....slightly.
I get:  

```


[ 2512.557930] lirc_dev: IR Remote Control driver registered, at major 61 
[ 2512.581108] lirc_serial: port 03f8 already in use
[ 2512.581115] lirc_serial: use 'setserial /dev/ttySX uart none'
[ 2512.581117] lirc_serial: or compile the serial port driver as module and
[ 2512.581119] lirc_serial: make sure this module is loaded first

```

Also, looking closer at the list when I run the 
dpkg-reconfigure lirc 
I did find the "Home-brew (16x50 UART compatible serial port) "
and set it to that.  But nothing changes in the lircd.conf file.   I did set it to chmod 777 to totally open it for read/write.

So, I'm closer but still really stuck on on irsend command where the list should show up.  I just need a name for that next, but confused and stuck.

Tom

---

### Post by tegwilym on 2007-12-21
Arrrggh!!! So close.....


I was messing around with the serial port again last night.  I made some progress and figured out from reading that I need to basically grab the port before the Kernel gets to it.  I got it working so I finally got a response from the ***irsend LIST "" "",*** the ***irw*** command worked since the cursor went away, and everything was responding as it should.

I tried to change channels with the MythTV, but it didn't work.  I went to try some other ideas, rebooted the machine......and never got it back to that point again.  :(

I know that MythTV is a pain to set up, but I think I'm about 90% there.  I guess the box control thing is what they meant about the pain of setup?  
Learning a lot, but still working on this.

Tom

---

### Post by OffAxis on 2007-12-24
did you overwrite the **/etc/serial.conf** file with the **/var/lib/setserial/autoserial.conf** file?

**setserial **should be set to 'Manual'

**/etc/serial.conf** should have a line that looks like
```
/dev/ttyS0 uart none
```
with everything else commented out.

> I went to try some other ideas, rebooted the machine......and never got it back to that point again.
The configuration options for setserial can override your modifications, so if you messed with the config with
```
sudo dpkg-reconfigure setserial
```
it could have negated your modifications on reboot.


After getting setserial to Manual and the serial.conf file set run
```
dmesg | grep -i lirc 
```

Pre-reboot I got this
```

dmesg | grep -i lirc
[169758.152000] lirc_serial: port 03f8 already in use
[169758.152000] lirc_serial: use 'setserial /dev/ttySX uart none'
[169758.152000] lirc_serial: or compile the serial port driver as module and
[169758.152000] lirc_serial: make sure this module is loaded first

```
presumably because the kernel driver still had control of the serial port.

Post reboot I got this
```
 dmesg | grep -i lirc
[   35.516000] lirc_dev: IR Remote Control driver registered, at major 61
[   36.032000] lirc_serial: auto-detected active high receiver
[   36.032000] lirc_dev: lirc_register_plugin: sample_rate: 0
```

---

### Post by tegwilym on 2007-12-24
Got it working again, I had to manually set the modprobe and setserial to get it started again.
Anyway, even though everything appeared to work, I couldn't get anything working with the loopback connector.  

when I did the same thing on my other computer, the loopback connector would work and I'd see stuff going out and coming back.  So it seems that I may have a dead serial port on the computer possibly.  I tried getting it working with a USB to Serial cable, and when I did the loopback test, that would work just fine.  But nothing from the IR.

I posted another message thread about this, and found out from someone that the USB to serial won't work with this.  So, I'll have to figure out a USB to IR, try again with a serial card, another computer, or just wait until I get some kind of dedicated box for this (which is my plan), or finally just try to do directly from the serial to the data port on back of the DirecTV box.

confusing!

Tom

---

### Post by nomikal on 2008-04-15
Finally, I've had some success. I am able to turn off my set top box with the irsend -d /dev/lircd SEND_ONCE DCT700 power cmd. But when using the irw command I get no output...I'm using a comcast remote... 

Heres my lircd.conf file: 

```
# this config file was originally generated
# using lirc-0.6.6(serial) on Fri Mar 28 22:46:44 2003
# modified by hand on Sunday Jul 17 00:12:00 2005
#
# contributed by rob scullion
# based on the DCT2000 file contrib'd by shane bradley
#
# brand:                       Motorola
# model no. of remote control: ? - Comcast badged
# devices being controlled by this remote: DCT2524/1612
#
# Note: The "ON DEMAND" button on the Comcast
# badged remote just sends a "1" followed by
# an "ok/select" and is thus not included in
# this config file.
                                                                                    
begin remote
 name  DCT700
  bits             16
  flags SPACE_ENC|CONST_LENGTH
  eps              30
  aeps            100

  header         9036  4424
  one             556  2185
  zero            556  4424
  ptrail          556
  gap          100025
  toggle_bit        0
 

      begin codes
          power                    0x000000000000AFF9
          rew                      0x00000000000087F7
          play                     0x00000000000027FD
          ffwd                     0x00000000000047FB
          stop                     0x000000000000C7F3
          pause                    0x00000000000007FF
          rec                      0x00000000000073FC
          skipback                 0x000000000000C3F7
          mydvr                    0x00000000000043FF
          live                     0x00000000000083F0
          pageup                   0x000000000000A3F3
          pagedown                 0x00000000000023FB
          a_lock                   0x00000000000097F6
          b_day-                   0x00000000000063FD
          c_day+                   0x000000000000E3F5
          up                       0x000000000000D3F6
          down                     0x00000000000053FE
          left                     0x00000000000093F1
          right                    0x00000000000013F9
          ok/select                0x00000000000077F8
          guide                    0x000000000000F3F4
          info                     0x00000000000033FA
          menu                     0x00000000000067F9
          exit                     0x000000000000B7F4
          help                     0x000000000000B3F2
          last                     0x00000000000037FC
          vol+                     0x0000000000004FF3
          vol-                     0x0000000000008FFB
          mute                     0x0000000000000FF7
          fav                      0x00000000000057FA
          ch+                      0x0000000000002FF5
          ch-                      0x000000000000CFFD
          1                        0x0000000000007FF0
          2                        0x000000000000BFF8
          3                        0x0000000000003FF4
          4                        0x000000000000DFFC
          5                        0x0000000000005FF2
          6                        0x0000000000009FFA
          7                        0x0000000000001FF6
          8                        0x000000000000EFFE
          9                        0x0000000000006FF1
          0                        0x000000000000FFFF
          tv/vcr_input             0x000000000000D7F2
          hdzoom_enter             0x000000000000FDFC
          pnp-swap                 0x0000000000003BF2
      end codes
 
end remote
```


And my hardware.conf file

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

Running ubuntu 7.10 gutsy using an irblaster from irblaster.info connected to COM1...

---

