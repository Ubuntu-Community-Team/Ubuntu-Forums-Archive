---
title: "Help with lirc-mythtv on Feisty"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by jimp180 on 2007-04-29
I have a Hdhomerun that I want to use as my receiver, I have managed to get it working with mythtv but I need a little help with where to put the commands so it all starts and works at boot time. The hdhomerun uses the udp driver (no driver required) for lirc, so I compiled lirc from source to enable the correct port to be used in hw_udp.c . After this I was able to use irrecord to make a lircd.conf file, then I used a preconfigured lircrc that I changed to work with my lircd.conf and placed it in /home/mythtv/.mythtv. At this point I found I needed irxevent to make mythtv and lirc talk to each other, this wasent installed so I had to apt-get install lirc-x.

now I have all the pieces, but to make it work this is what I have to do:

once I boot I have to ssh into the mythbox and kill the pid for lircd and then; ```
lircd -H udp -d 5000
``` so it starts with udp. after this I need to to start irxevent but I cant do this from ssh because it tells me it cant start a display and then exits. so I have to back out of mythtv and login as a normal user then open a terminal and type; ```
sudo irxevent &
``` after this I log out and let mythtv start back up and I can use my remote.

Could someone please help me with where to put these commands so the programs work and start when they should so when I boot myth just starts with the remote working?

Thanks

---

### Post by jimp180 on 2007-05-01
So nobody knows how to make things work at boot and when x  starts? guess i will just continue to start it like this then

---

### Post by deoncarr on 2007-07-30
hi there, 

I needed to do this myself but couldn't find the proper way of doing it so have hacked my mythfrontend script to start the irxevent. It works and kills irxevent and starts it again whenever mythfrontend is restarted (log out and back in again. I would prefer to do it in autostart.sh but that doesnt seem to be working. 

Its not perfect but beats manually starting it each time.

Anyway edit: /usr/bin/mythfrontend

I have added the two irxevent lines below

```
#!/bin/sh
# Mario Limonciello, March 2007

#source our dialog functions
. /usr/share/mythtv/dialog_functions.sh

#find the session, dialog, and su manager we will be using for display
find_session
find_dialog
find_su

#check that we are in the mythtv group
check_groups

#if group membership is okay, go ahead and launch
if [ "$IGNORE_NOT" = "0" ]; then
        killall irxevent
        /usr/bin/irxevent /home/mythtv/.mythtv/lircrc &

        /usr/bin/mythfrontend.real "$@"
fi
```

---

### Post by deoncarr on 2007-08-09
If you installed mythtv using the feisty guide you probably have openbox installed. 

The mythtvfrontend (and all other windowmanager scripts) iis started in the following script.

/usr/share/mythtv/startmythtv.sh

This would be the correct place to start irxevent.

---

### Post by cobaltcopy on 2007-08-12
jimp180,

I'm wondering if you could help me out. I have a HDHomerun box as well. I have executed the following commands:


```
sudo lircd -H udp -d 5000
hdhomerun_config 1010CFCF set /ir/target "192.168.2.212:5000 no_clear"
```

Each runs without complaint. Then, I try running irw and nothing happens. I know that the IR receiver works

```
22:24:39.139069 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 40
22:24:40.131059 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 38
22:26:56.347231 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 40
22:26:57.339209 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 38
22:28:50.094668 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 40
22:28:51.086625 IP marconi.lan > 192.168.2.230: ICMP marconi.lan udp port 5000 unreachable, length 38

```

---

### Post by cobaltcopy on 2007-08-12
Okay, I made a little bit of headway.

I ran the irrecord command with several options.
```
irrecord --driver=udp --device=5000 rca-universal2vi
```

And I was able to run the irrecord program and generate the following:
```

# brand:                       rca-universal2
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  rca-universal2
  bits           24
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       4015  3958
  one           546  1944
  zero          546   942
  ptrail        562
  gap          64202
  toggle_bit_mask 0x0

      begin codes
          DOWN                     0x7588A7
          UP                       0x7598A6
          LEFT                     0x7568A9
          RIGHT                    0x7578A8
          MENU                     0x7088F7
          GUIDE                    0x71A8E5
          ENTER                    0x7F480B
      end codes

end remote
```

---

### Post by cobaltcopy on 2007-08-13
I solved the problem...I compiled lirc myself and changed the port number.

Am still having trouble with the remote...some of the keys seem sticky.

---

### Post by scram69 on 2007-09-10
If anyone is still watching this thread...

I am also trying to get lirc working with my HDHomerun and Feisty.  I have followed both the Feisty Lirc and SiliconDust HOWTOs, but I cannot get a response from either irw or irrecord.

The original poster mentioned compiling lirc from source in order to enable the correct port.  Does this mean that "lircd -H udp -d 5000" as described in the HOWTO doesn't actually work?  What needs to be changed in the lirc source?  What port (if not 5000) should I be using?

Thanks-

---

