---
title: "USB-UIRT DISH Network Lirc MythTV Works!"
date: 2007-10-17
forum: Mythbuntu
---

### Post by Solarbaby on 2007-10-17
I'm using the **Lirc with USB-UIRT & Dish Network & It All works Perfectly**.
My Remotes are Echostar 5.3 IR 148784 & 142301
These remotes works on a good number of Dish Receivers.
I installed MythTV with the MythBuntu 7.10RC CD and Lirc was installed by default.
I made no modifications to Lirc other then what is listed here in this post.
Also I've not made any system updates such as apt-get install update & apt-get install upgrade
I plan on doing this later, I doubt it will make any differences as to this working or not.
Just in case you might want to do your upgrades later. Originally I had many problems 
making the Dish and The USB Uirt work together under Lirc, 
and so I Emailed usb-uirt support and they replied prompty with this..

> Dish remote is a 56KHz based remote, and therefore the USB-UIRT's long-range IR receiver 
cannot see this remote. The USB-UIRT can learn from a 56KHz remote normally by using its
special short-range 'learn' IR receiver. However, I don't believe the Lirc plugin 
(written by a user) uses the short-range sensor, and that is why you cannot learn the 
remote in Lirc.

cd /etc/lircd/

My lircd.conf file 


```
begin remote 

  name dish 
  bits           16 
  flags SPACE_ENC 
  eps            30 
  aeps          100 

  header        400  6100 
  one           400  1700 
  zero          400  2800 
  ptrail        400 
  gap          6200 
  min_repeat      4 
  toggle_bit      0 

  frequency    40000 

      begin codes 
          power                    0x0000000000000800 
          0                        0x0000000000004400 
          1                        0x0000000000001000 
          2                        0x0000000000001400 
          3                        0x0000000000001800 
          4                        0x0000000000002000 
          5                        0x0000000000002400 
          6                        0x0000000000002800 
          7                        0x0000000000003000 
          8                        0x0000000000003400 
          9                        0x0000000000003800 
          up                       0x0000000000006800 
          cancel                   0x0000000000004800 
      end codes 

end remote 
```


My hardware.conf file

```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/ttyUSB0"
LIRCD_OPTIONS="-H uirt2_raw -d /dev/ttyUSB0"
#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="uirt2_raw"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```


Now that my Configuration Files have been updated I reset lirc by typing

/etc/init.d/lirc restart

Now type this to see if your transmitting to your Dish Receiver

irsend -d /dev/lircd SEND_ONCE dish power

If all went well, it's time to prepare Myth.  Myth won't know how to change channels 
unless you tell it where to find the script that shakes hands with Lirc So heres what you do.

Open MythTV Backend Setup, Select #4.Input Connections Then under External Channel Changer Command
type /usr/local/bin/channel.pl  Tab down to Finish and your done.

Now you need to create channel.pl You can find a demo one here: 
/usr/share/doc/mythtv-backend/contrib/channel_changers


Heres Mine and it belongs in /usr/local/bin/

```
#!/usr/bin/perl



# make sure to set this string to

# the corresponding remote in /etc/lircd.conf

$remote_name = "dish";



sub change_channel {

        my($channel_digit) = @_;

        system ("irsend -d /dev/lircd SEND_ONCE $remote_name $channel_digit");

        sleep 1;

}



$channel=$ARGV[0];

sleep 1;

if (length($channel) > 2) {

        change_channel(substr($channel,0,1));

        change_channel(substr($channel,1,1));

        change_channel(substr($channel,2,1));

} elsif (length($channel) > 1) {

        change_channel(substr($channel,0,1));

        change_channel(substr($channel,1,1));

} else {

        change_channel(substr($channel,0,1));

}

system ("irsend -d /dev/lircd SEND_ONCE $remote_name ENTER"); 
```

Thats It.  You should be able to Record and Switch Channels Via MythTV.

---

### Post by karlec on 2007-10-17
Great! Someone with a somewhat similar setting.
What kind of tuner do you have in your mythbox?
How exactly do you get the dish signal into your box?

---

### Post by Solarbaby on 2008-01-09
I have a Hauppauge 350 TV Tuner, and I use SVIDEO from my Dish Network Box to my TV Tuner.

---

### Post by karlec on 2008-04-26
> **Solarbaby said:**
> I have a Hauppauge 350 TV Tuner, and I use SVIDEO from my Dish Network Box to my TV Tuner.

Solarbaby - Can you please post your lircrc?

Thnx

---

