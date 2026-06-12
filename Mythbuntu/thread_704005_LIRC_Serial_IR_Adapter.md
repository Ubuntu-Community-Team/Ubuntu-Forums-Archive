---
title: "LIRC Serial IR Adapter"
date: 2008-02-21
forum: Mythbuntu
---

### Post by nasha on 2008-02-21
Hey Guys,
I recently abandoned getting my Dual Digital 4 remote to work, and it was suggested that i build one of these:
[http://www.linuxjournal.com/article/8811](http://www.linuxjournal.com/article/8811)
Has anyone got one of these working on MythBuntu? (Supplied instructions are Fedora based). If so, how?
Any help would be greatly appreciated :)

Regards,
Nash

---

### Post by ian dobson on 2008-02-21
Hi,

In the installation PDF that you can download from mythbuntu there is a section about "homebrew" IR.

Basicely what you have to do is run setserial to disable kernel support for the serial port your using and tell LIRC to use this port.

I have a homebrew IR receiver/PVR 150 remote running on my frontend. It took afew hours to get it up and running.

Regards
Ian Dobson

---

### Post by nasha on 2008-02-22
Thanks for that. I'll take a look at the pdf :)

---

### Post by Flecko on 2008-02-22
I had a bunch of problems with my 'homebrew' serial IR adapter. So much so, that I scrapped it and just bought a streamzap USB remote. 

The serial IR adapter required tricky setup(took me hours to get it working) where the USB one worked right from install. The serial IR adapter would stop working after random periods of time and wouldn't work again until a hard reboot was performed, where the USB receiver works all the time.

This may have just been my personal experience as I'm sure a lot of people are using their serial IR adapters just fine, but I would recommend just spending the extra 20 or so dollars to get a decent receiver and remote.

Best of luck!
-Flecko

---

### Post by Nikas on 2008-02-22
My serial IR adapter works great. Really cheap to make your own. I use LIRC 0.8.3pre1.

MythBuntu comes with LIRC 0.8.2 and the serial support are broken in that version.

```
sudo wget http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb
sudo dpkg -i lirc_0.8.3~pre1-0ubuntu1_i386.deb
```

Then, i used setserial under "Disable kernel serial support" here:
[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

After that i manually modified my hardware.conf. I can post it when i have my frontend machine up and running. Past midnight here in Sweden now. :)

---

### Post by nasha on 2008-02-22
Thanks for the input guys, really appreciate it. 
I've heard mixed reports about the serial adapter, and replies clearly show mixed opinions :) 
I'll be attempting to get it going tonight after work, will report back here with success or failure.
Nikas: Is it really necessary to downgrade the version of lirc?

---

### Post by Nikas on 2008-02-23
> **nasha said:**
> Thanks for the input guys, really appreciate it. 
I've heard mixed reports about the serial adapter, and replies clearly show mixed opinions :) 
I'll be attempting to get it going tonight after work, will report back here with success or failure.
Nikas: Is it really necessary to downgrade the version of lirc?

My friend uses the same adapter and settings. Works great.

Downgrade? No. Just don't use 0.8.2.
I upgraded from 0.8.2 to 0.8.3.

---

### Post by nasha on 2008-02-23
Well i successfully got myself completely lost attempting this. Couldnt find a sufficient guide, so i had to pick bits an pieces from everywhere and im 100% positive something was left out.
I've disabled the serial from kernel usage, as per instructions in the MythBuntu documentation. Is there some way i can test it is now working? I've tried cat /dev/inputX for all available inputs (as suggested by one of the guies), and nothing...
From there i just edit the lirc .conf files, and im away?

---

### Post by Nikas on 2008-02-23
What do you have in your hardware.conf?

Heres mine:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"

# Arguments which will be used when launching lircd

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead

# Default configuration files for your hardware if any
DRIVER="default"
MODULES="lirc_dev lirc_serial"
DEVICE="/dev/lirc0"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd.conf"
LIRCMD_CONF=""

```

Restart lirc after modification: sudo /etc/init.d/lirc restart
If you want to see lirc in the foreground you can start lirc with sudo lircd -n instead to see what lirc complains about. :) Do sudo /etc/init.d/lirc stop first.

You can make your own lircd.conf with irrecord -d /dev/lirc0 lircd.conf (creates a new lircd.conf, modify as you wish)
If the program reacts to your remote you know that the receiver and lircd works.

Don't forget to upgrade lirc to at least 0.8.3.

---

### Post by nasha on 2008-02-23
My hardware.conf was just a template one, i wasnt sure what values to use for driver, modules & device. I'll fill in mine like yours.
I already have a lircd.conf for my remote, so that's handy :)
I'll upgrade lirc, and edit conf files tomorrow (3am here), and hopefully all goes well :)

---

### Post by Nikas on 2008-02-23
> **nasha said:**
> My hardware.conf was just a template one, i wasnt sure what values to use for driver, modules & device. I'll fill in mine like yours.
I already have a lircd.conf for my remote, so that's handy :)
I'll upgrade lirc, and edit conf files tomorrow (3am here), and hopefully all goes well :)

Okey. 5 PM here. ;-) Good luck!

You can try your remote with irw :) Just run the command and try your remote after changing the settings.
My lircd.conf for my remote was all wrong. hehe
Put your lircd.conf in /etc/lirc/
I had to do that even if i specified /etc/lirc.conf in my hardware.conf..

---

### Post by nasha on 2008-02-23
Upgraded to your same version of lirc, copied my hardware.conf lircd.conf andf lircrc, and restarted lirc.

When i restart lirc, it whinges about my hardware.conf. If i sudo lircd -n this is what follows:

[HTML]"error in configfile line 3"
"reading of config file failed"[/HTML]

Here's my hardware.conf:

[HTML]# /etc/lirc/hardware.conf
 #
 # Arguments which will be used when launching lircd
 LIRCD_ARGS=""
 
 #Don't start lircmd even if there seems to be a good config file
 START_LIRCMD=false
 
 #Try to load appropriate kernel modules
 LOAD_MODULES=true
 
 # Run "lircd --driver=help" for a list of supported drivers.
 # If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
 # automatically used instead
 
 DRIVER="default"
 DEVICE="/dev/lirc0"
 MODULES="lirc_dev lirc_serial"

 # Default configuration files for your hardware if any
 LIRCD_CONF="/etc/lirc/lircd.conf"
 LIRCMD_CONF=""[/HTML]

I can't help but feel im so close, yet so far :s

---

### Post by prop99 on 2008-02-24
I tried the same upgrade and config. 

For me, I think the problem is that I use ttyS1 (com2) for the remote. 

The "setserial" frees this port but I get a message that lirc tries to use ttyS0 - which it can't. 

So, please, where do you put the serial port id in? I guess it should be done in one of the config files... 

[Otherwise I could, of course, change the port identities in bios but it would be nice to know how to do it right...]

  //jan e

ps. I just tried LIRCD_ARGS = "-d /dev/ttyS1" but there was no change - it still tries to access port 0x3f8

---

### Post by nasha on 2008-02-24
I'm pretty sure this is what your after?

[HTML]Create a file entitled /etc/modprobe.d/lirc with these contents:

      #COM1 equivalent, /dev/ttyS0
      options lirc_serial irq=4 io=0x3f8
      #COM2 equivalent, /dev/ttyS1
      #options lirc_serial irq=3 io=0x2f8

Uncomment the appropriate line to represent serial port you have connected your transmitter. [/HTML]

From: [https://help.ubuntu.com/community/InstallLirc/Gutsy#head-96b7b2b16ed15b24db33dfc67f9a5adbcec91870](https://help.ubuntu.com/community/InstallLirc/Gutsy#head-96b7b2b16ed15b24db33dfc67f9a5adbcec91870)

From memory this is the only location the the specific serial port is mentioned... This is my first time through this, so i might not be correct. As you can see, ive yet to get min working :P

---

### Post by prop99 on 2008-02-24
Thanks :) 

I did that change before but it seems it was removed, probably in the upgrade process. 

Anyway, now I don't get any error message when i restart lircd but `irw' just returns directly. So there seems to be more to this...

  //jan e

---

### Post by nasha on 2008-02-24
No probs. I dont doubt there's more to it at all. There's always been something more setting up these damn remotes lol. I'm on my backup path already, and this doesnt look like im going to be able to get it going either :(
Wish i could help, but im just as stuck as you unfortunately!

---

### Post by Nikas on 2008-02-24
Reboot and post your dmesg | grep -i lirc

Try that irrecord i was talking about earlier too...

---

### Post by prop99 on 2008-02-24
Well, I'll let you know if I happen to make any progress. But right now I think I've had enough. There are better ways to spend a sunday :)

  //jan e

---

### Post by nasha on 2008-02-24
dmesg | grep -i lirc returns nothing, so that means lirc isnt running. When i try to start lirc:
```
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf:15:
: not foundardware.conf: 19:
' not supported.emon: lircdDriver `default
Supported drivers:
       /*output omitted*/
: not found/lirc: 144: false
```

Ill look into irrecord now

---

### Post by Nikas on 2008-02-24
How did you upgrade lirc?

---

### Post by nasha on 2008-02-24
Using the exact same command you specified earlier, wget to some address, and then dpkg to install.
irrecord says:
```
irrecord: error in configfile line 3
irrecord: file "lircd.conf" does not contain valid data
```

---

### Post by Nikas on 2008-02-24
> **nasha said:**
> Using the exact same command you specified earlier, wget to some address, and then dpkg to install.
irrecord says:
```
irrecord: error in configfile line 3
irrecord: file "lircd.conf" does not contain valid data
```

Check line 3 in your /etc/lirc/lircd.conf then. :)

---

### Post by nasha on 2008-02-24
```
# brand:  DViCO FusionHDTV DVB-T Dual Digital
 # model no. of remote control: Fusion MCE
 # devices being controlled by this remote:
 #
   
   begin remote
   
     name  DViCO_Dual_Digital
     bits           16
     eps            30
     aeps          100
   
     one             0     0
     zero            0     0
     pre_data_bits   16
     pre_data       0x1
     gap            251756
     toggle_bit      0   
```

I did, but i don't see anything wrong there?

---

### Post by Nikas on 2008-02-24
> **nasha said:**
> ```
begin remote
   
     name  DViCO_Dual_Digital
     bits           16
     eps            30
     aeps          100
   
     one             0     0
     zero            0     0
     pre_data_bits   16
     pre_data       0x1
     gap            251756
     toggle_bit      0   
```

I did, but i don't see anything wrong there?

Try to remove the lines like i did in the quote and try irrecord again to see if the line number changes.

---

### Post by nasha on 2008-02-24
No change :/

---

### Post by Nikas on 2008-02-24
Your hardware.conf does not look like mine.
Take a look again:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"

# Arguments which will be used when launching lircd

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead

# Default configuration files for your hardware if any
DRIVER="default"
MODULES="lirc_dev lirc_serial"
DEVICE="/dev/lirc0"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd.conf"
LIRCMD_CONF=""
```

Remove the line LIRCD_ARGS="" in your file.
Restart lirc and try irw.

---

### Post by nasha on 2008-02-24
Starting lirc is almost the same as before. Last line is no longer there

```
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf:15:
: not foundardware.conf: 19:
' not supported.emon: lircdDriver `default
Supported drivers:
       /*output omitted*/

```

irrecord still reports error in configfile line 3

/dev/lirc0 doesnt exist, just decided to check. I imagine this would be causing a problem...

---

### Post by Nikas on 2008-02-24
How did you edit your hardware.conf and how did you paste my settings?

Remove your hardware.conf and create a new one with sudo nano hardware.conf and paste my settings exit (CTRL+X) and save changes (y ENTER). Then restart lirc.

---

### Post by nasha on 2008-02-24
You make a valid point. Edited on a windows machine. Remove all the extra crap that microsoft throws in, and lirc starts!
irrecord starts and runs also, but doesnt get any input from the remote...

---

### Post by Nikas on 2008-02-24
> **nasha said:**
> You make a valid point. Edited on a windows machine. Remove all the extra crap that microsoft throws in, and lirc starts!
irrecord starts and runs also, but doesnt get any input from the remote...

You'll get like... windows format line endings.. and linux does not like that. :)

How about irw?

---

### Post by nasha on 2008-02-24
Yes, learnt that the hard way lol
nothing from irw either :(

---

### Post by Nikas on 2008-02-24
> **nasha said:**
> Yes, learnt that the hard way lol
nothing from irw either :(

irw only returns stuff if the lircd.conf works as it should..

Try
irrecord -d /dev/lirc0 test.conf to create a new file and follow the instructions. Try irrecord -d /dev/lirc/0 lircd.conf if the first one fails.
Are you sure your receiver works? I tried mine on a windows machine first. :)

---

### Post by nasha on 2008-02-24
When at the recording stage in irw, it recieves nothing. Im only assuming its working, electrically theres no reason why it shouldnt be. 
How do i test it on a windows machine?

---

### Post by Nikas on 2008-02-24
I used WinLIRC.
[http://winlirc.sourceforge.net/](http://winlirc.sourceforge.net/)

---

### Post by nasha on 2008-02-24
Gave winlirc a quick go, going to have to look more into getting that going than i'd hoped. Motivation level is slowly diminishing though :/
This is the second remote thats been painful to get going

---

### Post by Nikas on 2008-02-24
> **nasha said:**
> Gave winlirc a quick go, going to have to look more into getting that going than i'd hoped. Motivation level is slowly diminishing though :/
This is the second remote thats been painful to get going

Don't give up! :)
I gave WinLIRC like 5 mins to get it going.

---

### Post by nasha on 2008-02-24
The problem is, when it doesnt work, i dont know if im doing something wrong, or whether its all right but unit is dead. Its a never ending circle lol

---

### Post by prop99 on 2008-02-24
I have made some changes and some progress. I'm not there yet, but...

*  chmod /dev/lirc0 so all could read/write it

*  remove the args in LIRCD_ARGS="-d /dev/ttyS1"

And now lircd starts ok, irw runs (without reading anything - but it doesn't exit immediately as before)

The ir recording does not work. Nothing seems to be received by the sensor. I think I have the wrong baud rate (or handshake params or..) because the sensor works in geexbox. I'll try to find some info on what you could put in the modprobe.d/lirc file.

So I have to dig deeper... I'll post any progress.

Thanks for all help!

  //j

---

### Post by nasha on 2008-02-25
Sounds like your at about the stage im at. Lirc and irw are working fine, but getting no input. Any progress you make i would be keen to hear, as it may indeed help me :)

---

### Post by Nikas on 2008-02-26
Okay. Strange.
I just got it working on another computer with a new home made receiver. I only edited lircd.conf, hardware.conf and followed the instructions for setserial. I then used my own lircrc. Rebooted and it worked.

I did NOT toch /etc/modprobe.d/lirc...
Clean installed mashine.

---

### Post by nasha on 2008-02-26
Just attempting a clean install now on another machine, in a hope that it would make a difference... I'll give it a shot NOT editing the /etc/modprobe.d/lirc and hope it works :D
First i need to work out why the LiveCD wont boot properly :/

---

### Post by nasha on 2008-02-26
My hardware must be faulty... You just removed another step for getting it up and running, and still it's not working.

Carried out as follows:
```
run setserial > edit autoserial.conf > copy to /etc/serial.conf
update lirc
edit configs > hardware.conf & lircd.conf
```

Im going to have to make friends with someone nearby that has a working serial adapter setup, and just switch modules to confirm (or deny) working order...

Edit: Going to build another one to try and eliminate the faulty hardware. Will report back

---

### Post by nasha on 2008-02-27
Hardware isn't the issue... Just built another receiver and no change... I really wish i knew wtf is going on here...

Edit: Also just got input from the remote using WinLirc under XP... Linux is just hating me now
Wouldn't care to VNC me Nikas and see if you can find anything the matter??

---

### Post by apparle on 2008-02-27
Is there a good how to for installing linux.

I have the serial port hardware with TSOP1738 ready.

What to do,
Explain in step by step
Please

---

### Post by nasha on 2008-02-27
I suggest you start a new thread, with a bit more information so that people can actually help you

---

### Post by prop99 on 2008-02-27
nasha: 
Do you run on a notebook? 
The serial port could have too low DTR voltage for your receiver.

Just something I read somewhere...

  //jan e

---

### Post by nasha on 2008-02-27
Hi Jan,
Thankfully i've managed to get mine up and running, thanks to much help from Nikas. Turns out it was a dodgy hardware.conf causing the issues

---

