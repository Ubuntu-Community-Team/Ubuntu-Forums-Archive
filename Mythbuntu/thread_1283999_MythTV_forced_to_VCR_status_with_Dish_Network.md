---
title: "MythTV forced to VCR status with Dish Network?"
date: 2009-10-06
forum: Mythbuntu
---

### Post by Jeconti on 2009-10-06
Alright, so update to the other post this weekend.

I have connected the Dish Network Set Top box to my Happauge HVR 1600 via the S-Video/RCA hookups. The problem with this set up is that I can not change the channels from MythTV. I am forced to use the remote that came with the STB to change channels.

Of course, this means the DVR function won't work properly unless I preset the channel before Myth is scheduled to start recording, basically making it an early VCR.

Is there a way to allow Myth to change the channel on the STB?

---

### Post by gfowler on 2009-10-06
> **Jeconti said:**
> Alright, so update to the other post this weekend.

I have connected the Dish Network Set Top box to my Happauge HVR 1600 via the S-Video/RCA hookups. The problem with this set up is that I can not change the channels from MythTV. I am forced to use the remote that came with the STB to change channels.

Of course, this means the DVR function won't work properly unless I preset the channel before Myth is scheduled to start recording, basically making it an early VCR.

Is there a way to allow Myth to change the channel on the STB?

You need to make or buy an ir blaster and configure it.

[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV)

Jerry

---

### Post by Jeconti on 2009-10-06
I have the one that came with the capture card originally. But what I don't understand is how the card will communicate with the box to change the tuner when I schedule a recording.

---

### Post by ian dobson on 2009-10-06
Hi,

You don't need a IR receiver. Rather you need an IR blaster.

What you do is setup mythtv to use a script that activates the Blaster which sends the correct RC5 (Infrared signal) to the Dish network to change channels as if you pressed a button on the remote.

Regards
Ian Dobson

---

### Post by Jeconti on 2009-10-06
Is there anyway to do that outside of the Mythbuntu Control Center? The box currently does not have an Internet connection.

---

### Post by Jeconti on 2009-10-07
Alright, we're making some progress.

I tried the script located here [http://www.gossamer-threads.com/lists/mythtv/users/373511](http://www.gossamer-threads.com/lists/mythtv/users/373511)

```

#!/usr/bin/perl
# file /usr/local/bin/change-channel-lirc.pl
#

# name the file channel-change-lirc.pl then place in /usr/local/bin,
remember to chmod +xr
#
# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
#
$remote_name = "dish";
# Next two lines added to get rid of advertisement that comes up
# on Vip612 dish receive when inactive and to
# bring the VIP612 out of "low power" mode..
system ("irsend -d /dev/lircd SEND_ONCE $remote_name power_on");
sleep 5;
system ("irsend -d /dev/lircd SEND_ONCE $remote_name select");
sleep 1;


sub change_channel {
my($channel_digit) = @_;
system ("irsend -d /dev/lircd SEND_ONCE $remote_name
$channel_digit");
sleep 1;
}
# allow for four digit channels such as 9404 on Dishnetwork
$channel=$ARGV[0];
sleep 1;
if (length($channel) > 3) {
change_channel(substr($channel,0,1));
change_channel(substr($channel,1,1));
change_channel(substr($channel,2,1));
change_channel(substr($channel,3,1));
} elsif (length($channel) > 2) {
change_channel(substr($channel,0,1));
change_channel(substr($channel,1,1));
change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
change_channel(substr($channel,0,1));
change_channel(substr($channel,1,1));
} else {
change_channel(substr($channel,0,1));
}
system ("irsend -d /dev/lircd SEND_ONCE $remote_name select"); 
```

I modified the script to remove the part specific to his model DishNetwork STB and filled in the remote name as mceusb, then ran the script from the cl. I got back the following errors.

[email]jesse@MythBox:~$/usr/local/bin/change-channel-lirc.pl[/email] 2
irsend: not enough arguments
sh: 2: not found
irsend: command failed: SEND_ONCE mceusb select
irsend: unknown command: "select"

I'll be the first to admit I known nothing about scripting or anything of that nature. I'm taking shots in the dark, so any help would be appreciated.

---

### Post by ian dobson on 2009-10-07
Hi,

Does "dish" exist in your /etc/lircd.conf?

What do you get when you go to the terminal and do:-
irsend -d /dev/lircd SEND_ONCE $remote_name 100

when 100 is a valid channel.

Regards
Ian Dobson

---

### Post by Jeconti on 2009-10-07
my /etc/lircd.conf was generated automatically by the mythbuntu control center. it's hard to copy it here because the box currently doesn't have an internet connection.

remote: include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

transmitter: include /usr/share/lirc/transmitters/dish/general.conf

100 is not a valid channel, but 105 is.

irsend comes back with "not enough arguments"

---

### Post by Jeconti on 2009-10-07
On another interesting note, when I press guide on the remote for the STB, the ir receiver on the computer is picking it up. I'll run irw to see whatelse it picks up

---

