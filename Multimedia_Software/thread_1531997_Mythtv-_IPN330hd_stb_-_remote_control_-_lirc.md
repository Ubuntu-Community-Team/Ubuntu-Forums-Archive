---
title: "Mythtv- IPN330hd stb - remote control - lirc"
date: 2010-07-15
forum: Multimedia Software
---

### Post by vision06 on 2010-07-15
Mythtv- IPN330hd stb - remote control - lirc

Hello all,

I am currently trying to find a lircd file to control the ipn330hd stb (AT&T uverse).  I have tried different files but I haven't had any luck. I am wondering if anybody had any success controlling this STB.

I am currently using:

1) Ubuntu 10.04
2) lircd 0.8.6

I did find this file that sometimes works with the STB.  But it is not complete:sad:

begin remote

name ser1
flags RAW_CODES|CONST_LENGTH
eps 30
aeps 100

ptrail 0
repeat 0 0
gap 96946

begin raw_codes

name 1
450 150 300 200 200 600
200 200 250 700 250 350
250 200 250 200 250 200
250 200 200 550 200 400
250 550 200 250 250 200
200 250 150 450 200

name 2
500 150 300 150 250 550
250 200 200 750 200 400
200 250 200 200 250 200
250 550 200 600 200 400
150 600 200 250 200 250
200 250 200 550 200

name ok
500 200 200 250 200 550
250 200 150 800 250 350
250 200 250 200 150 300
200 250 200 550 200 400
200 600 200 400 200 400
200 750 200 250 200

end raw_codes

end remote

Thank you.

---

### Post by vision06 on 2010-07-22
I was able to find a configuration that will work with this STB.  I used the config for the 
Motorola VIP1200 ([link]("http://lirc.sourceforge.net/remotes/motorola/VIP_1200")) with the serial ir blaster from [www.irblaster.info]("http://www.irblaster.info/").

Thank you..

---

### Post by wileecoyote67 on 2010-07-29
> **vision06 said:**
> I was able to find a configuration that will work with this STB. I used the config for the 
Motorola VIP1200 ([link]("http://lirc.sourceforge.net/remotes/motorola/VIP_1200")) with the serial ir blaster from [www.irblaster.info]("http://www.irblaster.info/").
 
Thank you..
 
Wow, this is great news! Thanks vision06!!! I had given up on using MythTv as a backend simply because I couldnt get it to work correctly with the blasters hooked to my IPN330HD STB's. I will try this config file this weekend!
 
On a side note, do you think it matters that I am using the Microsoft blasters?

---

### Post by Lepy on 2010-08-07
I recently got uverse with an IPN330hd stb but have only just now got around to setting it up with myth. Thanks for the link to the VIP1200 config. It works great with the IPN330hd. 

Using an MCE remote with 2 blaster ports, I was able to update the lircd.conf entries and send 'irsend -d /dev/lircd SEND_ONCE att POWER' to turn the box on and off while 'irsend -d /dev/lircd SEND_ONCE att SEVEN' will change to channel 7.

I am having problems getting a channel change script setup with livetv. When using my old stb channel change script, livetv starts correctly, but obviously channels do not change:
```
:~/scripts$ cat change-channel-lirc-DCH-70.pl 
#!/usr/bin/perl
# Created by regx
# Simple perl script to change channels for Myth

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = 'DCT2000';

$channel=$ARGV[0];
@channel = split(//,$channel);
foreach(@channel){
        #print $_ . "\n";
        `irsend SEND_ONCE $remote_name $_`;
}
sleep 1;
`irsend SEND_ONCE $remote_name ENTER`;


```

So, I tried using a different script for changing channels. This box has a 'screen saver' mode where OK must be hit on the remote after powering on or being idle for a while, so I decided to try the suggested script for dish network boxes with similar behavior:
```
:~/scripts$ cat change-channel-lirc-ipn330hd.sh
 #!/bin/sh
REMOTE_NAME=att
irsend SET_TRANSMITTERS 1 #this is the plug on the left when looking at the back of IR receiver, 2 is the other one
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 

```

Livetv fails to start with a 'GetEntryAt(-1) failed.' error similar to what is described in this thread: [http://www.gossamer-threads.com/lists/mythtv/users/356905](http://www.gossamer-threads.com/lists/mythtv/users/356905)

Changing back to the old config and changing the remote name to att causes live tv to start but does not change channels and brings up the add channel to favourites tab (possibly because of the ENTER command). As suggested in the linked thread, I tried changing the suggested script sleep times in a range from 0.2 to 2, but Livetv still fails to start.

Any suggestions? Or could someone help me with the perl syntax to get and OK press before channel changes? Thanks!

---

