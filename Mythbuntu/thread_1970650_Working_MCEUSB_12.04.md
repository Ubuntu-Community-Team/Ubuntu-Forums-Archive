---
title: "Working MCEUSB 12.04?"
date: 2012-05-01
forum: Mythbuntu
---

### Post by grg3 on 2012-05-01
I have been unable to get my mceusb remote/transmitter to blast with 12.04. The remote works but ir blasting does not.

I have been using this setup with 11.10 without any problems (both remote and blasting) and I have not been able to get blasting going on 12.04. I have tried both upgrade and fresh install.

Anyone have mceusb remote with working blasting on 12.04?

---

### Post by jobcol on 2012-05-03
hey
I too am having the same issue, after upgrading to 12.04. My mceusb remote/transmitter worked perfectly in 11.04, but now remote is only partly functional (only partly works with no lirc installed, and not at all when i try installing lirc through MCC)
Ir blasting does not work at all.
Even when i try to irsend in Terminal  it just times out or says "hardware does not support sending"
I'm using the exact same lirc config files(lircd.conf,hardware.conf,lircrc etc.) as i was for 11.04.

Anyone have any clue as to whats going on?

---

### Post by grg3 on 2012-05-03
Glad to know it is not just me! 

I filed a bug to see if that might get some attention to this problem. 

[https://bugs.launchpad.net/bugs/992754](https://bugs.launchpad.net/bugs/992754)

Jobcol, maybe you can confirm?

---

### Post by anonymousdog on 2012-05-03
grg3, what say you post your /etc/lirc/lircd.conf file and the output of 'ls -lah /dev/lirc*'?

---

### Post by jobcol on 2012-05-05
ill post mine :)

/etc/lirc/lircd.conf
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box transmitter:
#include "/usr/share/lirc/extras/transmitters/scientificatlanta/general.conf"


begin remote

  name       ipn330hd
  bits           32
  flags RCMM|CONST_LENGTH
  eps           18
  aeps          100

  header        417   278
  three         167   778
  two           167   611
  one           167   444
  zero          167   278
  ptrail        167
  gap           99817
  min_repeat     4 
  toggle_bit_mask 0x8000

      begin codes
          0                        0x23402600
          1                        0x2340A601
          2                        0x23402602
          3                        0x2340A603
          4                        0x23402604
          5                        0x2340A605
          6                        0x2340A606
          7                        0x2340A607
          8                        0x23402608
          9                        0x2340A609
          LAST                     0x2340260A
          POWER                    0x2340A60C
          INFO                     0x2340260F
          CH+                      0x2340A620
          CH-                      0x2340A621
          FF                       0x23402628
          REW                      0x2340A629
          PLAY                     0x2340262C
          PAUSE                    0x23402630
          STOP                     0x2340A631
          RECORD                   0x23402637
          A                        0x2340A638
          B                        0x2340A639
          RECORDEDTV               0x23402644
          FWD                      0x2340A64C
          REPLAY                   0x2340264D
          MENU                     0x2340A654
          EXIT                     0x2340A655
          UP                       0x2340A658
          DOWN                     0x23402659
          LEFT                     0x2340A65A
          RIGHT                    0x2340A65B
          OK                       0x2340A65C
          BACK                     0x2340A683
          C                        0x2340A686
          DELETE                   0x2340A69E
          TVVIDEO                  0x234026A8
          GUIDE                    0x234026CC
          ENTER                    0x234026E1
          VOD                      0x2340A6F0
          gointeractive            0x2340A6FD
      end codes

end remote


#ls -lah /dev/lirc*
crw------- 1 root root 250, 0 May  5 00:12 /dev/lirc0
lrwxrwxrwx 1 root root     19 May  5 00:12 /dev/lircd -> /var/run/lirc/lircd

---

### Post by grg3 on 2012-05-05
Here is working versus not working: 

I did have to manually enter transmitter part in lircd.conf as it was not populated by setup. This makes me believe that something else was not setup for blasting.

11.10 - mceusb working lircd.conf:

```
#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Motorola Cable box transmitter:
include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
```

12.04 - mceusb not working lircd.conf

```
#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
```

11.10 - mceusb fully functional

```
 ls -lah /dev/lirc*
crw------- 1 root root 250, 0 2012-05-05 08:40 /dev/lirc0
lrwxrwxrwx 1 root root     19 2012-05-05 08:40 /dev/lircd -> /var/run/lirc/lircd
```


12.04 - mceusb no blasting

```
ls -lah /dev/lirc*
crw------- 1 root root 250, 0 May  5 08:47 /dev/lirc0
lrwxrwxrwx 1 root root     19 May  5 08:47 /dev/lircd -> /var/run/lirc/lircd
```

---

### Post by grg3 on 2012-05-05
jobcol

Normally your remote codes are not entered in lircd.conf, you should only have to uncomment the transmitter line:

```
#include "/usr/share/lirc/extras/transmitters/scientificatlanta/general.conf"
```

---

### Post by Akriss on 2012-05-05
Hi,

in the file /etc/lirc/hardware.conf

There is a line TRANSMITTER_MODULES=

It should have "mceusb" module listed.

Kind of like the line above it in the same file that reads: REMOTE_MODULES=

Thats all I got.
hope its a help.

---

### Post by grg3 on 2012-05-08
I have continued to play with this upgrade and I have compared config files and run updates. Still no ir blasting on 12.04. Existing 11.10 install works.

I did another clean install of 12.04 today. The remote setup correctly configured hardware.conf and lircd.conf on install but neither remote or blaster would work. I set remote and blaster to none using the irconfig tool in control center and rebooted.

After rebooting I ran remote config tool and setup remote and blaster. Again, hardware.conf and lircd.conf were correctly configured. This time, the remote worked but still no blasting.

I am using the same change_mce.sh script that I used in 11.10. Since there are two channels on the blaster i tried the channel change script with both 1 and 2. Still no blasting or reaction from the mceusb tranceiver.

It almost looks like the module for blasting with mceusb has been changed or removed. I am stumped on how to troubleshoot this further. I am open to suggestions.

---

### Post by anonymousdog on 2012-05-09
Please post broken 12.04 hardware.conf and output of
```
irsend LIST "" ""
```.  Thanks.  I'm super busy through the weekend, but this is a crucial issue for me; so, I'll keep coming back.

---

### Post by grg3 on 2012-05-09
Thanks for looking into this!

Here is hardware.conf 12.04:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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
```


And here is irsend LIST "" "":

```
rick@mythtv:~$ irsend LIST "" ""
irsend: DCT2000
irsend: mceusb
rick@mythtv:~$ 
```

This is the same as working 11.10 install. Remote works in 12,04 but not blaster.

---

### Post by jobcol on 2012-05-13
grg3, Im still in same boat, mceusb remote works fine on 12.04 but cant get blaster to work, so have since gone back to 11.10, where all works perfectly.
However, i notice you are using dctxxxx.conf in your setup. In my attempts to get irsend to transmit to my STB using my particular lircd.conf for my remote, I tested all the other lircd.confs in /usr/share/lirc/transmitters ,
including the dctxxxx.conf for Motorola and was able to get the mce blaster to transmit/ flash when running irsend in terminal.So I know the hardware works. It just wont work with my particular lircd.conf which uses the RCMM protocol.
Does your blaster flash when you run irsend in terminal? 
e.g.

```
# irsend SEND_ONCE DCT2000 *POWER*
```

What error messages does irsend give you when you run this, if any?

---

### Post by grg3 on 2012-05-15
Thanks for the info, but no luck here even using irsend in terminal. I have never seen the blaster led light up with 12.04. It is almost like it was before they got the mce blasting working. 

I used to use a serial blaster, but that has become difficult to get working because it is hard to find a mboard with serial anymore.

---

### Post by anonymousdog on 2012-05-16
Ok.  I just tested an MCE USB remote with blaster on 12.04 using a setup for MCEUSB v2 and Dish Network receivers.  That works fine (at least to the extent that the blaster does light up with appropriate irsend commands).

Would you be willing to reconfigure IR support for a Dish STB and test (just long enough to see whether the blaster even lights up)?  I think jobcol may have been onto something about a potentially broken dctxxxx.conf.  'irsend send_once dish select' should do it.

Also, what is the output of 'lsusb' (i.e., what model blaster do you have)?  I think we should elminate hardware/driver issues.  My successful test was with an IR device identifying as: ID 1784:0001 TopSeed Technology Corp.  I also have a blaster identifying as ID 2304:0225 Pinnacle Systems, Inc. [hex] I could use to test.

BTW, jobcol, thanks for picking this up...very rough last week and weekend that prevented my getting back to it.

---

### Post by grg3 on 2012-05-16
Here is lsusb 11.10 (working)

```
Bus 001 Device 003: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys
```

12.04 gives the same result for lsusb.

I tried setting the blaster to mce directtv and still no blasting.

I am beginning to wonder what I have done wrong. I have looked at every config file I can think oflooking at. 11.10 works 12.04 does not.

---

### Post by anonymousdog on 2012-05-18
Is this 64-bit or 32?  I cannot duplicate these symptoms with either of my available mceusb transceivers and 12.04 x86_64 on two different PCs.  Using the MCC to configure the MCE transceiver for Motorola STB, I get blaster flashes for all registered commands.

Your fresh builds: Are these on/over existing file systems (i.e., potentially inheriting an old /etc/init.d/lirc or other critical files)?

---

### Post by grg3 on 2012-05-20
The last build was fresh install on clean drive. I am beginning to think that my blaster is not supported anymore. (original mce) 

I guess my next step is to try the receiver that is on my frontend and see if it will blast with 12.04.

After that I will have to try to find another blaster that works. I notice that there are lots still available via ebay.

Thank goodness I still have my working 11.10 backend or I would be out of luck for sure.

---

### Post by grg3 on 2012-05-22
Well I can finally report some success. I swapped the transceiver from my frontend to my backend and now I have blasting in both 11.10 and 12.04.

Problem Transceiver:

```
Bus 001 Device 003: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys
```

Working Tranceiver:
```
Bus 002 Device 004: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

I should have tried this sooner! Maybe this post will help someone else out!

Now I can do some testing of 12.04. I have been hesitant to commit to upgrading after having the blaster problem. It appears that everything is working now. My backend does not like to "Watch TV", so we will see when I schedule some recordings.

Thanks everyone! I don't know why a transceiver that worked before doesn't work now, but I a glad that I didn't have two of them!

---

### Post by anonymousdog on 2012-05-23
I appreciate that this solves your problem, but it does not solve the underlying issue; your original config should work.  I wonder whether this is a problem that crept in during the migration to the new mceusb driver.

On your 11.10 box, what does 'lsmod | grep mceusb' return?  If lirc on 11.10 is using lirc_mceusb (vs mceusb), it might help to follow the advice at [http://ubuntuforums.org/showpost.php?p=11261863&postcount=5](http://ubuntuforums.org/showpost.php?p=11261863&postcount=5).

If using the lirc_mceusb driver (with mceusb blacklisted), IMO, that would point to a bug in the new mceusb driver.

---

### Post by grg3 on 2012-05-23
I spoke too soon. I upgraded my existing install (clean install and restore backup). I got everything setup and working and now, once again no blaster!

It is too late to run anymore tests on 11.10 as that is history, but I did check the driver as suggested above. 

I have the mceusb driver in my 12.04 and I didn't seem to have any luck trying to load the lirc_mceusb.

I am now dead in the water until I figure this out. I may try my old transceiver tomorrow.

---

### Post by grg3 on 2012-05-25
OK! I have a lovely new install of 12.04 and I was able to safely bring my database and recordings along. Still no blasting.

I am open to any and all suggestions. In the meantime I am manually changing the channel on my cable box.

I tried my other MCE transceiver and it does not blast either. Everything else seems to work fine.

---

### Post by DieMysticBoer on 2012-05-31
Hi,

I am also struggling with this. My HP branded MCE Transmitter/Receiver, can be learnt to see my remote, but unfortunately cannot blast. I've had my ossiloscope connected to the transmitter and have been seeing some interesting things.

First off, my Satellite box uses NEC protocoll, and from the learnt data, and the scope I can see that it is definitely NEC protocol. There is a 9000us lead-in, followed by a 4500us space, and then the IR data for the key code etc, all according to NEC specification.

The light on the transmitter never lights up when trying to transmit. I have found that the light does come on when using the config file of the SAE8000 found in "/usr/share/lirc/extras/transmitters/scienificatlanta/general.conf". And according to the data in the config file it has a "header" of 3397us On, and 3372us Off. Well, looking at this transmitted signal on the scope, the header is not being sent. The rest of the data is visible, but no header. **So just because the light goes on, does not mean it is sending the right stuff**.I then started debugging the "mceusb.c" kernel driver source, and sprinkled a couple of "printk's" around. I can see that the data from "irsend" is delivered correctly to the driver, and the driver is sending the correct data down the USB sub system, but the transmitter is just not doing what is asked from it.

I've used the "Windows-Media-Center-RC-IR-Collection-Green-Button-Specification-03-08-2011-V2.pdf" specification to check every last byte sent to the transmitter, and all looks correct.

So, I am at a loss. I don't know what else to try...

Regards,
Mystic :(

---

### Post by anonymousdog on 2012-05-31
Mystic, would you be willing to compile the lirc_mceusb legacy driver, blacklist the kernel mceusb driver, and configure lirc to use the legacy driver (and compare all your results)?

---

### Post by DieMysticBoer on 2012-05-31
> **anonymousdog said:**
> Mystic, would you be willing to compile the lirc_mceusb legacy driver, blacklist the kernel mceusb driver, and configure lirc to use the legacy driver (and compare all your results)?

Ok, I'll see what I can do tonight. Lets hope... :confused:

---

### Post by grg3 on 2012-05-31
OK! I had a day to set down and go over the config files again and I found that I had an error in my channel change script. My bad!

```
#!/bin/sh

REMOTE_NAME=dctxxxx
 irsend SET_TRANSMITTERS 2
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME SELECT
 exit 0
```

I forgot to change the REMOTE_NAME to dct2000. Once I did this the blaster started working. So I have at least confirmed, once again, that this transceiver works,

However, I now seem to have too much of a good thing and the blaster endlessly sends the channel over and over. I am looking for a fix for this but have not found it yet. It is possible to have too much of a good thing!

The script works fine from command line, but endlessly repeats from within mythtv. So far I have found one post on Ubuntu forums related to this but did not see solution. I will keep going over the config files.

---

### Post by DieMysticBoer on 2012-05-31
> **grg3 said:**
> OK! I had a day to set down and go over the config files again and I found that I had an error in my channel change script. My bad!

```
#!/bin/sh

REMOTE_NAME=dctxxxx
 irsend SET_TRANSMITTERS 2
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME SELECT
 exit 0
```I forgot to change the REMOTE_NAME to dct2000. Once I did this the blaster started working. So I have at least confirmed, once again, that this transceiver works,

However, I now seem to have too much of a good thing and the blaster endlessly sends the channel over and over. I am looking for a fix for this but have not found it yet. It is possible to have too much of a good thing!

The script works fine from command line, but endlessly repeats from within mythtv. So far I have found one post on Ubuntu forums related to this but did not see solution. I will keep going over the config files.

That's good news, it means that something somewhere kinda works. I however still do not have an idea whats wrong on my side, I'm trying what is suggested above, lets hope. Maybe it will shed light on your "repeat" problem.

---

### Post by DieMysticBoer on 2012-05-31
Well, there goes that idea...

#include <linux/smp_lock.h>, Things changed in the newer kernels regarding mutex handling, so the source for lirc_mceusb will not compile any more. I was tempted to remove all mutexes from the code and try again, but that will most probably cause nothing to work, and give false results.

I'm gonna go scratch in the driver some more, and check if I can hopefully pick something up.

Cheers.

---

### Post by anonymousdog on 2012-05-31
> **grg3 said:**
> 
However, I now seem to have too much of a good thing and the blaster endlessly sends the channel over and over.

The script works fine from command line, but endlessly repeats from within mythtv.

What's the tuning timeout value in mythbackend setup for your tuner card(s)? I'm guessing the value is rather short, you never get a "lock" (status message viewable on screen), and MythTV tries to tune repeatedly.  This is a restored DB, and you didn't delete/reconfigure tuner(s), right?

---

### Post by grg3 on 2012-05-31
OK! Here we go again!

I dug around in an old backup and found my original channel change script (which I should have used in the first place) and this is what I found:

```
REMOTE_NAME=dct2000
 irsend SET_TRANSMITTERS 2
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME OK
 exit 0
```

The key thing being the correct remote name and the "OK" at the end. That takes care of the endless looping.

SO, in summary this transceiver works with 12.04 (assuming the monkey at the keyboard sets things up correctly) while my original transceiver did not. Perhaps this is due to some change in the driver. I noticed that there appears to be some differences in the mceusb kernel module compared to the past.

The good news is that things are working again and perhaps someone will learn from my mistakes by reading this thread.

Thank you to all who helped and encouraged me!

---

### Post by anonymousdog on 2012-05-31
Glad you got it sorted, but I thought you stated the prior script ran fine in a terminal.  If the remote name was wrong and the irsend command wasn't valid, it wouldn't have worked properly.

---

### Post by grg3 on 2012-05-31
Evidently, having the OK at the end, as opposed to SELECT, prevents the loop from within mythtv. Running the script from the commandline worked because it didn't matter. The required digits were trasmitted and the script was done. 

The only other person I could find with this problem was back in 2010 and he never said if he figured it out. Makes you wonder...

I stumbled on a perl channel change script [http://www.mythtv.org/wiki/LircChannelChanger]("http://www.mythtv.org/wiki/LircChannelChanger") while researching this issue. I may have to see if it works any better than the one I have been using, but for now I am happy that at least one of my two blasters will work with 12.04.

---

