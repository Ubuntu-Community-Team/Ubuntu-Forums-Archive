---
title: "IRBlaster"
date: 2009-02-15
forum: Mythbuntu
---

### Post by mostr on 2009-02-15
I'm still having problems getting my irblaster to work to change channels on my bell receiver.

I just reinstalled mythbuntu 8.1 and only setup the irblaster. I will leave the receiver until I get the box changing channels.

My irblaster is on com1, and I have that set in /etc/lirc/hardware.conf.

I have picked the dish profile and I copied the change-channel-lirc.pl file to /usr/local/bin.

Is there another step I need to do? I get all OK's when I restart the service.

It's pretty straightforward I thought.

Thanks.

---

### Post by mostr on 2009-02-16
Bump.

---

### Post by azmyth on 2009-02-16
When you say not working. Do you mean it's just not changing the channel or it's not sending out any signals?

---

### Post by mostr on 2009-02-16
It's not changing the channel. It initializes ok, and sets up the files in /dev, but when I try the channel change script, it doesn't change the channel.

I don't know how else to test the blaster. I know how to test the receivers, but I'm not on that stage yet.

I'm moving to mythbuntu from fedora + mythpackages. So I know all the hardware works, it was working before I formatted my drives.

I'm not sure how else or what to test next.

Thank you for the reply.

---

### Post by azmyth on 2009-02-16
I just did the same moved from F8 to Mythbuntu. Take a digital camera and turn the camera on and hold the ir transmitter up to the lense and then execute a command to make the blaster send a command. You should see this in the camera's digital viewer.

---

### Post by gfowler on 2009-02-16
> **mostr said:**
> It's not changing the channel. It initializes ok, and sets up the files in /dev, but when I try the channel change script, it doesn't change the channel.

I don't know how else to test the blaster. I know how to test the receivers, but I'm not on that stage yet.

I'm moving to mythbuntu from fedora + mythpackages. So I know all the hardware works, it was working before I formatted my drives.

I'm not sure how else or what to test next.

Thank you for the reply.

Do you get any errors when you try sending a command lirc deamon?

irsend -d /dev/lircd send_once dish power_on

The above assumes only one lirc daemon and that you are using the dish codes, if not substitute the appropriate ones.  If you have an ir receiver set up check the sequence of the includes in /etc/lircd.conf.  In 8.04 if the transmiter include was not before the receiver include things wouldn't work.  Of course YMMV!

---

### Post by lafflam on 2009-03-25
I think I am having a similar problem as the original poster.

My setup:
Mythbuntu 8.10
Dish 322 satallite receiver, composite #1 output feeding into...
Pinnacle 800i composite input
Standard MythTV LIRC RS232 IR Blaster from [http://www.irblaster.info](http://www.irblaster.info)
SchedulesDirect account for program guide

lirc and my external channel changer script works perfectly for Myth to change channels on my satellite receiver in order to record *scheduled programs*.

My external channel changer script is in two parts. Myth calls change-channel-lirc.sh which looks like this:

```
/path/to/change-channel-lirc2.sh ${channel} &
```

change-channel-lirc2.sh looks like this:

```
REMOTE_NAME=dish
irsend -d /dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend -d /dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend -d /dev/lircd SEND_ONCE $REMOTE_NAME select
```

Both files are executable by all.

Again, this works perfectly for recording *scheduled programs*.

However, when I watch live TV (Watch TV from the main MythTV menu), I can watch the last channel Myth was recording. But I can't change channels from my keyboard.

If I type a new channel on my keyboard and hit Enter, the *Myth OSD* displays the desired channel on screen, the picture freezes for a few seconds, the *Myth OSD* briefly displays the new channel and program summary for the new desired channel, but the actual channel does not change. In fact, the *Dish OSD* displays the briefly displays the old channel and program summary.  

In other words, if I were watching Commedy Central via live MythTV, and typed in the channel for CNN, the Myth OSD appears to indicate that it thinks it changed channels to CNN, but the Dish OSD confirms that the channel stays on Commedy Central.

It's like the variable ${channel} uses the new channel digits I type for the Myth OSD and program guide, but sends the "last channel watched" digits to lirc.

Important note...if I fire up a command prompt and enter something like

```
irsend -d /dev/lircd SEND_ONCE dish 2 0 9 select
```

then the channel changes as expected, so I believe I have lirc set up correctly (but I assume Myth would remain unaware of the channel change).

I just want to be able to type a new channel on my keyboard while watching live TV and have Myth use lirc to change the channel on my Dish receiver.

What am I missing?

TIA,

Jim

---

### Post by lafflam on 2009-03-25
FIXED MINE

I changed ${channel} to $1 in change-channel-lirc.sh

That's it. That fixed my problem.

Hope this helps more ppl than me :-)

---

