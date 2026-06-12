---
title: "lirc only works when started manually"
date: 2010-03-25
forum: Mythbuntu
---

### Post by jdk82 on 2010-03-25
Hi all,

I have a problem with lirc and the xbox dvd dongle. If I start lirc using

```
sudo services lirc start
```

irw will connect to the socket, but I get no response to keypresses. On the other hand, if I start lirc manually

```
sudo lircd -n --device=/dev/lirc0 -o /dev/lircd /etc/lirc/lircd.conf
```

both irw and mythtv work just fine. I have tried just about every configuration of lirc that I can think of with the same result. Here is my current hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET="/dev/lircd"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS="''"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
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

# Receiver settings required by gnome-lirc-properties
#RECEIVER_MODEL="UDP\ Port\ Listener"
#RECEIVER_VENDOR="Generic"

# Remote settings required by gnome-lirc-properties
#REMOTE_MODEL="Linux\ Input\ Layer\ compatible\ Remote"
#REMOTE_VENDOR="Generic"
```

I have also verified that xpad is not loading, obviously it works if I start lirc without using the scripts. Any help, even just explaining how to get lirc to run without backgrounding (tried several switches in hardware.conf, lirc seems to ignore some of them), or how to enable logging (googled for that one, couldn't find it) would be greatly appreciated. If anyone needs any further info, I will be happy to provide it.

Josh

---

### Post by jdk82 on 2010-03-25
Okay,

I figured out where the log was (duh), and this is what shows up when I start lirc using the service command:

```
@mythtv:/etc/lirc$ tail /var/log/syslog
Mar 25 18:09:01 mythtv CRON[3178]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 25 18:13:25 mythtv lircd-0.8.6[3250]: could not open config file ''''
Mar 25 18:13:25 mythtv lircd-0.8.6[3250]: No such file or directory
Mar 25 18:13:25 mythtv lircd-0.8.6[3251]: lircd(default) ready, using /dev/lircd
Mar 25 18:14:12 mythtv lircd-0.8.6[3251]: caught signal
Mar 25 18:17:01 mythtv CRON[3293]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 25 18:17:59 mythtv lircd-0.8.6[3345]: could not open config file ''''
Mar 25 18:17:59 mythtv lircd-0.8.6[3345]: No such file or directory
Mar 25 18:17:59 mythtv lircd-0.8.6[3346]: lircd(default) ready, using /dev/lircd
Mar 25 18:18:04 mythtv lircd-0.8.6[3346]: accepted new client on /dev/lircd
```

I think the relative part is
```
mythtv lircd-0.8.6[3250]: could not open config file ''''
```
I have the config file specified in hardware.conf. Any ideas??

Josh

---

### Post by phroman on 2010-03-25
Hi jdk82, maybe a dumb question but are you sure your lircd.conf file is the correct one for the xbox, and that it is indeed in the correct location.  Look at your /etc/lirc/lircd.conf file.  Depending on your configuration, that file may just link to the actual lircd.conf file that is used by lirc.  So, you'd need to place your lircd.conf file there, or re-point it to wherever you want it to be.  Good luck, let me know what happens.

---

### Post by jdk82 on 2010-03-26
Hi phroman,

Yes, I'm sure that the lircd.conf file is correct. It is just an include line, but I've verified that the file it points to is correct, and starting lirc manually with the options included above points lirc to the same file, which works. The only thing I can think of is that starting lirc using
```
/etc/init.d/lirc start
```

or

```
service lirc start
```
is somehow causing it to ignore the hardware.conf file?

Josh

---

### Post by jdk82 on 2010-03-26
Hi all,

Okay, I fixed it. I changed
```
REMOTE_LIRCD_ARGS="''"

```
to
```
REMOTE_LIRCD_ARGS="'/etc/lirc/lircd.conf'"
```
which resulted in
```
mythtv lircd-0.8.6[6749]: could not open config file ''/etc/lirc/lircd.conf''
```
so I removed the single quotation marks from that line, making it this
```
REMOTE_LIRCD_ARGS="/etc/lirc/lircd.conf"
```
And lirc now opens the config files correctly. So, could someone with a little more experience tell me if I should file a bug against this?

Thanks,

Josh

---

### Post by phroman on 2010-03-26
Oh man, I should have noticed that, sorry.  Well cool, glad you got it fixed.

---

