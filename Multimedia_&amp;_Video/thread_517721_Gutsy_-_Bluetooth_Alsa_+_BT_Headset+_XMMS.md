---
title: "Gutsy - Bluetooth Alsa + BT Headset+ XMMS"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by ULTRAChihuahua on 2007-08-04
I just upgraded my distro to Gutsy, i had Feisty previously.  
Using Synaptic i've installed the following packages:
-bluetooth-alsa
-xmms

I have the 590Plantronics BT Headset,  
For starters, I can't seem to pair up my headset.


/etc/bluetooth/hcid.conf
```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	#passkey "1234";

	# PIN helper
	# pin_helper /tmp/bluepin.sh;
}	

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

device 00:12:A1:61:43:BC {
	name "Targus BT Laser Notebook Mouse"
	aut enable;
	encrypt enable;

device 00:0D:3C:40:75:85 {
     	name "VKB Keyboard";
     	auth enable;
  	encrypt enable;
}
device 00:03:89:94:80:8A {
     	name "590Plantronics";
     	auth enable;
}

```

My BT Mouse pairs up fine, as well as my BT Keyboard

I have tried the following to pair up my BT Headset


```

console:~$ sudo hcitool scan
Scanning ...
        00:03:89:94:80:8A       590Plantronics
console:~$ sudo hcitool cc  00:03:89:94:80:8A 
console:~$ sudo hcitool con
Connections:
console:~$ 

```



The following are my .asoundrc and .a2dprc files
I know they're not necessary yet, until i pair up my Headset but i might as will put down all my configurations


~/.a2dprc
```

[a2dpd]
#
# Rate
# use 32000 if your headset seems to not support 44100 (HP/Logitech works well at 44100, Sonorix at 32000)
# However, 44100 is mandatory
# If using SCO, then 8000hz is the value needed.
# if the plugin do not give the 8000hz stream, then the conversion will be done by the daemon
# Until we use a real resample library, we won't get a good quality, this is prototype software.
#
rate=44100
#rate=32000

# buggy if I remember well
#channels=2

#
# plugin-rate default is the rate used between the plugin and the daemon
# if this value is not 0 then alsa will convert all stream to the specified rate and then send it to the daemon
# if this value is 0, then alsa will do no conversion at all, the daemon will do it's own resampling.
# This "features" is disabled because of the crappy quality of the daemon resampler
# For example, to test a2dpd resampling from 32000 to 44100 use plugin-rate=32000 and rate=44100
#plugin-rate=32000

# Allows to specify the sbc bitpool, this can help reducing bandwith
# 8 Allows to run on a 115200 bauds with corresponding quality ;)
# 64 needs USB or 921600 bauds
# Recommended value from Bluetooth spec. is 53
sbcbitpool=32

# flags that will later be combinable
# 1: display bandwith each seconds.
# 3: current state
flags=0

# Recommended
enablereversestereo=1

# Automatically connect to selected headset if a stream if started
# not recommended if running on battery ;)
enableautoconnect=1

# Automatically disconnect after a timeout (seconds)
timeout=20

#
# AVRCP Commands to run
# If these entries are emptied, then some keyboard entry will be sent to /dev/uinput
#
cmdplay=xmms --play
cmdpause=xmms --pause
cmdprev=xmms --rew
cmdnext=xmms --fwd
cmdnew=xmms --play
cmdstop=xmms --stop
#cmdplay=dcop amarok player play
#cmdpause=dcop amarok player pause
#cmdprev=dcop amarok player prev
#cmdnext=dcop amarok player next
#cmdnew=dcop amarok player play
#cmdstop=dcop amarok player stop

# Put to 0 to ignore AVRCP (if your computer freezes when commands are received)
enableavrcp=1

#
# Audio routing
#
# If set to 1 (at a2dp startup only) a2dp will reread configuration file
# for audio routing changes each second
# This is now deprecated and should not be used, moreover, if the address is changed using dbus
# or a2dpd_ctl, then the file is reread and the change is lost...
enablerereadconfig=0

# Display debug traces or not
enabledebug=1

# Redirect stdout to this file
#logfile=/dev/null

# Poll stdin for control commands ('c'onnect/'s'tart/'p'ause/'d'isconnect/'a'utoconnect)
# Use a2dpd_ctl instead
enablestdin=0

# 0 => Bluetooth A2DP Sink
# 1 => Alsa
enableredirectalsa=0

# Your bluetooth headset address
address=00:03:89:94:80:8A

# Address of your alsa output (default : plughw:0,0) you have to know what to do
alsaoutput=


```

~/.asoundrc
```

pcm.a2dpd {
        type a2dpd
}

```


Can someone help me get this configuration going please?
Thank you

---

### Post by wieman01 on 2007-08-07
I had an issue on Kubuntu Feisty as well. This is how I was able to solve it:

[http://ubuntuforums.org/showthread.php?t=486087]("http://ubuntuforums.org/showthread.php?t=486087")

No idea if it helps but we can continue from there.

---

### Post by ULTRAChihuahua on 2007-11-11
Got it working

i used this tutorial

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

and it is working like a charm.  Except for the fact that my Bluetooth Mouse makes 
the audio sound choppy.  However when i turn it off everything is fine and sound is crystal clear.  

i tried using XMMS and I switched to Beep Media Player after XMMS did not stream any sound to my Plantronics 590 headset.  

BTW: i am running Gutsy

:)

---

