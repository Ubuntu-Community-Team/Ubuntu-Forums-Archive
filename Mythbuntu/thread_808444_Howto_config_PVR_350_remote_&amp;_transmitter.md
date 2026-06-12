---
title: "Howto config PVR 350 remote &amp; transmitter?"
date: 2008-05-26
forum: Mythbuntu
---

### Post by lenn-art on 2008-05-26
My PVR350 card has a remote control (A415-HPG) and a transmitter. I found the wiki on myth.org ([http://www.mythtv.org/wiki/index.php/PVR-350_Remote_Quick_Guide](http://www.mythtv.org/wiki/index.php/PVR-350_Remote_Quick_Guide)) and the lirc files ([http://lirc.sourceforge.net/remotes/hauppauge/](http://lirc.sourceforge.net/remotes/hauppauge/)) but i dont get the remote working :(

Can anyone with the same hardware help me? A screenshot of MCC / IR or something! Thanks ...

---

### Post by Bal_Zac on 2008-05-26
What do you mean by transmitter?  My 350 only came with a remote and a reciever which plugs into the 350's headphone jack looking port ( I think it's a 3.5 mm analog jack or something like that).  If that's the case, just start up mythbuntu-control-center, and under the section IR select remote, and set it up as in the picture below, ignoring the part about the ir transmitter

If you also made a homemade serial ir transmitter, see this thread as per installation of the 350 remote and the serial blaster, as you have to manually edit a few files.
[http://ubuntuforums.org/showthread.php?t=789608&highlight=ir+blaster](http://ubuntuforums.org/showthread.php?t=789608&highlight=ir+blaster)

---

### Post by Bal_Zac on 2008-05-26
Also, I forgot, but you don't need to fill in any of the greyed out boxes.  Just check use remote control, and select Hauppage TV card.  The rest should be filled in automatically for you.

---

### Post by usererror on 2008-05-26
Does the remote AT ALL??  If the IR receiver is plugged in run 'irw' in a terminal window via SSH or locally and see if it recognizes the remote when you push a button, that will tell you at least that the remote is successfully reaching the receiver.

Make sure your .lircrc file is in the correct user home folder.

The first time I setup my remote it could not get it to work because I was putting it in the wrong home folder.

---

### Post by lenn-art on 2008-05-27
@Bal_zac: transmitter is the receiver .. i think ... i supposed that the transmitter is the thiny little receiver that goes in the (2,5mm ;-) ?) jack. Or is it something else?

@usererror: On other IR-device's (like my TV, audio), i see that my IR is working: the led on the TV / audio is blinking when i push a button. When i use the command # sudo irw i get the msg 'connect: connection refused :?

---

### Post by usererror on 2008-05-27
> @usererror: On other IR-device's (like my TV, audio), i see that my IR is working: the led on the TV / audio is blinking when i push a button. When i use the command # sudo irw i get the msg 'connect: connection refused :?

That is correct, the light will blink when you point your remote at the receiver.

try running irw not as sudo. I don't have to run it as sudo.

But if irw still does not run then you've got an issue with lirc (i think).

Is the service running?

what is the model of your remote?

---

### Post by loyd86 on 2008-05-27
I am having trouble with my remote as well. I followed the direction to get it working just as was said here and elsewhere. I ran dmesg and got
```

[ 3585.710986] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[ 3585.711036] lirc_dev: lirc_register_plugin: sample_rate: 10

```
So it seems to be working right

I ran
```

ps -A | grep lircd

```
and it found it running.

I looked at my remote, with a camera and the IR LED always seems to be on.

I have the reciever plugged in, but whenever I run
```
 irw 
``` I get nothing.

---

### Post by IamHungry on 2008-05-28
I am having the same trouble.  This is my first build and things are going pretty smooth.  The remote works fine configured as Hauppauge TV-card in MCC.  

According to the Hauppauge web site: 

[http://www.hauppauge.com/pages/products/data_pvr350.html](http://www.hauppauge.com/pages/products/data_pvr350.html) 

"Included in the WinTV-PVR-350 package
Infra-red remote control receiver with a 1 meter extender cable
Infra-red remote control transmitter"

I am having a hell of a time getting ir commands to be sent by it.  I saw this  
[https://bugs.launchpad.net/mythbuntu/+bug/222250](https://bugs.launchpad.net/mythbuntu/+bug/222250)  
and this
[http://ubuntuforums.org/showthread.php?t=742672](http://ubuntuforums.org/showthread.php?t=742672)

But I have no answers.:)

---

### Post by gfowler on 2008-05-28
> **loyd86 said:**
> I am having trouble with my remote as well. I followed the direction to get it working just as was said here and elsewhere. I ran dmesg and got
```

[ 3585.710986] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[ 3585.711036] lirc_dev: lirc_register_plugin: sample_rate: 10

```
So it seems to be working right

I ran
```

ps -A | grep lircd

```
and it found it running.

I looked at my remote, with a camera and the IR LED always seems to be on.

I have the reciever plugged in, but whenever I run
```
 irw 
``` I get nothing.

Hi,
You may already have solved your issue, I had one similar and the problem was the barrel of the plug for the IR receiver was shorted to the case of the computer because the PVR-350 card was cocked in the computer slot. Not withstanding a bad sensor, bad remote, batteries in remote, and gremlins in the works, irw should give you a response if the lirc daemon is up and running, 'ls -la /dev/lirc*' (without the single quotes) should give you /dev/lirc0 and /dev/lircd.  If not try restarting the lirc daemon with 'sudo /etc/init.d/lirc restart' and check logs for errors.

Jerry

---

