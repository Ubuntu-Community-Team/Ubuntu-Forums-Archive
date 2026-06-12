---
title: "External Channel Change Command"
date: 2009-07-26
forum: Mythbuntu
---

### Post by dsbw on 2009-07-26
Is there a list of external channel change commands anywhere?

I'm trying to get MythTV to change channels on my DirecTV H23.

At the command line I can issue an irsend and it will work, but I'm not sure how to relate that to the setting in myth.

Thanks!:KS

---

### Post by newlinux on 2009-07-27
You need to create an script to change channels and then setup mythbackend to use that script to change channels. More on that below:

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)


[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV#Configuring_Myth_Backend](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV#Configuring_Myth_Backend)

shows how to set it up in the mythbackend once you have your channel change script created properly (test it from the commandline).

The link below has information about controlling the set top box with a serial or USB connection (I suspect the instructions for the H20 and H21 will work with an H23
[http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial](http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial)

Hope this helps...

---

### Post by dsbw on 2009-07-29
Thanks, NL, I'll give it a try. 

Am I wrong to be surprised by there not being an existing file?

---

### Post by newlinux on 2009-07-29
there should be channelchange scripts in:

/usr/share/doc/mythtv-backend/contrib/channel_changers

---

### Post by dsbw on 2009-07-31
> **newlinux said:**
> there should be channelchange scripts in:

/usr/share/doc/mythtv-backend/contrib/channel_changers

Am I just overthinking this? There is a setting for direcTV receivers in myth setup. Huh. That still doesn't tell Myth which tuner needs the channel changing script.

OK, here's what I did. I took the Perl script from [this page]("http://thecrane.wordpress.com/category/mythtv/pvr-150/"):

```
#!/usr/bin/perl
# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = “blaster”;

sub change_channel {
my($channel_digit) = @_;
system (”irsend SEND_ONCE $remote_name $channel_digit”);
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
```

chmodded it to be executable, and this script works to change the channel outside of myth. I'm not sure it's working inside of myth yet. (It thinks it's recording something for the next half-hour, and won't let me stop it.)

---

### Post by newlinux on 2009-07-31
I've used a channel changer with cable boxes, and the only thing I had to do was have a workign script and put the path to it in the tuner's input connections channel change script location. I used to do this for firewire back in myth .20.2 - not sure if things have changed since then.

---

