---
title: "Streamzap remote control key bounce in 11.10 with MythTV"
date: 2012-01-29
forum: Multimedia Software
---

### Post by jeremybear on 2012-01-29
Symptoms: when pressing certain keys on your remote control, the key appears to have been pressed twice.  For example, when key '1' is pressed, the output is '11'. Not all keys exhibit the same issue.

I spent many frustrating hours trying to solve this problem: there are several threads on the subject applicable to earlier releases and other remote controls, but none of the suggested solutions worked completely for me.

You will need to ensure that your configuration does not recognize the remote control as a keyboard and use instead the functionality of lirc and setserial as built into the kernel.

Here are the steps to follow (I hope I have got these in the right order, because I went round in circles many times before getting to this point):

1. Make sure your system has all the latest 11.10 updates. My kernel version is 3.0.0-15-generic-pae.

2. Configure lirc to use the Streamzap remote:

 $ sudo dpkg-reconfigure lirc 

and select the Streamzap option when prompted.

3. Install mythbuntu-lirc-generator and ir-keytable:

  $ sudo apt-get install mythbuntu-lirc-generator ir-keytable

4. Execute the commands 

  $ mythbuntu-lirc-generator
  $ mythbuntu-lircrc-generator
  $ ir-keytable

   ir-keytable will return something like:

        [INDENT]Found /sys/class/rc/rc0/ (/dev/input/event5) with:
	Driver streamzap, table rc-streamzap
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: LIRC[/INDENT]

   Note the /dev/input/event number (5) and the enabled protocol (LIRC).   If it's showing another protocol, enable lirc by typing:
   
  $ sudo ir-keytable -p lirc

5. Ensure that setserial is configured to use kernel settings, not a local configuration:

 $ sudo dpkg-reconfigure setserial

then when prompted choose the "kernel" option. (This may only apply if you have been fiddling with setserial like I did, to get another remote control working).

6. Change the first block of your lirc hardware.conf file:

   $ sudo gedit /etc/lirc/hardware.conf

[INDENT]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""[/INDENT]

(other lines remain as default)

Note particularly that REMOTE DRIVER should not be "devinput" and REMOTE DEVICE should not be "/dev/input/event(n)" - both settings used to work for me in 10.04 and below, but now we use lirc directly.

7. Save the modified hardware.conf and restart the lirc daemon:

  $ sudo /etc/init.d/lirc restart

8. Now check that the remote key presses are detected by the IR receiver:

  $ irw

  (you should see key codes in the terminal window when remote keys are pressed).  If this does not work, some have suggested low level testing using the command 

$ sudo mode2  

Unfortunately, mode2 is looking for /dev/lirc which no longer exists, so you will first have to do 

$ sudo ln -s /dev/lirc0 /dev/lirc

 so that mode2 will work.  If mode2 fails to generate any output when remote keys are pressed, then your remote is faulty or perhaps you have a flat battery. Resolve this before proceeding.

9. If irw worked as expected in the step above, you are ready to test with the multimedia application, which in my case is MythTV.  Start up MythTV and verify that the remote control works as expected.

10. Finally, customization of key press responses can be made in $HOME/.lirc/mythtv by editing the file to create the keybindings required. The basic ones provided by mythbuntu-lirc-generator may be sufficient for your needs.

---

### Post by apos on 2012-02-17
Thanks Jeremy for the article.

When I configure lirc:

> **jeremybear said:**
> 
2. Configure lirc to use the Streamzap remote:

 $ sudo dpkg-reconfigure lirc 

and select the Streamzap option when prompted.

what did you choose for the receiver?

[LIST]
[*]Custom
[*]None
[*]UART ...
[/LIST]

Seams to work with Custom.

Greets
Axel

---

### Post by jeremybear on 2012-08-05
Hi Axel, 

Sorry for the late reply.  If the configuration works for you with "Custom", that's great, but I scrolled down and found an option for the Streamzap remote control, which is the device I have.  I guess these instructions will work for other remotes also - you just choose the correct model.

BTW I tested the above on 12.04 Precise and it works fine.

Cheers,
Jeremy

---

