---
title: "Channel change script and livetv error"
date: 2010-08-09
forum: Mythbuntu
---

### Post by Lepy on 2010-08-09
I recently got att uverse with an IPN330hd stb but have only just now got around to setting it up with myth. I found a thread with a working config file for blasting the stb.

Using an MCE remote with 2 blaster ports, I was able to update the lircd.conf entries and 'irsend -d /dev/lircd SEND_ONCE att POWER' to turn the box on and off while 'irsend -d /dev/lircd SEND_ONCE att SEVEN' will change to channel 7.

However, I am having problems getting a channel change script setup with livetv. When using my old stb channel change script, livetv starts correctly, but obviously channels do not change:
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

Livetv fails to start with a 'GetEntryAt(-1) failed.' error similar to what is described in this thread: [http://www.gossamer-threads.com/list...v/users/356905](http://www.gossamer-threads.com/list...v/users/356905)

Changing back to the old config and changing the remote name to att causes live tv to start but does not change channels and brings up the add channel to favourites tab (because of the ENTER command instead of OK). As suggested in the linked thread, I tried changing the new script's sleep times in a range from 0.2 to 2, but Livetv still fails to start with the same error.

Any suggestions? Or could someone help me with the perl syntax to get an OK press before channel changes? Thanks!

---

### Post by ian dobson on 2010-08-10
Hi,

Maybe try increasing the delays (sleep) abit. Also increase the tuning timeout in myth-setup.

I use an external (ethernet) tuner and had to increase the tuner timeout to almost 5 seconds as the channel change script takes a long time to switch channels (wget page).

Regards
Ian Dobson

---

### Post by Lepy on 2010-08-10
Found my answer on this thread: [http://ubuntuforums.org/showthread.php?t=1439174](http://ubuntuforums.org/showthread.php?t=1439174)

> sudo -u mythtv /home/xbmc/scripts/change-channel-lirc-ipn330hd.sh
[sudo] password for xbmc: 
irsend: command failed: SEND_ONCE att select
irsend: unknown command: "select"
irsend: command failed: SEND_ONCE att select
irsend: unknown command: "select"


So, I changed my script to read:
> :~/scripts$ cat change-channel-lirc-ipn330hd.sh
 #!/bin/sh
REMOTE_NAME=att
irsend SET_TRANSMITTERS 1 #this is the plug on the left when looking at the back of IR receiver, 2 is the other one
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME OK
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME OK

LiveTV started, but channels still did not change. I fixed this by editing the file referenced in /etc/lirc/lircd.conf. The channel script was expecting digits, but the remote config file referenced the the number 1 as ONE.

Anyway, seems to be working! Solved and thanks.

---

