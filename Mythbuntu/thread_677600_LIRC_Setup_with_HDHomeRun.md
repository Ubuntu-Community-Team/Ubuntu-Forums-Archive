---
title: "LIRC Setup with HDHomeRun"
date: 2008-01-25
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2008-01-25
I'm trying to get mythbuntu working with a hdhomerun's ir receiver.  I'm close but I can't get it working and I could use some help.

I have lircd running and talking to the hdhomerun.  I have a lircd.conf file that knows the remote (Samsung_BN59).  I can run irw and see the remote buttons being pressed.

I've done a .lircrc file and put it in /home/mythtv/.lircrc  (chowned to mythtv:mythtv)

I've put a symbolic link in /home/mythtv/.mythtv/.lircrc back to the /home/mythtv/.lircrc file.  (again all owned to mythtv:mythtv)

I've also put a copy of the .lircrc file in /etc/lirc

Myth doesn't respond to the remote.

I've tried adding an entry in the .lircrc files that says:

begin
  prog = irexec
  button = RIGHT
  config = echo Right Button
end

and irexec doesn't respond to the remote.

I'm assuming I've a disconnect between the lircd getting the remote buttons and dispatching the keypresses to the the application.

My hardware.conf seems the likely source of trouble (especially since I'm just makin this stuff up as I go - spend some time looking at /etc/init.d/lirc and try to guess what to do ;)  ).  The file has:

LIRCD_ARGS="-H udp -d 5000"
START_LIRCMD=false
LOAD_MODULES=true
DRIVER="default"
DEVICE=""
MODULES=""
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCDM_CONF=""

There is talk on the web pages about what lirc devices appear under /dev - I only have /dev/lircd  - there seem to be lots of people setting DEVICE= and MODULES= but I have no idea what to set them to in my case.

Any ideas what I've got disconnected here?

Thanks

---

### Post by Dewey_Oxberger on 2008-01-28
A more focus question here:

Is it MythTV that reads the lircrc file and then uses the lirclib to do the translation?  

If so, where should the lircrc file be placed?

~/.mythtv/lircrc   or ~/.mythtv/.lircrc

---

### Post by Dewey_Oxberger on 2008-01-28
Well, it works now.  I'll post it here for future problem solving...

Myth 0.20.2 likes the lircrc file to be in ~/.mythtv/lircrc

You have to go into the MythTV setup and hunt down the IR Remote setup and tell Myth to listen for the lircd packets.  That was the step I was missing.  Enable it in mythtv.

It looks like the lirc model is applications have to listen for the packets and use the lirc library to help them translate the packets into commands.

If there is one thing I can say about Myth - it has a lot of configuration screens and it's easy to overlook some setting.

---

### Post by jason456 on 2008-03-15
I kind of new to the mythtv.  I have been playing around with it for the last couple of weeks.  So far everything has worked out great until I tried to set up my remote with IR on the hdhomerun.  I have spent the last couple of days searching everywhere.  This is the closest I got to a possible solution.  I have several remotes to try.  I have been currently trying the series 2 tivo.  I think my problem resides before the remote.  I have followed the instructions on the silicon dust website but when I get to "irw" it does nothing.  I then try to use irrecord but first I need to remove the /var/run/lircd.pid because it says "there seems to already be a lircd process with pid 6050"  6050 seems to change as I use the command "sudo lircd -H udp -d 5000" then remove /var/run/lircd.pid.  Does the pid need to be 5000?  I go into nano text editor before I remove it and start another process and the only thing in it is the number 6050 or whatever it changes too.  Should it be 5000?  The irrecord does nothing as well.  It just times out after about 10second.  Could someone please guide me in the right direction it would be greatly appreciated.

---

### Post by petersenjc on 2008-04-11
Did you ever figure this out? I have the same problem.

---

### Post by petersenjc on 2008-08-03
It turns out I had bad hardware. I did an RMA on my hardware and the new one SiliconDust sent worked without any problems.

---

### Post by brenthaag on 2009-03-15
I already had a setup that worked good with the Hauppauge PVR-150's IR receiver.  For the HDHomeRun, it didn't take much to change...this is my tweaked hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="udp"
REMOTE_DEVICE="5000"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"
```

So far, it works great.  I am hoping that the HDHomeRun's IR receiver is a little better than the Hauppauge's and it won't need to be taped or somehow kept from moving (in addition to not having a cable length issue).

jason456 - the PID is totally unrelated the port that the IR data is coming in on.  The process ID is just a number assigned to a process when it is started (usually sequential from when the PC was booted).

---

