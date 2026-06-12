---
title: "HDPVR-New Setup IR Problems"
date: 2012-10-24
forum: Mythbuntu
---

### Post by dr01dy on 2012-10-24
Hi Everyone, 

I was wondering if you could guide me in the right direction.

I am trying to get channel changes to work with my Hauapage HDPVR to work with 0.25. I am able to get audio and video to work but I am a comcast customer with a Scientific Atlantic 8300HD/4250HDC subscriber.

I tired mythcontoller with all the settings but it wont change the channel.

My next option was to use the built in IR in the HDPVR but I'm not sure what I should be putting under the "External channel change command" in the Input section of mythtv-setup.

Can someone maybe point me in the right direction?

Thanks

Jeff

---

### Post by dannyboy79 on 2012-10-25
> **dr01dy said:**
> Hi Everyone, 

I was wondering if you could guide me in the right direction.

I am trying to get channel changes to work with my Hauapage HDPVR to work with 0.25. I am able to get audio and video to work but I am a comcast customer with a Scientific Atlantic 8300HD/4250HDC subscriber.

I tired mythcontoller with all the settings but it wont change the channel.

My next option was to use the built in IR in the HDPVR but I'm not sure what I should be putting under the "External channel change command" in the Input section of mythtv-setup.

Can someone maybe point me in the right direction?

Thanks

Jeffdid you follow the directions for getting the HDPVR IR enabled?

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Enable_IR_Transmitter](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Enable_IR_Transmitter)

---

### Post by dr01dy on 2012-10-28
I'm getting this..


[ 1699.583376] lirc_zilog: IR unit on Hauppage HD PVR I2C (i2c-0) registered as lirc1 and ready
[ 1699.583381] lirc_zilog: probe of IR Tx on Hauppage HD PVR I2C (i2c-0) done
[ 1699.583416] lirc_zilog: initialization complete
jlloyd@moth:~$ 


but I'm not sure how I tell the IR to change the channel on the STB.. that's where I am getting confused.

I have a SA 8300HD from Comcast

Thanks for helping me

---

### Post by nickrout on 2012-10-29
> **dr01dy said:**
> I'm getting this..


[ 1699.583376] lirc_zilog: IR unit on Hauppage HD PVR I2C (i2c-0) registered as lirc1 and ready
[ 1699.583381] lirc_zilog: probe of IR Tx on Hauppage HD PVR I2C (i2c-0) done
[ 1699.583416] lirc_zilog: initialization complete
jlloyd@moth:~$ 


but I'm not sure how I tell the IR to change the channel on the STB.. that's where I am getting confused.

I have a SA 8300HD from Comcast

Thanks for helping meyou need to set a channel change script in mythtv-setup. 

You may also be able to change via firewire, which is generally more accurate as it misses the "analogue" step of converting to IR and converting back :)

---

### Post by dr01dy on 2012-10-29
I tried using mythchanger using the firewire port but I think my provider disabled changing channels with firewire.

I found this script but I am having no luck when I add it as the external channel change

> #!/bin/bash

 REMOTE_NAME=blaster
 DEVICE=/dev/lircd
 SLEEP_TIME="0.4"
 STB=0_103


 send () {
   irsend --device=${DEVICE} SEND_ONCE ${REMOTE_NAME} ${STB}_${1}
   sleep ${SLEEP_TIME}
 }

 for DIGIT in $(echo ${1} | sed -e 's/./& /g'); do
   send KEY_${DIGIT}
 done

 send KEY_ENTER

 #
 # If your cable box is slow to change channels, sleep so that Mythtv doesn't
 # move forward until after the resolution has changed
 #
 sleep 7


---

### Post by dannyboy79 on 2012-10-29
do you have all the correct lircd config files setup? its not an easy task.

to make sure the HD PVR is actually sending any signals at all you can use a digital camera view window to look at the emitter, there is a response which goes down into the infra-red and blaster pulses can be easily detected. (this will first insure that you are actually controlling the HD PVR correctly)

then you need to make sure you have to correct config to control the SA 8300HD box with correct input codes. Example: channel up, channel down, etc etc

the config you need for the SA 8300HD is here: 
[http://lircconfig.commandir.com/lircd.conf/?viewremote=105](http://lircconfig.commandir.com/lircd.conf/?viewremote=105)

then of course once you have all the correct cofigs in place (one for the HD PVR and one for the set top box) you'll need the script which does the channel changing and what not.

Good luck

---

### Post by dr01dy on 2012-10-29
I added that SE800 config you posted above and rebooted

root@moth:/opt/bin# irsend send_once SAE8000  settings
irsend: command failed: send_once SAE8000 settings
irsend: transmission failed
root@moth:/opt/bin# 


I guess I should also explain I don't want to use a remote, I just want the HDPVR to send the command to the SA8300. Does that make my configuration different ?

Thanks for all the help

---

### Post by dannyboy79 on 2012-10-29
no, it doesn't matter you aren't using a remote (the hd pvr transmitter is acting like the sa 8300HD remote), the hd pvr needs to know the correct codes to send to the SA 8300HD box for it to change the channel etc.

You really need to follow that guide I linked you to.

also, read the note posted here about as of April 2011:
[http://www.mythtv.org/wiki/HD-PVR#IR_Transmitter_Support](http://www.mythtv.org/wiki/HD-PVR#IR_Transmitter_Support)

---

### Post by dr01dy on 2012-10-30
Thanks for all of you're help!

We finally got it working! I had to do this..

[http://www.mythtv.org/wiki/HD-PVR#Steps_to_Enable_IR_Transmitter](http://www.mythtv.org/wiki/HD-PVR#Steps_to_Enable_IR_Transmitter)


but what its doesn't say is that you need to do this every time you reboot..

/etc/init.d/lirc start
sudo modprobe hdpvr
sudo modprobe lirc_zilog

dmesg

> [  169.602007] lirc_dev: IR Remote Control driver registered, major 249 
[  169.618754] lirc_zilog: module is from the staging directory, the quality is unknown, you have been warned.
[  169.619493] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  169.620993] lirc_zilog: probing IR Rx on Hauppage HD PVR I2C (i2c-0)
[  169.621117] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-0) done. Waiting on IR Tx.
[  169.621194] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-0) done
[  169.621203] lirc_zilog: probing IR Tx on Hauppage HD PVR I2C (i2c-0)
[  169.648577] i2c i2c-0: lirc_dev: driver lirc_zilog registered at minor = 0
[  169.648583] lirc_zilog: IR unit on Hauppage HD PVR I2C (i2c-0) registered as lirc0 and ready
[  169.648588] lirc_zilog: probe of IR Tx on Hauppage HD PVR I2C (i2c-0) done
[  169.648614] lirc_zilog: initialization complete



hardware.conf
> #Chosen IR transmitter
TRANSMITTER="HD-PVR"
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""



Thanks for sticking with me and helping me out!

Now I am going to try and wrap this all up in a VM for VMware Fustion/MAC instead of a loud linux machine running

---

### Post by nickrout on 2012-10-31
> **dr01dy said:**
> Thanks for all of you're help!

We finally got it working! I had to do this..

[http://www.mythtv.org/wiki/HD-PVR#Steps_to_Enable_IR_Transmitter](http://www.mythtv.org/wiki/HD-PVR#Steps_to_Enable_IR_Transmitter)


but what its doesn't say is that you need to do this every time you reboot..

/etc/init.d/lirc start
sudo modprobe hdpvr
sudo modprobe lirc_zilog

dmesg




hardware.conf




Thanks for sticking with me and helping me out!

Now I am going to try and wrap this all up in a VM for VMware Fustion/MAC instead of a loud linux machine runningI don't believe that is a very good idea. The HDPVR is flaky enough, let alone trying to make it work on a VM. There has been some stuff on the mailing list, ask some questions there before you try this.

---

