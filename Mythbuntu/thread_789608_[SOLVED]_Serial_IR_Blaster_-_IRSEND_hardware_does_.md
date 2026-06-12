---
title: "[SOLVED] Serial IR Blaster - IRSEND hardware does not support sending"
date: 2008-05-10
forum: Mythbuntu
---

### Post by Don Giovanni on 2008-05-10
Running Hardy with hauppauge pvr 350 and using a serial IR blaster.
Using dpkg-reconfigure lirc-modules-source to pick the serial ir blaster prevents my ir reciever from working all together so i am setting up the ir blaster manually.

I followed section 12.2.1 of the Mythbunu installation manual [http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf)

when I try irsend I get this error:```

irsend send_once SRC-200A_3 select
irsend: command failed: send_once SRC-200A_3 select
irsend: hardware does not support sending

```

My /etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="SRC-200A_3"
TRANSMITTER_MODULES="lirc_serial lirc_dev"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="mts/mtstvlirc.conf"
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

My /etc/lirc/lircd.conf
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

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
#Configuration for the Serial IR transmitter:
include /usr/share/lirc/transmitters/mts/mtstvlirc.conf
```

My ir blaster config /usr/share/lirc/transmitters/mts/mtstvlirc.conf:
```
#
# this config file was automatically generated
# using WinLIRC 0.6.5 (LIRC 0.6.1pre3) on Mon May 09 10:49:02 2005
#
# contributed by toonces
#
# brand: MTS TV or Quest Choice TV
# model: NextLevel or Motorolla RG2200            
# supported devices: RG2000 RG2200 RG2400
#
# Remote is SRC-200A (should work with other similar models)
#
# Programmed using factory defaults (will work without setting gateway id):
# Infared, stream 3
#

begin remote

  name  SRC-200A_3
  bits            8
  flags SPACE_ENC
  eps            25
  aeps          100

  header       5057  2889
  one          1065   902
  zero         1065  2889
  ptrail       1065
  post_data_bits  8
  post_data      0xFF
  gap          46655
  toggle_bit      0


      begin codes
          select                   0x00000000000000CC
          1                        0x000000000000000C
          2                        0x0000000000000074
          3                        0x00000000000000B4
          4                        0x0000000000000014
          5                        0x0000000000000064
          6                        0x0000000000000024
          7                        0x00000000000000AC
          8                        0x000000000000006C
          9                        0x000000000000008C
          0                        0x00000000000000D8
          chan_up                  0x000000000000002C
          chan_down                0x00000000000000F4
          b                        0x00000000000000A8
          exit                     0x00000000000000A4
          last_chan                0x00000000000000E4
          call_id                  0x00000000000000D4
      end codes

end remote
```

and lastly /etc/modprobe.d/lirc edited as suggested in the manual:
```
#COM1 equivalent , /dev/ttyS0
options lirc \_serial irq=4 io=0x3f8 softcarrier=1
#COM1 equivalent , /dev/ttyS2
#options lirc \_serial irq=3 io=0x2f8
```

I have tried with and without the sofcarrier option. My remote still works fine, but i can't get the irblaster going.

I always get the irsend: command failed: send_once SRC-200A_3 select
irsend: hardware does not support sending error.

Any ideas?

---

### Post by gfowler on 2008-05-13
> **Don Giovanni said:**
> Running Hardy with hauppauge pvr 350 and using a serial IR blaster
I have tried with and without the sofcarrier option. My remote still works fine, but i can't get the irblaster going.

I always get the irsend: command failed: send_once SRC-200A_3 select
irsend: hardware does not support sending error.

Any ideas?

I have a PVR-350 and using the IR Blaster. Using the Mythbuntu Configure Centre and selecting either the WinTV remote or the Serial Dish but not both will work.  Selecting both causes neither of them to work.  I think I have read every configuration blog on Google to no avail.  Not a solution, here just more data.:(

Jerry

---

### Post by Don Giovanni on 2008-05-13
I'm sure this can can work.  I'm probably just missing something here...

I was doing more looking around and it looks like i may have had an error with my irsend command...however what I thought would fix it did not.
I wasn't specifying lirc1 device previously with the irsend
```

irsend -d /dev/lirc1 SEND_ONCE SRC-200A_3 select
irsend: could not connect to socket
irsend: Connection refused

```

However as you can see its still not transmitting :P

Hope someone can shed some insight.
Thanks!

---

### Post by gfowler on 2008-05-14
> **Don Giovanni said:**
> I'm sure this can can work.  I'm probably just missing something here...

I was doing more looking around and it looks like i may have had an error with my irsend command...however what I thought would fix it did not.
I wasn't specifying lirc1 device previously with the irsend
```

irsend -d /dev/lirc1 SEND_ONCE SRC-200A_3 select
irsend: could not connect to socket
irsend: Connection refused

```

However as you can see its still not transmitting :P

Hope someone can shed some insight.
Thanks!

Thumping around in the dark here I have more data.  If you select both a remote and a transmitter using the Mythbuntu Control Centre Infared Devices the /etc/lirc/hardware.conf will have empty _Device parameters.  I have no way of knowing if this is correct or not.  If you configure one or the other the _Device parameters have entries /dev/lirc0.  
If you configure both ls -l /dev/lirc* will show you two character devices: /dev/lirc0 and /dev/lirc1 with /dev/lircd daemon, which I think is correct.

With this configuration irw will give no results and irsend send_once REMOTE BUTTON will fail as not a transmitting device.

Now, if one manually enters a device in the /etc/lirc/hardware.conf for the transmitter and restarts the lirc daemon you can get the transmitter to work. Making the transmitter device /dev/lirc1 will result in another daemon /dev/lircd1 and you will need to specify the device in the irsend -d /dev/lircd1 REMOTE BUTTON sequence. 
At no time with both configured can I get any output from irw. Remove the transmitter from the config screen and let the script run and irw will give output. Put the transmitter back and nothing works, the hardware.conf _DEVICE parameters are erased.   Sooo, no letters left on my keyboard and less hair, here I sit :confused:

---

### Post by Don Giovanni on 2008-05-14
> **gfowler said:**
> Making the transmitter device /dev/lirc1 will result in another daemon /dev/lircd1 and you will need to specify the device in the irsend -d /dev/lircd1 REMOTE BUTTON sequence. 


DAMN silly me. I was typing irsend -d /dev/lirc1 SEND_ONCE SRC-200A_3 select


You are completely correct I should have been using
```
irsend -d /dev/**lircd1** SEND_ONCE SRC-200A_3 select
```

Just tried that and sure enough the set top box responds...So both remote and ir blaster are working :D
Now I just need to get a decent channel changing script and append it accordingly.

Thanks gfowler!


*update*
I used the script found here [http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl]("http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl")

and updated it for my remote (I have marked the segments I updated in bold, hopefully this will give others who were lost an idea of what needs to be changed).
```

#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "**SRC-200A_3**";

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend **-d /dev/lircd1** SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend **-d /dev/lircd1** SEND_ONCE $remote_name **select**");
```

Gfowler: Good luck in getting your remote and IR blaster going, you helped me find my own error!  I suggest to you not to bother using the Mythbuntu control center to set up both the PVR-350 remote and the IR blaster it just doesn't seem to work.  With the bug reports filed hopefully this will get worked out for others in the future.
I used the mythbuntu control center ONLY to set up my remote, and picked NONE for IR transmitter. I then then appended all files manually (i edited out a lot of sections from the auto generated lirc file for my remote since most of it wasn't needed).  Since your setup is so similar to mine if you use my config files as a guide you should be able to get your setup going.  Let us know how things work out for you.

---

### Post by gfowler on 2008-05-15
> **Don Giovanni said:**
> DAMN silly me. I was typing irsend -d /dev/lirc1 SEND_ONCE SRC-200A_3 select


You are completely correct I should have been using
```
irsend -d /dev/**lircd1** SEND_ONCE SRC-200A_3 select
```

Just tried that and sure enough the set top box responds...So both remote and ir blaster are working :D
Now I just need to get a decent channel changing script and append it accordingly.

Thanks gfowler!



Gfowler: Good luck in getting your remote and IR blaster going, you helped me find my own error!  I suggest to you not to bother using the Mythbuntu control center to set up both the PVR-350 remote and the IR blaster it just doesn't seem to work.  With the bug reports filed hopefully this will get worked out for others in the future.
I used the mythbuntu control center ONLY to set up my remote, and picked NONE for IR transmitter. I then then appended all files manually (i edited out a lot of sections from the auto generated lirc file for my remote since most of it wasn't needed).  Since your setup is so similar to mine if you use my config files as a guide you should be able to get your setup going.  Let us know how things work out for you.

Glad you figured out your issue, the ol' forest for the trees syndrome :)

Still no go here, I have discovered that my issue with the PVR-350 remote ceasing to work is associated with the second include statement in /etc/lircd.conf.  One works, two breaks the 350 remote.  I even went so far as to use your transmitter configuration, that's how I discovered the include issue.  At this point I am dumbfounded as to the underlying difficulty.  I see by comments that the include statement is a recent add to the new version.  I'll keep plodding on.  BTW, off topic but are you using your TV to display the monitor.  Couldn't get that to work either.

Thanks
Jerry

*** Update ***
Solved my issue.  The sequence of the include statements in /etc/lircd.conf made the difference.  The Mythbuntu Control Centre will put the remote include first, the IR Blaster (Dish) second.  For what ever reason the gremlins did NOT like this.  My fix was to put the transmitter (Dish) first and then the Hauppauge Remote second in /etc/lirc/lircd.conf.  Then I got codes from irw and could send codes from /dev/lircd1.  

Just a refresh I used the Install section 12.1 as Don Govanni suggested, and did the /etc/modprobe.d/lirc serial config iteration, plus disabled the kernal serial support via setserial.   Now if ET will just phone home!! Off to X out to TV trouble.  Hope this helps someone!!

Jerry

---

### Post by Bal_Zac on 2008-05-19
> **gfowler said:**
> 

*** Update ***
Solved my issue.  The sequence of the include statements in /etc/lircd.conf made the difference.  The Mythbuntu Control Centre will put the remote include first, the IR Blaster (Dish) second.  For what ever reason the gremlins did NOT like this.  My fix was to put the transmitter (Dish) first and then the Hauppauge Remote second in /etc/lirc/lircd.conf.  Then I got codes from irw and could send codes from /dev/lircd1. 



WOW THANKS.  I have a Hauppage 350 and  a homemade serial blaster which didn't like each other, did what you said and now they actually work.  Looks like a bug in the mythbuntu control center.

---

### Post by Cyber Source on 2008-10-09
Hello All,
  I have followed all the above, downloaded Mario's script and tried and old one I had for sending to my satellite box that was working before with an ledxmit lirc package that was around from before 1 install of lirc could do both sending and receiving. However, I can see the lights being lit as the digits are passed onto the receiver but it's not changing channels. I tried with the stock dish config that came with lirc and the one that I used to use but both just send red signals and dont change the receiver. If I send from command line, I see no complaints. Any thoughts anyone ??

---

### Post by derek1234 on 2008-12-03
I also had the "IRSEND hardware does not support sending" issue. It turned out that it was because I was trying to run the command as su. It took me a while to figure that out, so I thought I would post it in case anyone else has the issue.

---

### Post by dannyboy79 on 2009-06-16
> **Don Giovanni said:**
> DAMN silly me. I was typing irsend -d /dev/lirc1 SEND_ONCE SRC-200A_3 select


You are completely correct I should have been using
```
irsend -d /dev/**lircd1** SEND_ONCE SRC-200A_3 select
```

Just tried that and sure enough the set top box responds...So both remote and ir blaster are working :D
Now I just need to get a decent channel changing script and append it accordingly.

Thanks gfowler!


*update*
I used the script found here [http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl]("http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl")

and updated it for my remote (I have marked the segments I updated in bold, hopefully this will give others who were lost an idea of what needs to be changed).
```

#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "**SRC-200A_3**";

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend **-d /dev/lircd1** SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend **-d /dev/lircd1** SEND_ONCE $remote_name **select**");
```

Gfowler: Good luck in getting your remote and IR blaster going, you helped me find my own error!  I suggest to you not to bother using the Mythbuntu control center to set up both the PVR-350 remote and the IR blaster it just doesn't seem to work.  With the bug reports filed hopefully this will get worked out for others in the future.
I used the mythbuntu control center ONLY to set up my remote, and picked NONE for IR transmitter. I then then appended all files manually (i edited out a lot of sections from the auto generated lirc file for my remote since most of it wasn't needed).  Since your setup is so similar to mine if you use my config files as a guide you should be able to get your setup going.  Let us know how things work out for you.

this worked for me! great guide.

---

### Post by www.pantz.org on 2009-10-14
I had the same problem with Mythbuntu 8.04.1  What finally fixed my problem was changing the serial port settings in the BIOS.

 I started using irq=3 io=0x2f8 setting it to COM2. I kept getting the dreaded "IRSEND hardware does not support sending". I knew all config files where correct so I went into my BIOS and just turned on both COM ports and set their traditional io and irq ports and memory addresses. Which is COM2 irq=3 io=0x2f8 and COM1 irq=4 io=0x3f8. In my BIOS you can set any combo of irq and io port. 

I rebooted and everything came up and worked. So don't over look something as simple as changing the COM port settings or just turning every blasted port on in the BIOS. 

During my journey in doing this I learned a few things that I'll share.

1. Check that lirc_serial is getting set correctly with dmesg. It should say ***lirc_serial: auto-detected active high receiver*** and make sure it's not spitting out "use setserial ..." if so you have to use setserial to give the kernel control before the lirc_serial module is loaded. If it's giving the setserial message in dmesg after everything has loaded then just put at setserial line in at the very bottom of the following file  /etc/rcS.d/S30etc-setserial. My install was not setting the serial line correctly even though I had it correctly set with ***sudo dpkg-reconfigure setserial***. 

Set serial lines look like: ***setserial /dev/ttyS0 uart none***

2. Check that your serial port is turned on in your BIOS. Seriously. And if it is and the other port is turned off try turning that on. Also, try moving the memory addresses and irq's around if you can.

3. In /etc/lirc/lircd.conf swith the lines of the remotes and the blasters the blasters have to go first and the remotes have to go second. If that does not work or that's the way you had it reverse it. This is the thing fixed the orginal posters problem. Thanks [gfowler]("http://swiss.ubuntuforums.org/member.php?u=196644").

4. In the /etc/lirc/hardware.conf file try switching the REMOTE_DEVICE="/dev/lirc1" lines. Change the remote to /dev/lirc0 and the blaster to /dev/lirc1. Switch them back and forth to test. That is if your using a blaster and a remote.

---

### Post by Cyber Source on 2009-12-25
Hello all,
  In keeping with the open source ideology and in the hopes I can save someone some grief, I'm sending to this thread again, as I can see I sent to it back in 08. The broken state of lirc continues in Ubuntu's Karmic Koala, as I just found out the following system/script error.
Problem: Combined use of lirc for sending and receiving.
Solved / Solution: /etc/init.d/lirc is not correct. If lircd.conf and hardware.conf are properly configured for 2 devices, the init script creates the devices and symlinks correctly but the second symlink device points to the wrong socket, i.e., lircd1 points to /var/run/lirc/lircd and NOT /var/run/lirc/lircd1 like it should. Solution is to edit /etc/init.d/lirc on line 83 change this - "${TRANSMITTER_SOCKET}1" to this - "${TRANSMITTER_SOCKET}" and on line 131 change this - TRANSMITTER_SOCKET="/var/run/lirc/lircd" to this - TRANSMITTER_SOCKET="/var/run/lirc/lircd1". All should be well after that. Also, my lirc_serial module would NOT load if I had the option "softcarrier=1" in /etc/modprobe.d/lirc-serial.conf. After a "service lirc restart", both receiver and sender should be working.

---

### Post by pilesofspam on 2010-01-04
Confirmed.  Works well thank you.  Streamzap ir receiver, serial port ir blaster.

(edit) -sorry i forgot to say *what* worked- Cyber Source's solution above.

---

### Post by r50880 on 2010-01-22
Thank you a million times over for the information in this post.  I have also confirmed that the fix listed by Cyber Source above worked for me.  I'm using a homebrew serial IR blaster and iMon Pad remote control.

Thanks again!

---

### Post by russell5 on 2010-02-17
> **Cyber Source said:**
> Hello all,
  In keeping with the open source ideology and in the hopes I can save someone some grief, I'm sending to this thread again, as I can see I sent to it back in 08. The broken state of lirc continues in Ubuntu's Karmic Koala, as I just found out the following system/script error.
Problem: Combined use of lirc for sending and receiving.
Solved / Solution: /etc/init.d/lirc is not correct. If lircd.conf and hardware.conf are properly configured for 2 devices, the init script creates the devices and symlinks correctly but the second symlink device points to the wrong socket, i.e., lircd1 points to /var/run/lirc/lircd and NOT /var/run/lirc/lircd1 like it should. Solution is to edit /etc/init.d/lirc on line 83 change this - "${TRANSMITTER_SOCKET}1" to this - "${TRANSMITTER_SOCKET}" and on line 131 change this - TRANSMITTER_SOCKET="/var/run/lirc/lircd" to this - TRANSMITTER_SOCKET="/var/run/lirc/lircd1". All should be well after that. Also, my lirc_serial module would NOT load if I had the option "softcarrier=1" in /etc/modprobe.d/lirc-serial.conf. After a "service lirc restart", both receiver and sender should be working.



Thanks for this whole post and thanks for the above post. I now have it working you guys rock!!!!!!!

---

### Post by helpdeskdan on 2010-02-24
A FOURTH thank you - I've been fighting this for HOURS!  Thanks [www.pantz.org](www.pantz.org)!  Has somebody posted this as a bug?  Spread the word!

---

### Post by gslauen on 2010-02-25
I have been very patiently trying to get a serial ir blaster and a hauppauge remote working for a very long time now. I have spent weeks reading this forum and others trying to figure out where I am going wrong.
I am using mythbuntu hardy a motorola 2500 digital box a store bought ir serial blaster.
I suspect my problem is here somewhere. 

ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-02-25 05:31 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-25 05:31 /dev/lirc1
srw-rw-rw- 1 root root     0 2010-02-25 06:16 /dev/lircd

I have read about a bug in the actual lirc but when I try to run the patch fix for it I get an error

patching file etc/init.d/lirc
Hunk #1 FAILED at 80.
Hunk #2 FAILED at 128.
2 out of 2 hunks FAILED -- saving rejects to file etc/init.d/lirc.rej

Here are some of my other configs.
dmesg | grep lirc
[   59.848699] lirc_dev: IR Remote Control driver registered, at major 61 
[   60.376430] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   60.376492] lirc_dev: lirc_register_plugin: sample_rate: 10
[   60.948844] lirc_serial: auto-detected active high receiver
[   60.948854] lirc_dev: lirc_register_plugin: sample_rate: 0

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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

I am using a change channel .sh script and when I run that to test I get this

 /usr/local/bin/change-channel-lirc.sh 200
irsend: could not connect to socket
irsend: No such file or directory
irsend: could not connect to socket
irsend: No such file or directory
irsend: could not connect to socket
irsend: No such file or directory

I am at a loss. Also, once I add the ir blaster to my config the hauppauge remote stops working which was working fine.

Can anyone please shed some light on this?????????

I am more than happy to provide anymore info you might need.

---

### Post by rodercot on 2010-02-25
> **gslauen said:**
> I have been very patiently trying to get a serial ir blaster and a hauppauge remote working for a very long time now. I have spent weeks reading this forum and others trying to figure out where I am going wrong.
I am using mythbuntu hardy a motorola 2500 digital box a store bought ir serial blaster.
I suspect my problem is here somewhere. 

ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-02-25 05:31 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-25 05:31 /dev/lirc1
srw-rw-rw- 1 root root     0 2010-02-25 06:16 /dev/lircd

I have read about a bug in the actual lirc but when I try to run the patch fix for it I get an error

patching file etc/init.d/lirc
Hunk #1 FAILED at 80.
Hunk #2 FAILED at 128.
2 out of 2 hunks FAILED -- saving rejects to file etc/init.d/lirc.rej

Here are some of my other configs.
dmesg | grep lirc
[   59.848699] lirc_dev: IR Remote Control driver registered, at major 61 
[   60.376430] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   60.376492] lirc_dev: lirc_register_plugin: sample_rate: 10
[   60.948844] lirc_serial: auto-detected active high receiver
[   60.948854] lirc_dev: lirc_register_plugin: sample_rate: 0

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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

I am using a change channel .sh script and when I run that to test I get this

 /usr/local/bin/change-channel-lirc.sh 200
irsend: could not connect to socket
irsend: No such file or directory
irsend: could not connect to socket
irsend: No such file or directory
irsend: could not connect to socket
irsend: No such file or directory

I am at a loss. Also, once I add the ir blaster to my config the hauppauge remote stops working which was working fine.

Can anyone please shed some light on this?????????

I am more than happy to provide anymore info you might need.


 What version of Lirc and operating system are you using. 

 Is that ls -l /dev/lirc after you add you lirc_serial to the h.conf file. 

 post your channel change script please, also tell me what line 83 and line 131 in your /etc/init.d/lirc script says.

 rgds,

 Dave

---

### Post by gslauen on 2010-02-25
> **rodercot said:**
> What version of Lirc and operating system are you using. 

 Is that ls -l /dev/lirc after you add you lirc_serial to the h.conf file. 

 post your channel change script please, also tell me what line 83 and line 131 in your /etc/init.d/lirc script says.

 rgds,

 Dave

Thanks for responding Dave
I am using mythbuntu version 8.04 not sure how to tell what version of lirc I am using.

Yes the ls -l /dev/lirc is after I add lirc_serial to the h.conf

Here is the change channel script. Actually I have a .pl and a .sh as I understand it is better to use a .sh

#!/bin/sh

REMOTE_NAME=DCT2000
cmd="$1"

case $cmd in
[0-9]*)
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 1
# If things work OK with sleep 1, try this for faster channel changes:
# sleep 0.3
done
;;

*)
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $cmd
;;
esac


OK I have gotten the remote to work by adding /dev/lirc0 to the h.conf on the REMOTE_DEVICE= line
Also now I do not get irsend could not connect to socket error.
However, I am testing the change channel script by using a digital camera to see if the ir blaster is sending a signal and there is nothing.

Could it be the serial port? How can I test the port. I don't think I have an old serial mouse around anywhere just so I could see if the port is working.

---

### Post by rodercot on 2010-02-25
Yes sh is better to use. 

 Well you problem is that there is no /dev/lircd1 being created for your serial device to transmit to so the errors you are seeing are correct. did serial devices not link to /dev/ttyS0 or the like at one point not sure if that has changed.

 That an old version, now to try and think back as to how I made things work back then. Things have changed in newer versions 

 I think the lirc command is

 lirc --version 

 you need to get a lircd1 device created to be linked to your lirc1 eg lirc_serial.

 here is a howto from the early days. depending on the lirc version you have it still may be relevant to you. I have not worked with lirc_serial module much so I am not 100% sure. 

 [https://help.ubuntu.com/community/InstallLirc/Edgy](https://help.ubuntu.com/community/InstallLirc/Edgy)

 Look at the multiple device and the lirc_serial sections

 Regards,

 Dave

---

### Post by gslauen on 2010-02-25
OK I have gotten the remote to work by adding /dev/lirc0 to the h.conf on the REMOTE_DEVICE= line
Also now I do not get irsend could not connect to socket error.
However, I am testing the change channel script by using a digital camera to see if the ir blaster is sending a signal and there is nothing.

Could it be the serial port? How can I test the port. I don't think I have an old serial mouse around anywhere just so I could see if the port is working.

---

### Post by rodercot on 2010-02-25
> **gslauen said:**
> OK I have gotten the remote to work by adding /dev/lirc0 to the h.conf on the REMOTE_DEVICE= line
Also now I do not get irsend could not connect to socket error.
However, I am testing the change channel script by using a digital camera to see if the ir blaster is sending a signal and there is nothing.

Could it be the serial port? How can I test the port. I don't think I have an old serial mouse around anywhere just so I could see if the port is working.


 What does ls -l /dev/lirc* show now.

 Dave

---

### Post by gslauen on 2010-02-25
ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-02-25 07:45 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-25 07:45 /dev/lirc1
srw-rw-rw- 1 root root     0 2010-02-25 09:50 /dev/lircd
srw-rw-rw- 1 root root     0 2010-02-25 09:50 /dev/lircd1

---

### Post by rodercot on 2010-02-25
> **gslauen said:**
> ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-02-25 07:45 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-25 07:45 /dev/lirc1
srw-rw-rw- 1 root root     0 2010-02-25 09:50 /dev/lircd
srw-rw-rw- 1 root root     0 2010-02-25 09:50 /dev/lircd1

 ok it should be working then. You can always try to send it to lircd first and make sure the devices are reversed. 

 Dave

---

### Post by gslauen on 2010-02-25
> **rodercot said:**
> ok it should be working then. You can always try to send it to lircd first and make sure the devices are reversed. 

 Dave

Sorry, I'm not sure I know what you mean by trying to send it to lircd first and reversing the devices. How would I do that?

Thanks Dave

---

### Post by rodercot on 2010-02-25
> **gslauen said:**
> Sorry, I'm not sure I know what you mean by trying to send it to lircd first and reversing the devices. How would I do that?

Thanks Dave

 From the command line you would type something like

 irsend --device-/dev/lircd send_one (remote_name) (command to send)

 right now your c.change script sends to /dev/lircd1 
 
 but actually something just I just thought off you said you were testing on a digital camera I am not sure of how that is happening. 

 you need a remote configured in your lircd.conf file. to send to. 

 So for instance in my lircd.conf file I have recorded the remotes for my sharp TV and my Denon Rcvr.

 so to test my setup I run

 irsend --device=/dev/lircd1 send_once Denon off

 and this shuts off the denon rcrv by flashing it through my MCE USB Dongle to an emitter on the front of the Denon rcvr. 

 If you can run your existing c.change script and you get no errors doing so I would assume things are working so you could actually test it on the cable box itself to be sure.

 Regards,

 Dave

---

### Post by gslauen on 2010-02-25
> **rodercot said:**
> From the command line you would type something like

 irsend --device-/dev/lircd send_one (remote_name) (command to send)

 right now your c.change script sends to /dev/lircd1 
 
 but actually something just I just thought off you said you were testing on a digital camera I am not sure of how that is happening. 

 you need a remote configured in your lircd.conf file. to send to. 

 So for instance in my lircd.conf file I have recorded the remotes for my sharp TV and my Denon Rcvr.

 so to test my setup I run

 irsend --device=/dev/lircd1 send_once Denon off

 and this shuts off the denon rcrv by flashing it through my MCE USB Dongle to an emitter on the front of the Denon rcvr. 

 If you can run your existing c.change script and you get no errors doing so I would assume things are working so you could actually test it on the cable box itself to be sure.

 Regards,

 Dave

Ok a couple of things. When I say I am using a camera to test it is just a way to see if the signal from the ir blaster is sending. By looking through a digital camera you can see if a infrared signal is being emitted. There is no signal. For example if you hold your remote and point it at the camera and change a channel say, you will see the light in the camera.

Now back to the problem. 
When I try  
/usr/share/lirc/transmitters/motorola$ irsend --device=/dev/lircd send_once DCT2000 power
irsend: command failed: send_once DCT2000 power
irsend: hardware does not support sending

When I try
 irsend --device=/dev/lircd1 send_once DCT2000 power
nothing happens, no error and no infrared signal sends.

1. Is there a way to test the actual serial port to see if that works.
I don't think a signal is getting to the serial ir blaster.

2. I was wondering if it matters that My digital box is actually a motorola DCT2500 not a DCT2000 does that make a difference but I don;t think the signal is even being transmitted.

---

### Post by rodercot on 2010-02-25
In that link to that old how to there was info about setting the serial port irq - address etc... I am not sure on testing the actual port, you have it enable in the Mainboard's bios I assume. 

 I think setserial was the program it mentioned. Not sure again I have not tried serial devices, mine are all usb.

 Dave

---

### Post by gslauen on 2010-02-26
> **rodercot said:**
> In that link to that old how to there was info about setting the serial port irq - address etc... I am not sure on testing the actual port, you have it enable in the Mainboard's bios I assume. 

 I think setserial was the program it mentioned. Not sure again I have not tried serial devices, mine are all usb.

 Dave

I think I have done everything right with the setsserial. I have it set to manual and the port is enabled in the bios. I am just not sure where it is failing. 

My DTC2500 supports usb perhaps that would be an easier way to go.
How does that work. Where does the usb run from the computer to the digital box and do I need a special cable for that? Of course I would have to do a whole other set of study on usb. I am just wondering if you could give me a quick overview of what's involved. What is your setup like for example.
As I said I have a older hauggpage card. I run s-video and audio to the computer from the motorola box I just can change channels which sucks for auto recording.

---

### Post by rodercot on 2010-02-26
> **gslauen said:**
> I think I have done everything right with the setsserial. I have it set to manual and the port is enabled in the bios. I am just not sure where it is failing. 

My DTC2500 supports usb perhaps that would be an easier way to go.
How does that work. Where does the usb run from the computer to the digital box and do I need a special cable for that? Of course I would have to do a whole other set of study on usb. I am just wondering if you could give me a quick overview of what's involved. What is your setup like for example.
As I said I have a older hauggpage card. I run s-video and audio to the computer from the motorola box I just can change channels which sucks for auto recording.

 I have an mce usb remote package. Mediagate and several other make em. The medigate VERSION 2 supports sending and includes the dongle and emitter, the remote that is included works just fine as well. 

 Plug the dongle into your USB port on the pc, plug the emitter into the dongle stick the other end on your cable box. Use mythbuntu control center to configure both the remote and the transmitter as Windows Media Center Remote and Windows Media Center trnasmitter for your cable box there is a drop down box to select these options. reboot and test you can configure a little past this and create a lircd.conf file by combining the two that are listed in the hardware.conf file or if you have your own currently then just replace the remote_licrd line in hardware.conf with the address of your lircd.conf file and then under the transmitter section you can just delete the one they have listed for your cable box and make it look like this
trasmitter_remote_lircd="".
 
 Ok but before all of the above you DO have your cable box defined as a remote in your lircd..conf file currently I hope. If you do not then the system does not know what command from what device to send. 

 Regards,
 Dave

---

### Post by gslauen on 2010-02-26
> **rodercot said:**
> I have an mce usb remote package. Mediagate and several other make em. The medigate VERSION 2 supports sending and includes the dongle and emitter, the remote that is included works just fine as well. 

 Plug the dongle into your USB port on the pc, plug the emitter into the dongle stick the other end on your cable box. Use mythbuntu control center to configure both the remote and the transmitter as Windows Media Center Remote and Windows Media Center trnasmitter for your cable box there is a drop down box to select these options. reboot and test you can configure a little past this and create a lircd.conf file by combining the two that are listed in the hardware.conf file or if you have your own currently then just replace the remote_licrd line in hardware.conf with the address of your lircd.conf file and then under the transmitter section you can just delete the one they have listed for your cable box and make it look like this
trasmitter_remote_lircd="".
 
 Ok but before all of the above you DO have your cable box defined as a remote in your lircd..conf file currently I hope. If you do not then the system does not know what command from what device to send. 

 Regards,
 Dave
No I do not have the cable box defined as a remote but as a transmitter and now that you mention it that does sound like a problem.

I was just following how other people have this setup.
#Configuration for the Serial Port (UART) : Motorola Cable box transmitter:
This is my lirc.conf
include /usr/share/lirc/transmitters/motorola/dctxxxx.conf

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

OK so maybe this is the problem. 
Logically I want the serial ir blaster to be the transmitter and the cable box to be the receiver.

So I am really confused now.
Acutally that is how mythbuntu sets it up if you add serial mototorola in the infrared config in the mcc control panel when I choose serial port uart mototorola cable box but now I am going to try command ir mototorola cable box

It still adds it as a transmitter as in fact the ir is transmitting to the box

Of course now I am getting the connection refused message again.
could not connect to socket I may need to reboot.

---

### Post by rodercot on 2010-02-26
Here you can try this. back up your existing lircd.conf file WHICH should be in your /etc/lirc directory. 

 create a new file with this paste and call it lircd.conf place it in your /etc/lirc directory.

 ```
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

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg www.lugv.at
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800

      begin codes
          power                    0x17BD
          go                       0x17BB
          tv                       0x179C
          videos                   0x1798
          music                    0x1799
          pictures                 0x179A
          guide                    0x179B
          radio                    0x178C
          exit                     0x179F
          menu                     0x178D
          prevch                   0x1792
          mute                     0x178F
          up                       0x1794
          down                     0x1795
          left                     0x1796
          right                    0x1797
          ok                       0x17A5
          volup                    0x1790
          voldown                  0x1791
          chup                     0x17A0
          chdown                   0x17A1
          record                   0x17B7
          stop                     0x17B6
          rewind                   0x17B2
          fastfwd                  0x17B4
          play                     0x17B5
          replay                   0x17A4
          skip                     0x179E
          pause                    0x17B0
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          *                        0x178A
          0                        0x1780
          #                        0x178E
          red                      0x178B
          green                    0x17AE
          yellow                   0x17B8
          blue                     0x17A9
          sub/cc                   0x178E
          text                     0x178A
          home                     0x17BB
      end codes

end remote

begin remote
 name  DCT2000
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100
 
  header       9036  4424
  one           556  2185
  zero          556  4424
  ptrail        556
  gap          100025
  toggle_bit      0
 
 
      begin codes
          HELP                     0x000000000000B3F2
          POWER                    0x000000000000AFF9
          MUTE                     0x0000000000000FF7
          PAGE+                    0x000000000000A3F3
          PAGE-                    0x00000000000023FB
          LOCK                     0x00000000000097F6
          EXIT                     0x000000000000B7F4
          AUP                      0x000000000000D3F6
          ADOWN                    0x00000000000053FE
          ALEFT                    0x00000000000093F1
          ARIGHT                   0x00000000000013F9
          OK                       0x00000000000077F8
          GUIDE                    0x000000000000F3F4
          MENU                     0x00000000000067F9
          VOL+                     0x0000000000004FF3
          VOL-                     0x0000000000008FFB
          LAST                     0x00000000000037FC
          FAV                      0x00000000000057FA
          CH+                      0x0000000000002FF5
          CH-                      0x000000000000CFFD
          A                        0x00000000000017FE
          B                        0x0000000000001BF1
          C                        0x000000000000EBF9
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
          BYPASS                   0x000000000000D7F2
          MUSIC                    0x000000000000F7F0
          STOP                     0x00000000000063FD
          PAUSE                    0x00000000000007FF
          PLAY                     0x000000000000E3F5
          REW                      0x00000000000087F7
          REC                      0x00000000000073FC
          FFWD                     0x00000000000047FB
      end codes
 
end remote

```

 Now in your hardware.conf file make sure your proper modules are listed in each section this should not have changed.

 in the REMOTE section look for the the 

 REMOTE_LIRCD_CONF="" line and place this in between the quotes

 /etc/lirc/lircd.conf

 make sure that your remote device is still 

 /dev/lirc0 for the remote and /dev/lirc1 for the transmitter. 

 In the transmitter section make sure that this line

 TRANSMITTER_LIRCD_CONF="" looks like this. 

 Then from the command line

 sudo /etc/init.d/lirc restart.  if it fails one of the daemons try the command again. 

 Then look in your 

 ls -l /dev/lirc* and make sure you have your

 lirc0, lirc1, lircd, lircd1 if you do then try your send 
command again.

 I do notice that the motorola box is for a 2000 series I hope that will work with yours as you said a few post ago.

 Regards,

 Dave

---

### Post by gslauen on 2010-02-26
> **rodercot said:**
> Here you can try this. back up your existing lircd.conf file WHICH should be in your /etc/lirc directory. 

 create a new file with this paste and call it lircd.conf place it in your /etc/lirc directory.

 ```
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

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg www.lugv.at
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800

      begin codes
          power                    0x17BD
          go                       0x17BB
          tv                       0x179C
          videos                   0x1798
          music                    0x1799
          pictures                 0x179A
          guide                    0x179B
          radio                    0x178C
          exit                     0x179F
          menu                     0x178D
          prevch                   0x1792
          mute                     0x178F
          up                       0x1794
          down                     0x1795
          left                     0x1796
          right                    0x1797
          ok                       0x17A5
          volup                    0x1790
          voldown                  0x1791
          chup                     0x17A0
          chdown                   0x17A1
          record                   0x17B7
          stop                     0x17B6
          rewind                   0x17B2
          fastfwd                  0x17B4
          play                     0x17B5
          replay                   0x17A4
          skip                     0x179E
          pause                    0x17B0
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          *                        0x178A
          0                        0x1780
          #                        0x178E
          red                      0x178B
          green                    0x17AE
          yellow                   0x17B8
          blue                     0x17A9
          sub/cc                   0x178E
          text                     0x178A
          home                     0x17BB
      end codes

end remote

begin remote
 name  DCT2000
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100
 
  header       9036  4424
  one           556  2185
  zero          556  4424
  ptrail        556
  gap          100025
  toggle_bit      0
 
 
      begin codes
          HELP                     0x000000000000B3F2
          POWER                    0x000000000000AFF9
          MUTE                     0x0000000000000FF7
          PAGE+                    0x000000000000A3F3
          PAGE-                    0x00000000000023FB
          LOCK                     0x00000000000097F6
          EXIT                     0x000000000000B7F4
          AUP                      0x000000000000D3F6
          ADOWN                    0x00000000000053FE
          ALEFT                    0x00000000000093F1
          ARIGHT                   0x00000000000013F9
          OK                       0x00000000000077F8
          GUIDE                    0x000000000000F3F4
          MENU                     0x00000000000067F9
          VOL+                     0x0000000000004FF3
          VOL-                     0x0000000000008FFB
          LAST                     0x00000000000037FC
          FAV                      0x00000000000057FA
          CH+                      0x0000000000002FF5
          CH-                      0x000000000000CFFD
          A                        0x00000000000017FE
          B                        0x0000000000001BF1
          C                        0x000000000000EBF9
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
          BYPASS                   0x000000000000D7F2
          MUSIC                    0x000000000000F7F0
          STOP                     0x00000000000063FD
          PAUSE                    0x00000000000007FF
          PLAY                     0x000000000000E3F5
          REW                      0x00000000000087F7
          REC                      0x00000000000073FC
          FFWD                     0x00000000000047FB
      end codes
 
end remote

```

 Now in your hardware.conf file make sure your proper modules are listed in each section this should not have changed.

 in the REMOTE section look for the the 

 REMOTE_LIRCD_CONF="" line and place this in between the quotes

 /etc/lirc/lircd.conf

 make sure that your remote device is still 

 /dev/lirc0 for the remote and /dev/lirc1 for the transmitter. 

 In the transmitter section make sure that this line

 TRANSMITTER_LIRCD_CONF="" looks like this. 

 Then from the command line

 sudo /etc/init.d/lirc restart.  if it fails one of the daemons try the command again. 

 Then look in your 

 ls -l /dev/lirc* and make sure you have your

 lirc0, lirc1, lircd, lircd1 if you do then try your send 
command again.

 I do notice that the motorola box is for a 2000 series I hope that will work with yours as you said a few post ago.

 Regards,

 Dave

Well I changed all of the conf's etc but unfortunely I still get the same thing. The commands send but there is no infrared being sent to the ir blaster. I have a feeling the problem is in the serial port itself or the ir blaster. The blaster is brand new though. No signal seems to be getting to the transmitter.

I don't know what else to try. I have an old serial mouse but I don't know if it works so I am going to look around and see what I can figure out.

Thanks again for all your help I will update you when I find out more.
I may just go and by the MCE usb dongle.

---

### Post by gslauen on 2010-02-27
> **gslauen said:**
> Well I changed all of the conf's etc but unfortunely I still get the same thing. The commands send but there is no infrared being sent to the ir blaster. I have a feeling the problem is in the serial port itself or the ir blaster. The blaster is brand new though. No signal seems to be getting to the transmitter.

I don't know what else to try. I have an old serial mouse but I don't know if it works so I am going to look around and see what I can figure out.

Thanks again for all your help I will update you when I find out more.
I may just go and by the MCE usb dongle.

OMG well I can't believe it but I got it working. I think the biggest part of the problem was that I was testing it by trying to see in the digital camera when this particular model of ir blaster does not emit a light just a signal. 
I agreed with you that if there was no error message and it was sending it should be working so I tried it on the mototorola box itself and viola.
Now my problem is the change channel script.
It understands commands like power or ch+ but does not understand say 200 or 81 which is what I need to change the channels.
But the DCT20000 conf does seem to work for power on off etc.

This is the dctxxxx.conf


# this config file was automatically generated
# using lirc-0.6.6(serial) on Fri Mar 28 22:46:44 2003
#
# contributed by shane bradley
#
#
#
# brand:                       Motorola
# model no. of remote control: DCT2000
# devices being controlled by this remote:
#
                                                                                    
begin remote
 name  DCT2000
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100
 
  header       9036  4424
  one           556  2185
  zero          556  4424
  ptrail        556
  gap          100025
  toggle_bit      0
 
 
      begin codes
          HELP                     0x000000000000B3F2
          POWER                    0x000000000000AFF9
          MUTE                     0x0000000000000FF7
          PAGE+                    0x000000000000A3F3
          PAGE-                    0x00000000000023FB
          LOCK                     0x00000000000097F6
          EXIT                     0x000000000000B7F4
          AUP                      0x000000000000D3F6
          ADOWN                    0x00000000000053FE
          ALEFT                    0x00000000000093F1
          ARIGHT                   0x00000000000013F9
          OK                       0x00000000000077F8
          GUIDE                    0x000000000000F3F4
          MENU                     0x00000000000067F9
          VOL+                     0x0000000000004FF3
          VOL-                     0x0000000000008FFB
          LAST                     0x00000000000037FC
          FAV                      0x00000000000057FA
          CH+                      0x0000000000002FF5
          CH-                      0x000000000000CFFD
          A                        0x00000000000017FE
          B                        0x0000000000001BF1
          C                        0x000000000000EBF9
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
          BYPASS                   0x000000000000D7F2
          MUSIC                    0x000000000000F7F0
          STOP                     0x00000000000063FD
          PAUSE                    0x00000000000007FF
          PLAY                     0x000000000000E3F5
          REW                      0x00000000000087F7
          REC                      0x00000000000073FC
          FFWD                     0x00000000000047FB
      end codes
 
end remote

And this is my change-channel-lirc.sh

#!/bin/sh

REMOTE_NAME=gi-motorola-dct2000
cmd="$1"

case $cmd in
    [0-9]*)
    for digit in $(echo $1 | sed -e 's/./& /g'); do
        irsend SEND_ONCE $REMOTE_NAME $digit
        sleep 1
        # If things work OK with sleep 1, try this for faster channel changes:
        # sleep 0.3
    done
    ;;

    *)
        irsend SEND_ONCE $REMOTE_NAME $cmd
        ;;
esac

When I use
irsend --device=/dev/lircd1 SEND_ONCE DCT2000 power
the power goes on or off
when I use 
irsend --device=/dev/lircd1 SEND_ONCE DCT2000 81
of course this is irsend: unknown command: "81"
How does the program change to say channel 81 if that is the channel I want to record?
I have place the path to my change channel script in the mythtv-backend.

I am so close now.

---

### Post by rodercot on 2010-02-27
Why not try this and see if it works Change the remote name in your script as follows

 Your existing script - 

REMOTE_NAME=gi-motorola-dct2000

 Change to this:

REMOTE_NAME=DCT2000

 Also when testing with irsend you need to leave a space between the numbers.

 irsend --device=/dev/lircd1 send_once DTC2000 2 4 5 

 you will have to goggle the path location, i cannot recall which folder it goes in /usr??? rings a bell. 
 
 you set it in your backend settings.

 Dave

---

### Post by gslauen on 2010-02-28
> **rodercot said:**
> Why not try this and see if it works Change the remote name in your script as follows

 Your existing script - 

REMOTE_NAME=gi-motorola-dct2000

 Change to this:

REMOTE_NAME=DCT2000

 Also when testing with irsend you need to leave a space between the numbers.

 irsend --device=/dev/lircd1 send_once DTC2000 2 4 5 

 you will have to goggle the path location, i cannot recall which folder it goes in /usr??? rings a bell. 
 
 you set it in your backend settings.

 Dave

Dave it is all working now.
Again thanks for your help but the main thing was the serial port does not work on that machine. I switched machines for one thing and that is how I got the blaster working in the first place.

I did change the remote name back to DCT2000 the REMOTE_NAME=gi-motorola-dct2000 came from somewhere else. Once I started send the irsend commands to the digital box and it was responding it was a little trial and error.
I also could not get the change channel .sh script working but the .pl does 
I had to make some modifications in the script like the rsend --device=/dev/lircd1 SEND_ONCE
A really funny one though was instead of using an enter command as that was getting an error I just substituted OK for the command instead and it works great now.
I can change channels with the hauppage remote and it changes the digital box channels and I tested with recording and it works as well.

So there were a few things working against me the serial port, the fact the infrared didn't send a light and the change channel script. However, it is all sorted out now. 

If any of that is as clear as mud I can show you all my config files.

Thanks again Dave.

---

### Post by gslauen on 2010-03-01
> **gslauen said:**
> Dave it is all working now.
Again thanks for your help but the main thing was the serial port does not work on that machine. I switched machines for one thing and that is how I got the blaster working in the first place.

I did change the remote name back to DCT2000 the REMOTE_NAME=gi-motorola-dct2000 came from somewhere else. Once I started send the irsend commands to the digital box and it was responding it was a little trial and error.
I also could not get the change channel .sh script working but the .pl does 
I had to make some modifications in the script like the rsend --device=/dev/lircd1 SEND_ONCE
A really funny one though was instead of using an enter command as that was getting an error I just substituted OK for the command instead and it works great now.
I can change channels with the hauppage remote and it changes the digital box channels and I tested with recording and it works as well.

So there were a few things working against me the serial port, the fact the infrared didn't send a light and the change channel script. However, it is all sorted out now. 

If any of that is as clear as mud I can show you all my config files.

Thanks again Dave.

Just an update now my remote seems to stop working and I remove it and add it again and it works. I am guessing that it is something in the start up.
Also, I am using Karmic on this machine mythbuntu 9.10

---

### Post by duppyman on 2010-03-18
Howdy to all participants of this forum. First of all, I am new to linux but hoping to learn as I proceed. Very glad to have found this forum.
I recently downloaded Mythbuntu 9.10 and had a few hiccups that I have figured out. I can watch and record TV. The program guide is populated with info from Schedules Direct. My only challenge is trying to get my, Hauppauge PVR 350 remote and ir blaster working. The set up at the beginning of this thread looks good but I notice it is using lirc-0.8.2 and Mythbuntu 9.10 uses lirc-0.8.6.
So after a long preamble, my question is has anyone out there successfully used this procedure with Mythbuntu 9.10? If the answer is yes would you be able to share the changes you had to make to the original process.
Hoping someone can help or point me in the correct direction.

---

### Post by rlauzon on 2010-03-31
Well, I know I haven't yet.

I have Mythbuntu 9.10.  lircd 0.8.6
One serial port with an irblaster ([http://www.irblaster.info/](http://www.irblaster.info/)) hooked to it.

I cannot get this thing to transmit.

/etc/modprobe.d/lirc-serial.conf is set to the ttyS0.  I verified that the irq/io address are set to the same values that the BIOS says that it's on.

lircd is running.  A /dev/lircd0 exists.

The command:
irsend  SEND_ONCE DCT2000 5
does nothing.  The irblaster is supposed to light up on transmit, but no light.  I placed it in front of an ir receiver and the receiver shows nothing is being transmitted.  And, most frustrating, no error message from irsend.  It thinks everything worked fine.

The only errors I see are:
lirc_serial: ignoring spike: 0 0 4bb3d55d 4bb3d55d ed475 dc620
which correspond exactly when I run the irsend command.

It's very frustrating.  I don't think there's a hardware issue with the PC since everything sees the serial port.  But I can't verify that the irblaster is defective or not.

If anyone has any other ideas to try, I'd appreciate it.

---

### Post by rlauzon on 2010-04-02
Well, I figured out my current problem: there's an issue with the serial port on that PC.  I knew there was a reason I had a StreamZap on that box originally instead of an IR Man.

So a new USB IR blaster is on order and hopefully that will solve the issues.

---

