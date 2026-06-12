---
title: "encoders not loading on boot up"
date: 2010-07-04
forum: Mythbuntu
---

### Post by benlyboy on 2010-07-04
I know this has been covered before but I couldn't find the thread. 

My problem is that when I boot my system, most of the time the tuners fail to load. I then have to stop the backend and restart it, this will fix it and they will load

I know from what I remember of the other thread that it has to do with the backend starting up before the tuner drivers have time to load.

I did try the script that was posted but it just seemed to stop my tuners from loading at all...I'm sure it was the way I set it up.

In any case I have just updated to 10.1 and all is good apart from the fact that my tuners still don't load on boot.

I have to take my wife back up to mayo in a couple of weeks and would love to have this fixed before then, as she likes to record her programs why we are gone. and last trip a power cut meant she missed half of what she recorded.

So if someone could walk me through how to fix this I would be very very greatful thanks

---

### Post by ian dobson on 2010-07-04
Hi.

Have a look here [http://ubuntuforums.org/showthread.php?t=1522827](http://ubuntuforums.org/showthread.php?t=1522827) maybe myth-backend is starting before the tuners are fully loaded.

Regards
Ian Dobson

---

### Post by benlyboy on 2010-07-04
Thanks for the reply

Yes I think something like this is what I need. However I was never able to get this script to work that is why I was asking for some help

---

### Post by benlyboy on 2010-07-05
hi all ok took another look at the post that ian dobson mentioned above, I guess i'm not sure how to use the script in it.

This is my mythtv-backend.conf file

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script
```

and this is the script 

```
script	
	#added to ensure that the DVB-T cards are init before myth
	while [ -c !/dev/dvb/adapter0/frontend0 ] || [ -c !/dev/dvb/adapter1/frontend0 ]; do
		date >> /home/mythbox/.mythbackend-init.log
		echo "Mythtv-backend Upstart: DVB-T devices are not yet registered. Waiting 1 second then trying again..." >> /home/mythbox/.mythbackend-init.log
		sleep 1s
	done
	date  >> /home/mythbox/.mythbackend-init.log
	echo  "Mythtv-backend Upstart: DVB-T devices are now registered. Starting mythbackend" >> /home/mythbox/.mythbackend-init.log
        #end of additions - original code below
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```


How do I tire the two together???

---

### Post by ian dobson on 2010-07-05
Hi,

If you add this to your myth-backend.conf config file:-

```

pre-start script
# wait for listen on port 80
  while ! -e /dev/dvb/adapter1; do
    sleep 1;
  done
end script

```

Where /dev/dvb/adapter1 is your dev device.

What this script does is sit in a loop waiting until the dvb device exists in the file system. -e means exist and ! means not. This script is called before calling the myth-backend process.

Regards
Ian Dobson

---

### Post by benlyboy on 2010-07-05
Thanks for the help
 
I have a two questions if you could help that would be great.

First up I have four tuners on two cards, they show up as encoders 5,6,7,8 don't ask why.. in any case should the code be changed to reflect this. 

The other question is, this script should it just be placed at the beginning of the code? 

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

# like say here?????????

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script
```

Thanks again for taking the time

---

### Post by ian dobson on 2010-07-05
Hi,

So does myth actually have 4 real tuners (ie your tuner cards are dual tuners) or do you have 2 tuners and have multirec enabled?

If you go to the terminal and do a ls /dev you'll see a list of device files. What are your tuner cards called (/dev/dvb/adapterX) if the cards are dvb cards.

What cards have you defind in mythtv-setup (v4l,dvb etc).

Regards
Ian Dobson

---

### Post by benlyboy on 2010-07-07
Hay just thought I would say thanks for the replay.

I'm away from home just now but will get home tomorrow, and will look at the things you talked about then and post again.

But one queston I can answer from here is that my mythbox does have 4 tuners. I have two Pvr500's (2 tuners per card) 

will get the rest of the info as soon as I get home thanks

---

### Post by benlyboy on 2010-07-08
hi


Ok i'm home and i did as you asked and put ls /dev into terminal but i'm having trouble understanding the output, i'm just not sure what are the tuners.

```
adsp             loop7               ram8        tty17  tty48    vbi2
audio            mapper              ram9        tty18  tty49    vbi3
block            mcelog              random      tty19  tty5     vcs
bsg              mem                 rfkill      tty2   tty50    vcs1
bus              mixer               root        tty20  tty51    vcs2
cdrom            net                 rtc         tty21  tty52    vcs3
cdrw             network_latency     rtc0        tty22  tty53    vcs4
char             network_throughput  scd0        tty23  tty54    vcs5
console          null                sda         tty24  tty55    vcs6
core             nvidia0             sda1        tty25  tty56    vcs7
cpu_dma_latency  nvidiactl           sda2        tty26  tty57    vcsa
disk             oldmem              sda5        tty27  tty58    vcsa1
dsp              pktcdvd             sequencer   tty28  tty59    vcsa2
dvd              port                sequencer2  tty29  tty6     vcsa3
dvdrw            ppp                 sg0         tty3   tty60    vcsa4
ecryptfs         psaux               sg1         tty30  tty61    vcsa5
fb0              ptmx                shm         tty31  tty62    vcsa6
fd               pts                 snapshot    tty32  tty63    vcsa7
full             radio0              snd         tty33  tty7     vga_arbiter
fuse             radio2              sndstat     tty34  tty8     video0
hidraw0          ram0                sr0         tty35  tty9     video1
hpet             ram1                stderr      tty36  ttyS0    video2
input            ram10               stdin       tty37  ttyS1    video24
kmsg             ram11               stdout      tty38  ttyS2    video25
lirc0            ram12               tty         tty39  ttyS3    video26
lircd            ram13               tty0        tty4   urandom  video27
log              ram14               tty1        tty40  usbmon0  video3
loop0            ram15               tty10       tty41  usbmon1  video32
loop1            ram2                tty11       tty42  usbmon2  video33
loop2            ram3                tty12       tty43  usbmon3  video34
loop3            ram4                tty13       tty44  usbmon4  video35
loop4            ram5                tty14       tty45  v4l      zero
loop5            ram6                tty15       tty46  vbi0
loop6            ram7                tty16       tty47  vbi1

```

thanks again

---

### Post by ian dobson on 2010-07-08
Hi,

Your tuners are /dev/video0, /dev/video1,/dev/video2,/dev/video3

So maybe we just need to make the script wait until /dev/video3 exists.

Regards
Ian Dobson

---

### Post by benlyboy on 2010-07-09
ok 

Ok so do I have to rewrite this line?
And how should it read?

```
while [ -c !/dev/dvb/adapter0/frontend0 ] || [ -c !/dev/dvb/adapter1/frontend0 ]; do
		date >> /home/mythbox/.mythbackend-init.log

```

Also where in the backend config file should it be placed.

sorry if i sound dense

---

### Post by ian dobson on 2010-07-10
Hi.

OK your myth configuration script looks like this:-

```

# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script

```

what you need to do is add this just after the respawn line :-

```

pre-start script
# wait for second PVR500 to come online
  while ! -e /dev/video3; do
    sleep 2;
    date >> /tmp/myth-wait.log
  done
end script

```

Note I've not testsed this really well as I don't have a PVR500 but it looks correct to me. Note the script writes the date/time to a log file /tmp/myth-wait.log everything it goes through the loop.

This script is in the /etc/init directory and should be called something like myth-backend.conf

Regards
Ian Dobson

---

### Post by benlyboy on 2010-07-10
hay thanks for the help

I'm away from home, but will try out the script change the minute I get home.

But work or not I want to thank you for all the help


I will post how i get on

---

