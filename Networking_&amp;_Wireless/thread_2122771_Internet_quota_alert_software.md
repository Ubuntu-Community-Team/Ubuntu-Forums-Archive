---
title: "Internet quota alert software?"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by sirgad on 2013-03-06
I'm setting up a Ubuntu-based laptop between my modem and my router.  It'll serve a number of duties but the most important one is alerting me automatically by email when I'm approaching my ISP's fair usage limits.

Unfortunately, those fair usage limits are measured over various periods throughout the day, and the software I've found so far only alerts to *daily* usage limits or longer.  I need to measure, and receive alerts for, internet _downloads_ during the following periods daily:

1) 10am - 3pm

2) 5pm - 10pm

I also need to measure just _upload_ traffic for one additional period:

3) 3pm - 8pm

Each of those periods has its own fair use limit.  Fair use limits do not carry forward.

If I breach the fair use limits for either of the _download_ periods, I get hit with a 50% download slowdown for 5 hours; if I breach the _upload_ limit, it's a 75% upload slowdown for 5 hours!

The laptop running this software will be performing some small internet-related tasks itself (eg. NTP) so its activity needs to be included in totals, but the bulk of my internet bandwidth is used streaming audio and video from 4oD, iPlayer, TV Catchup and so on.

Is there anything out there that's able to do this?

---

### Post by albandy on 2013-03-06
Try with something similar to my script:
```

#! /bin/sh
#you have to add this script to crontab
#install sendemail: sudo apt-get install sendemail
IFACE=br1 #here you have to put your internet iface
PREVIOUS_RX=/tmp/rx.txt
PREVIOUS_TX=/tmp/tx.txt

DATA_TXRX=$(ifconfig $IFACE | grep "Bytes RX:")
RX=$(echo $DATA_TXRX | cut -f 2 -d ':' | cut -f '1' -d '(')
TX=$(echo $DATA_TXRX | cut -f 3 -d ':' | cut -f '1' -d '(')
PRE_RX=$(cat $PREVIOUS_RX)
PRE_TX=$(cat $PREVIOUS_TX)

TOTAL_RX=$(expr $RX - $PRE_RX)
TOTAL_TX=$(expr $TX - $PRE_TX)
TOTAL_RXTX=$(expr $TOTAL_RX + $TOTAL_TX)


echo $RX > $PREVIOUS_RX
echo $TX > $PREVIOUS_TX

sendEmail -f youremail@gmail.com -t youremail@gmail.com -u Internet data usage -m "RX: $TOTAL_RX, TX: $TOTAL_TX, RX+TX: $TOTAL_RXTX" -s smtp.gmail.com -o tls=yes -xu yourgmailuser -xp yourgmailpassword

```

---

### Post by sirgad on 2013-03-07
Thanks for replying.

Would you mind telling me what this actually does?  I'm not familiar with rx.txt and tx.txt.  I'm assuming they keep logs regarding input and output, but do they log actual quantity of data, or simply the number of packets?

The reason I ask is that further research on this matter has shown it to be one that is resource-hungry and typically carried out by specialised hardware - that is, if you want it to be accurate.  I actually browsed to my thread with the aim of closing it when I saw your response.

Ta :)

---

### Post by bellaseem on 2013-03-07
The way I do it is silly but effective... Using system monitor (in the resources tab, at the bottom (Network History) it shows the total received and sent data in MiB....

---

### Post by albandy on 2013-03-08
> **sirgad said:**
> Thanks for replying.

Would you mind telling me what this actually does?  I'm not familiar with rx.txt and tx.txt.  I'm assuming they keep logs regarding input and output, but do they log actual quantity of data, or simply the number of packets?

The reason I ask is that further research on this matter has shown it to be one that is resource-hungry and typically carried out by specialised hardware - that is, if you want it to be accurate.  I actually browsed to my thread with the aim of closing it when I saw your response.

Ta :)

See my explanation video: [http://www.youtube.com/watch?v=4oL7WYDAKRY](http://www.youtube.com/watch?v=4oL7WYDAKRY)

---

### Post by schragge on 2013-03-08
@**albandy**
On my system (Debian wheezy) the output of *ifconfig* doesn't contain [COLOR=red]Bytes RX:[/COLOR].  That line reads [COLOR=red]RX bytes:[/COLOR] instead. I guess it depends on your locale (mine is en_US.UTF-8). So, I decided to rewrite your script slightly:
```

#!/bin/sh
# you have to add this script to crontab
# install sendemail: sudo apt-get install sendemail
IFACE=br1 #here you have to put your internet iface
IFACE_STAT=/proc/net/dev
PREVIOUS_RXTX=/var/tmp/rxtx.txt

# The best option is to use ifdata from moreutils:
# sudo apt-get install moreutils
#RX=$(ifdata -sib $IFACE) TX=$(ifdata -sob $IFACE)

# Alternatively, parse /proc/net/dev with awk
<<! read RX TX
    $(awk /$IFACE:/'{print  $2, $10}' $IFACE_STAT)
!

test -r "$PREVIOUS_RXTX" && read PRE_RX PRE_TX <"$PREVIOUS_RXTX"

TOTAL_RX=$((RX-PRE_RX))
TOTAL_TX=$((TX-PRE_TX))
TOTAL_RXTX=$((TOTAL_RX+TOTAL_TX))

echo $RX $TX >"$PREVIOUS_RXTX"

sendEmail \
        -f youremail@gmail.com \
        -t youremail@gmail.com \
        -u Internet data usage \
        -m "RX: $TOTAL_RX, TX: $TOTAL_TX, RX+TX: $TOTAL_RXTX" \
        -s smtp.gmail.com -o tls=yes -xu yourgmailuser -xp yourgmailpassword

```
I also combined *rx.txt* and *tx.txt* into *rxtx.txt*, and changed its location to */var/tmp* to guarantee data persistence over reboots.

---

