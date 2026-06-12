---
title: "LiveTV fails to start with channel changing script"
date: 2009-11-09
forum: Mythbuntu
---

### Post by Jeconti on 2009-11-09
So I'm back at it again trying to figure this out. I'm running Mythbuntu 9.04 with Myth 0.21

I'm trying to configure an external channel changing script for my DishNet reciever. The reciever is connected to the box via an S-Video cable and component audio cables.

The script I am currently using with my Happauge HVR-1600 provided remote is as follows

```
#!/bin/sh
REMOTE_NAME=mceusb
irsend SET_TRANSMITTERS 1
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 
```

[code from the community help page]("https://help.ubuntu.com/community/MythTV_External_Channel_Changer") 

in backend setup, i have tried the command entry the following ways
bash /usr/local/bin/change-channel-lirc.sh
/usr/local/bin/change-channel-lirc.sh
bash change-channel-lirc.sh
change-channel-lirc.sh

each time I subsequently try to start livetv, a black screen appears for a moment then it dumps me back to the main menu. I have to remove the entry from the backend setup to get it to work.

Ideas?

---

### Post by azmyth on 2009-11-09
What are you trying to change channel with IR Blaster? Firewire?

---

### Post by Jeconti on 2009-11-09
I'm using the IR Blaster that came with the capture card. It transmits to an IR receiver connected by USB.

---

### Post by azmyth on 2009-11-10
Put the IR end up to a digital camera lens and look through the camera's view port then issue a channel change. You should see the view port light up. If yes, then it could be a wrong lirc file. If no, lirc or hardware issue.

---

### Post by Jeconti on 2009-11-11
No, the issue is not with the lirc. I've configured and used the IR Blaster with a previous setup that just had a cable line running to the card. The issue has to be in the channel changing script.

I have a USB IR receiver that also has two spots in the back for an IR transmitter (?) a small black thing no bigger than a lego piece that plugs into the back through what looks like a headphone  jack.

Then I have a black remote control, which I assume is the IR Blaster. It says RC6 ir on the back.

Now, as I understand it, the IR blaster transmits to the IR receiver which gives the information to the box, and then tells the IR transmitter to send the information to the set top box.

Please correct me if I am wrong about any of that.

Now, I think I have it set up correctly. In the Mythbuntu control center, I have the remote configured as a newer model Windows Media Center Philips, et al., and then set the transmitter as the USB Dish receiver option.

But I don't understand why even if I haven't configured that properly, would LiveTV just stop initiating.

Help? Frustration levels rising.

---

### Post by azmyth on 2009-11-12
I ran into a similar situation as I changed cable companies and went from a Motorola to a Scientific Atlanta box. I couldn't get the blaster to change the SA box. I found out I had to set a frequency in the transmitter's lirc.conf file. I'd see if your box has some special setting that is needed. You could do this by googling your box make and model #.

---

### Post by Jeconti on 2009-11-12
Right, and that would help solve any issues that arise if I can get into LiveTV and actually experiment, but I still don't understand why telling Myth that a script exists to change channels externally results in LiveTV not even starting up.

I remember early on in this adventure that LiveTV wouldn't even start if the recordings directory was properly setup. Does the same issue happen with an external script? If it's not configured properly, will LiveTV do the same thing?

---

### Post by Jeconti on 2009-11-13
Solved.

Assistance was provided here.

[http://ubuntuforums.org/archive/index.php/t-900860.html](http://ubuntuforums.org/archive/index.php/t-900860.html)

The trouble was properly configuring the IR transmitter. And yes, LiveTV is just that picky about things being exactly right otherwise it won't start.

---

