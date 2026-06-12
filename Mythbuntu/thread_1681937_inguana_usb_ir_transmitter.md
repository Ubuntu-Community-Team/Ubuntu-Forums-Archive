---
title: "inguana usb ir transmitter"
date: 2011-02-05
forum: Mythbuntu
---

### Post by crazyone on 2011-02-05
hi i am trying to use an iguana ir transmitter and got the lirc installed form thier website and the driver for it installed. but my problem is when i run the command irsend set_transmitters 1 2 3 4" like the website says to do i get back "irsend: command failed: set_transmitters 1 2 3 4
irsend: hardware does not support sending" it does this with any irsend comand that i use to see if i can get the thing working.

my hardware.conf file looks like this


DRIVER="iguanaIR"
DEVICE="/dev/iguanaIR/0"
#Chosen IR Transmitter
TRANSMITTER="IguanaIR"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="iguanaIR"
TRANSMITTER_DEVICE="/dev/iguanaIR/0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="pace/dct50x.conf"
TRANSMITTER_LIRCD_ARGS=""


any help on this would be great. it is the last part of my media center that i need to get working and then i can have all my channels back. thanks for looking. btw i am running mythbuntu 10.10 64bit if that helps anyone. 
i have tried fallowing [http://www.mythtv.org/wiki/IguanaIR](http://www.mythtv.org/wiki/IguanaIR) and also [http://iguanaworks.net/projects/IguanaIR/wiki/GettingStarted](http://iguanaworks.net/projects/IguanaIR/wiki/GettingStarted) to try and get it working


edit: ok so i jsut was able to get it working by running the comand "lircd -H iguanaIR -d /dev/iguanaIR/0" idk where to make sure it is using the right stuff then becuase i also need it to be able to work with my remote that i use which uses a differnt reciver becuase of it being rf

---

### Post by klc5555 on 2011-02-05
I use 3 of these devices -- 2 on Slackware machines and one on a Mythbuntu box.

The main difficulty with Mythbuntu (after I realized the lirc Mythbuntu  comes packaged with didn't include the IguanaIR driver) was that IguanaWork's own lirc deb package installs to a directory structure that doesn't quite match Ubuntu's, and doesn't clean up the earlier lirc properly.

So check as to whether you have two lircd's. Odds are that your original default Mythbuntu lircd (without Iguana support) is the one actually running in (I think --it's been a while--) /usr/sbin and your spiffy new lircd is sitting unused somewhere like in /usr/local/sbin You'll need to fix this manually, and there are various ways to do so.

Also note that if you have difficulties with the igdaemon itself starting properly, I seem to recall the Iguana startup script (iguanaIR) also ending up in some non-Ubuntu location initially, and having to be moved manually to its proper Ubuntu location under /etc/init.d But it was nearly a year ago and I don't remember for certain.

Once these initial hurdles were cleared, however, the device has performed nearly flawlessly for those pesky Comcast dc50x DTAs, as long as something else is not happening on the USB bus at the exact moment the channel-change script is attempting to transmit through the device.

---

### Post by crazyone on 2011-02-05
ok thanks just looked in those locations and i only have lircd at /usr/sbin not at /usr/local/sbin too so i dont think that is the problem. the igdaemon is running fine form what i can tell.

edit: so after i removed my remotes config from the lircd.conf and the hardware.conf file i am able to run the commands jsut fine. whcih means that the problem must be that i need to have 2 lircd's running one for the remote and one for the transmitter. and just so you know it is a snapstream firefly remote. it is the original rf one.

---

