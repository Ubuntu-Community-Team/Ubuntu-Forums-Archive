---
title: "hdhomerun IR setup"
date: 2008-03-16
forum: Mythbuntu
---

### Post by jason456 on 2008-03-16
I kind of new to the mythtv. I have been playing around with it for the last couple of weeks. So far everything has worked out great until I tried to set up my remote with IR on the hdhomerun. I have spent the last couple of days searching everywhere. I have several remotes to try. I have been currently trying the series 2 tivo. I think my problem resides before the remote. I have followed the instructions on the silicon dust website but when I get to "irw" it does nothing. I then try to use irrecord but first I need to remove the /var/run/lircd.pid because it says "there seems to already be a lircd process with pid 6050" 6050 seems to change as I use the command "sudo lircd -H udp -d 5000" then remove /var/run/lircd.pid. Does the pid need to be 5000? I go into nano text editor before I remove it and start another process and the only thing in it is the number 6050 or whatever it changes too. Should it be 5000? The irrecord does nothing as well. It just times out after about 10second. Could someone please guide me in the right direction it would be greatly appreciated.  I just need to know what lirc files need to go where.  I think everything is in the right spot.  Maybe my configuration of those files is messed up.  The hdhomerun tuner works fine  it's just the IR I can't get to do anything.

---

### Post by foxbuntu on 2008-03-18
If you are using MythTV why are you setting up an HDHR with IR? MythTV will control it VIA the backend over the network.

---

### Post by jason456 on 2008-03-18
The HDHR is the only IR I have on the system.  I want to use a remote to control the Mythtv frontend.  My only other option is to use a serial IR, which I have ordered parts to make.  I was just hoping to be able to use the HDHR IR then it would be one less device.

---

### Post by foxbuntu on 2008-03-19
Ok, I understand now. the pid file is just the process lock for lirc it can be anything. Im not familiar with using the HDHR for this but if anyone else has ideas I would be intrested in hearing the fix for this as well.

---

### Post by spalVl on 2008-03-19
I've done it on Knoppmyth, should be similar.   Used this howto (see lirc)

[http://www.silicondust.com/wiki/hdhomerun/instructions/mythtv](http://www.silicondust.com/wiki/hdhomerun/instructions/mythtv)

just remember to use sudo before command.   Here is my /etc/lirc/hardware.conf

> 
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS="-d 5000"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="udp"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_dev"

After got that setup use irrecord to setup your remote's lircd.conf file and irw when complete to test.

---

